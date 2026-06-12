---
title: "[SOLVED] USB Harddrive wont mount."
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by jusmurph on 2007-06-30
This is what i tried:

```
anthonii@smurph:~$ ntfsfix /dev/sde1
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS partition /dev/sde1 was processed successfully.
anthonii@smurph:~$ sudo mount -t ntfs-3g /dev/sde1 /media/SEA_DISK -o force
WARNING: Dirty volume mount was forced by the 'force' mount option.
fusermount: failed to access mountpoint /media/SEA_DISK: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sde1 (SEA_DISK)

```

I also tried booting windows twice as it says... shudder.

what is going on here? I thought it was a fat 32 drive...

---

### Post by Tea4all on 2007-06-30
Try to format it in windows.  Note you will lose all data!

---

### Post by jusmurph on 2007-06-30
It says the volume is scheduled for a check. It works fine in windows so i do not see why i need to format it :|

---

### Post by merlinus on 2007-06-30
You might try running 

chkdsk <drive letter>: /f 

from a windows cli, and then see if it will mount in ubuntu.

-merlin

---

### Post by jusmurph on 2007-06-30
> **merlinus said:**
> You might try running 

chkdsk <drive letter>: /f 

from a windows cli, and then see if it will mount in ubuntu.

-merlin

Did it. Its healthy. Though it still refuses to mount (it is ntfs)

I also tried to plug the hard drive into another computer and it did not like that either. Whats wrong with this thing.

---

### Post by jusmurph on 2007-06-30
Is there a way to commandline check this disk in ubuntu.

---

### Post by jusmurph on 2007-06-30
Common, i refuse to let windows win on this one.

---

### Post by kiotae on 2007-06-30
You may need to use the modprobe command to get it to recognize your drive.  I'm not an expert at modprobe, but take a look at the man page and google is your friend :-)

The dmesg command will should you all sorts of wonderful goop about what is succeeding and what is failing.  After you think you've find the right modprobe incantation, you can run dmesg to see if it recognized the drive.

I don't remember if it applies to newly attached drives or just revised partition tables, but you may want to follow all that with partprobe.

If you have any brainstorms, post them, too.  I'm fighting a finicky usb drive with a non-linux fs, too. :(

---

### Post by jusmurph on 2007-06-30
Thanks for your help, however to be honest, i barely have any idea what your talking about :(

---

### Post by dabl on 2007-07-01
If your USB drive is formatted as NTFS, that's the main problem.

If you want to share it between Ubuntu and Windows, then you're going to have to do 3 things:

1. Install ntfs-3g: ```
sudo apt-get install ntfs-3g
```

2. Add yourself to the "fuse" group.  Open Administration >Users& Groups, and add yourself to fuse.

3. Make a new mount point for your NTFS-formatted USB drive, like /media/NTFS_USB

this is done in a console window as ```
sudo mkdir /media/NTFS_USB
```

Then, after connecting your USB drive, you need to figure out where in your filesystem it is being added, by checking /etc/fstab.  On my system, it ends up at  /dev/sdd1.  You have to figure this out, and it depends on your USB bus and how many other USB items you have plugged in at the moment.

Once you know the device ID of your drive, you can mount it with a command similar to:

```
sudo mount -t ntfs-3g /dev/sdd1 /media/NTFS_USB
```

:)

---

### Post by jusmurph on 2007-07-01
> **dabl said:**
> If your USB drive is formatted as NTFS, that's the main problem.

If you want to share it between Ubuntu and Windows, then you're going to have to do 3 things:

1. Install ntfs-3g: ```
sudo apt-get install ntfs-3g
```

2. Add yourself to the "fuse" group.  Open Administration >Users& Groups, and add yourself to fuse.

3. Make a new mount point for your NTFS-formatted USB drive, like /media/NTFS_USB

this is done in a console window as ```
sudo mkdir /media/NTFS_USB
```

Then, after connecting your USB drive, you need to figure out where in your filesystem it is being added, by checking /etc/fstab.  On my system, it ends up at  /dev/sdd1.  You have to figure this out, and it depends on your USB bus and how many other USB items you have plugged in at the moment.

Once you know the device ID of your drive, you can mount it with a command similar to:

```
sudo mount -t ntfs-3g /dev/sdd1 /media/NTFS_USB
```

:)

You Sir, Are a freaking LEGEND :KS:KS

Thank you very much!

Now that it is mounted... is it still going to complain about being a dirty volume/needing a check?

---

### Post by RealityDitch on 2007-08-12
thank you that totally worked for me.  I kept on trying to mount using the gui without success and I thought maybe I was doing something wrong.  It's just Kubuntu not allowing me to mount because I am not a root.

---

### Post by jusmurph on 2007-08-14
> **RealityDitch said:**
> because I am not a root.

That just made my day :KS

---

### Post by RealityDitch on 2007-08-16
I can't seem to create a new thread, I can't find any links to create a new thread maybe I don't have enough rights?  but anywho, also this isn't related to harddrive mounting prob
but I was wondering if any of you could help me with thunderbird crashing everytime it starts up.  only way to make it not crash is to use terminal and use sudo instead of launching from launcher.  I shouldn't have to do that.  any ideas?  obviously there's gotta be a file it can't access when launching as normal user.

---

### Post by RealityDitch on 2007-08-16
could you tell me why the mount works but it keeps disappearing after every reboot?
I was all happy about it then I rebooted my computer and I had to remount everytime.

---

### Post by RealityDitch on 2007-08-17
never mind.
Problem solved.

this actually isn't the best way to mount ntfs volume because you have to do this everytime.

betterway is what I found on this ubuntu page

use this for mounting ntfs volumes that are internal and for external usb ntfs volumes just let it auto mount and then click properties and set it as writeable.
[http://ubuntuforums.org/showthread.php?t=217009&highlight=mount+usb+drive](http://ubuntuforums.org/showthread.php?t=217009&highlight=mount+usb+drive)

---

### Post by anonymous_x on 2007-11-27
But Why Does Ubuntu need Windows for certain tasks . . .
Can't ubuntu run on its own?
Right now, I have to open my system and take out the HDD to slave on a WIndows Machine and eject from "My Computer" just because I want to view my Files from Ubuntu . .
I mean, something should be done . . .

I formatted my system and I have just Ubuntu on the Machine!

---

### Post by jpblock82 on 2007-11-29
It only shows my etx3 file system, my sda1 partition and my CD-ROM, here...have a looksy:

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=6e517265-489e-4308-b6a5-94bc3300cb5c / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=FAE88A13E889CDF7 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda5 :
UUID=5f46b036-8dde-4b0b-a02d-e13809727c52 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0


I did the mentioned instructions and still nothing appears...why o why can't I get my USB drives to work????

---

