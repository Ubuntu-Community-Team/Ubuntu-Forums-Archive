---
title: "laptop install freezes up and other problems"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by Balidey on 2009-05-21
Hi, firstly some background. I have an old P4 desktop PC running Mythbuntu 8.10 (but with mythtv turned off as I am not yet ready to connect it to the TV) so basically I am used to running Ubuntu 8.10 and installed it with no problems and have been using it with no problems, so I am (was) a happy Ubuntu user.

I now have a laptop I wanted to install Ubuntu on. Its a Fujitsu Siemens Amilo Pro V2055. Its got a new 160gb HDD now, that was clean with no OS on it. I originally tried to use my Mythbuntu 8.10 install CD that worked on my desktop, but after the language screen the install screen was larger than the size of the laptop screen, so the 'back' 'cancel' and 'next' buttons were not visible, they were off the bottom right hand of the screen. And the mouse pad was (nearly) working as there was no cursor visible, I could just see things highlight as the cursor went over them. So after a brief atempt using tabs and enters I gave up and got a CD of 9.04 to try.

Now if I try to install 9.04 I get the cursor on the screen, but the 'next' buttons are still off the screen, but if I boot up with reduced graphics the buttons are on the screen.

So now I try to install, I get the set location screen, then the partition screen (using whole disc to install), the username screen and then install begins, but it always freezes at about 25%. The mouse does not respond, the CD stops spinning.

If I shut down and try again its the same, must have tried a dozen times, often leaving it for an hour to see if it starts up again, but it doesn't

I can boot from the cd, and I get a desktop, but again the screen is missing the right hand inch or so. I am not sure what the top right hand icons are. I think one of them must have the quit or shutdown option as I can not see it on the other pull down menus (where it was on 8.10). So I have to shut down by powering off.

And on the desktop I have the install icon and when I use it, again it will move the install window offcentre so I can not see the buttons and it freezes up about 25 to 30% everytime.

Also from the live cd I have tried altering my laptop screen size to get the entire window visible, but every time I try and adjust the resolution the screen splits and goes fuzzy and I can't then see the desktop so I have to shut down again. The monitor is 'unknown'.

So its almost working, I have tried all the install options from the F6 menu, but no matter what I do I can't get beyond the 25% install.

I have not tried to install 9.04 on my desktop, its stable so I'm leaving it until I get the laptop working. I have checked the CD and its fine, I have scanned my HDD and its fine.

Any ideas what to try? I don't have the laptop with me now, but any suggestions I can try out tonight? I have not tried anything in the console as I am not used to using it, as all my other installs have all been done using the GUI, so if I need to do any sudo commands then please let me know where to open the console (ie get a desktop off the cd first, or before install after the language screen).
Thanks,
Steve

---

### Post by Balidey on 2009-05-28
Just incase anyone has similar problems to these I have now sorted all my issues.

1: Tried using DVD instead of CD, made no difference.
2: Tried new HDD. The original one, even though scans showed it as fine, refused to let me install on it. So new (new to me) HDD and ubuntu installed straight away.

3: But I still had issues with the screen being off centre. So with some help of a friend we managed to remove the default screen size in the VI editor and force in the correct size. For some reason the resolution was about 1600 instead of 1200 so all the right hand side of the screen was off the edge.

But all sorted now.

---

