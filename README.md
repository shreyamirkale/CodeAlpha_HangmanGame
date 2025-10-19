# CodeAlpha_HangmanGame
#✅ TASK 1: Hangman Game Goal: Create a simple text-based Hangman game where the player guesses a word one letter at a time.
import random

words = ["python", "hangman", "computer", "programming", "developer"]
secret = random.choice(words).lower()
display = ['_'] * len(secret)
guessed = set()
wrong = 0
max_wrong = 6

print("Hangman! Guess the word (", len(secret), "letters).")

while wrong < max_wrong and '_' in display:
    print(' '.join(display), "| Guessed:", ', '.join(sorted(guessed)) if guessed else 'None', "| Left:", max_wrong - wrong)
    guess = input("Letter: ").lower().strip()
    
    if len(guess) != 1 or not guess.isalpha() or guess in guessed:
        print("Invalid guess.")
        continue
    
    guessed.add(guess)
    
    if guess in secret:
        for i in range(len(secret)):
            if secret[i] == guess:
                display[i] = guess
        print("Correct!")
    else:
        wrong += 1
        print("Wrong!")

print("\nGame over!")
if '_' not in display:
    print("You win! Word:", secret)
else:
    print("You lose! Word:", secret)
