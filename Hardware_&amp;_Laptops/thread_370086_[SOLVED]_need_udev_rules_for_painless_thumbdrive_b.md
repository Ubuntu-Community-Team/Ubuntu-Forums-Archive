---
title: "[SOLVED] need udev rules for painless thumbdrive backup"
date: 2007-02-25
forum: Hardware &amp; Laptops
---

### Post by Jeff294 on 2007-02-25
I am trying to implement the "painless thumbdrive backup" that I saw in the article in the February 2007 issue of Linux Journal magazine, and I can't get the udev rule that I entered to trigger when I connect my usb thumbdrive.  I'm using Feisty, and I've entered a udev rule that looks as follows, except that it's all on one line: 

SUBSYSTEMS=="usb-device", 
ATTRS{serial}=="09203A60F12268DF", 
RUN+="aplay /usr/share/sounds/gnibbles/reverse.wav > /dev/null 2>&1"

This rule should play a sound when I connect the thumbdrive, but I can't get it to work.  I've verified that the sound plays if I run the aplay... command at the command line.  Any of you udev experts out there have any suggestions? 

Any help is greatly appreciated. 
...Jeff

---

