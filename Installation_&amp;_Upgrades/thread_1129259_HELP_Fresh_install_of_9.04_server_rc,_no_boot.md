---
title: "HELP: Fresh install of 9.04 server rc, no boot"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by theosib on 2009-04-18
I'm stuck trying to figure out how to get my new Jaunty install to boot.

I just did a clean install of 9.04 server rc. I did have a heck of a time wresting with partman, but I finally, after several tries, got my disks set up with mdraid. 

Here's my partition layout (same on both disks, one on sda2, the other on sda4):
- Partition #2 at the beginning of the disk - almost all of the 500GB disk, raid physical
- Partition #1 at the end of the disk - 20GB swap

I used Software RAID to combine the two RAID partitions, to mount as /, formatted as ext4. The disks are SATA, as is the CDROM (which the installer had no trouble with). The motherboard is an MSI X48 platinum with an Intel X48 and ICH9R.

Grub obviously loaded, but perhaps one of the following happened:
- No mdraid driver is being loaded
- It can't find the drives
- Grub was not configured correctly
- The initrd was not setup correctly
- Something else, since I have no idea what I'm doing.

The install otherwise goes through just fine. Then it's time to reboot, and the first thing I get is four errors about there being "no block device found". It times out, then asks me if I want to boot degraded RAID, which itself times out too quickly, and then I get an error, "ALERT! /dev/md0 does not exist."

Dead in the water. This is a total show-stopper for me. Can anyone help?

---

### Post by cariboo on 2009-04-18
Have a look at this [thread=408461]software raid howto[/thread], it may help.

Jim

---

### Post by theosib on 2009-04-18
> **cariboo907 said:**
> Have a look at this [thread=408461]software raid howto[/thread], it may help.

Jim

I'll go through it, but what confuses me is that the installer seems to support installs to software RAID.  Plus, I've installed earlier versions of Ubuntu with software RAID.  So either there's a major oversight in the install process, software RAID support has been partially removed from Ubuntu, or there's some unrelated problem with the boot process.

---

### Post by theosib on 2009-04-18
Well, the How-To is for an older version of Ubuntu, so a lot of the process is automatic now.  Nevertheless, I'm basically doing all of the things that it says to do.  It just won't boot.

---

### Post by theosib on 2009-04-18
I forgot to mention that the first error I get is "no block devices found".

---

### Post by theosib on 2009-04-18
I did some poking around.  When the boot fails, I'm dropped into busybox.  I can type these:

mdadm -As
exit

And then the system boots.

How do I fix this permanently?

---

### Post by theosib on 2009-04-18
Does no one actually use RAID1 with ubuntu?  If not, can someone suggest another distro to use instead that does support software RAID well?

---

### Post by wiz561 on 2009-06-01
If you haven't given up yet, I just wanted to let you know that I'm having the same exact problem with raid0.  :(

---

