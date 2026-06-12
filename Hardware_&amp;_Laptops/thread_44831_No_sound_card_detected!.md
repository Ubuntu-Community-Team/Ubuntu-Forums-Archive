---
title: "No sound card detected?!"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by Hex on 2005-06-27
Hi, guys,

I just installed Ubuntu and it doesn't detect my onboard soundcard (as if it doesn't exist).

What are the initial steps here? Other people seem to be having problems with ALSA, but I can't get Ubuntu to detect my soundcard to get to the ALSA problems :)

Help!

Thanks in advance!

---

### Post by andlinux21 on 2005-06-29
It (Ubuntu) doesn't see my sound card either ESS1879 
but when i type 

modprobe sb io=0x220 dma=1 mpu_io=0x330 irq=5

it sees the card but still no sound I will keep trying to get it to work

---

### Post by andlinux21 on 2005-06-29
i got my sound working!!!!! thank goodness it took me long enough now my laptop is complete well almost I cant hear anything in MPlayer but i am sure i can fix that too with a little reading. What i did was i added 

sb io=0x220 dma=1 mpu_io=0x330 irq=5

to the module start up file and that did the trick it loaded my soundcard :)

---

### Post by linuxrobot on 2005-06-29
I can't get my sound card working either.
I tried this, and it didn't work.
Is there something I'm missing?
Thanks!

**LinuxRobot**

---

### Post by andlinux21 on 2005-06-29
what kind of card are you using and is it a laptop or desktop??

---

### Post by linuxrobot on 2005-06-30
My sound card is integrated with my motherboard.  It is a Desktop.
Pentium II 400Mhz, etc.  An old system, but....hey, Ubuntu works great (except for sound and internet)

**LinuxRobot**  :)

---

### Post by andlinux21 on 2005-06-30
If you can post the specs on your board maybe we can figure out how to get it to work

---

### Post by linuxrobot on 2005-07-01
I got this computer second-hand.  I don't know what my mobo's specs are.  Is there any way of finding that out without tearing the computer apart?
Thanks!

**LinuxRobot**  :smile:

---

### Post by andlinux21 on 2005-07-06
are you dual booting? or is this computer linux only if you are dual booting there is a program called Belarc Advisor that will tell you everything on your PC its free if its linux only you would have to do a little googling to see if you could find something to do the same thing

---

### Post by linuxrobot on 2005-07-07
[QUOTE=andlinux21]are you dual booting? or is this computer linux only if you are dual booting there is a program called Belarc Advisor that will tell you everything on your PC its free if its linux only you would have to do a little googling to see if you could find something to do the same thing[/QUOTE]

Yes, my pc's a dual boot (MS Windows 98SE and Ubuntu 5.04)
I'm going to check out Belarc Advisor, and I'll let you know what I find... :) 

**LinuxRobot**  8)

---

### Post by linuxrobot on 2005-07-07
OK, here's my info:

MotherBoard:
Intel Corporation JN440BX AA729057-406

Multimedia:
Crystal WDM Audio Codec (2x)
Crystal WDM Audio Control Registers

That's what I got when I did the Belarc Advisor.  That is a great program!
Hope this helps!

**LinuxRobot**  8)

---

### Post by t2kburl on 2005-09-11
I have a similar device also not detected

any help would be greatly appreciated

---

### Post by mlomker on 2005-09-11
The **lspci** command is the most useful--it'll give you the chipset of the card.  From there you can search on here and google using the chipset number to look for a driver.

---

### Post by mweston on 2006-02-03
[QUOTE=Hex]Hi, guys,

I just installed Ubuntu and it doesn't detect my onboard soundcard (as if it doesn't exist).

What are the initial steps here? Other people seem to be having problems with ALSA, but I can't get Ubuntu to detect my soundcard to get to the ALSA problems :)

Help!

Thanks in advance![/QUOTE]
I seem to have the same problem. It is an Armada 7400 333mhz laptop. I finally got the screen resolution fixed, and the wireless NIC to work, but there appears to be no sound hardware detected. From another post, I created a file: etc/modprobe.d/soundcard/snd-es1879 file, but I keep getting "FATAL: Module snd_es1879 not found."

I am still very new to Linux, so I'm not sure how to handle this. I can't delete the file I created to try again, but I don't know if that will help. 

Any ideas ?

---

### Post by mlomker on 2006-02-03
[QUOTE=mweston]Any ideas ?[/QUOTE]

I don't know the solution, but I did a few Google searches and looked on my machine.  It looks like Breezy calls the driver snd-es18xx and not the name that you used.

---

### Post by mweston on 2006-02-03
You are correct. I renamed the file and its references to ES18xx, and now it works.

Thanks.

---

