---
title: "Adaptec 3085 RAID controller driver install"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by jrleighton on 2009-02-01
Hi - I am having real trouble figuring out how to install the driver for the above RAID card. It's not a fake raid card, but I do also have software RAID 1 on my ubuntu box provided by mdadm.  The RAID card I now want to install is for an external SAS/SATA RAID storage array. I have the latest (v 10 ) kernel has I have just installed the latest version of ubuntu.

A few things I have managed to figure out so far:-
(i) the driver needed is for 'aac' according to documentation I can find - which is included in the Ubuntu distro supposedly.
(ii) the included driver doesn't work for me - the card is not recognised.
(iii) the Adaptec supplied software monitoring application - Storage Manager - doesn't work with the ordinary aac driver, but does with the Adaptec supplied aac driver
(iv) in order to install the Adaptec aac driver, the kernel needs to be patched.  
(v) when booting my machine there is an error - caused by the RAID card as the error does not happen with the card removed - where the system fails to scan my RAID card drives, and then wants to launch a maintenance module. I assume this is because it is not even recognising the card with the ubuntu aac driver, even though I have yet to attempt to install the Adaptec aac driver.

There are a few clues out there about patching a kernel, but none that look comprehensive - and nothing about the ubuntu 10 kernel.

Can anyone please help me at all ?

Many thanks

---

### Post by r m h on 2009-02-01
Here's the solution that has solved this problem for me, time and again.

(1) create an MS Windows floppy for the driver(s)
(2) using any Windows XP Pro disk, start a Windows installation
(3) hit F6 when the prompt to hit F6 to install additional drivers is seen
(4) insert the Windows floppy for the drivers and press Enter 
(5) select the drivers to install from the floppy and press Enter
(6) when Windows gets to the point of asking you to press F3 to quit the Windows installation or Enter to continue, hit F3, hit F3 again to reboot your computer
(7) while said computer is rebooting, remove Windows XP installation disk and the floppy disk and insert your Ubuntu installation disk
(8) Now install Ubuntu - the drivers will be available for Ubuntu to see your disks as a RAID array

I haven't found any other solution or workaround for this other than these 8 steps, but these 8 steps have always worked for me so far.

If anybody has a better solution to this situation, let us all know, please!

I typically run Ubuntu on a RAID1 (mirror) array off the mainboard and I have the rest of my data on 3Ware RAID5 arrays.  This has enabled me to achieve 80+MBps sustained writes to the RAID5 arrays via SAMBA from linux, and less than that from Windows (gosh does that mean that SAMBA and smbclients on Linux can surpass the throughput of Windows to Windows?  YES!).  Note that I do use the tw_cli tool from 3Ware to set up my 3Ware controllers after installing Ubuntu on the RAID1 array.

Hope this helps

---

### Post by daniel.pool on 2011-01-16
> **jrleighton said:**
> Hi - I am having real trouble figuring out how to install the driver for the above RAID card. It's not a fake raid card, but I do also have software RAID 1 on my ubuntu box provided by mdadm.  The RAID card I now want to install is for an external SAS/SATA RAID storage array. I have the latest (v 10 ) kernel has I have just installed the latest version of ubuntu.

A few things I have managed to figure out so far:-
(i) the driver needed is for 'aac' according to documentation I can find - which is included in the Ubuntu distro supposedly.
(ii) the included driver doesn't work for me - the card is not recognised.
(iii) the Adaptec supplied software monitoring application - Storage Manager - doesn't work with the ordinary aac driver, but does with the Adaptec supplied aac driver
(iv) in order to install the Adaptec aac driver, the kernel needs to be patched.  
(v) when booting my machine there is an error - caused by the RAID card as the error does not happen with the card removed - where the system fails to scan my RAID card drives, and then wants to launch a maintenance module. I assume this is because it is not even recognising the card with the ubuntu aac driver, even though I have yet to attempt to install the Adaptec aac driver.

There are a few clues out there about patching a kernel, but none that look comprehensive - and nothing about the ubuntu 10 kernel.

Can anyone please help me at all ?

Many thanks

Hi jrleighton,

Sorry for resurrecting a dead thread, but did you ever work out how to use this card with Ubuntu? I'm at the same point you were, considering compiling the drivers provided by Adaptec into the kernel and wondering just how you do that. If you found a way to do this, or if r m h's solution worked it would be really good to get some feedback?

Cheers,
~Daniel

---

