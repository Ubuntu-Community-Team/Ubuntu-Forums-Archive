---
title: "remove second (blanco) HD without grub error 21"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by Frankels on 2009-01-02
Hi, Grub is giving error 21 at stage 1.5 after I remove my second (empty) hard disk. I want to be able to physically exchange my two disks and have ubuntu on one and some windows or whatever on the other. I dont want dual boot or anything. But I cant find out how to tell grub to ignore the removal of the empty disk. I can give more information if necessary

And, second...is there a grub configuration gui? will there be one?
thanks

---

### Post by logos34 on 2009-01-02
instructions here:
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

---

### Post by Frankels on 2009-01-02
Thanks for the reply. I'm sorry but thats just a link to some general information that doesn't hold the solution (or instructions) to my specific problem. I need to know exactly how to tell grub to stop looking for an empty disk. I understand there may be something in the MBR but it doesn't show up when I mount the disk and show hidden files...so what is grub looking for???

---

### Post by logos34 on 2009-01-02
> **Frankels said:**
> Thanks for the reply. I'm sorry but thats just a link to some general information that doesn't hold the solution (or instructions) to my specific problem.

you didn't wait for the page to fully load (it's big). It should eventually scroll down to 'error 21' section.  try the suggestions there.  post back if still having problems


startupmanager - Grub and Splash screen configuration

sudo apt-get install startupmanager

startupmanager 

(or system>admin>startup-manager)

---

### Post by Frankels on 2009-01-02
Thanks again for the reply. I did actually wait, it took about a second and firefox 3 took me to the exact location of error 21. Of course I have also googled error 21 before I posted here, and found out:

"21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. "

I know. I removed the disk personally. I'm glad you have also noticed the disk is gone. It was empty. Now take me to my desktop please?


Just knowing what the problem *is* doesn't solve it. I don't know where grub stores the information that it has to look for a completely empty disk. Startup manager doesn't let me edit all the little empty disks grub wants to look for in it's spare time while trying to boot ubuntu. I'm sorry, I'm getting a little irritated (not with you, logos34, you have been most helpfull) 

I'll try formulating my question as clear as possible:

The question is: which file do I have to edit in which way to make grub stop looking for an empty and removed disk and just boot already?



edit: startup manager is exactly what I need, by the way. But where's the tab "usefull" or "really advanced" or "grub actions"

---

### Post by logos34 on 2009-01-02
Try botting the live cd and reinstalling grub to the MBR.  

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If you get a grub menu screen but it errors out when it tries to boot ubuntu, press 'e' to edit highlighted ubuntu kernel entry, 'e' again on 'root' line (assuming that and not 'UUID')...it should read '(hd**0**,?)'

---

### Post by Frankels on 2009-01-11
I've now tried reinstalling grub (with the gutsy gibbon live cd) but everywhere someone explains how to do this (like here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)) they forget to include that you have to mount the harddisk before you can find /boot/grub/stage1.(edit: someone did include it...) And I dont seem to be able to mount it with 
sudo mount -t ext3 /dev/sda /mnt/sda
which I don't understand. (I did sudo mkdir /mnt/sda ofcourse)
So I'm stuck again.

I can't stand the fact grub stage1 is supposed to be on an empty disk: I cant see the file on the disk, not even with show hidden files. And why can't grub just work without level1....This should be fixed. I'm getting close to doing a reinstall.... I can't be bothered with all this nerdy looking around for solutions to a problem that should have been avoided by the people who programmed this. I'm gratefull for ubuntu, don't get me wrong, but this kind of stuff is why most people are still paying for other operating systems. A car can have a fancy soundsystem, 350 pk's, airbags, abs, and be able to go from 0 to 80mph in under 10 seconds...but without wheels its just no use...

---

