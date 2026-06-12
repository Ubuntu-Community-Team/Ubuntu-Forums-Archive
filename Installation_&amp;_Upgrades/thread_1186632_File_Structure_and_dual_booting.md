---
title: "File Structure and dual booting"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by jolo on 2009-06-13
I am about to get a laptop computer from either Red Bard or System 76. 
With both of them, I can get them custom made and I can get Ubuntu 9.04 pre-installed, then I will install either XP or Vista and create a dual boot situation, "just in case". 

In a email dialog with System 76, the salesperson referred me to a Wiki that gave instructions on how to create a dual boot system on a computer that already has Ubuntu on it. 

The Wiki is here [**[COLOR="Navy"]Link to adding Windows to Ubuntu[/COLOR]**]("http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine")

There is one part of this Wiki that might not be correct and I would like your help in verifying it.
 Install Windows

[SIZE="3"][I]"Simply run through the installation process.
When you get to the partition screen choose to install Windows on your new Unpartitioned Space.
**Partition the space FAT32 if you want to be able to exchange files between Ubuntu and Windows partitions**."[/I][/SIZE]
With formatting, on Windows, the Windows control freaks removed the ability to format a hard drive as FAT32. When I wanted to do that, to create an external drive that I can write to from my Windows Vista PC, then have it connected via USBII to my DVD player, I needed to get a third party program to format my external drive as FAT32. 

**[COLOR="Blue"]I also was of the belief that Ubuntu 9.04 supported NTFS and that if I want to share data that could be readable in both Ubuntu and Windows, that it should be NTFS. [/COLOR]**

PLEASE let me know what is correct ??

Thanks,

Jon :D

---

### Post by jbruced on 2009-06-13
In my experience, NTFS has worked out of the box reliably. 

Doing a web search may show older websites offering older solutions, but it is so reliable, it's a non-issue now. 

I screwed up and formatted an external HD for compatibility reasons to FAT32 close to a year ago. It works, but would rather have done it in NTFS.

btw, my internal XP ntfs partition is accessed easily from Ubuntu.

---

### Post by merlinus on 2009-06-13
+10 for ntfs.

But you may wish to specify how you want your partitions set up.  I would suggest leaving 20G (or even more if you will be installing lots of win software) in a primary partition at the very front of the hdd.

Then everything else should go into an extended partition, with 10-15G for / and at least 7G /home, and 1.5G /swap.  The rest of the space can be a /data partition formatted as ntfs.

---

### Post by jimv on 2009-06-13
You can also go the virtual machine route, so that way you can just start up your Windows VM from Ubuntu instead of rebooting.

---

