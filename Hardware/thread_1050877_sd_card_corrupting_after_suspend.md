---
title: "sd card corrupting after suspend"
date: 2009-01-26
forum: Hardware
---

### Post by mjaallen on 2009-01-26
Hey guys... 

I just brought a dell mini 9 and have installed 8.10 on it.  After reading through some internet sites, everything is working very well apart from two things.  First wpa enterprise does not work, which i've seen as being a known bug with the broadcom driver (annoying as i need it for school).  However my main problem is -> I went out and got 16gig SDHC card to use as a place to store my data. I put a file system on it and mounted to /home/username/data by adding an entry to my fstab and it all works well, until I suspend the laptop.  When I resume, I get an error message saying that it cannot mount the volume, after which I can't seem to access the SD without going into fdisk and putting a new partition on it.  I thought I might try making a shell script to unmount the volume before it suspends and remount on resume to try and stop it from corrupting.  It there a place where I can put a shell script that will run when I press the suspend button and also a place where I can run a script when it resumes?  Or is there something else that might be worth trying?

Regards
Mike.

---

### Post by dsm iv tr on 2009-01-26
IIRC, data corruption on SD cards left in during suspend is a known problem.

You can make a simple script in /etc/pm/sleep.d/ like:

```

case "$1" in
        suspend|hibernate)
        umount /media/yourdevice
        ;;
        resume|thaw)
        mount /media/yourdevice
        ;;
esac

exit $?

```

Call it 99-umount-sd.sh or something, set it executable (chmod +x /etc/pm/sleep.d/99-umount-sd.sh), and test.

Good luck.

---

### Post by mjaallen on 2009-01-27
I tried it... and it seems to be working. My home drive space
has effectively doubled. 



Thanks a lot :)

---

### Post by pjalegria on 2009-03-17
Should it be "/media/yourdevice" or "/dev/yourdevice" ???

---

### Post by Chareos on 2009-09-16
I use this solution to prevent data corruption, but I found this is preventing system from suspend if there is not a SD card inserted (mounted)

/etc/pm/sleep.d/99-umount-sd.sh suspend suspend: umount: /archivio_sd: not mounted
Returned exit code 1.
Wed Sep 16 22:06:14 CEST 2009: Inhibit found, will not perform suspend
Wed Sep 16 22:06:14 CEST 2009: Running hooks for resume

How could this script be modified in order to umount the sd IF present (mounted) but not prevent suspend if not present ?

Thanks

---

### Post by Disidente on 2009-09-21
I got the same problem and solved with the following script:

```

#!/bin/sh
# Drop to: /etc/pm/sleep.d
# Use this script to prevent data loss on gnome-mounted MMC/SD
# cards. It syncs data and umounts all mmcblk devices prior to
# suspend, and cancels suspend if umounting was not posssible
# (i.e: something locks a file)
case "$1" in
    hibernate|suspend)
        sync
        for drive in $( ls /dev/mmcblk* ); do
            gnome-mount -und ${drive} > /dev/null
            # If umount failed: abort suspend
            if [ $? -gt 0 ]; then
            # Test if device keeps mounted. Previous command could fail
            # (i.e device was not mounted) with a non-stopper
            # problem for the suspend precess
            mount | grep ${drive}
            if [ $? -eq 0 ]; then
                exit 1
            fi
            fi
        done
        ;;
esac

```

This one umounts dynamically mounted mmcblk devices, and if it is not possible to umount them, aborts suspend process

---

