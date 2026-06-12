---
title: "Wireless launcher missing!"
date: 2008-11-25
forum: General Help
---

### Post by Zamfire on 2008-11-25
Alright, so this is my first time to even get on here, let alone post a thread. Now I have already looked around for an answer and I am stumped. 

This is my problem:

You know the application in the upper right hand corner of the screen that lets you know how well you are connected to wireless routers, it also allows you to choose to disable wireless or networks in general? and it allows you to choose from the detected routers in the area. You know, the wireless app that has 4 bars on it that looks like a cellphone connection thing. 

Yea, well i lost it. Its not that i lost it, its just that i cant get it back up. i accidently chose "remove from panel" and now its gone! i have no idea how to get it back, i even did a search for all things with the name of wireless on my computer with no luck. How do i fix this?

---

### Post by Zamfire on 2008-11-26
cant anyone help me please? im desperate! i need to connect to my router! right now im connected to the guys next door and the connection is terrible! thats why i need to change it! please someone

---

### Post by CholericKoala on 2008-11-26
nm-applet 

then sudo /etc/init.d/NetworkManager restart

---

### Post by Zamfire on 2008-11-26
Thank you for trying to help me, but im so new i dont know what that means. 

perhaps i have to go to the terminal here?

well i did, except i typed what you wrote and nothing happened.

look im sorry for being a pain, but i dont know what to do, and i know this is probably annoying, but can someone just please walk me through this?

i mean what are the forums for if people cant help people right? this is really frustrating! i mean i really like Ubuntu, but what am i supposed to do if i feel like an idiot because i cant do something so simple as to look at my wireless internet connection.? it should be right there. but its not! 

i mean, do i have to be a computer genius to even use Ubuntu? this isn't my first problem iv had, i just dont know how to fix the other ones, and now a serious issue has come up and i have been spending hours trying to do something that i feel isnt possible for someone who doesnt know code...

am i the only one so frustrated? if i am ill just put ubuntu in the past and go back to windows. since im obviosly too stupid to even use it. sorry to rant people but what do new users do here? suffer?

---

### Post by CholericKoala on 2008-11-26
in the terminal, when you type nm-applet, nothing happens?

That is strange.
Typing "nm-applet" in the terminal will start your network manager applet, which is the applet in the top panel you are describing.

Typing this in terminal will restart your network manager.
sudo /etc/init.d/NetworkManager restart

---

### Post by spandon on 2008-11-26
Hi Zamfire,
Right click on top panel.
from drop down menu - select +add to panel.
from drop down menu - select network monitor.
click on add.
the network monitor should now be displayed again.
hope that helps?
Don

---

### Post by CholericKoala on 2008-11-26
> **spandon said:**
> Hi Zamfire,
Right click on top panel.
from drop down menu - select +add to panel.
from drop down menu - select network monitor.
click on add.
the network monitor should now be displayed again.
hope that helps?
Don

He is looking for the applet that displays the connection and allows you to choose your wifi connection.

---

### Post by Zamfire on 2008-11-27
hi- thank you for your help, but it seems im running into problem after problem. for instance, i opened my terminal, and typed in help and nothing happened. i typed in sudo and nothing happaned, infact i typed a bunch of random stuff and nothing happened either. i dont really know what to do, maybe i should transfer all the stuff i want onto an external hdd and start from scratch?

---

### Post by Zamfire on 2008-11-28
i seem to have fixed this issue. it was actually simple, but was impossible to tell where to find it, so ill tell anyone who reads this now. 

when you right click on the panel, and select add to panel you see a long list of things to add, well you would think its easier to find, but its not. the app is called "notification center" its completly generic so impossible to tell until you have added all apps to your panel.

i think this should be worked on in the next ubuntu, it was silly and something very easy to find, but impossible for someone who has never done it before. atleast ubuntu could have some form of undo button or something, so if we delete an app by mistake - and its easy to do - then it would go right back the way it was. simple as that. well thanks for the help guys, its much appreciated.

---

