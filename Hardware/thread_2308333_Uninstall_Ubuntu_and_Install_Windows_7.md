---
title: "Uninstall Ubuntu and Install Windows 7"
date: 2016-01-02
forum: Hardware
---

### Post by Jayanth_Krishnamoo on 2016-01-02
Hi,

I have ubuntu 14.04 LTS running on my laptop (Compaq Presario C700). I upgraded from 2GB to 4GB RAM. After upgrading, I observe that once I log into ubuntu, after a period of about 10 minutes my system totally freezes (including keyboard and mouse). No amount of help here has help me solve my problem. So I thought I would reinstall Windows 7. To my dismay, the system is not even recognizing Windows 7 CD. Can you please assist me here? Any suggestion (workable) would be welcome. Kindly assist me. My entire new years day has been spent on this, without success.

With warm regards
K.N.Jayanth Krishnamoorthy

---

### Post by P0c-TeaM on 2016-01-02
what is your full pc specification? model.. maker.. type.. etc// ?

maybe the cd is bad ? maybe you should play a little with BIOS settings ? what will boot first .. HD or CD or usb or what

maybe the new rams is not compartable with your pc DDR3 or DDR2 something like that and try removing the rams and try your windows cd again .. i dont know try everything lol

---

### Post by coldraven on 2016-01-02
Did you try removing the extra RAM? If it worked OK before the upgrade maybe the RAM is defective.
If you want to remove Ubuntu then boot up with an Ubuntu install disc and select "Try Ubuntu". 
Run the program "gparted" and delete all partitions leaving them as "Unallocated". **This will delete all your data so make sure that you have made a backup first.**
As mentioned in the previous post you need to change the boot order in your BIOS settings to boot from CD before the hard drive.

---

### Post by Bucky Ball on 2016-01-02
*Thread moved to **Hardware**.*

***Installations and Upgrades*** is for Ubuntu installs and upgrades. This looks like a hardware issue you should explore before going much further in any case. ;) 

> **coldraven said:**
> Did you try removing the extra RAM? If it worked OK before the upgrade maybe the RAM is defective.

Remove the new sticks. Boot with just the old ones and make sure everything is as it should be. Add one stick of RAM if all was good with the originals. Boot the machine. All good after an hour? Pull the new stick and add the other. Boot the machine. All good after an hour? If so, it is not a defective stick. 

When you boot with all of them in, is Ubuntu seeing the full contingent of RAM (i.e. if you have 16Gb in there, does Ubuntu report 16Gb)? Are you running a 32bit or 64bit install? 32bit will not see more than 3Gb. Maybe a silly question, but are you positive your motherboard will handle a) the amount of RAM you are throwing at it and b) the clock speed of the RAM you are throwing at it?

If you add RAM and the machine is suddenly crashing when it wasn't before, can't see what installing another operating system is going to achieve. There's something happening with hardware (or you are running a 32bit OS and there could be some problem with that).

PS: The contacts can sometimes be dodgy on new RAM. They get manufacturing gunk residue on there. Sounds crazy, but a rubber, as in a pencil eraser, lightly across the contacts will not damage the RAM but will remove any residual manufacturing gunk.

---

### Post by Jayanth_Krishnamoo on 2016-01-04
Solved.

I tried replacing the existing RAMs with my previous ones. Then tried  re-installing Windows 7 (32 bit), however, the installation failed. So, I  tried installing Ubuntu, yet again. The installation went through  successfully. Now the machine is back to normal - but not hanging. So, I  found the problem is really with RAM. In the system settings, the  memory showed 4 GB, yet the system was hanging. Now, it shows 2 GB and  doesn't hang.

---

### Post by Bucky Ball on 2016-01-04
Unfortunate, but at least you found the cause. 

Please see the first link in my signature to mark the thread solved. Thanks.

---

