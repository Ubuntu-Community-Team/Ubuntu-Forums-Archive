---
title: "Issue with LIRC, XBMC, and MCE Remote"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by Sethar on 2009-03-13
Hello all,

I am slowly driving myself insane trying to get this setup working.  I have installed XBMC, and it's (now) working like a charm.  However, I cannot seem to get the IR remote to recognize.  
I've spent about 3 hours combing through various forums and Google trying to find a solution to my problems but I haven't had any luck.

This is where I stand:  I did a *sudo apt-get install lirc*, and everything installed fine.  The config popped up, I selected the incorrect remote, and things went downhill from there.  After a ton of wrangling around, re-installing, etc...I finally figured out I could have simply done a *dpkg-reconfigure lirc* to re-select a remote.  I went back and reconfigured lirc for the Windows MCE Remote (v2).  After I selected the remote, it asked which transceiver I had.  I don't have one (it's a receiver + remote) so I selected None.

After running various things like irrecord or irw (no idea what they do -- I was under the impression one of those would display your remote button presses in hex values so you can verify you are getting raw input) nothing shows up, at all in my terminal window.

The Receiver light is blinking red, and so is the remote.  I thought I may have made a mistake by selecting no transceiver, so i went back and one at a time selected every option that had anything to do with usb and windows media center remote...no dice.

So, the long and short of it is lirc is installed, selected the correct remote, but it does not recognize at all in xbmc or in the terminal using the command irw or irrecord.  This is where I am lost -- I know I am overlooking something or doing something wrong...please help!

---

### Post by Surkow on 2009-04-04
I had exactly the same issue with a second generation Philips MCE remote control. The problem was a wrongly configured /etc/lirc/lircd.conf file. I solved it by removing the /etc/lirc directory and reinstalling lirc.

The contents of my lircd.conf file:
```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Windows Media Center Remotes (new version Philips et al.) remote:
include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb
```

---

### Post by odinb on 2009-05-20
try this guide, it worked for me: [https://help.ubuntu.com/community/IMON_VFD_and_LCD/](https://help.ubuntu.com/community/IMON_VFD_and_LCD/)

Good luck!

//Odin

---

