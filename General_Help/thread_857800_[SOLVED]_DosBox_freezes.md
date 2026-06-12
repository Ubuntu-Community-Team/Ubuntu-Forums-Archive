---
title: "[SOLVED] DosBox freezes"
date: 2008-07-12
forum: General Help
---

### Post by pixnaps on 2008-07-12
Hi, I have a Toshiba Satellite A135-S4527. My computer has been crashing a lot in Ubuntu recently, especially when playing 'Master of Orion' in DosBox (it seemed fine at first, but now only lasts about 5-10 mins before freezing). Ctrl-Shift-BkSp is no help, all I can do is hold down the power button.

(Sometimes, at least for the non-dosbox-related crashes, I can move my mouse but not select anything. Then, ctrl-ALT-bksp will take me to a "command line" of sorts -- a black screen with text, at least -- but I can't find any way to quit or exit from there, so still need to hard reboot.)

Any ideas? (I see someone else is having [similar problems with DosEmu](http://ubuntuforums.org/showthread.php?t=855310), and other folks with Toshiba laptops have reported my exact problem [here](http://ubuntuforums.org/showthread.php?t=512767).)

---

### Post by pixnaps on 2008-07-15
Switching to the -rt kernel seems to have fixed the problem.

---

### Post by dbruce100 on 2010-02-03
The post about using the -rt (real time client also fixed lock ups with 9.10 on a Toshiba A75.  Install for the rt client is below in the following link:

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

You only need to perform the following command from the link:

[FONT=Arial]sudo apt-get install linux-rt linux-headers-rt

For the first time, my laptop was usuable first thing in the morning with hyperthreading enabled.  Before the rt, it would always be locked up.
[/FONT]

---

