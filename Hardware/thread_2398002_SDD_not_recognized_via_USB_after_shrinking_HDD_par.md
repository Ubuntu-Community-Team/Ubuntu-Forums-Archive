---
title: "SDD not recognized via USB after shrinking HDD partitions"
date: 2018-08-06
forum: Hardware
---

### Post by tL0z on 2018-08-06
Hi everyone,

I bought a Samsung EVO 860 500GB SSD for my Samsung 700Z3C which currently has a 1TB HDD. My plan was to clone the HDD to the SSD with GParted via USB and then to physically replace the disks. 

My HDD has a Windows partition which I occasionally use to play games, and a few partitions for Ubuntu. As I was about to copy the partitions from the HDD to the SSD, I learned that I had to shrink the partitions in the HDD before copying them to the SDD. At this stage the SSD was successfully recognized both by Ubuntu and by the GParted live USB.

I then did the following:
[LIST=1]
[*]Logged into Windows and shrank the Windows partition using the Windows built in tool.
[*]Booted with the Gparted Live usb and shrank the couple Ubuntu partitions.
[/LIST]

After doing this, my SSD was no longer recognized by GParted or Ubuntu through USB. Any idea of what might be wrong? 

Thank you.

---

### Post by oldfred on 2018-08-06
New UEFI based systems use gpt partitioning.
And you cannot easily clone partitions. Gpt has GUID for each partition and those are stored in both the partition table and the backup partition table. If you just clone a partition, then you have a GUID in partition that does not match partition table. 

You can clone entire drive, but if SSD is smaller, must use tools that do not copy the unused space.
If Windows was not involved, I would suggest partitioning in advance and a total new install in UEFI mode to SSD. Then copy ESP & /home from HDD to SSD. If you have manually installed lots of apps you can export list to make it easy to reinstall. And if you manually edited hardware settings those would be in /etc. This is just like restoring from your backup, which then becomes a good test of your backup procedures and relatively save, since you still have HDD to find what you originally miss.

But with Windows I think you have to clone, unless you really wanted a new clean install of Windows.

Do not know Windows tools, and I do not use cloning as backup, but have seen these recommended.
       **Full image backups**
[http://clonezilla.org/](http://clonezilla.org/)
[https://www.ostechnix.com/systemback-restore-ubuntu-desktop-and-server-to-previous-state/](https://www.ostechnix.com/systemback-restore-ubuntu-desktop-and-server-to-previous-state/)
fsarchiver
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page) 
[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

---

### Post by tL0z on 2018-08-07
Hi oldfred,

Thanks for your reply.

The current partition table in my HDD is MSDOS, not GPT. Do you think it would be better to use GPT? In addition, my laptop still has a BIOS, not UEFI, would it be better to upgrade it?

Nonetheless, do you have any idea of why my SDD can't be recognized? Yesterday I plugged it to another laptop, and no luck too. Do you think it died?

---

### Post by oldfred on 2018-08-07
My first small SSD was on my old BIOS system. I also had XP. But XP only booted with drive set for IDE and SSD only booted with drives set for AHCI. So I retired XP. :)

Check that drives are set for AHCI, not RAID, nor IDE or anything else.

Only a very few systems had ways to convert from BIOS to UEFI. But if system is less than 5 years old it is UEFI, and many vendors still call it BIOS. When Windows 8 came out 5 years ago all systems had to be UEFI.

If drive is MBR, Windows has to boot in BIOS mode. You cannot easily convert to gpt as Windows only boots from gpt with UEFI.

And if BIOS/MBR systems, you can copy partitions. But may have to run repairs to fix booting issues.
If cloned, you also cannot keep both drives active at same time. You will have duplicate UUIDs once cloned and duplicate UUIDs are not allowed. Or if used, you may one time save data to one drive and next time to the other drive as it depends on which drive BIOS sees first on which it may use.

---

