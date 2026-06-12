---
title: "Hard Drive Boot Issues"
date: 2014-01-11
forum: Hardware
---

### Post by jjbernacki on 2014-01-11
Hello,

I am having very large issues.  All boot and hard drive related. These are them.

I run 2 laptops on Ubuntu:

Dell Inspiron 6000 on Ubuntu 11.04
Acer Aspire 5250 on Ubuntu 12.??

The Dell was working fine, then went black.  Hard shut down brought it back to normal.  Then again, it went black.  Hard shut down brought it back to normal.  Then again.  I tried to run my live disk 11.10 and that was fine.  Theen I tried to install from the disk and it said the hard drive was only 4 gigs available.  This made me think it was a major hard disk problem.  I resigned myself to buying a new one and put it aside.  Problem one explained.

This prompted me to grab my Acer machine and begin turning it over to Windows again.  Based on my purchase of some blackberry products and some wifi networking issues this was a good option.  I hoped to run the Dell on Ubuntu and the Acer on Windows.    I inserted the System Restore Disk I made upon buying the computer to get it back on Windows, and had some trouble identifying the correct disks.  I think I inserted the wrong one a few times and had to switch back and forth, and eventually this process was frozen.  It was asking for disk, and when I inserted it it made no progress.  So, I gave up on that.  I tried to simply load up normally to what I hoped was the Ubuntu, and it did not load.  Boot manager error.  I tried my ubuntu live 11.10 disk, and it froze during loading the live disk.  My 11.04 disk did the same.  My really old Windows XP disk eventually crashes to  hard drive error that says to run checkdisk after uninstalling new hardware.  Iam unable or unaware how to do this.  In the BIOS the hard disk seems to be recognized properly.  But still I get the boot mgr is missing error upon booting to the hard drive. I am stumped.  I can't load to hdd and can't load to 3 different live disks.  

Any help on either computer is apprecisted.  I am fully backed up, so total format is fine...if I could figure out how to do it.  

Thanks
Jack

---

### Post by Shadius on 2014-01-11
I believe you have messed up GRUB and that is why you're getting the boot manager is missing error.  Let me get some clarification though.  You want to return your Acer to Windows, am I correct?

---

### Post by jjbernacki on 2014-01-12
Yes.  But either way is fine as long as they work.  Ubuntu would be fine as well.  I can look into windows down the line.

---

### Post by oldfred on 2014-01-12
Better to use a newer version of Ubuntu. The 11.04 expired, so updates are not available.

Bootmgr missing is a Windows boot error.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by jjbernacki on 2014-01-12
I'm sorry, but I don't really know what most of that means.  One thing is that I think I can't do the Create Boot Info because I can't get into a live cd fully.  It crashes when loading.  I will try to get a third computer to create the boot repair disk and run it on the Acer.  This could take a day or two, or more, though.

As for the Dell, I'll try a newer version of Ubuntu on a live cd, but am not hopefull that it will recognize the hdd. 

Thanks for the help.

---

### Post by jjbernacki on 2014-01-12
Just got the Dell back up.  Appears normal.  Seems to recognize full hdd. Will scan around to ensure everything seems right.  Can confirm it is on Ubuntu 12.04. Will use dell to make boot repair cd for the acer.

Thanks again.

---

### Post by Shadius on 2014-01-12
> **jjbernacki said:**
> Just got the Dell back up.  Appears normal.  Seems to recognize full hdd. Will scan around to ensure everything seems right.  Can confirm it is on Ubuntu 12.04. Will use dell to make boot repair cd for the acer.

Thanks again.

I'm assuming you used the Boot Repair LiveCD?  If you already have the Boot-Repair LiveCD, there's no need to make a separate one for the Dell, just use the same CD. Hope that helps.

---

