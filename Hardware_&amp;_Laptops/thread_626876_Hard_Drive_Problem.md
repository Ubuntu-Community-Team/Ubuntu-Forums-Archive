---
title: "Hard Drive Problem?"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by hagstrom on 2007-11-29
I'm having a persistent problem with my linux filesystems. My system is an amd laptop with a 64 bit processor, running Ubuntu 7.10 and windows (because I don't have a 64 bit linux compatible version of matlab).

I originally had 6.06 and it was working perfectly. Then it started having problems, specifically when the computer would start up there would be filesystem errors. Often times fsck would not be able to automatically fix it and I would have to run fsck -y . 

The typical output of this program was a list of thousands of different errors on my filesystem (which was ext3). The most common of these was a "Buffer I/O error". If it helps I can find the actual output from fsck. At first this worked, but the problems worsened and started to effect the functioning of the operating system in various ways, and Ubuntu started working inconsistently. Sometimes it would start correctly, sometimes it wouldn't start at all, sometimes it would freeze while I was using it, and a host of other little things.

Interestingly, Windows hasn't had major problems, but I have noticed a few times it has claimed that its filesystem had errors and it needed to use its own filesystem utility. I strongly suspect that this is related to the problem on the linux filesystem. This is why I'm worried that I have a hardware problem.

I since have switched to Ubuntu 7.10, which works great when it starts, but was difficult to install (the installer had trouble dealing with the filesystem) and starting. It has the exact same problem with fsck and Buffer I/O errors.

Based on my description of the problem, do you guys think I have some sort of hardware problem? I looked around the forum and there seemed to be one or two other threads where a similar problem occurred, but in those cases it was less persistent, i.e. it was fixed by running fsck -y manually. Could it be possible that I just haven't used fsck correctly (perhaps it didn't have the correct permissions or didn't do what it needed to or something like that?)

And lastly, is there some utility (Linux or otherwise) that can check my harddisk for "physical" problems? I seem to remember using one many years ago, and it would be convenient if there was a simple diagnostic tool that could determine if I needed to replace my harddrive.

Anyways, I appreciate any information that ya'll can provide.

---

### Post by matthewboh on 2007-11-30
I'm having a similar problem.  Basically, I've been running 7.10 Gutsy for about a month now, and just started getting errors during boot.  Here's some of the lines from the kern.log file

```
Nov 30 13:21:02 mlb-laptop kernel: [ 2458.584000]          res 51/40:04:53:ae:d0/00:00:00:00:00/e0 Emask 0x9 (media error)
Nov 30 13:21:02 mlb-laptop kernel: [ 2458.608000] ata1.00: configured for UDMA/100
Nov 30 13:21:02 mlb-laptop kernel: [ 2458.608000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 30 13:21:02 mlb-laptop kernel: [ 2458.608000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Nov 30 13:21:02 mlb-laptop kernel: [ 2458.608000] Descriptor sense data with sense descriptors (in hex):
Nov 30 13:21:02 mlb-laptop kernel: [ 2458.608000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Nov 30 13:21:02 mlb-laptop kernel: [ 2458.608000]         00 d0 ae 53 
Nov 30 13:21:02 mlb-laptop kernel: [ 2458.608000] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Nov 30 13:21:02 mlb-laptop kernel: [ 2458.608000] end_request: I/O error, dev sda, sector 13676115
Nov 30 13:21:02 mlb-laptop kernel: [ 2458.608000] Buffer I/O error on device sda1, logical block 1709506
Nov 30 13:21:02 mlb-laptop kernel: [ 2458.608000] ata1: EH complete
Nov 30 13:21:02 mlb-laptop kernel: [ 2458.616000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Nov 30 13:21:02 mlb-laptop kernel: [ 2458.616000] sd 0:0:0:0: [sda] Write Protect is off
Nov 30 13:21:02 mlb-laptop kernel: [ 2458.616000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 30 13:21:02 mlb-laptop kernel: [ 2458.616000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 30 13:21:02 mlb-laptop kernel: [ 2458.616000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Nov 30 13:21:02 mlb-laptop kernel: [ 2458.616000] sd 0:0:0:0: [sda] Write Protect is off
Nov 30 13:21:02 mlb-laptop kernel: [ 2458.616000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 30 13:21:02 mlb-laptop kernel: [ 2458.620000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

So, I booted off a LiveCD (7.04) and unmounted the hard disk drive and ran
```

fsck -f /dev/sda1
```

and there were no errors, no problems reported.  However, I am still getting the error.  There is one file that constantly causes the disk to hash - it's /var/log/messages and I get the same error messages in the kern.log.  Any ideas on how to fix?

---

### Post by crouton on 2007-11-30
There are various manufacturer utilities to check harddrive status, but you have to find out what brand you have first.  'dmesg | grep hd' for IDE and 'dmesg | grep sd' for SATA will get you something like ** hdd: ST3120814A, ATA DISK Drive **.  A google search would help you determine who made the drive and how to get the utility.  (Mine is a Seagate.)

I/O buffer errors usually indicate hardware failure of some type. If Windows and Linux are sharing the same harddrive and both are complaining, start your backups ASAP and get another drive.

---

