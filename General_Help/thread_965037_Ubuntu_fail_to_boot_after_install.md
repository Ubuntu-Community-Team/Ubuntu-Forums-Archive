---
title: "Ubuntu fail to boot after install"
date: 2008-10-31
forum: General Help
---

### Post by SpinningAround on 2008-10-31
After I had installed ubuntu (32bit) without any problems did I reboot and waited for ubuntu to boot up, then this message showed up during the boot.

COMRESET failed (errno=-16)

unsure what it mean, it also did start initramfs that I think is a type of terminal, is there any way to fix this problem? I noticed with my other computers that a kernel update is released, is there some way from me to update my system in the current state?

---

### Post by ddrichardson on 2008-11-01
If you are running 8.10 then there are three things you can try, if not then try 8.10:

At the grub menu, can you press "e" then add 
```
irqpoll
```
To the end of the kernel line.

Set you SATA mode to AHCPI in BIOS.

Upgrade your BIOS.

Let me know if this doesn't help.

---

### Post by SpinningAround on 2008-11-02
> **ddrichardson said:**
> If you are running 8.10 then there are three things you can try, if not then try 8.10:

At the grub menu, can you press "e" then add 
```
irqpoll
```
To the end of the kernel line.

Set you SATA mode to AHCPI in BIOS.

Upgrade your BIOS.

Let me know if this doesn't help.

I think I have set it to AHCPI since I where able to install XP pro without any problems, old version of XP that didn't include SP1 or SP2

My bios should be up to date tho my motherboard is quite old so the last update was 2006 or so, here is the motherboard [URL="http://global.msi.eu/index.php?func=proddesc&maincat_no=1&cat2_no=&cat3_no=&prod_no=177"]
K8N Neo4-F[/URL]

I tried irqpoll but did get this message
```

(initramfs) irqpoll
/bin/sh: irqpoll: not found
(initramfs)

```

I tried to do some more searching regarding the problem and I think it has something to do with my SATA cable and motherboard only supporting 1.5Mbit while my harddrive support 3.0Mbit. Something that maybe also causing a problem is that I have set up one "/" partition and one "/home" partition.

what are ata3 and ata4, are they partitions or entire disks 
Some of the info that is printed out
```

Ubuntu 8.10, kernel 2.6.27-7-generic

ata3: link is slow to respond, please be patient (ready=0)
ata3: COMRESET failed (errno=-16)
Done
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmd/cmdline)
	- Check rootdelay= (did the system wait long enough?)
	- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/84d40c08-e648-4010-ad0a-c3257c66df7e does not exist. 
Dropping to a shell

BusyBox v1.10.2 (ubuntu:1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs) [58.588022] ata3: COMRESET failed (errno=-16)
ata3: COMRESET failed (errno=-16)
ata3: rest failed, giving up
ata4: COMRESET failed (errno=-16) /* only "normal mode" */
ata4: rest failed, giving up /* only "normal boot" and "normal mode" stop here */
ata3: limiting SATA link speed to 1.5 Gbps /* only in recovery mode */
...
Driver 'sd' needs updating - please use bus_type methods /* only in recovery mode */
sd 6:9:9:9: [sda] Attached SCSI removable /* only in recovery mode */

```

---

### Post by ddrichardson on 2008-11-02
Did you type noirqpoll onto the end of the kernel parameters at the boot menu?

---

### Post by SpinningAround on 2008-11-03
Sadly do it look like none of them worked (unsure what they would do) I guess it have something to do with Ubuntu using 3Mbit for SATA and not 1.5Mbit since my system don't work with 3Mbit together with my ubuntu installation being partition.

I notice this post from someone that did have the same problem as I [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=962818](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=962818)

---

### Post by ddrichardson on 2008-11-03
There are two bugs that this seems similar to:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256637](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256637)
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/150259](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/150259)

---

