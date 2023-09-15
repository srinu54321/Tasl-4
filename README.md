import tkinter as tk
import random

# Initialize scores
user_score = 0
computer_score = 0

# Function to determine the winner
def determine_winner(user_choice, computer_choice):
    global user_score, computer_score
    if user_choice == computer_choice:
        return "It's a tie!"
    elif (
        (user_choice == "rock" and computer_choice == "scissors")
        or (user_choice == "scissors" and computer_choice == "paper")
        or (user_choice == "paper" and computer_choice == "rock")
    ):
        user_score += 1
        return "You win!"
    else:
        computer_score += 1
        return "Computer wins!"

# Function to handle user's choice
def user_choice(choice):
    computer_choices = ["rock", "paper", "scissors"]
    computer_choice = random.choice(computer_choices)
    result = determine_winner(choice, computer_choice)

    # Update the labels with user and computer choices and the result
    user_label.config(text="Your Choice: " + choice)
    computer_label.config(text="Computer's Choice: " + computer_choice)
    result_label.config(text="Result: " + result)
    score_label.config(text="Score - You: {} Computer: {}".format(user_score, computer_score))

# Create the main window
window = tk.Tk()
window.title("Rock-Paper-Scissors Game")

# Create and configure labels
user_label = tk.Label(window, text="Your Choice:")
computer_label = tk.Label(window, text="Computer's Choice:")
result_label = tk.Label(window, text="Result:")
score_label = tk.Label(window, text="Score - You: 0 Computer: 0")

user_label.pack()
computer_label.pack()
result_label.pack()
score_label.pack()

# Create and configure buttons for user choices
rock_button = tk.Button(window, text="Rock", command=lambda: user_choice("rock"))
paper_button = tk.Button(window, text="Paper", command=lambda: user_choice("paper"))
scissors_button = tk.Button(window, text="Scissors", command=lambda: user_choice("scissors"))

rock_button.pack()
paper_button.pack()
scissors_button.pack()

# Start the Tkinter main loop
window.mainloop()
