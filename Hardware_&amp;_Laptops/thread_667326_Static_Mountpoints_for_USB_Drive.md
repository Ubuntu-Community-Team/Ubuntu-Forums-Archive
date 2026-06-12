---
title: "Static Mountpoints for USB Drive?"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by dgray_from_dc on 2008-01-14
Thought I'd revive my question from here [http://ubuntuforums.org/showthread.php?t=613075](http://ubuntuforums.org/showthread.php?t=613075)

I'm trying to create a RAID 5 using USB disks.  However, when Linux detects USB disks, it's first come, first serve for mountpoints.  I've had some success without static mountpoints.  ([http://ubuntuforums.org/showpost.php...2&postcount=20](http://ubuntuforums.org/showpost.php...2&postcount=20)) However, I want this server to be as stable as possible.

I've looked this up before and this is what I found [http://ubuntuforums.org/showthread.php?t=91948](http://ubuntuforums.org/showthread.php?t=91948)

This solution didn't work as it was written a few years ago for Dapper and does not work with Dapper in its current state.  There have since been changes in how disks are handled.

Any thoughts?

---

### Post by kidders on 2008-01-15
Hi there,

You shouldn't be trying to mount individual components of a RAID array ... it could be quite destructive. The only thing that should have a mount point is the array itself.

---

### Post by dgray_from_dc on 2008-01-15
I'm not actually trying to mount each disk.  However, each disk has to have an identifier i.e. /dev/sda, /dev/sdb etc.  I wish to make those static.

---

### Post by kidders on 2008-01-16
Hey again,

In that case, creating a set of udev rules is the right thing to do ... along the lines of one of the threads you mentioned.

If it doesn't work for you, there are a few things you could check...[LIST]
[*]Did you remember to run **sudo udevcontrol reload_rules** after altering your udev rules? (Rebooting will also do the job, but it takes longer.)
[*]Are your new rules too early or too late in the rule chain?
[*]Are you using device attributes from more than one level in your device chain? (That one requires a little explanation!)
[*]Are the sysfs/etc. details you specified for your devices really correct? Sometimes, for example, hardware manufacturers pad attribute names with spaces ... so you may need to write [FONT=Courier New]**ATTRS{model}=="ST3500841AS     (spaces here)" **[/FONT]instead of[FONT=Courier New]** "ATTRS{model}=="ST3500841AS"**[/FONT].[/LIST]A quick note about device chains...
[SIZE=1]Utilities like **udevinfo** scan a device (eg as USB hard disk), and then work upwards through your SCSI interface controller, USB host, and so on, right back to the PCI interface that connects your hardware to your motherboard. When writing udev rules, you can only use information from one level in the chain ... ie a rule describing the manufacturer of your USB controller and the model name of the device plugged into it won't work.
[/SIZE]
If you find udev a bit weird, there *may* be a way to avoid having to mess with it. For example, the mdadm.conf for one of my arrays contains...```
DEVICE /dev/hda6 /dev/etherd/e1.[0123456789]
```...which means that /dev/hda6, and any of /dev/etherd/e1.0, /dev/etherd/e1.1, etc. may be part of the array. If, for the sake of example, you composed your array out of **/dev/sd[abcde]1**, it may not turn out to matter that the /dev names of your USB disks move around a bit.

Alternatively, you could take a look at the contents of /dev/disk for other ways of addressing your dynamically named devices. The subdirectories of /dev/disk contain symlinks whose names describe things like UUIDs, device addresses, etc., and always point to the correct place (eg /dev/sdb), even if its name changes between reboots.

Anyhow, these may be things you've already dismissed as possible solutions, but I thought I would mention them, just in case. If you'd prefer to stick with your preferred option (ie forcing your devices' /dev names to be consistent), could you post the rules you've created and some "udevinfo" output, just in case there's something wrong that's easy to spot?

---

### Post by dgray_from_dc on 2008-01-17
You just went completely above and beyond my knowledge base.  I think understand what you are saying, and thats probably what I want to do.  Is there a thread or sight you can point me to with a tutorial?

---

### Post by kidders on 2008-01-17
Oops... sorry about that. There are udev & RAID tutorials all over the place ... Google/etc. are probably your best bet, imo.

Essentially, what I meant to say in my last post is that you probably don't *have* to go fiddling with udev (because you don't really _need_ static /dev names to use RAID). Just in case you want to create static /dev paths to your devices anyway though, I felt I should try to come up with a list of common pitfalls.

