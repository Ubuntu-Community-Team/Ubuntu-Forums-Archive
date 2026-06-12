---
title: "USB Alernate Install Disk"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by RoseKnight on 2009-02-02
I used ubuntus "create usb start disk" with an alternate installer iso
this file: ubuntu-8.04.2-alternate-i386.iso

when I run it, it tells me it can't find the cdrom so i followed this help entry: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

and did these steps using the (execute shell) command through the installer:

```

# mkdir /cdrom /dev/cdroms
# cd /dev/cdroms
# ln -s ../sda1 cdrom0 (where sda1 is your USB stick)
# mount -t vfat /dev/cdroms/cdrom0 /cdrom

```

then I go back to where the installer wants to detect and mount the cdrom and I get this error:

```

There was a problem reading data from the CD-ROM. Please make sure it
is in the drive. If retrying does now work, you should check the
integrity of your CD-ROM.

Failed to copy file from CD-ROM. Retry?

<yes>      <no>

```

Any help making this work would be much appreciated.

---

