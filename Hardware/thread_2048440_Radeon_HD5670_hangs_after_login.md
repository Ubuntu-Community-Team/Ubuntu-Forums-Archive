---
title: "Radeon HD5670 hangs after login"
date: 2012-08-26
forum: Hardware
---

### Post by pKaresz on 2012-08-26
Hello!
Thanks in advance for your advices.

I installed, Ubuntu 12.04 today, on my PC with a Radeon hd5670 graphics card. The first error I encountered, (just like the first time Unity came out - after witch I waited to try Ubuntu again until now) is, that it hanged after login at the desktop wallpaper, with only the mouse cursor. Well actually the first problem was with the live CD, but I managed to install it, using the install now, not the try now. Live CD has the same problem, as after install. 
So, after installing and getting the error, I searched of course before asking this:) 
I found this: [http://askubuntu.com/questions/120096/ubuntu-hangs-at-purple-screen](http://askubuntu.com/questions/120096/ubuntu-hangs-at-purple-screen)

The accepted answer there helped me to get to this. (note, that the below picture is a screen taken from a working desktop, and then erased the parts that don't show on mine.)
[http://i.stack.imgur.com/ik5Qs.png](http://i.stack.imgur.com/ik5Qs.png)

Note that there is nothing at the top except the brown bar. No shutdown button, no nothing. The system hangs, I can't click on anything, I can only wiggle around with my mouse XD

---

### Post by pKaresz on 2012-08-30
So I continued my research. 

  For testing purposes I've installed gnome3 from the console. After  that I've noticed a mistake I've made. I've forgotten to test the Ubuntu  2D desktop enviroment.
  So I did it quick, and Ubuntu 2D works perfect. Then I've tried  gnome. Gnome3 and Gnome classic do the same thing as the Unity desktop.  Namely freeze. So I've tried Gnome classis(no effects) and of course,  that works. 

  So conclusion:  Unity/Gnome/Gnome Classic - produce the same problem Unity 2D/Gnome Classic (no effects) - work flawless

  Then I've decided to reinstall my ati drivers using: [What is the correct way to install ATI Catalyst Video Drivers?]("http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers") The outcome remained the same.
  Of course I've confirmed if the drivers were working using: "fglrxinfo" And they are working. Then I've decided to try out some games. And the outcome: the games work 100% no problem. 

  At this point I'm done with trying, and accepted the fact, that this is the best thing I can get, at this point in time.


  Final thoughts.
  The first time Unity came out, the problem stuck at the drivers. No  games would work, all would freeze. Only Gnome classic (no effects)  worked at that time. I'm happy to see, that this is some form of  improvemen. Because altough I can't use the defauld desktop, I can use  Ubuntu the way I want, well at least to this point in time. Video card  demanding thigs seem to work correctly, desktop is usable. The problem I  have is, that in this state Ubuntu isn't as user friendly as it wants  to be. You can't give somebody an Install disk and rest easy, because  you know, that there will be something wrong. In my opinion, Ubuntu  takes steps forward, but unfortunately it also takes steps backward.  Well the final test will of course be, steam and Left 4 Dead 2, if it  really comes out. 


  Thank you for your time.

---

