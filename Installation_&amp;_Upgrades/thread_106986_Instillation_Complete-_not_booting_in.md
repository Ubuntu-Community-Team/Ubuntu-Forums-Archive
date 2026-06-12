---
title: "Instillation Complete- not booting in"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by mrmoose19 on 2005-12-22
After a long and arduous installation (it's a slow computer.  7 hours.  Woo.), the installation of 5.10, apparently, is almost complete.  The final screen in the "1st" set of blue screens ("Finishing Your Installation") has come and gone, and it's all well and good.  When the machine tries to boot to complete the last minute whatnot, it runs through the "Starting Ubuntu" black DOS-like screen (sorry, lacking the proper/good word for it.), and it gets through all the "OK/FAIL" listings (the last one of which, I think, is setting system clock, or something like that)  When it advances to the next screen...that's it.  It just sits there.  Black screen, no flashing cursor, and the monitor, after a period of activity, turns itself off because there's no input.  When it first advances to this screen, the middle third of the screen horizontally and a small square centered vertically flash in less than a second, then the blackness starts.  Thoughts?

---

### Post by amohanty on 2005-12-22
Can you log into the recovery mode?

---

### Post by az on 2005-12-22
What kind of old machine and what kind of video card.   You probably only have a misconfigured X server (the thing that displays graphics instead of text - an easy fix)

---

### Post by mrmoose19 on 2005-12-22
The computer is a HP Vectra.  Display stuff is integrated directly into the motherboard.  And since I'm new to the whole Ubuntu hardcore usage thing, I don't know how to do much of anything aside from install and play.  Heh heh.

---

### Post by amohanty on 2005-12-22
Can you log into recovery mode. And then at the command prompt type:

> startx

post any errors that come up.

---

### Post by mrmoose19 on 2005-12-22
When I boot into recovery mode, everything goes smoothly, and I get to the root@#ubuntu prompt.  Typed in "startx," and the computer started responding.  It printed about 8-10 lines of text before advancing to the next screen...where the monitor promptly shut off/went into standby again due to lack of something.  I can hear the hard drive et al still spinning, so it's not like that died.  Yet.  Heh heh.

---

### Post by az on 2005-12-22
Boot into recovery mode and run

dpkg-reconfigure xserver-xorg

What video driver is the default?  Try setting it to vesa.  Try setting the resolution to 800x600 (monitor section, pick medium instread of advanced) (You will know what I mean)

when you are done,
init 2 

to try too go into graphical mode.

CTRL-ALT-F1 if it does not work, and try again

login
sudo dpkg-reconfigure xserver-xorg.

Good luck.

---

### Post by mrmoose19 on 2005-12-22
I did the above, and now it at least is telling me that the graphical interface is incorrect, would I like to proof the settings, so on and soforth.  Suggestions on how to make it stop?  Heh heh.

---

### Post by amohanty on 2005-12-22
[QUOTE=mrmoose19]I did the above, and now it at least is telling me that the graphical interface is incorrect, would I like to proof the settings, so on and soforth.  Suggestions on how to make it stop?  Heh heh.[/QUOTE]

The **_exact_** error messages/instructions would be really helpful in debugging. Otherwise the range of possibly wrong things is too big for us to be helpful.

Also if you can please post the contents of the following file:
/etc/X11/xorg.conf

AM

---

### Post by cker on 2005-12-24
Hi I am having similar problems 

My computer dies half way through installation - 66% into installing the packages.

I tried runing startx and received errors 11 and 3. I tried:
 sudo dpkg-reconfigure xserver-xorg 

I am told that xserver is broken or not fuly installed.
I tried looking for /etc/x11/xorg.conf and was told that no file or directory by this name is installed on my computer

I am at loss here - any ideas how to move forward?

Thanks 
Eyal

---

### Post by amohanty on 2005-12-24
[QUOTE=cker]Hi I am having similar problems 

My computer dies half way through installation - 66% into installing the packages.

I tried runing startx and received errors 11 and 3. I tried:
 sudo dpkg-reconfigure xserver-xorg 

I am told that xserver is broken or not fuly installed.
I tried looking for /etc/x11/xorg.conf and was told that no file or directory by this name is installed on my computer

I am at loss here - any ideas how to move forward?

Thanks 
Eyal[/QUOTE]


Usually if  an installation breaks while installing packages, it is usually due to a bad cd. I would suggest redownloading the ISO and writing a new CD, and verifying the cd after write. Also when installing at the boot prompt type
```
expert
``` In the second or third screen you will see a long list of available tasks. Scroll down to 'Verify install media' or something like that and verify the installation media, before proceeding with the install

HTH
AM

---

