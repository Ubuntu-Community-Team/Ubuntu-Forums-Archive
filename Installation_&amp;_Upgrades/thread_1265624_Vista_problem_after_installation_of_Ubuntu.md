---
title: "Vista problem after installation of Ubuntu"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by jjoxford2007 on 2009-09-13
Hey, I just got done installing Ubuntu onto my external hdd (very much seperate from my computers actual hdd) and i restarted the computer after installation like it told me to. Now the problem happens when i goto load up either OS, it tries loading grub(idk what grub is but I do know it's suppose to be there from seeing other posts) then I get an error 17. Then when I unplug my ext. hdd I get error 21(that I know has to do with the ext hdd being unplugged). If anyone can help me I'd greatly appreciate it. I just wanna use my computer again lol.:confused: ](*,) ill fiddle around with my computer some but i really dont think i will be able to figure it out on my own :(

---

### Post by bumanie on 2009-09-13
Assuming your bios has the option to boot from an external hdd, the best thing for you to do would be to repair vista's mbr with the install cd. If you only have a restore partition, go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") to get a repair cd.Then go here and follow this to get the hard drive working correctly. [This]("http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/") may help.
PS: grub stands for GRand Universal Bootloader.

---

### Post by jjoxford2007 on 2009-09-13
um the second "here" that u put isnt a link can u fix that please or else i cant fix my computer D: lol (i tried fixing it on my own doing a system restore but that didnt work and it wont let me do a repair from a back up even though i have a recovery partion.) is there anyway to access the recovery partion from command prompt? ](*,)this is how i feel atm lol

---

### Post by presence1960 on 2009-09-13
> **jjoxford2007 said:**
> um the second "here" that u put isnt a link can u fix that please or else i cant fix my computer D: lol (i tried fixing it on my own doing a system restore but that didnt work and it wont let me do a repair from a back up even though i have a recovery partion.) is there anyway to access the recovery partion from command prompt? ](*,)this is how i feel atm lol

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) This is the how to to restore vista's bootloader to MBR of your internal disk. That is unlike bumanie, he is usually very thorough. he must have overlooked that.

---

### Post by jjoxford2007 on 2009-09-13
I never got a installation cd with my computer as it has the recovery partion but ive tried to restore it that way by downloading the recovery disc as bumanie suggested and it really didnt help. i wish there was a way to get my hands on an installation cd without buying it cuz i doubt my parents would buy one since i know they cost like in the 80$+ range ;-;

---

### Post by Bucky Ball on 2009-09-13
Unless there is a really good reason for installing on an external drive, just wondering why you don't put both OSs on same drive and reserve external for data. You may have your reasons. Would avoid some of the issues you are having (although could be others).

Generally Ubuntu then picks up the other OS and works it into the Grub accordingly. Worked without a hitch my last three installs.

---

### Post by jjoxford2007 on 2009-09-13
Okay I've fixed my problem now. Thanks you guys I got vista running again. Now I just need to get ubuntu to work. but ill look around forums on how to do it properly so i dont bug anyone else. again thanks everyone :D

---

