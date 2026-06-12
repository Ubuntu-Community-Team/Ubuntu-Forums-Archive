---
title: "Ubuntu Freezing Porblem"
date: 2008-08-02
forum: General Help
---

### Post by syntheticz on 2008-08-02
Hi, If I am on second life, after a short while ubuntu just simply freezes up, if music is playing the music jams too, and it does not unjam.. It has also done this while normally on Linux and has done it on both the 64 and 32bit versions. I tried turning compiz off but it has not fixed the problem. I know it is a vague description but thats all I can really describe it with, its really annoying as its one of my main applications and if Ubuntu wont do it I will have to go back to windows.

---

### Post by syntheticz on 2008-08-02
anything at all?

---

### Post by syntheticz on 2008-08-03
Some additional information is that it also did this on linux mint as well. I am not sure what could be causing this but I can only think it could be to do with the graphics.

---

### Post by syntheticz on 2008-08-03
Tested the ram using memtest86+ The ram is fine, so it cant be that.

---

### Post by bholliday72 on 2008-08-03
Hello fellow Ubuntu user,

I am also having a freezing problem.  For me it is not always a short while, it is often after I have been playing around for at least an hour.  I have described it in more detail [HERE]("http://ubuntuforums.org/showthread.php?t=877279").  For the time being I am using Windows XP Pro SP3 and have never experienced a complete system lockup.

It is a very hard problem to diagnose over an internet forum I know, but do any of you advanced users / devs out there have any idea what is going on with this?

EDIT: To the opening poster, check out my hardware configuration.  Is yours similar?

Also, my computer does not lock up from any specific web site or game (Second Life) but just does so randomly, usually while web browsing in FF3 but not always.

---

### Post by bholliday72 on 2008-08-03
bump

---

### Post by linux_tech on 2008-08-03
Freezing could be caused by a number of things. Have you checked the system monitor to check the cpu and mem usage? Best to try to narrow down.
* How often does it freeze?
* Is freezing associated with an application or activity?
* When it freezes, can you move the mouse, use the keyboard, or switch to a virtual terminal (Ctrl-Alt-F1)?
* Does it "melt"? That is, does the freeze go away after awhile?

Some places you may want to look:

/var/log/syslog - Almost everything logs here.
/var/log/Xorg.0.log - Xorg is one common source of freezing problems.
/var/log/kern.log - kernal
/var/log/dmesg - Mostly hardware and boot issues are logged here.
~/.xsession-errors - application errors

Make sure to look at these as soon as possible after the crash.

Try installing another browser, Opera or epiphany, for example, install one and see if it freezes or not when using it.  If it does not, then it is probably firefox, in which case this page might help: 

[http://kb.mozillazine.org/Standard_diagnostic_-_Firefox](http://kb.mozillazine.org/Standard_diagnostic_-_Firefox)

---

### Post by syntheticz on 2008-08-04
My current set up is

2.8ghz Intel Pentium D
1 GB 266mhz DDR2 RAM
Nvidia Geforce 7600 GT 256MB
OEM Packard Bell Cuba Motherboard
140GB IDE Hardrive

I will try and find read outs after the next freeze up.

It freezes up on games usually within the hour if not sometimes within minutes. 

It freezes MORE whilst on applications like Second Life but it does it normally on desktop.

When it freezes nothing will respond, the cursor and keyboard are frozen too.

No the freeze does not melt.

---

### Post by syntheticz on 2008-08-04
I have saved the logs to the documents folder, shall I post them on the forum, they seem to be very long.

---

### Post by AdamWood on 2008-08-04
Have you tried turning off Desktop Effects?

I had some crashes caused by my Nvidia gfx card that went away after I stopped using Desktop Effects.

---

### Post by linux_tech on 2008-08-04
If you go through the logs, towards the end - do you see any clues to the freeze? You can save the files as attachments to the post.
 
Do you currently have the 32 bit or 64 bit vers of ubuntu installed?

Going with the asssumption it could be the video card,  
Download and reinstall the correct version of the video driver- 
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

NVIDIA now provides a utility to assist you with configuration of your X server configuration file. I attached the file. Installing this may help.


NVidia linux forums link:
[http://www.nvnews.net/vbulletin/showthread.php?t=76535&highlight=7600+freeze](http://www.nvnews.net/vbulletin/showthread.php?t=76535&highlight=7600+freeze)

---

### Post by syntheticz on 2008-08-05
im on the 32bit version.

I think however it may be the card overheating because the card is running hot over 100 degrees.

---

### Post by linux_tech on 2008-08-05
Is the fan on the card working?  You could add a additional fan in the box
but you should make sure the fan on the card is working correct first.

---

### Post by syntheticz on 2008-08-05
There is no fan on the card, It seems to reach levels of 110 degrees, but it froze at 70 before, so I no longer think heat is the problem. Here are the logs.

---

### Post by AnarchyCow on 2008-08-05
I have a 8800GT, and it will go up to about 100C before it crashes, and that's hard to get to. The highes I've ever seen it going is around 65C.

Might be that your ram is full? =\ A suggestion, or it might even be something with secondlife.

---

### Post by syntheticz on 2008-08-06
It does it even when not on SecondLife, I don't see how the RAM could be full because it always coped ok and never did this on windows, I did a memeorytest and the RAM had no errors.

---

