---
title: "Ubuntu 5.10 Install Problem"
date: 2005-12-26
forum: Installation &amp; Upgrades
---

### Post by \root\home\ on 2005-12-26
Hello everybody....

I have original Ubuntu 5.10 Install CD also i have 5.10 Live CD. I put my install cd and i boot it, than i press enter for default installation, then i choose my language and language for keyboard. Then the setup detecting my hardware, after a detecting is finished i got blue screen and bottom line is white, after some time i got message on the display:

! Detect and mount CD-ROM

Your installation cd-rom couldn`t be mounted. This probably means that cd-rom was not in drive. If so you can insert it adn try again.

Try again to mount the cd-rom 

Yes     No

-----------

That is error message, i cant understand why he display me that because cd-rom is in the drive.

Processor : Intel Pentium PIV 3.06 FSB 800
RAM: 512 MB
Hard Disk: Maxtor 6Y080L0 80 GB
CD-ROM: LG HL-DT-ST RW/DVD 6CC-4521B
Motherboard: Asus P4 S800-x

Please if anybody can help me..... :(

---

### Post by ed_d on 2005-12-26
Try to burn the install cd at like 4 to 6 speed and try again. Friend of mine had same problem and that fixed it.

---

### Post by \root\home\ on 2005-12-26
Hmmm this is original pack which i have. Box comes with Ubuntu 5.10 Install and Ubuntu 5.10 Live CD. But i will try that sollution.

---

### Post by ed_d on 2005-12-26
Also, mabye see if you have any defects on the box set cds. I have had install issues with other os installs, where as I had a nice thumbprint on the cd that I didnt notice. Try the breath test on the cd to see, and give it a good clean.

---

### Post by \root\home\ on 2005-12-26
I got same problem :( . Please if somebody to help me .....

---

### Post by ed_d on 2005-12-26
I was reading in the forums, someone said to make sure that you put in YOUR time zone. Try that and see...

---

### Post by \root\home\ on 2005-12-26
what to put :S i cant understand ?

---

### Post by ed_d on 2005-12-26
well, where to you live?

When prompted for the time zone, dont just hit enter but actually select the closest to your area. Im not sure it will work for you or not, just trying to come up with something to assist you.

---

### Post by \root\home\ on 2005-12-26
There is no help in installer menu i can just setup my keyboard and language, :( , i dont know how to solve this problem :(

---

### Post by \root\home\ on 2005-12-26
I have tryed to enter this commands on Boot: 

" Boot: linux acpi=off noapic nolapic" but later when i choose language and keyboard, i got screen with Detecting hardware to find cd-rom drives, which freeze on 83% . Operation was Loading module 'ide-disk' foe linux ata disk.

Please help if anybody have any solutions.

---

### Post by 504harry on 2005-12-27
Your message sounds like the CD ROM is not being detected properly -
 - - - You don't give much system info - - -
//
 My own PC is a few years old and I have to supply a CD driver.....when I used a "Live CD" - it would not work without a Working  HDD connected - so I presume it was taking the CD driver from the HDD. (there being no Win boot-floppy present - I've lost it.) 
Without the HDD, the Live CD would not fire.....and I presume I'd need a prog like MSCDEX to get the CD operational.
In my experience, it then found a driver and the drive was correctly addressed as a CD/DVD read/writer - I had nothing to do extra. However, I haven't tried CD writing from a live distro.

---

### Post by djlilyazi on 2006-01-04
[QUOTE=\root\home\]I have tryed to enter this commands on Boot: 

" Boot: linux acpi=off noapic nolapic" but later when i choose language and keyboard, i got screen with Detecting hardware to find cd-rom drives, which freeze on 83% . Operation was Loading module 'ide-disk' foe linux ata disk.

Please help if anybody have any solutions.[/QUOTE]


I HAVE THE EXCAT SAME DAM PROBLEM .......

---

