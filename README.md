# AI-Study-Guide-Generator-
AI Study Guide Generator for a College Subject  

# ==========================================================
c# ==========================================================

import textwrap
from datetime import datetime

# ----------------------------------------------------------
# 1. Display welcome message
# ----------------------------------------------------------

def welcome():
    print("=" * 60)
    print("       AI STUDY GUIDE GENERATOR")
    print("          For College Students")
    print("=" * 60)
    print("Generate study notes, questions, quizzes and study plans.")
    print()


# ----------------------------------------------------------
# 2. Generate study notes
# ----------------------------------------------------------

def generate_notes(subject, topic):
    notes = f"""
STUDY NOTES
-----------
Subject: {subject}
Topic: {topic}

1. Introduction
{topic} is an important topic in the subject of {subject}.
It helps students understand the basic concepts and principles.

2. Basic Concepts
- Understand the definition of {topic}.
- Learn its important terms and concepts.
- Study the main components and working principles.
- Understand the advantages and limitations.

3. Applications
- Used in academic learning and research.
- Helps solve practical problems.
- Can be applied in real-world situations.
- Supports further learning in {subject}.

4. Advantages
- Improves subject knowledge.
- Helps develop problem-solving skills.
- Supports examination preparation.

5. Limitations
- Requires regular practice.
- Some concepts may be difficult initially.
- Practical examples may be needed for better understanding.

6. Conclusion
Learning {topic} helps students improve their knowledge of
{subject}. Regular revision and practice are recommended.
"""
    return notes


# ----------------------------------------------------------
# 3. Generate important questions
# ----------------------------------------------------------

def generate_questions(subject, topic):
    questions = [
        f"1. Define {topic}.",
        f"2. Explain the basic concepts of {topic}.",
        f"3. Describe the working principles of {topic}.",
        f"4. Explain the applications of {topic}.",
        f"5. Discuss the advantages of {topic}.",
        f"6. What are the limitations of {topic}?",
        f"7. Explain {topic} with a suitable example.",
        f"8. Draw and explain the architecture of {topic}, if applicable.",
        f"9. Compare the important types of {topic}, if applicable.",
        f"10. Write a short note on {topic}."
    ]

    print("\nIMPORTANT QUESTIONS")
    print("-" * 40)
    for question in questions:
        print(question)

    return questions


# ----------------------------------------------------------
# 4. Generate a study timetable
# ----------------------------------------------------------

def generate_timetable(days, topic):
    print("\nPERSONALIZED STUDY TIMETABLE")
    print("-" * 40)

    for day in range(1, days + 1):
        if day == 1:
            task = f"Study the introduction and definition of {topic}"
        elif day == days:
            task = f"Revise {topic} and practise questions"
        elif day % 3 == 0:
            task = f"Practise examples and test your knowledge of {topic}"
        else:
            task = f"Study detailed concepts and applications of {topic}"

        print(f"Day {day}: {task}")


# ----------------------------------------------------------
# 5. Generate revision tips
# ----------------------------------------------------------

def revision_tips():
    tips = [
        "Study for 25-30 minutes, then take a short break.",
        "Write short notes using your own words.",
        "Practise diagrams and important definitions.",
        "Solve previous examination questions.",
        "Revise difficult topics more frequently.",
        "Test yourself without looking at your notes.",
        "Get sufficient sleep before the examination."
    ]

    print("\nREVISION TIPS")
    print("-" * 40)

    for number, tip in enumerate(tips, start=1):
        print(f"{number}. {tip}")

    return tips


# ----------------------------------------------------------
# 6. Simple multiple-choice quiz
# ----------------------------------------------------------

def conduct_quiz(topic):
    quiz = [
        {
            "question": f"What should you learn first when studying {topic}?",
            "options": [
                "A. Basic definition",
                "B. Only advanced topics",
                "C. Ignore the fundamentals",
                "D. Nothing"
            ],
            "answer": "A"
        },
        {
            "question": "Which method helps improve understanding?",
            "options": [
                "A. Avoiding practice",
                "B. Regular revision",
                "C. Skipping all examples",
                "D. Never testing yourself"
            ],
            "answer": "B"
        },
        {
            "question": "Why should students practise questions?",
            "options": [
                "A. To avoid learning",
                "B. To forget concepts",
                "C. To check understanding",
                "D. To waste time"
            ],
            "answer": "C"
        }
    ]

    score = 0

    print("\nKNOWLEDGE QUIZ")
    print("-" * 40)
    print("Enter A, B, C or D.")

    for item in quiz:
        print("\n" + item["question"])

        for option in item["options"]:
            print(option)

        answer = input("Your answer: ").strip().upper()

        if answer == item["answer"]:
            print("Correct answer!")
            score += 1
        else:
            print("Incorrect.")
            print("Correct answer:", item["answer"])

    print(f"\nYour score: {score}/{len(quiz)}")
    percentage = score / len(quiz) * 100
    print(f"Percentage: {percentage:.1f}%")

    if percentage >= 80:
        print("Excellent work!")
    elif percentage >= 50:
        print("Good effort. Revise the topic again.")
    else:
        print("Keep practising and try again.")

    return score, len(quiz)


