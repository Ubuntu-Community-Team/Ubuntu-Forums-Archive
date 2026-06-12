---
title: "[SOLVED] WD My Book refuses to sleep on shutdown"
date: 2008-05-06
forum: Hardware
---

### Post by Fisslefink on 2008-05-06
**My setup:**
I have a WD My Book Studio Edition 1 TB drive connected by Firewire 400 to an Asus P4P800-E Deluxe motherboard. I'm running Ubuntu 7.04 Feisty Fawn with the latest kernel and updates.

[COLOR="Red"][B]
My problem:[/B][/COLOR]
The drive did not spin down or go to sleep when the computer shut down.  If I put my ear to the drive, I could hear the drive spinning, even 12 hours after the computer was turned off.  Also, the LED light stayed on.  Spinning constantly (24 hours a day) is sure to reduce the lifespan of the drive, and I don't want that.

[COLOR="SeaGreen"]**My solution:**[/COLOR]
I used the scsi-spin commands from [morgengenuss's script in a previous thread]("http://ubuntuforums.org/showpost.php?p=4636426&postcount=43") in a simpler script which is executed on shutdown.  The script is here:

/etc/init.d/WDshutdown
```
 
#!/bin/bash
# Spins down WD MyBook before shutdown
# inspired by script from http://ubuntuforums.org/archive/index.php/t-451344.html

echo -e "\n\n--------- Attempting spin down `date` ---------" >> /var/log/wdshutdown.log

## drives are automatically unmounted by umountfs during shutdown

## Spin them down
echo "=== begin spinning down: ===" >> /var/log/wdshutdown.log

scsi-spin --verbose=2 -d /dev/sdc3 >> /var/log/wdshutdown.log 2>&1
scsi-spin --verbose=2 -d /dev/sdc4 >> /var/log/wdshutdown.log 2>&1
scsi-spin --verbose=2 -d /dev/sdc5 >> /var/log/wdshutdown.log 2>&1
scsi-spin --verbose=2 -d /dev/sdc6 >> /var/log/wdshutdown.log 2>&1

echo "=== end spinning down ===" >> /var/log/wdshutdown.log
```

My drive has **four active partitions** (/dev/sdc3, /dev/sdc4, /dev/sdc5, /dev/sdc6), so you'll notice I used "sdc3, sdc4, sdc5, sdc6" in my script.  Change the script according to your setup.

I put this script in /etc/init.d and made it executable
```
sudo chmod +x /etc/init.d/WDshutdown
```
I also made a link to tell Ubuntu to execute this script when the computer shuts down (rc0.d), after the drives are unmounted.
```
sudo ln -s /etc/init.d/WDshutdown /etc/rc0.d/S43WDshutdown
```

On my system, this script **must be executed after the drives are unmounted with S40umountfs, but before S60umountroot is run** ... putting this script between those in the sequence (ie. with "S43WDshutdown") should assure that the drive will be spun down after it is unmounted.

If you want to test the script, first unmount the drive with 'umount', then run the script.  When the script is run from a current login session, the LED on the drive 'glitters' with intermittent pulses for a couple of seconds, the disk spins down, then the LED shuts off (but pulses once every 5 seconds).  The disk does not spin in this 'sleep mode.'  If you tell the computer to shut down at this point, the drive will continue to 'sleep' while the computer is off.

With the script linked from /etc/rc0.d/S43WDspindown, my drive spins down when the computer is shut down [it does the LED 'glitter' thing], and continues to 'sleep' when the computer is off.  Finally!!!

Thanks again to the people on thread [4898808]("http://ubuntuforums.org/showthread.php?p=4898808#post4898808")

---

### Post by Psykotik on 2008-06-22
It seems this very issue has been resolved on latest ubuntu (8.04 in my case).

BUT... it still doesn't spin off as expected to. Look at the [bug report]("https://bugs.launchpad.net/ubuntu/+bug/241927").

---

