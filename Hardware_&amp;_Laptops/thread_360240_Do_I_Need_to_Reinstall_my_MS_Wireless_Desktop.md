---
title: "Do I Need to Reinstall my MS Wireless Desktop?"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by JLuv on 2007-02-12
I found a thread [here](http://ubuntuforums.org/showthread.php?t=183547&highlight=microsoft+tilt+wheel+ms) that would make life so much easier for me. But the problem starts at
> 1. First make sure your Intellimouse is plugged in to a USB port. I tried this with the supplied PS/2 connector and it failed.

Well, my mouse & keyboard are plugged into the PS/2 ports. I restarted my computer with them plugged into a USB port, but got some very weird behavior (sticky keys, blinking lights, no mouse movement) which makes login impossible. I can't even get to command line b/c my keystrokes aren't caught. 
When I installed 6.10, I used the regular drivers, so I'm assuming that my install just doesn't recognize the keyboard & mouse through the USB port. So, my question is how would I get these guys installed to use USB instead of PS/2?
I'd like to avoid a reinstall b/c I have a few days worth of preferences and customizations already. Thanks for any help.

---

### Post by scrooge_74 on 2007-02-13
How is that they are first using Ps/2 ports and later you have them using USB ports? Are you using a converter of sort?

if you plug them back into PS/2 ports and then boot, they should be recognize

---

### Post by JLuv on 2007-02-13
MS Wireless Desktop is default USB, but comes with a PS/2 adapter. So I can easity switch between PS/2 and USB on Windows.

However, when I installed Ubuntu, I didn't use USB. My keyboard and mouse work fine through PS/2. So i'm assuming that I need to explicitly tell Ubuntu to use USB. And I don't know how/where/when to do that.

---

### Post by scrooge_74 on 2007-02-13
usually if you plug things before you boot the system it will take care of it, but I read somewhere that those wireless keyboards and mouse do give trouble in Linux

---

### Post by JLuv on 2007-02-13
Yea, it's giving me trouble. No settings or anything change when I plug in my keyboard & mouse through USB. All I get is no mouse movement and stuttery keys.  :-/

---

### Post by scrooge_74 on 2007-02-13
Do you have a normal keyboard you can use? 

When plug in ps/2 can you log in a terminal and do sudo dpkg-reconfiguire xserver-xorg

Probably you can do this from recovery mode when booting

---

### Post by JLuv on 2007-02-13
No, I don't have an extra keyboard. And now that I think about it, everyone I know uses wireless.

Yes, If I use PS/2 instead of USB, I can do anything. So, if I type dpkg-reconfigure xserver-xorg it will give me the option to load USB drivers? Or how exactly would that work for me?

---

### Post by JLuv on 2007-02-14
Ok, so I typed in the terminal sudo dpkg-reconfigure xserver-xorg and I got this message...

> $ sudo dpkg-reconfigure xerver-xorg
Password:
Package `xerver-xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xerver-xorg is not installed


---

### Post by scrooge_74 on 2007-02-14
check your post it says you typed xerver-xorg instead of xserver-xorg

just a litlle typo error

---

### Post by JLuv on 2007-02-14
:oops:  #-o LOL!

I'll try that again.

---

