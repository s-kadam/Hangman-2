/*
Hangman2.java
* Author: Shubham Kadam
* Submission Date: March 17, 2017 *
* Purpose: This is a hangman game which selects a random word and asks the user to guess letters in the word.
* The following code represents my own work. I have neither
* received nor given inappropriate assistance. I have not copied
* or modified code from any source other than the course webpage
* or the course textbook. I recognize that any unauthorized
* assistance or plagiarism will be handled in accordance with
* the University of Georgia's Academic Honesty Policy and the
* policies of this course. I recognize that my work is based
* on an assignment created by the Department of Computer
* Science at the University of Georgia. Any publishing
* or posting of source code for this project is strictly
* prohibited unless you have written consent from the Department
* of Computer Science at the University of Georgia. */
import java.util.Scanner;
public class Hangman2 {
	
	private static final boolean testingMode = true;
	
	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		
		int count = 20;
		
		// the entire game in a loop
		
		while (count > 0){
			
			// declaring and initializing variables
			
			int GuessesRemaining;
			int SpacesToGuess;
			int indexcheck = 0;
			int correctletters;
			String difficulty;
			String hiddenword = "";
			String newhiddenword = "";
			String guess;
			String secretword = RandomWord.newWord();
			String spaces;
			
			// beginning of game, choosing difficulty
			
			System.out.println("Enter your difficulty: Easy (e), Intermediate (i), or Hard(h)");
			difficulty = input.nextLine();
			difficulty = difficulty.substring(0,1);
				
			if (difficulty.equalsIgnoreCase("e"))
			{
				GuessesRemaining = 15;
				SpacesToGuess = 4;	
			}
			else if (difficulty.equalsIgnoreCase("i"))
			{
				GuessesRemaining = 12;					
				SpacesToGuess = 3;					
			}
			else if (difficulty.equalsIgnoreCase("h"))
			{	
				GuessesRemaining = 10;
				SpacesToGuess = 2;
			}
			else
			{
				System.out.println("Invalid difficulty. Try Again...");
				continue;
			}
				
				// testingMode true or false, to show the secret word or not
				
			if ( testingMode == true)
			{
				System.out.println("The Secret Word is: " + secretword);
					
			}
			
				//Writing out the dashes for hidden word
				
			for( int i = 0; i < secretword.length(); i++)
			{
				hiddenword += "-";
			}
			newhiddenword = hiddenword;	
			
				
			System.out.println("The word is: " + hiddenword);
				
			// the user's guess loop
			while (GuessesRemaining > 0)
			{
				System.out.print("Please enter the letter you want to guess: ");
				
				guess = input.nextLine();
				guess = guess.toLowerCase().trim();
					
					// what happens if the user decides to solve the answer
				if (guess.equalsIgnoreCase("solve"))
				{
					System.out.println("Please solve the answer");
					String answer = input.nextLine();
					
					if (answer.trim().equalsIgnoreCase(secretword))
					{
						System.out.println("You win!");
						System.out.println("You have guessed the word!");
						break;
					}
					else
					{
						GuessesRemaining--;
						System.out.println("That is not the word");
						System.out.println("Guesses Remaining: " + GuessesRemaining);
						continue;
					}
				}
			
				// making sure the user only enters letters, no numbers or characters. Used ASCII table to define the parameters	
				char result = guess.charAt(0);
				if (result > 122 || result < 65 || (result > 90 && result < 97))
				{
					System.out.println("Your input is not valid. Please try again.");
					System.out.println("Guesses Remaining: " + GuessesRemaining);
					continue;
				}
							
						// where the user enters in what spaces they want to check
							
				System.out.println("Please enter your spaces you want to check (separated by spaces)");
						
				spaces = input.nextLine();
						
						/* I figured if I trim the users input, if the enter it correctly, 
						it always has to be the the number of spaces they check times two then minus one.*/
						
				if (spaces.trim().length() != ((SpacesToGuess*2)-1))
				{
					System.out.println("Your input is not valid. Please try again.");
					System.out.println("Guesses Remaining: " + GuessesRemaining);
					continue;
				}
						
						
						
						// calling a new scanner to go through the spaces
					
				Scanner s = new Scanner (spaces);
						
						// the loop that checks the word
				
				correctletters = 0;		
				for (int i = 0; i < SpacesToGuess; i++)
				{
					indexcheck = s.nextInt();
							
					if (indexcheck >= secretword.length())
					{
						break;
					}
					else if (result == secretword.charAt(indexcheck))
					{								
						newhiddenword = newhiddenword.substring(0, indexcheck) + result + newhiddenword.substring(indexcheck+1);
						correctletters++;
					}
								
				}
						
				// whether or not the guesses are correct or not, using the correct letters int
						
				if (indexcheck >= secretword.length())
				{
					System.out.println("Your input is not valid. Please try again");
					System.out.println("Guesses Remaining: " + GuessesRemaining);
					continue;
				}
				
				if (newhiddenword.equalsIgnoreCase(secretword))
				{
					System.out.println("Your guess is in the word!");
					System.out.println("The updatated word is: " + newhiddenword);
					System.out.println("Guesses Remaining: " + GuessesRemaining);
					System.out.println("You have guessed the word! Congratulations!");
					break;
				}
				
				if (correctletters > 0)
				{
					System.out.println("Your guess is in the word!");
					System.out.println("The updatated word is: " + newhiddenword);
					System.out.println("Guesses Remaining: " + GuessesRemaining);
					hiddenword = newhiddenword;
				}
				else
				{
					System.out.println("Your letter was not found in the spaces you provided.");
					GuessesRemaining--;
					System.out.println("Guesses Remaining: " + GuessesRemaining);
				}
						 
					// if the user runs out of guesses
						
				if (GuessesRemaining == 0)
				{
					System.out.println("You have failed to guess the word... :(");
					break;
				}
			}
			
				// do you want to play again?
				
		System.out.println("Do you want to play again? Yes(y) or No(n)");
				
		String playagain = input.nextLine();
		playagain = playagain.substring(0,1);
				
		count--;
			
		if (playagain.equalsIgnoreCase("y"))
		{
			continue;
		}
		else if (playagain.equalsIgnoreCase("n"))
		{
			System.exit(0);
		}
		
	}
		// after twenty games, the program says this
		
	System.out.println("You have played 20 games, shutting down...");
	System.exit(0);
	
	}
}
