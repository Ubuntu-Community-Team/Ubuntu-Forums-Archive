---
title: "Problem with 9.04 on dual boot"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by kd0afk on 2009-04-29
I installed ubuntu 9.04 on a dual boot using wubi on windows XP.
Everything was fine until today. 
I was thinking of reinstalling umbutu to get rid of windows so I burned the install iso file to a disk and I changed my bios to start from CD first At the OS choice screen it says to hit F8 so I did to see what my options are and now whenever I choose ubuntu, it takes me to another screen that asks me which version I want to install. I can NOT get out of it.
I was told earlier that all I have to do is to go to type "sudo fdisk -l" and then I can wipe the windows partition with "-dd" and I want to do this eventually but I can't even get into ubuntu now.
I can't even get into the bios screen anymore to change the boot order back.
Please, someone help me out on this.

---

### Post by kd0afk on 2009-04-30
WOW, thanks for the help guys.](*,)

---

### Post by Mark Phelps on 2009-04-30
Hey ... you think we're magicians here???

First off, you said you set up dual-boot using Wubi.  That is a contradictions of terms!  Wubi installs Ubuntu as an application INSIDE MS Windows.  It is NOT dual-boot, even if you install it to a different partition or drive.

Second, when you boot from a LiveCD, you will NOT get an "OS choice screen". So, regardless of what you thought you did, the machine is NOT booting from the CD.  You get the OS choice screen because the machine is still booting into the hard drive.

Third, "sudo fdisk" has nothing at all to do with wiping an entire disk.  The easy way to do that is to boot into a LiveCD, bring up Partition Editor, select all the partitions on the drive, and delete them.

Oh, and when you do that, it will wipe out Ubuntu -- because you installed it using Wubi.

---

### Post by mschraier on 2009-05-01
A related question,  I had originally in 9.04 using Wubi.  Then uninstalled using Add/Remove in Windows.  I did a fixmbr.  However, the Grub menu is still there.  What other way is there to remove that so the boot goes directly into Windows again?  I will be re-installing 9.04 but want to clear this up before I do.

:confused:   :confused:    :confused:

---

