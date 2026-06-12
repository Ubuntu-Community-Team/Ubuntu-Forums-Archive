---
title: "Wiping an SSD w/Linux"
date: 2010-12-28
forum: Hardware
---

### Post by emeraldgirl08 on 2010-12-28
I'm wondering if there's a utility in Ubuntu or linux in general that I can use to securely wipe an SSD? I've read through some forums and am a little confused. There's talk about "disabling AHCI" first and switching to "legacy mode." If anyone can help me I'd appreciate it.

I used to just use DBAN or Killdisk to do this on mechanical drives but SSDs are new to me.

TIA.

---

### Post by dabl on 2010-12-28
The same tools you use to wipe a conventional hard disk drive will work the same, with the same results, on a SSD.  I don't know of any reason why it would be necessary to change the SATA channel mode, just because you are performing a wipe operation.  If it is working correctly in AHCI mode, then leave it there to do the wipe.  If it needs to be Legacy IDE (or "compatibility") to work correctly for data storage, then you should leave it there to do the wipe also.

---

### Post by impact on 2010-12-28
I think it has something to do with the wear levelling.

---

### Post by runesvend on 2011-02-01
I'm also looking for a solution to this issue. I want to install Maverick, but before I do this I might as well wipe the drive to restore it to its original state. I tried this:

```
ubuntu@ubuntu:~$ sudo hdparm --trim-sector-ranges 0:156301488 /dev/sda
  trim-sector-ranges[0]: bad/missing sector count

```

Where 0 is the starting LBA and 156301488 is the number of sectors reported by hdparm:

```
ubuntu@ubuntu:~$ sudo hdparm /dev/sda | grep geometry
 geometry      = 9729/255/63, sectors = 156301488, start = 0

```

But as you can see it was a no go.

> **dabl said:**
> The same tools you use to wipe a conventional hard disk drive will work the same, with the same results, on a SSD.
SSDs need to be to told to delete blocks on the drive before it will actually use them again, because SSDs can't overwrite existing data, it needs to delete data, then write. Conventional HDDs can overwrite existing data without problems.

---

### Post by runesvend on 2011-02-01
After a bit of searching, I found a page that explains how to do this:

[https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)

As far as I can tell this does exactly the same as the HDDErase utility, except from within Linux :).

Note: I updated the hdparm utility to the version found in Natty (I'm running Maverick from a USB stick right now). You can get it here: [https://launchpad.net/ubuntu/natty/+source/hdparm/9.32-1ubuntu1](https://launchpad.net/ubuntu/natty/+source/hdparm/9.32-1ubuntu1)
just select your appropriate architecture under "Builds", and download and install the *hdparm_9.32-1ubuntu1_<architecture>.deb* package.

---