In any case, I wouldn't advise tinkering with your udev configuration until you are reasonably familiar with how it works ... mistakes have the potential to screw up your device management. You might like to take a look at [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html) or similar documents, for some background info.

---

### Post by dgray_from_dc on 2008-01-17
Thanks for all the help!!  I'm on a business trip now, but I can't wait to experiment.

---

### Post by dgray_from_dc on 2008-01-23
I've returned from my business trip, and I'm starting my build-up.  I ran across this post [http://ubuntuforums.org/showthread.php?t=663240](http://ubuntuforums.org/showthread.php?t=663240)

And it brought up an interesting question.  Would the method you described

> If you find udev a bit weird, there may be a way to avoid having to mess with it. For example, the mdadm.conf for one of my arrays contains...
```

DEVICE /dev/hda6 /dev/etherd/e1.[0123456789]

```
...which means that /dev/hda6, and any of /dev/etherd/e1.0, /dev/etherd/e1.1, etc. may be part of the array. If, for the sake of example, you composed your array out of /dev/sd[abcde]1, it may not turn out to matter that the /dev names of your USB disks move around a bit.


If I added a new drive and it displaced the existing ones, could the array still pick up the right drives?

For example if I set up my array using sdb, c, and d and then entered /dev/sd[bcdef]1 in mdadm.conf to account for two unexpected drives, would it work?

---

### Post by kidders on 2008-01-23
Welcome back!

It's hard to say what caused a disk to drop out of that user's array. Configuring *your* array with the sort of DEVICES line you mentioned really ought to work for you though. RAID arrays have unique identifiers that prevent other things being mistaken for array components ... mdadm should select the three correct devices out of "sd[bcdef]1" for you.

---

### Post by dgray_from_dc on 2008-01-23
I've started my build, I created my array, it began to build itself.  One concern, this is my /proc/mdstat

```
dontrel@SR-388:~$ cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4]
md0 : active raid5 sde1[4] sdd1[2] sdc1[1] sdb1[0]
      732587520 blocks level 5, 128k chunk, algorithm 2 [4/3] [UUU_]
      [>....................]  recovery =  0.1% (321024/244195840) finish=3712.8min speed=1093K/sec

unused devices: <none>

```

I'm not exactly sure what all of this means.  Well I'm OK with all but the second line. This array seems to have multiple personalities RAID4, 5, & 6.

I considered (briefly) that it may be attempting to rebuild the data from one of my previous build-ups.  These are the same drives I used on my previous attempt, I had RAID 5, I may have tried RAID 6.  However, I never bothered with 4 so that kinda eliminated the rebuild theory.

I'm thinking that this is because the striping for 4, 5, & 6 are similar so it just means "I'm building a 4/5/6 type array" or something.  Is that possible?

---

### Post by dgray_from_dc on 2008-01-26
I completed my build-up and things have gone wrong somehow.  The array completed its build, I formatted it ext3 and when I went to write to it, I discovered that it had been mounted read-only.  I added rw to /dev/md0 in fstab shown here:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c2014623-e2a7-411d-b1a8-3ce4f8e85f1d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=30fba4d8-3cf1-4525-a032-49266991b322 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/md0  /media/raid  ext3  rw,suid,dev,exec  0  0

```

At which point the array ceased to function giving me a bad superblock error.  Here is my mdadm.conf (generated automatically by webmin)

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=04a18870:a4b367c7:94b5d1ba:012439dd

# This file was auto-generated on Wed, 23 Jan 2008 23:39:21 -0500
# by mkconf $Id: mkconf 324 2007-05-05 18:49:44Z madduck $
DEVICE /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
ARRAY /dev/md0 level=raid5 devices=/dev/sdb1,/dev/sdc1,/dev/sdd1,/dev/sde1

```

and my cat /proc/mdstat

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdd1[3](S) sdc1[2](S) sdb1[1](S) sde1[0](S)
      976783360 blocks

unused devices: <none>

```

I've tinkered with mdadm.conf a bit commenting out lines that I think are unnecessary, but the result doesn't change.

When I try to assemble manualy, it get this:

```
dontrel@SR-388:~$ sudo mdadm --assemble --scan /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: ARRAY line /dev/md0 has no identity information.
mdadm: /dev/sdb1 not identified in config file.
mdadm: /dev/sdc1 not identified in config file.
mdadm: /dev/sdd1 not identified in config file.
mdadm: /dev/sde1 not identified in config file.

dontrel@SR-388:~$ sudo mdadm --assemble /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: ARRAY line /dev/md0 has no identity information.
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: /dev/sdc1 has no superblock - assembly aborted

dontrel@SR-388:~$ sudo mdadm --assemble --scan
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.

dontrel@SR-388:~$ sudo mdadm --assemble /dev/md0
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.

```

---

### Post by dgray_from_dc on 2008-01-26
OK.  Having noticed that my USB disks were re-ordered during boot-up, I unplugged all of my drives, and plugged them in in the right order.

I re-activated the array and it worked.  My array is now going through its second two day long rebuild.

This now poses my original question.  How exactly can I ensure that disk 1 goes to /dev/sdb and disk 2 goes to /dev/sdc and so on?

Looking at the udevinfo output from the thread mentioned in my original post, I have three disks which are indistinguishable because they're identical and I can see no unique serial numbers.  I'll be researching the udevinfo command, but any help would be appreciated.

---

### Post by fjgaude on 2008-01-26
Well, it seems if you are using Gutsy it seems to know how to assemble the original array even if the names have changed. This happens with my five-drive system all the time without incident.

To know the name vs the serial number of a device, this is one of several ways:

```
sudo hdparm -i -v /dev/sd[nn]
```

Do it device by device. You can do it also by the Hardware Information menu under System/Preferences.

Have fun!

---

### Post by dgray_from_dc on 2008-01-26
This is what I get

```
sudo hdparm -i -v /dev/sdc

/dev/sdc:
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 30401/255/63, sectors = 488397168, start = 0
 HDIO_GET_IDENTITY failed: Invalid argument

```

Also, I'm using Xubuntu due to my 733Mhz CPU and 128MB of RAM.

Edit:  I've looked in the man page used the -I  --Istdin --Istdout with the same results.

---

### Post by fjgaude on 2008-01-26
Likely has something to do with either the USB drives not being like regular devices, or the Xubuntu.

I don't have much of a clue. It works for me.

There is another command that gives the drive name and the SN but I just can't think of it right now.

Good luck, fellow, but do continue to have fun!

---

### Post by dgray_from_dc on 2008-01-26
It's the USB interface.  I tried it with the drive I use for bootup and it worked fine.

---

### Post by fjgaude on 2008-01-26
Praise the Lord but please do pass the ammunition. <smile>

Pray, let us all live and learn.

---

### Post by dgray_from_dc on 2008-01-28
It doesn't seem to be picky about any drive but the first.  When the array goes down, it's because disk 1 isn't assigned to /dev/sdb.  I can rearrange any of the other drives without issue.  A little inconvenient, but I can live with it while looking for better solutions.

Another question, how do you de-activate an array?  I can't seem to find the specific command.  In order to make sure the drives come up in order, I have to boot without them connected and then plug them in.  Problem with that, is with my 4 drive array, as soon as it detects 3 of them, it goes active degraded.  When I plug in the fourth drive, it doesn't put it into the array.  Instead, I have to manually add the last drive at the command line and endure a rebuild.

I'm looking into connecting the disks to my motherboard directly.  USB hot-swappability was a good idea, but it's just turning out to be a headache.  Problem is, with this being older equipment, the BIOS can't see a 250GB hdd.:rolleyes:

---

