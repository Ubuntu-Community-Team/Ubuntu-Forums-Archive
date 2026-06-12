---
title: "fsck is broken"
date: 2008-03-22
forum: Hardware &amp; Laptops
---

### Post by nosh on 2008-03-22
The fsck freezes at random spots, regardless of running from hard disk or live boot.  Here are the details:

I have a HP Pavillion dv6000 laptop running Ubuntu, kernal 2.6.20-16-generic dual-booting with windows vista.  Ubuntu has been installed since last August and ever since then fsck has been broken.  Whenever it is called to run, rather automatically or from a live boot, it freezes at some point during the check and simply stops.  There is no consitency to when it stops; it appears random.  Furthermore, at the point at which it freezes the uderscore at the beginning of the line which was blinking at a constant rate dissappears.  Once ubuntu was installed that time, I used vista to access fstab and disable fsck for all drives and partitions.

This worked fine for awhile until just recently.  When vista had a problem and was forcefully shutdown, it scaned it's own disk on reboot and fixd itself and has been just fine after that.  However the Ubuntu boot now reports:

```
*Checking root file system...
fsck 1.40-WIP (14-Nov-2006)
/dev/sda3 contains a filesystem with errors, check forced.
/dev/sda3:\========                                  /18.5%
```

and so it freezes every time on boot up.  /dev/sda3 is the windows partition and it in fact clean by windows standards.  Is there some way to disable this fsck check?  More importantly is there some way to fix fsck for this computer?  Please help :(

---

### Post by reyhan on 2008-03-22
maybe there is an bad sector on your hard disk...?

if you want to disable fsck check try this

```
sudo tune2fs -c 30 /dev/xxxx
```

xxxx is your hard drive is it Sda or Hda

---

### Post by nosh on 2008-03-23
Does that need to be run from the local operating system, or will a liveboot acess the right files?  If I knew the configuration file that that command accessed and what it should look like, it may be easier.  As for the hard drive, it is sda and I've discussed the possibility of a bad sector with the manufacturer; as long as the bios' disk scan is successful, which it is, they hold that the hard drive is flawless.

---

### Post by nosh on 2008-03-24
please help?

---

### Post by nosh on 2008-03-26
Is there anybody who has any idea why this is happening?

---

