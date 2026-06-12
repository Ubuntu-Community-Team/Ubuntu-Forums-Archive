---
title: "Problems With HP-dv5000 Hardrive"
date: 2010-06-17
forum: Hardware
---

### Post by schach on 2010-06-17
I have a HP-dv5000t laptop, which is about 5 years old. It functioned fine (with Ubuntu 9.04 I believe, but I really don't remember) until just a few days ago. I would try to turn it on and after loaded for a little while it said "Kernel Panic: Unable to load init" or something of the sort (I understand direct quotes would be more helpful, but I hadn't written them down). I tried booting from various diferent kernel options I had on the system (all 2.6.something.number that went down by 1 for each selection) which I had accessed by pressing escape while grub was loading.

So after feeling rather hopeless for that, I downloaded a 10.4 iso and put it on a CD. I boot up, go into the live CD hoping to be able to back up some of my data (which is on a separate partition; I have one for my /home directory and one for /). only to encounter an error that says:

```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```So here is the output of dmesg | tail
```
ubuntu@ubuntu:~$ dmesg | tail
[ 3804.503232] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 3804.503244] Descriptor sense data with sense descriptors (in hex):
[ 3804.503251]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 3804.503279]         02 9f 8b 3b 
[ 3804.503291] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 3804.503306] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 02 9f 8b 3b 00 00 08 00
[ 3804.503332] end_request: I/O error, dev sda, sector 44010299
[ 3804.503378] ata3: EH complete
[ 3804.503414] EXT3-fs error (device sda4): ext3_get_inode_loc: unable to read inode block - inode=8, block=1033
[ 3804.503724] EXT3-fs: no journal found.
```So I think maybe this problem will magically solve itself after the reinstall (perhaps by quickly convert to various religions and begin praying until it does magically fix itself), so I try to install 10.4. Everything in the install goes normal and then I partition the harddrive, keeping my /home directory intact and formating what was the / partition (would should be noted was able to mount when the /home couldn't). But around 75% or so during the "copying files" part of installation a window pops up that says that there was an error. I remember the first time I tried and failed it mentioned something about the possibility of my harddrive malfunctioning, either by overheating (which I doubted, it didn't seem too bad to me) or some sort of hardware malfunction. The second time I tried to install it didn't say the exact same error message, but still told me that there was an error that required it to quit the install.

So next I open up "Disk Utility" under System>Administration and run a "Check File system" test and it tells me:
```
File system check on "98 GB Filesystem" (Partition 4 of ATA ST9120821AS) completed
File system is NOT clean.
```I don't know. Do you guys have any ideas? 

By the way, thanks for reading this post, and potentially responding/solving the problem in advance.

---

### Post by schach on 2010-06-19
Well, I tried to install 10.4 again, and it worked this time (I have no idea why) and am typing this off of my new install.

However, i still cannot mount my separate partition that has my data on it. Any ideas would be appreciated.

---

