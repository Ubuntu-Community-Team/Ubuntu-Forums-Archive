---
title: "No Operating System after Normal Install ?"
date: 2005-12-16
forum: Installation &amp; Upgrades
---

### Post by Fermanagh on 2005-12-16
I am trying to install EdUBUNTU 5.1 (i386) on an IBM Netfinity 3000 machine that has SCSI Hard Drives. The Hard Drives don't show up in BIOS as IDE devices. The install seems to run OK, but when I then try to start the system, it goes through the BIOS stage and then reports that there is no operating system on the machine? I tried the defaut install and rhe server install and both installs behave the same way. It's like the hard drive is seen during the install, but the machine can't see the edubuntu operating system. This is my 1st time doing an install on a machine with SCSI drives. Does anyone have any ideas on what the problem might be?

---

### Post by prammy on 2005-12-16
You said your drives are scsi but shows up in BIOS as IDE drives ?

You may have IDE drives on your machine (which you may have installed Ubuntu to), but IDE is not set to boot and thus is trying to boot from the SCSI (which has no OS on it).

---

### Post by Fermanagh on 2005-12-17
There are no IDE drives in the machine. 

The machine has 2 SCSI drives. The normal motherboard BIOS can't see the SCSI drives. 

When the machine boots, I get a message that the SCSI BIOS is OK. 

This tells me that the SCSI drives have their own seperate BIOS. 

The install of edubuntu is normal, but when I then try to boot into edubuntu, the machine reports that there is no operating system on the machine.

I did some research and learned that the SCSI bus is completely seperate from the motherboard's main bus. When your computer boots and finds a SCSI adapter on the motherboard, it does not see the details of the drives.

In fact, if you go into the normal BIOS, you see that all of the IDE drives report that their are no IDE drives on the machine. 


It seems like, what I might need is a special boot disk or boot CD that somehow tells the machine to go to the SCSI hard drive to find the operating system during a normal boot.


The edubuntu OS is installed on the SCSI drive, but when the machine boots it does not see the OS on the SCSI drive and simply reports that there is no operating system on the machine.

One fix is to simply remove all the SCSI drives and the SCSI adapter from the machine and install a new IDE drive.

---

### Post by kosmic on 2005-12-17
OR in the instalation when you get to the GRUB part instead of putting GRUB in the MBR save the GRUB to a floppy drive :)

---

### Post by afhp on 2005-12-17
Doesn't the Netfinity BIOS have an option to boot from SCSI devices ? That's what you'd need.

---

### Post by AllenGG on 2005-12-17
As above:
 "Doesn't the Netfinity BIOS have an option to boot from SCSI devices ? That's what you'd need."
The SCSI (scuzzy) is always set from the BIOS. Tricky.
And most BIOS sets see S-ATA as scuzzies.
You may have to go here:
[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-4HLQKZ&tempselected=5]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-4HLQKZ&tempselected=5")

The "RAID" feature is, usually, automatically selected, but the Netfinity machines have been around for some time. You need to de-select the RAID .
In many installs that I've seen, the BIOS is 90% of all problems.
Allen

---

### Post by Fermanagh on 2005-12-17
All,
Thanks for your help. 
I was able to fiddle with the BIOS settings and now everything works OK. 
The setting to boot from the SCSI drives was not obvious.

---