# ----------------------------------------------------------
# 7. Save study guide to a text file
# ----------------------------------------------------------

def save_guide(subject, topic, notes, questions, days):
    filename = "study_guide.txt"

    with open(filename, "w", encoding="utf-8") as file:
        file.write("=" * 50 + "\n")
        file.write("AI STUDY GUIDE GENERATOR\n")
        file.write("=" * 50 + "\n")
        file.write(f"Generated on: {datetime.now()}\n")
        file.write(f"Subject: {subject}\n")
        file.write(f"Topic: {topic}\n")
        file.write(f"Preparation days: {days}\n\n")

        file.write(notes)
        file.write("\n\nIMPORTANT QUESTIONS\n")
        file.write("-" * 30 + "\n")

        for question in questions:
            file.write(question + "\n")

        file.write("\nSTUDY TIMETABLE\n")
        file.write("-" * 30 + "\n")

        for day in range(1, days + 1):
            file.write(f"Day {day}: Study and revise {topic}\n")

        file.write("\nStudy regularly and practise questions.\n")

    print(f"\nStudy guide saved successfully as '{filename}'.")


# ----------------------------------------------------------
# 8. Display the main menu
# ----------------------------------------------------------

def main():
    welcome()

    subject = input("Enter your college subject: ").strip()
    topic = input("Enter the topic to study: ").strip()

    if not subject or not topic:
        print("Error: Subject and topic cannot be empty.")
        return

    while True:
        try:
            days = int(input("Enter number of preparation days: "))
            if days > 0:
                break
            print("Enter a number greater than zero.")
        except ValueError:
            print("Please enter a valid whole number.")

    notes = generate_notes(subject, topic)
    questions = [
        f"Define {topic}.",
        f"Explain the concepts of {topic}.",
        f"Describe the applications of {topic}.",
        f"Discuss the advantages and limitations of {topic}.",
        f"Explain {topic} with an example."
    ]

    while True:
        print("\n" + "=" * 45)
        print("MAIN MENU")
        print("=" * 45)
        print("1. Generate study notes")
        print("2. Generate important questions")
        print("3. Generate study timetable")
        print("4. Display revision tips")
        print("5. Take a knowledge quiz")
        print("6. Save study guide to a file")
        print("7. Exit")

        choice = input("\nEnter your choice (1-7): ").strip()

        if choice == "1":
            print(notes)

        elif choice == "2":
            generate_questions(subject, topic)

        elif choice == "3":
            generate_timetable(days, topic)

        elif choice == "4":
            revision_tips()

        elif choice == "5":
            conduct_quiz(topic)

        elif choice == "6":
            save_guide(subject, topic, notes, questions, days)

        elif choice == "7":
            print("Thank you for using the Study Guide Generator!")
            break

        else:
            print("Invalid choice. Please enter a number from 1 to 7.")


# ----------------------------------------------------------
# 9. Run the project
# ----------------------------------------------------------

if __name__ == "__main__":
    main()
============================================================
       AI STUDY GUIDE GENERATOR
          For College Students
============================================================
Generate study notes, questions, quizzes and study plans.


=============================================
MAIN MENU
=============================================
1. Generate study notes
2. Generate important questions
3. Generate study timetable
4. Display revision tips
5. Take a knowledge quiz
6. Save study guide to a file
7. Exit
Invalid choice. Please enter a number from 1 to 7.

=============================================
MAIN MENU
=============================================
1. Generate study notes
2. Generate important questions
3. Generate study timetable
4. Display revision tips
5. Take a knowledge quiz
6. Save study guide to a file
7. Exit
Invalid choice. Please enter a number from 1 to 7.

=============================================
MAIN MENU
=============================================
1. Generate study notes
2. Generate important questions
3. Generate study timetable
4. Display revision tips
5. Take a knowledge quiz
6. Save study guide to a file
7. Exit
Invalid choice. Please enter a number from 1 to 7.

=============================================
MAIN MENU
=============================================
1. Generate study notes
2. Generate important questions
3. Generate study timetable
4. Display revision tips
5. Take a knowledge quiz
6. Save study guide to a file
7. Exit
Invalid choice. Please enter a number from 1 to 7.

=============================================
MAIN MENU
=============================================
1. Generate study notes
2. Generate important questions
3. Generate study timetable
4. Display revision tips
5. Take a knowledge quiz
6. Save study guide to a file
7. Exit

Enter your choice (1-7): 04
Invalid choice. Please enter a number from 1 to 7.

=============================================
MAIN MENU
=============================================
1. Generate study notes
2. Generate important questions
3. Generate study timetable
4. Display revision tips
5. Take a knowledge quiz
6. Save study guide to a file
7. Exit
