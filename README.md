# PyBlack_Jack

Blackjack is the most widely played casino banking game in the world. The game is played with decks of 52 cards and is an American descendant
of a global family of banking games known as Twenty-One. This family of card games also includes the British game of Pontoon and the
European game, Vingt-et-Un.

## Program

    import random
    import os
    import art 

    def dealercard():
      cards=[11,1,2,3,4,5,6,7,8,9,10]
      dcard = random.choice(cards)
      return dcard

    def calculatecard(cards):
      if sum(cards)==21 and len(cards)==2:
        return 0
      if 11 in cards and sum(cards)>21:
        cards.remove(11)
        cards.append(1)
      return sum(cards)

    def compare(userscore,comscore):
      if (userscore ==0 and comscore ==0) or userscore==comscore:
        print("Draw")
      elif userscore ==0 or comscore>21:
        print("You win, BlackJack")
      elif comscore == 0 or comscore>userscore:
        print("You lost")
      elif userscore>21:
        print("Bust")
      elif comscore>21:
        print("You win")
      elif comscore>userscore:
        print("You lost")
      else:
        print("You Win")


    def play():
      usercard=[]
      comcard =[]
      gameover =False
      print(art.logo)
      for _ in range(2):
        usercard.append(dealercard())
        comcard.append(dealercard())

      while not gameover:
        userscore = calculatecard(usercard)
        comscore = calculatecard(comcard)
        print(f"Your cards are: {usercard}\nSum: {userscore}\n ")
        print(f"Computer card: {comcard[0]}\n")
        if userscore==0 or comscore ==0 or userscore > 21:
          gameover=True
        else:
          continu = input("Get another card 'y or 'n' : ")
          if continu=="y":
            usercard.append(dealercard())
          else:
            gameover = True

      while comscore!=0 and comscore<17:
          comcard.append(dealercard())
          comscore=calculatecard(comcard)

      print(f"Computer hand: {comcard}, Computer Score: {comscore}")    
      compare(userscore,comscore)

    while input("Do you want to play a game of Blackjack? Type 'y' or 'n': ") == "y":
      os.system('clear')
      play()
      
## Output


    .------.            _     _            _    _            _    
    |A_  _ |.          | |   | |          | |  (_)          | |   
    |( \/ ).-----.     | |__ | | __ _  ___| | ___  __ _  ___| | __
    | \  /|K /\  |     | '_ \| |/ _` |/ __| |/ / |/ _` |/ __| |/ /
    |  \/ | /  \ |     | |_) | | (_| | (__|   <| | (_| | (__|   < 
    `-----| \  / |     |_.__/|_|\__,_|\___|_|\_\ |\__,_|\___|_|\_\
          |  \/ K|                            _/ |                
          `------'                           |__/           

    Your cards are: [9, 6]
    Sum: 15

    Computer card: 2

    Get another card 'y or 'n' : y
    Your cards are: [9, 6, 10]
    Sum: 25

    Computer card: 2

    Computer hand: [2, 7, 10], Computer Score: 19
    Bust
    Do you want to play a game of Blackjack? Type 'y' or 'n':
