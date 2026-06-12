---
title: "Graphic problems with Karmic kernels"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Mayfairy on 2009-11-01
I just upgraded from 9.04 to 9.10 yesterday and Karmic kernels don't seem to go well with my graphics.

At first I got Error 15 with Karmic kernels. I could only boot with my old 2.6.28-13 kernel, but upgrading to Grub2 manually fixed this.

Now the problem is that whenever I choose a Karmic kernel I go to a TTY1 and it asks me for login details. If I could log in like that I could at least look at the problem but my screen is blinking like no tomorrow. Not only is it visual but it doesn't like to accept any key presses at certain times. 
Typing my login name is doable since I can see if it accepts what I type and then try again, but with password there's no indication whether it accepts my presses or not. 

I'm using a Nvidia 9800 GT card and it worked nicely with 9.04 with Compiz and all. Now with Karmic using my old kernel (2.6.28-13) Metacity works nicely but when I try to enable Compiz it gives black background with white window rectangles and while mouse does move I can't Ctrl-Alt-Backspace to login screen. Ctrl-Alt-F1 does work though. 

With Jaunty I had some problems with my monitor refresh rates. I experienced the same blinking I have now but I managed to fix it by manually changing xorg.conf.

EDIT: Partly solved. Changing from 185 nvidia drivers to 173 ("sudo apt-get install nvidia-glx-173" for those a bit ubuntu illiterate). Before that I backed up my xorg.conf just in case (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backed-up-with-original-name-so-I-will-know-it-is-this-and-not-some-other-backup) and rebooted. 

I chose a Karmic kernel 2.6.31.14 and was greeted with the same black screen with flickering cursor. Other tty's at least gave me the terminal login prompt, but after waiting a while it just kicked up the graphical login. I didn't have to do anything. Guess it was trying to automatically find suitable settings. I logged in and everything was fine until it suddenly kicked me back to graphical login. I just logged in and have been logged in since then.

Problem is I still can't enable Compiz. There's been change however. When I enable Compiz through Fusion Icon it eats my window borders. Changing to another Emerald theme doesn't change things. 
When I try to enable desktop effects through Appearance page I get a message that they couldn't be enabled.

'emerald --replace' on terminal doesn't do anything. Reinstalling emerald doesn't help either.

---

