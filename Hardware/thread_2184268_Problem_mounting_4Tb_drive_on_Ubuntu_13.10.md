---
title: "Problem mounting 4Tb drive on Ubuntu 13.10"
date: 2013-10-28
forum: Hardware
---

### Post by subs2 on 2013-10-28
On a new installation of Ubuntu Server 13.10, I'm having problems setting up Seagate 4Tb desktop drive.

When connecting it via either the internatl SATAIII 6Gbs or SATAII 3Gbs connectors on the motherboard, the drive does not show up when I run BLKID. However, the drive does show up using FDISK -l but with issues since it says it does not support GPT disks - but at least it shows that the system is seeing the drive. It gives it a logical location (sdd1) but I can't mount to that at all.

However, when I connect the drive via a SATA-to-USB3 converter and plug it into one of the USB3 ports, Ubuntu picks up the drive perfectly with no hassles. Shows up fined in BLKID and mounts with no problems.

Can anybody think of a reason why I can use the drive in USB3, but not SATA? 

What do I need to do to get it to recognise the drive via a SATA connection?

---

### Post by oldfred on 2013-10-28
You cannot use fdisk on gpt drives and a drive that large must use gpt partitioning. 
Download and use gdisk which is the fdisk for gpt drives.
       MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

sudo apt-get install gdisk
      
 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

Is this perhaps an Asrock motherboard? The asmedia ports have issues.
Someone posted this:

 So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!

---

