---
title: "Hard Disk not recognized! please help!"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by Ionut_Romania on 2007-11-13
Hello!
I have a problem with my Fujitsu Siemens AMILO Pro V3515.
When i try to install Ubuntu LTS6.06 Drapper Drake it doesn't recognize my Hard Disk. I have a 80 GB SCSI HDD that came with my laptop. This drive currently has no partition on it. I can't download or upgrade ubuntu since there's no space to save the download in, and i would appreciate if anyone can give me some advice. I really like Ubuntu and i don't want to go back to windows xp.
Please help!
thank you

---

### Post by briandu on 2007-11-13
[COLOR=Black]Do yourself a favour[/COLOR][COLOR=Black] a first boot up with DSL/PartImage and see if the disk is visible. U can the partition by hand if you want and get it ready for Ubuntu.

a;so check your BIOS to ensure the drive is mapped scsi ans IDE
[/COLOR]

---

### Post by tech9 on 2007-11-13
> **Ionut_Romania said:**
> Hello!
I have a problem with my Fujitsu Siemens AMILO Pro V3515.
When i try to install Ubuntu LTS6.06 Drapper Drake it doesn't recognize my Hard Disk. I have a 80 GB SCSI HDD that came with my laptop. This drive currently has no partition on it. I can't download or upgrade ubuntu since there's no space to save the download in, and i would appreciate if anyone can give me some advice. I really like Ubuntu and i don't want to go back to windows xp.
Please help!
thank you

check your BIOS to make sure your HD shows and is enabled.

---

### Post by pete.dawgg on 2007-11-13
do an ```
lspci
``` and modprobe the right modules for your scsi-controller. if the ubu-install (=busybox) shell is too limited, use a different cd to boot, like system-rescue-cd ([www.sysresccd.org](www.sysresccd.org))
should be no problem.

---

### Post by Ionut_Romania on 2007-11-13
I'm back. i just tryied an windows xp setup and it works just fine. what you are talking about is chinese to me. i only have this ubuntu cd and windows xp sp2 pro in hand. this is the first time i'm trying to install Ubuntu. so if you know some "ubuntu-for-dummies" about how to fix my problem please let me know. The HDD works just fine when attepmting an windows installation, but doesn`t get recognized by Ubuntu setup, Partition Editor or Drive information. I'm really starting to freak out, cause i'm fascinated with Ubuntu, and shoul i can't install it it wil break my heart:)

so, on the short-term: what i'm really trying to ask you if you can explain the sollutions offered by you in plain english. what exactly am i suposed to do? and where do i find DSL/PartImage?

there's a six-pack of Carlsberg at stake:)

---

### Post by taurus on 2007-11-13
Boot from Ubuntu LiveCD.  Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- Lower case letter l, not number 1.
```

---

### Post by Ionut_Romania on 2007-11-13
> **taurus said:**
> Boot from Ubuntu LiveCD.  Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- Lower case letter l, not number 1.
```

done that. nothing happens, the terminal just brings out another line

ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$


that's all that it says.
this is really starting to get on my nerves...
got another sugestion?

---

### Post by az on 2007-11-13
> **Ionut_Romania said:**
> 
this is really starting to get on my nerves...
got another sugestion?

The hard drive is either not working, misconfigured or it is not plugged in properly.

Most laptops use the drive in single drive mode (no jumpers on any connections.  You can try playing around with the jumpers, making the drive master or CS.  Also, on some motherboards, you need to have the BIOS auto-detect the hardware when you change drives/cdroms.

---

### Post by Ionut_Romania on 2007-11-13
okay, i'm back, one more time.
i did the following: installed windows xp professional sp 2, then i created a 2 gb Linux - Swap partition using Partition Magic 8 and a Linux EXT3 30GB partition using the same program. Still no results yet, Ubuntu doesn't "see" any hard drive on my computer, just the two: tmppfs and unionfs (hope i typed correctly). Windows works just fine. I remember that i did the same thing on a desktop, using the same Ubuntu CD and it recognized that hard drive, but for some reason Install didn't start. I also have a Kiwi - Linux CD. i'll try that one, see how it works.
Anyway, thank you for your kindness and i hope i become a Ubuntu proud user soon:)

---

### Post by Ionut_Romania on 2007-11-13
i made the partitions, the livecd starts, ubuntu starts but it says "BIOS BUG #81 FOUND" and "cannot allocate mem resources" like 3 times. i have absolutely no idea why is this happening to me...

---

### Post by dabl on 2007-11-13
Mehhh -- I just did a Google search on "bios bug #81"  -- wow, what an eyeful!  Maybe there's a solution in there somewhere .....   :(

---

### Post by zazuge on 2008-05-30
U have to install a new kernelthat handle sata HD
I've run into this with my fathers v3515
old distos don't detect the HD
Ubuntu 7.04 and up got no problems iwth it.

---

