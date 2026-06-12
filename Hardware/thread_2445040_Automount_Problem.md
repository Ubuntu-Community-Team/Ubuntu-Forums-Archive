---
title: "Automount Problem"
date: 2020-06-08
forum: Hardware
---

### Post by Ronco Pizatto on 2020-06-08
I had Ubuntu 18.04 running well for many months but my motherboard got buggy. 

I moved my original desktop's SSD with Ubuntu 18.04 to an HP 6300 SFF i5 computer.
Everything works great except automount.

When i first boot I can plug in a flash drive and it automounts and works.
If I work a while and then plug it in, no automount.

when unmounted lsusb shows the flash drive. Disks and gparted do not.

I reboot and the same flash drive automounts fine.

Also if I eject the first auto mounted drive and plug in another I get the name of the first drive displayed instead of the name of the newly inserted drive.

My phone requires a reboot to automount and my external usb hard drive needs a reboot to automount.

Thanks for any suggestions.

---

### Post by TheFu on 2020-06-08
I don't have 18.04, just 16.04 and 20.04. The 20.04 is a virtual machine, so I've not tried USB connected devices with it.

I've seen autofs acting a little flaky too.  I don't reboot, just manually **umount** the storage. Reboot isn't something I do very often, usually just after a new kernel is installed on Saturday mornings.  
```
$ uptime
 12:43:05 up 9 days,  5:09,  5 users,  
```

The connected USB storage doesn't always get seen by the kernel/udev according to **dmesg**, so I'm guessing a kernel or udev problem.  When the USB storage does show up in dmesg, the mount works as expected.  I have 2 USB3 ports on the front of the system. The right port doesn't register storage changes.  The left port does:
```
[795758.140264] sd 16:0:0:0: [sdc] Write Protect is off
[795758.140268] sd 16:0:0:0: [sdc] Mode Sense: 34 00 00 00
[795758.143263] sd 16:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[795758.155304]  sdc: sdc1
[795758.161242] sd 16:0:0:0: [sdc] Attached SCSI disk
```
This is the exact same storage and has been used and working for years on many different Linux systems, including this one.  It is only in the last few months this problem started.

The front-port device is an after-market thing with support for 35+ different USB2, USB3, eSATA, mSATA, SDHC, MicroSD, MemoryStick, and CF slots. It also has audio-mic and audio-speaker/headset jacks that work.  It is about 18 months old. Only reason I got it was really for the USB3.1 and eSATA ports, but the others were *nice-to-have*. Competing products didn't have as many ports and were more expensive.  Have an Anker 2-USB3 port front-panel on another box and it has been working flawlessly 5+ yrs. Next time, I'll stick with Anker or a powered Anker USB3+ hub. Always get powered external hubs.

I've been playing with the systemd-automounter and it behaves a little differently, but once mounted, it is solid.  It doesn't seem to honor the autofs-like timeout option for releasing unused mounts. That's the only reason I still use autofs - well, plus the "ghost" option is convenient for some end users with their point-n-click needs.

Does **dmesg** show your USB storage connections?  If so and the problem still exists, then our issues are different.

```
tf@hadar:/misc/250G$ df -h  .
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdc1       233G   72M  233G   1% /misc/250G

tf@hadar:/misc/250G$ mount|grep 250
/etc/auto.misc on /misc/250G type **autofs** (rw,relatime,fd=6,pgrp=9407,timeout=60,minproto=5,maxproto=5,direct,pipe_ino=4725855)
/dev/sdc1 on /misc/250G type fuseblk (rw,nosuid,nodev,noatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096)
```
Those are my mount options for this specific USB storage.

Don't know if this matters, probably not, but my USB storage above has NTFS for the file system.

Check dmesg.

---

### Post by Ronco Pizatto on 2020-06-09
Thank-you tremendously for the detailed answer.

dmesg uncovered a system problem. The dmesg output says "No NVIDIA graphics adapter found!"
This is correct since I have an AMD 7570.
Then it says that it unregistered the Nvlink Core for major device number 239
These 2 lines from dmesg are repeated about 100 times or more. That's all.
The mounted flash drive is not mentioned.

I'll try NTFS. All my flash drives are FAT32.

More info coming later.

---

### Post by TheFu on 2020-06-09
Does dmesg show the storage device about 2-5 seconds after you plug it in?  Yes or no?  The file system has NOTHING to do with the plug/unplug dmesg results.  At least I don't think it does.  Changing the file system shouldn't matter.

The GPU thing isn't related.

I'm using NTFS for 1 HDD only.  All my other storage uses ufs, NFS or f2fs or some other native-Linux storage. The file system that should be used depends on the other devices that need to read it.  99% of the time, my flash storage is only used by Linux systems and f2fs is specifically designed for flash media use while retaining Unix permissions and flash performance.

---

### Post by Ronco Pizatto on 2020-06-09
You got me thinking about what might impact usb performance.
That jogged my memory and I realized that I implemented Unity desktop last year and my system has booted Unity ever since.
I switched back to Gnome and no more usb malfunction.

I don't know what goes on in Unity or Gnome to impact usb service but something does.

Many thanks. I wouldn't have thought my way through this without your help.

PS - It's interesting that this particular problem only started when I switched from my Gigabyte/AMD FX system to my HP 6300 i5 system.
The Gigabyte board had a documented USB issue but completely different from the HP system with Unity.

---

### Post by TheFu on 2020-06-09
I suspect you use the term "automounter" without really understanding that is a very specific tool, controlled by autofs.  These don't have anything to do with GUI stuff and are configured only through /etc/ text, config, files.

IMHO, GUIs cause 90% of all issues. Unity was a set of problems and Gnome3 brings 2x more problems since the Gnome developers have a very different philosophy about this stuff than a typical Unix developer does.  Best to avoid them when possible.  

I bet you could setup a true autofs solution that "just worked." Fear the GUI.

---

### Post by Ronco Pizatto on 2020-06-10
Yes. I lack understanding of all things automount. As such, I appreciate your patience.

You caused me to uncover my problem. So if I can figure how to mark this solved, I'll do so.

---

