---
title: "Can I Install Win98....."
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by BC_Kush420 on 2009-03-05
i was wondering if i can install windows 98 on my laptap that has ubuntu alredy on it???? i wanna double boot ubuntu and windows 98 and yeah ino i dont spell rite or use capitals/punctuation but i can type faster like this

---

### Post by WatchingThePain on 2009-03-05
Hi,
You can but it's better to put Windows on first.
What some people do is have Windows on a virtual machine (like Virtualbox or similar) inside Ubuntu.

---

### Post by .Maleficus. on 2009-03-05
Installing Windows over Ubuntu will probably overwrite GRUB, so you'd have to use say, the LiveCD to reinstall GRUB over the MBR after Windows is installed (or at least I think that would work).  This is also assuming you don't accidently wipe Ubuntu while partitioning.

And wouldn't it be faster to type and spell correctly, rather than write another sentence alerting us of your bad typing?

---

### Post by BC_Kush420 on 2009-03-05
Nice can u tell me how to put Windows on a virtual machine (like Virtualbox or similar) while ubuntu is alredy on it that would be GREATLY APPECIATED

---

### Post by BC_Kush420 on 2009-03-05
i've never heard of virtual machine

---

### Post by .Maleficus. on 2009-03-05
Virtualbox is in the repos so open Synaptic, search for 'virtualbox' and install it.  After that, run Virtualbox from Applications and create a new Machine for Windows 98SE.  It will walk you through the hardware setup and then require your disc for the actual install.  After that it's just a matter of running through the Windows installer.  To use Windows, you need to open up Virtualbox and click 'Start' on the newly created machine.

---

### Post by BC_Kush420 on 2009-03-05
im brand new to ubuntu i got given a laptop that has it on it whats Synaptic a web site or that add remove programs thing that u can search???

---

### Post by BC_Kush420 on 2009-03-05
how do i open synaptic i searched the add remove programs and it sais i alredy have it im BRAND NEW at this i dont even know how to navigate through the computer very well its so different than windows i like it tho

---

### Post by BC_Kush420 on 2009-03-05
theres no program called virtualbox in synaptic i checked

---

### Post by BC_Kush420 on 2009-03-05
aight im downloading some other virtual machine program called Qemu Launcher so when i get a virtual machine goin how do i Install windows on it and how do i set my computer to dual boot so i can choose windows 98 or linux???

---

### Post by Fenris_rising on 2009-03-05
If your going to install 98 into a virtual machine you don't need to dual boot. VM is a program within Linux so you open it to access the win98 OS within its own window on the Linux Desktop.

regards

Fenris

---

### Post by howefield on 2009-03-05
> **BC_Kush420 said:**
> theres no program called virtualbox in synaptic i checked

The version of virtualbox in Synaptic is virtualbox-ose 

OSE meaning open source edition. IMHO you are better getting the PUEL (Personal Use and Evaluation Licence)  version from virtualbox.org as it supports USB which the OSE doesn't.

If you get virtualbox from virtualbox.org make sure you download the .deb file that correspends with your version of Ubuntu, to do this open a terminal (Applications > Accessories > Terminal) and type 

```
lsb_release -a
```

---

### Post by WatchingThePain on 2009-03-05
Well I'm using vmware player downloaded as a 'bundle' which makes it easy to install.
Winblows goes on that for the odd application that doesn't work on Linux.

---

### Post by BC_Kush420 on 2009-03-06
alrite well i havent gotten any results im back to square one

can anyone send me a link to a good step by step guide on howto install Windows 98 on my laptop that has ubuntu on it ?

jus tell me wut program to download and how to use it cuz ubuntu Lacks in readme files and help sections

---

### Post by BC_Kush420 on 2009-03-06
K im goona download VMware after i download VM ware how do i install windows? and how do i install it as a Bundle or whatever do i jus go Applications>add/remove   and search for it??

---

### Post by BC_Kush420 on 2009-03-06
cant find VMware no results

---

### Post by Mark Phelps on 2009-03-07
Can't find VMWare?  Took me all of 10 seconds using Google to find the following link:

[http://www.vmware.com/]("http://www.vmware.com/")

You need to check the VMWare Workstation under Desktop Products on the right.  And, by the way, this is a 30-day trial.

If you want free permanent solution, try Virtualbox as has been suggested earlier.

---

