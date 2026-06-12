---
title: "problem with installing new SATA drive"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by antbully on 2007-12-14
Hello,

I have a Ubuntu gutsy gibbon system installed and working great, and now I want to add another hard drive.  I've got 3 already, but always need more :-).

I have a SATA drive as my boot and OS disk, and 2 PATA drives for /home and data.  The new drive is a SATA 3.0 Gbps drive, so I would like to plug it in to that interface on the mainboard.  It will be another data disk.

In the mainboard BIOS, you can set the drive you want to boot from.  So this is set to be the original SATA drive.  Now on boot up, the system boots and I get the Ubuntu graphical progress bar all the way to the end, but then the screen switches to console 8 with the last text message from boot: rc.local

So I switch to another console and log in as root.  I do a "df".  Normally, my boot drive shows up as /dev/sda, but instead, it's /dev/sdb, and all the partitions are mounted correctly, but they're on /dev/sdb!  How this happens I do not know.  And "hdparm -i /dev/sda" shows info about the new drive.

Hmm, so the OS thinks the new drive is /dev/sda and the old one is /dev/sdb, and for some reason, this prevents the system from completing startup.  How can I make these switch?  Actually, I kind of like sda being the boot disk, but I'll settle for making this same disk be sdb if I can just get things to finish starting up.  The BIOS doesn't seem to offer any other options for making these assignments...

Thanks for any help,

Antbully

---

### Post by jbulcher on 2007-12-15
Which controllers do you have the HDs connected to? I think they're labeled SATA 0, SATA 1, etc. My experience suggests that sda corresponds to the lowest numbered controller you have the HD connected to.

---

### Post by antbully on 2007-12-17
> **jbulcher said:**
> Which controllers do you have the HDs connected to? I think they're labeled SATA 0, SATA 1, etc. My experience suggests that sda corresponds to the lowest numbered controller you have the HD connected to.

Hmm, ok, that must explain it.  I connected the new drive to SATA1 with boot drive remaining on SATA0 and everything works.  But the 3 Gbps SATA interface must be numbered lower than the 1.5 Gbps interfaces (-1?), since it wants to be sda when there's a drive hooked up there.  I guess I won't be using that interface for now!

Antbully

---

### Post by jbulcher on 2007-12-18
I'm glad you got the computer booting! You sounded like you might like to get the computer to boot the other way, too. Would you mind posting your fstab (/etc/fstab)? Does it use UUIDs (it would look like there's a long string of random letters/numbers)? if not, it might help to use UUIDs, or just specify the current partition name (switch sda & sdb).

to get the UUID of a sda1, use:
```
sudo vol_id --uuid /dev/sda1
```

UUID stands for Universally Unique IDentifier, so theoretically it doesn't matter whether the device is on /dev/sda or /dev/sdb - it'll mount just the same.

---

### Post by antbully on 2008-01-01
Thanks for the reply.  It's been a while since I checked for replies.

My fstab does have the UUIDs in it.  Was wondering how to get that info - thanks for the tip.

I guess there are too many things I do not understand right now.  For one, is it worth the effort to try to get my 3.0 Gbps SATA drive to operate on the 3.0 Gbps SATA  interface?  If there's no real performance difference, then I don't think there is much point in trying.  After that, if it's too complicated, well, hey, at least it works now :-)

Antbully

---

