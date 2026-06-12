---
title: "Recover Raid 0+1 with one dead hard drive"
date: 2008-10-21
forum: Hardware
---

### Post by wtfbrb on 2008-10-21
I had a dual boot system going with windows 2003 and ubuntu, I was down to using quickbooks and dreamweaver in my windows system which had a raid 0+1, that is 4 disks.  One of them died and it doesn't want to boot anymore.  I don't really want to dual boot anymore any how I can create a virtual box for my 2 windows needs.  But I do need all the data off the broken raid.  I have looked through the data recovery options for ubuntu, but I don't know what to use or do I think they quite cover my situation.  I found dmraid, but it doesn't seem to do it since my array is broken.  Here is what dmraid -r gives me:

/dev/sdd: isw, "isw_dadgbjihhe", GROUP, ok, 72303837 sectors, data@ 0
/dev/sdb: isw, "isw_dadgbjihhe", GROUP, ok, 72303837 sectors, data@ 0
/dev/sda: isw, "isw_dadgbjihhe", GROUP, ok, 72303837 sectors, data@ 0

then dmraid -ay gives:
ERROR: isw: unsupported map state 0x2 on /dev/sdd for raptors
ERROR: adding /dev/sdd to RAID set "isw_dadgbjihhe"
ERROR: removing RAID set "isw_dadgbjihhe"
ERROR: isw: unsupported map state 0x2 on /dev/sdb for raptors
ERROR: adding /dev/sdb to RAID set "isw_dadgbjihhe"
ERROR: removing RAID set "isw_dadgbjihhe"
ERROR: isw: unsupported map state 0x2 on /dev/sda for raptors
ERROR: adding /dev/sda to RAID set "isw_dadgbjihhe"
ERROR: removing RAID set "isw_dadgbjihhe"


Any suggestion, it has been 2 months since I backed up my data...

---

### Post by jmate24 on 2008-10-28
Is your windows partition dead?
If it is then can you access your ubuntu installation?
Do you have backups of your files?
Do you have an available external usb, firewire, or eSATA drive with enough space for your useable files? (to backup the install that is currently working)

---

