<!DOCTYPE html>
<html>
<head>
  <title>Page Title</title>
</head>
<body>
  <script>

        function computerPlay(user) {
        let choice = ['rock', 'paper', 'scissors'];
        return choice[Math.floor(Math.random() * choice.length)];
        
    }
    
    function playRound(playerSelection, computerSelection) {
        if ((playerSelection == 'rock' && computerSelection == 'scissors') ||
            (playerSelection == 'paper' && computerSelection == 'rock') ||
            (playerSelection == 'scissors' && computerSelection == 'paper')) {
            
            return(`You've won! ${playerSelection} beats ${computerSelection}!`)
        }
        else if ((playerSelection == 'rock' && computerSelection == 'paper') ||
                (playerSelection == 'paper' && computerSelection == 'scissors') ||
                (playerSelection == 'scissors' && computerSelection == 'rock')) {
            
            return(`You've lost! ${computerSelection} beats ${playerSelection}!`)
        }
        else if (playerSelection == computerSelection) {
            return('Draw!');
        }
        else {
            console.log('Invalid option, try again.');
        }
    }

    function game() {

            let playerscore = 0;
            let computerscore = 0;
            let message;

        for (let x = 1; x <= 5; x++) {
            const playerSelection = prompt(`Round ${x}: Rock, paper, or scissors?`).toLowerCase();
            const computerSelection = computerPlay(); 
            let result = playRound(playerSelection, computerSelection);

            if (result.includes('won')) {
                playerscore++;
            }
            else if (result.includes('lost')) {
                computerscore++;
            }
            
            console.log(result);
        }

        message = (playerscore > computerscore) ? 'You win!' :
                    (playerscore < computerscore) ? 'You lose!' :
                      'Draw!';

        return(`Your score: ${playerscore}, Computer Score: ${computerscore}. ${message}`)
    }
    
    
    console.log(game());
