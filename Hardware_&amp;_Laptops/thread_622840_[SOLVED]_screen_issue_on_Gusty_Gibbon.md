---
title: "[SOLVED] screen issue on Gusty Gibbon"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by Purplecatty on 2007-11-25
I am having trouble getting Screen set to 1280x1024 (saving settings) permanently..  Every time I power up or rebooting Ubuntu,  it switched back to 1152x768 (my monitor screen was shifted to right about 3 inches off)  I tried to edit by typing on console under Root user:  gedit /ect/X11/xorg.conf and nano /ect/X11/xorg.conf,  both edit show blank!! huh!??  Even tried to Sudo dpkg-reconfigure xserver.xorg and configured it.  It doesn't resolve this (I wanted to weed out refresh rate down to 1024x768 and 1280x1024 for Screen and graphic selection).  I decide to go through root file, browsed through /ect/X11 folders and saw xorg.conf.  I tried to edit but say must be the owner.... Doing console as Root like I mentioned above wouldn't do!!  OH sheesh!!  I wanted to edit those refresh rate and also delete extra files such as xorg.conf1, xorg.conf2, xorg.conf3 and so on.. It had been adding up.

MY monitor is Acer 76c and my system is Abit AV8 with AMD 64 3500 "venice core", ATI Radeon 9000 pro 128mb, 512mb DDR.  It's my monitor issue tho.. I already change monitor model to Acer 76c in Screen and Graphic and it kept it's setting..

Also when I boot up or reboot Ubuntu to login screen, It been set to 1152x768 as usual till I log in and it'll switch back to 1280x1024.  How do I get the log in screen fixed too??  

I need your help!!

Much appreciated 
Catty!!

---

### Post by Yellow Pasque on 2007-11-25
it's /etc , not /ect

:lolflag:

Try again and see if that helps.

---

### Post by Purplecatty on 2007-11-26
maybe that could be it!  I will try
Thanks!
Catty

---

### Post by Purplecatty on 2007-11-26
Bingo! Got it.  Sorry for my silly mistake.  It's great to have you with sharp eye.  Maybe I need a Bifocal Kidding.

Catty

---

### Post by Purplecatty on 2007-11-26
Ok everything gone well now and when I rebooted,  the Log on screen did set to correct refresh rate (1280x1024) for very brief second then went blank then went back on as 1152x768.  I logged on and it switched to 1280x1024 automatically as set for. .  How do I fix Log On screen refresh rate.  I already edited xorg.conf file by deleting all "1152x768" on list and saved it.  As mentioned above, I rebooted and Log on screen went for wrong refresh rate (1152x768 ).  I checked X11 folder and saw new file "xorg.conf.1".  It automatically created new file.  How can I fix that to stick with 1280x1024 for Log on screen?

Hint Hint??:???::???:

Catty

---

### Post by Purplecatty on 2007-12-07
I still have problem with screen resolution,  It's something else,  I ran game under WINE with full screen.  After quitting game,  the screen resolution was switched to 1400X1050.  The desktop screen was little off.  I had to change resolution back to 1280X1024 (System---Preference--Screen Resolution).  I went back to X11 and edited Xorg.conf file to remove 1400X1050 from list then saved it (I use Terminal and typed "sudo nautilus" LOL).  It didn't help at all after playing WINE game and under System--Preference---Screen Resolution,  it is still showing 1400X1050 on list.  How do I remove it so it won't fall back??  Same goes for Logon screen.  Suggestion Hint Hint!!!???

Help!!!

Catty

---

### Post by Purplecatty on 2007-12-19
Never mind,  It's my Acer 76c 17inch monitor problem.  I recently got Gateway2000 Crystalscan 17 inch monitor from my parent.  Crystalscan works fine on both login and desktop without any hitch.  

If any of you have problem with login screen and been struggling to get it fixed.  Try swap to  different monitor.  This may help.  Some monitors automatically adjust to resolution changes.

Thanks
Catty

---

