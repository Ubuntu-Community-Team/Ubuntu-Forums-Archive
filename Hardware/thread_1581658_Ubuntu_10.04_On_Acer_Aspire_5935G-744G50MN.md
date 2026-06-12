---
title: "Ubuntu 10.04 On Acer Aspire 5935G-744G50MN"
date: 2010-09-25
forum: Hardware
---

### Post by speakershock on 2010-09-25
Hello Everybody at Ubuntuforums!
 
I always had a weak for Ubuntu, but now i wanted to try it myself, but..
 
I installed Ubuntu 10.04 with a dualboot to Windows 7 on my Acer Aspire 5935G
And at first glance everythink seemed to work perfectly, but then after a reboot i got the Black screen on boot. I searched the internet for an anwser and found one, saying i should put nosetmode in the line (i think its called the grub :P). And i could revisit my ubuntu desktop again, but.. (yes again a but) I can only see it in Low graphics mode.. How can i start my laptop on ubuntu without having to change the line to nosetmode, and still have it in high graphics?
 
Specs of my laptop are:
 
CPU: Intel Core 2 Duo Mobile P7450
Chipset: Intel Mobile GM45
Videocard: Nvidia Geforce GT130m
 
I hope anyone can help me with this problem because i really want to become a part of the Ubuntu community
 
Thanks in advance,
 
Speakershock

---

### Post by gale401 on 2010-09-25
Hi
have a look how your Ubuntu system is arranged on your hard drive, possibly its conflicting with space used by the  proprietary system. 

If you run your ubuntu installation disc you can see the makeup of the drive,- ie you do not have to reinstall - simply run Ubuntu as a live system then exit the disc  , or  

 G parted can be downloaded as an .iso file, you can then run it to see
the make up of your hard drive. G parted is a very powerful program capable of removing all info from all hard drives so use it with utmost care !!  Linux systems use ext journal type, whereas proprietary systems use NTFS or FAT. 

Most Linux systems will use Xorg as a video graphics file and the  visual component can be started with command startx 

See if you can possibly live without proprietary software, I think it is causing the problems you are experiencing. g parted and Ubuntu live system will probably show you in terms of the partitioning where
the problem is. I have found proprietary software is arranged to take up all available space.
Remember G parted is a very powerful program.   you can also resize partitions that can take 10 mins or so if your proprietary system is being greedy.

here is a rough guide with linux you need a ext 2 or 4 journal system that has say 40 gb to work with
Linux also needs a swap drive of at least the Ram size, i usually allocate 4 gb - now these can be on 
separate partitions ie the linux system and the swap, or you can evoke some fancy partitioning with
extensions, but the two little partition system seems to work a treat. There are lots of guides to partitioning linux on the internet.     

Hope this helps

---

### Post by speakershock on 2010-09-26
Thanks for the reply!

I made a screenshot of Gparted, Hope this tells you what i did wrong.
But I think its the Nvidia drivers messing around on my laptop, because when i don't activate them Ubuntu starts without a problem, but when i activate the 3d drivers for my video card Ubuntu wont start no more. there must be more people having this problem.
[IMG]http://img208.imageshack.us/img208/7828/schermafdrukf.png[/IMG]

---

### Post by gale401 on 2010-09-26
Your partioning is good, so problem then is recognition of nvidia hardware. I will try and find an answer for you. I am just back from a 10 hr dirt road trip so need zzzz

---

