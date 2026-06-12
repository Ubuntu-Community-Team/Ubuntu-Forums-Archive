---
title: "HDD throwing comreset error=16"
date: 2016-06-16
forum: Hardware
---

### Post by dgd on 2016-06-16
Is my HD dead?
sys: 
ubuntu 14.04

Just got on BOOT an ata 2 comreset error=16.
I typed EXIT to get out of the failed boot BTW... I followed the process with:
sudo add-apt-repository ppa:yannubuntu/boot-repair

I'm now on Ubuntu 14.04 now but ...

$blkid 
only shows my boot drive and not the other drive :(

$sudo blkid
 (shows only the SSD and not the HDD)
/dev/sda1: UUID="155c3c3c-daa6-414c-ac3d-0f8c492592c0" TYPE="ext4" 
/dev/sda5: UUID="69f2e3e2-4aa9-4ccb-a32e-0339d1e1a049" TYPE="swap" 

$hardinfo
storage  devices> only shows my boot drive and not the other drive :(

$sudo gparted
only shows my boot drive and not the other drive :(

I've checked my cables, they are connected. The HDD is spinning, I can feel it and it is warm. I had not made any mods to my hardware before the comreset error. 

I did notice that some of my DIRS in the missing HDD were showing 0 files... though I knew there were many files... My windows training told me to reboot... :/ Bad move, I know.

Please advise on next step.
thank you
Dennis

---

### Post by weatherman2 on 2016-06-16
Yeah, sounds like a failed hard drive.  Hard drive failure is extremely common - they are not very reliable devices compared to everything else in a PC (except maybe your power supply).  I've replaced a few dozen failed hard drives in my day.  If you make regular backups, it's not a big worry - like buying new tires for your car when they wear out.

---

### Post by dgd on 2016-06-19
Ok. Thanks. I'm reading up on [http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html) and hoping I can salvage at least some of my data...

---

