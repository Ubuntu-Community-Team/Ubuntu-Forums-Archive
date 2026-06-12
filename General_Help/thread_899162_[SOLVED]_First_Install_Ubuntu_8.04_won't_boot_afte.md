---
title: "[SOLVED] First Install Ubuntu 8.04 won't boot after automatic updates (ATI)"
date: 2008-08-24
forum: General Help
---

### Post by Poilot on 2008-08-24
Hi!
I managed to install Ubuntu from Live CD in a second partition on my main hard drive (XP is on the first partition).
I removed the CD and rebooted as instructed. Grub works fine; I'm able to boot XP and to boot Ubuntu for the first time.
I left it do it's things like detecting my printer, webcam, and ATI graphic card. Then I am prompted to do some security updates. There is also an update for my graphic card which I enable.
Reboot as instructed again, and then nothing… I still have Grub working, the Ubuntu logo with the slide bar and when the bar is full, I have a blank screen and it all seems frozen (no hard drive activity).
I tried the "recover" Grub option, checked the packages and they all seem OK.
Could it be a graphic card issue? How may I fix this, like using the default display driver?
I'm a real newbie, and do not know much about using the console. 

Thank you.

---

### Post by eggdeng on 2008-08-24
At the white screen, press Ctrl + Alt + F1 to get you to a terminal.
Now type
```
sudo nano /etc/X11/xorg.conf
```
Use the arrow buttons to find the line
```
Driver          "fglrx"
```
Change it to
```
Driver          "ati"
```
unless it already says ati, in which case try
```
Driver          "vesa"
```
Press Ctrl + X to exit, then Y and Intro to save. Reboot.

---

### Post by Poilot on 2008-08-24
Thanks Eggdeng.
I have tried to enter console mode, but it won't let me do anything.
Hitting the ctrl+alt+F1 only had effect when in the "slide bar" phase but it did not somehow pause so I couldn't enter the command line.
Is there another way around like entering specific commands while in Grub?

Thanks again!

---

### Post by eggdeng on 2008-08-24
Sorry for the delay, day out today. Have you tried to boot in recovery mode, using the arrow keys at the grub screen?

---

### Post by Poilot on 2008-08-24
Thank you so much! :)
It works very well now.

---

