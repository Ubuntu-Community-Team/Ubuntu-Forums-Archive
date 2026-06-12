---
title: "I have a problem..."
date: 2008-08-07
forum: General Help
---

### Post by luchsieh on 2008-08-07
I have no idea what happens to my computer, but basically sometimes as I am using the computer normally, such as surfing the net and chatting on messenger, some programs will just not function right all of the sudden. For example, Pidgin Messenger will close by itself, or programs wouldn't open and instead freeze. And when I close everything and try to restart the computer, I press on the Power-button on the top right corner, and everything freezes.

How do I fix this?

---

### Post by phidia on 2008-08-07
Could you tell us what your system specs are and what version of ubuntu you have installed? 

Basically cpu speed, memory amount, video card and so on... thanks

---

### Post by tuxxy on 2008-08-07
When it all freezes try pressing CTRL + ALT + F1 and then atleast you will be able to reboot the machine from the command line

---

### Post by jkid on 2008-08-07
if you dont tell us what is your system spec with can work and try to be more specific and the thread title or more creative.......

---

### Post by loligager on 2008-08-08
ok... if that happens try CTRL ALT BACKSPACE
that will get u back to the log on screen
ALSO NEVER RUN AS ROOT!!!
NEVER
NEVER NEVER
This might be a bug... but it depends what you are doing...
Are you running Compiz?

---

### Post by luchsieh on 2008-08-08
ok my system specs are:

Processor:  Intel Pentium 4 3.0Ghz
Memory: 1GB RAM
Hard drive: 80GB
Video card: nvidia GeForce FX 5200
Motherboard: ASUS P5P800 SE
OS: Ubuntu 8.04

btw, what is the command to reboot computer if I press CTRL + ATL + F1? sorry I'm new to Ubuntu.

---

### Post by aaronanderson on 2008-08-08
When you hit Ctrl-Alt-F1, you should get a login prompt. Login as yourself and then run:
sudo halt
or
sudo reboot

---

### Post by luchsieh on 2008-08-08
Hmm..ok thanks! But I still want to know what the problem is with my computer. >.<

---

### Post by aaronanderson on 2008-08-08
Unfortunately I'm not that good at troubleshooting X windows related issues :(

One thing you can try is running s few of those programs from a terminal instead of using the launcher icon. That way you can see what it is spitting out when it stops working.

---

### Post by aaronanderson on 2008-08-08
Another thing to do is maybe run a memory test. When you first boot up and get the GRUB prompt, select the memtest option. Alternatively you can download an Ubuntu Live CD. It has the same option on boot up.

Also you can run dmesg when the problem occurs. It will spew a whole bunch of information but read what the last 10 or lines have (or alternatively run dmesg | tail -20 ) It might give you an indication of what's happening.

---

### Post by BobSongs on 2008-08-08
Thanks for the specifications.

Two things come to mind, neither of which can be blamed on Ubuntu:

1. Cooling. 2. RAM.

An improperly cooled PC will perform in wonky ways. Verify the system's cooling by checking the various internal fans. The main processor's fan usually sits on a "heat sink", a grill of some sort that often gets clogged with hair, dust, fur, etc. I lost a processor to neglect and over-heating.

If all is well inside the PC you may wish to give the RAM a test. I believe the Ubuntu setup CD-ROM comes with an application at boot time that allows you to test the system's Random Access Memory (RAM) to see that all is well. Often a system's start up sequence's RAM test is very superficial and not rigorous enough to detect small imperfections that cause system errors.

---

### Post by luchsieh on 2008-08-08
Well, just now the problem happened again. I tried opening Terminal but even Terminal opened and then froze right away. So I really don't know what to do now.

---

### Post by aaronanderson on 2008-08-08
As mentioned by BobSongs and myself, run the memory test. Also check if your BIOS has an temperature sensors. Some BIOSes tell your the temperature of the motherboard and processor. Make sure they aren't running hot (approx over 45-50 but it varies greatly).

---

### Post by phidia on 2008-08-08
Take a look at your log files in hardy (8.04) there is a menu way to view logfiles from System > Administration > 
You can also just do that through the file manger /var/log/messages also dmesg, xorg.0.log and maybe others.

---

