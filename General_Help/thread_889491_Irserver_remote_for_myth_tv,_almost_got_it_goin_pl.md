---
title: "Irserver remote for myth tv, almost got it goin please help figure out what i forgot."
date: 2008-08-14
forum: General Help
---

### Post by kenno_bell on 2008-08-14
Cannot get remote to work in Myth tv (ubunto 7.10). As far as i know this proves the remote actually works.....

 sudo irserver -codedump -debug_code -loglevel 4 /dev/ttyUSB0

IRTRans Send Done: 1
Name   : 
Version: D5.03.08
FW SNo : 13628
Capab  : Power On; 
FW Cap : 0x3c8019
USB SNo: 
Node   : /dev/ttyUSB0

IRServer Version 5.11.10
[ 0]:                      D5.03.08     SN: 13628
Remote zalman               compiled:    12 Timings -     47 Commands
Duplicate Commands for zalman.vol+:   zalman.knobcw  zalman.knobccw
Duplicate Commands for zalman.knobcw:   zalman.knobccw
Total:   1 Remotes  -  12 Timings -   47 Commands -    0 Calib. Commands
         0 CCF Data -   0 CCF RAW -    0 CCF Error
IRTRans Send status: 0 - 0
IRTRans Send status: 1 - 69
IRTRans Send Done: 3
IRTRans Send Done: 1
[0.0] play zalman
[0.0] play zalman
[0.0] up zalman
[0.0] up zalman 

I have zalman hd160 case and remote.

I am a complete noob to linux and probably forgot to do something obvious.

 i followed the how to forum @ [http://ubuntuforums.org/showthread.php?t=304807](http://ubuntuforums.org/showthread.php?t=304807) as best i can. Maybe i didn't install irserver correctly as it is not in any menus. Or maybe it conflicts with lirc which i installed and uninstalled and played with for days, but im pretty sure lirc is gone.

Please please help get my remote going.

---

### Post by kenno_bell on 2008-08-15
omg, i am such a newb. all i have to do is type the following in terminal.

sudo irserver -daemon /dev/ttyUSB0

this starts the irserver and remote now works in mythtv.

now all i have to figure out is how to make it all startup when i power up and my media center will be complete.

---

