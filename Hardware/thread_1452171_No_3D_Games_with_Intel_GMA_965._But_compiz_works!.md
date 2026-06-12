---
title: "No 3D Games with Intel GMA 965. But compiz works!?"
date: 2010-04-11
forum: Hardware
---

### Post by NT2015 on 2010-04-11
Just as the title says, I cannot play any 3D games using the Intel GMA 965 video card. My compiz effects work beautifully. glxgears works just fine. but, so far none of the games ive tried to run in wine work. I have tried World of Warcraft, and Battlezone II, and neither will run on my laptop with the  GMA965:confused:, but both run beautifully on my desktop with a GeForce 7900 GS though:P. 


I have searched high and low and just cant find anything on this issue. As a matter of fact most of what I found was people who couldn't get the card working at all... 

I can post a terminal output if it will help, but there didn't really seem to be anything important in there so i figured i would only post it if someone wanted it.

I am running 9.10

---

### Post by NT2015 on 2010-04-17
BUMPification.

---

### Post by dragonboss on 2010-04-17
The games you're trying to run are not linux native?

---

### Post by NT2015 on 2010-04-17
no there not linux native, I run them through wine. But both of these games have a gold rating on the wineHQ, and they both run absolutely perfect on my desktop computer, which has a GeForce 7900 GS. it seems to only be computers with Intel graphics that dont work.

---

### Post by dragonboss on 2010-04-17
Have you tried any linux native games to see if the graphics problem is only from wine?

---

### Post by NT2015 on 2010-04-23
Sorry , it took me so long to respond. But I did try a native linux game. I got TuxKart from the software center, and it ran. Although it ran Horribly horribly slow, and choppy. Theres got to be a better driver for this card out there.

---

### Post by NT2015 on 2010-08-12
I know this is a old thread but....I gotta bump it since my desktop blew up, and now im stuck with nothing but my laptop. :(

---

### Post by 3Miro on 2010-08-12
Can you play any games at all or just newer ones. I can play older games on my laptop with Intel video (Diablo II, Starcraft, Zeus). The only newer game that I ever tries was Sims 3, I got everything working except for the text. Here is the comment that I posted on winehq forums, it took some time for someone to give me an advice and I haven't tested it.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664)

---

### Post by Yellow Pasque on 2010-08-12
Tried turning off desktop effects when running a game? Tried newer driver/mesa from xorg-edgers PPA?

---

### Post by NT2015 on 2010-08-12
> **Temüjin said:**
> Tried turning off desktop effects when running a game? Tried newer driver/mesa from xorg-edgers PPA?

I have tried turning off desktop effects, it made no noticeable difference. What is xorg-edgers PPA? and what would I look for? 

Sorry to sound like such a noob, but I've always had nVidia cards so I've never had to deal with this before.

---

### Post by NT2015 on 2010-08-13
Ok, so I have no idea how, but it just started working when I updated to 10.04! The game I was trying to get working was WOW, im not a huge fan, but its a really fun way to keep in contact with friends that have moved. 

Anyway, so the game runs now, but it is running with 16-bit color(even though it says 24), and I get about 5FPS. But it ran like crap in windows too. The Intel 965 is a huge POS!

I did some research on that PPA, I still have no clue what it is, if someone could tell me about that?

---

### Post by Marcelo Ruiz on 2010-08-14
I guess you have an hybrid graphics card, so you need to complain to nVidia... as we all do.
You can try by downloading Kernel 2.6.35-12 which has vga_switcheroo (you can also download Ubuntu Control Center 0.5 Beta which has a GUI to switch between the graphic cards).
I hope this helps you!

---

