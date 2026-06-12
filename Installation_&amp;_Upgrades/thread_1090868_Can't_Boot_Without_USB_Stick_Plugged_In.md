---
title: "Can't Boot Without USB Stick Plugged In"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by foxmajik on 2009-03-08
I installed Intrepid using unetbootin from a USB stick.

For some reason it installed the boot loader onto the USB stick so I can't boot without having the USB stick plugged in because there is no boot loader on my hard drive.

How do I put the boot loader onto my hard drive so I don't have to have the USB stick plugged in to boot?

---

### Post by dstew on 2009-03-08
What you probably did is install the grub stage1 to the hard disk MBR, but with the configuration that it gets its stage2 and menu from the USB stick.

Do you want to boot grub from the hard disk, or from the USB stick only?

---

### Post by foxmajik on 2009-03-08
> **dstew said:**
> What you probably did is install the grub stage1 to the hard disk MBR, but with the configuration that it gets its stage2 and menu from the USB stick.

Do you want to boot grub from the hard disk, or from the USB stick only?

I want to boot from the hard drive.

I tried using Grub to setup the disk but it does not work.

Disk 2 partition 1 is where Ubuntu is installed:

```
grub> root (hd2,1)
root (hd2,1)

Error 21: Selected disk does not exist
```

I can't get a list of disks as Grub sees them because in order to list devices in Grub you're supposed to press the TAB key after typing:

```
root (
```

...However, pressing tab on Ubuntu X64 systems just makes the cursor move right rather than suggestion completions for the command as it's supposed to.

---

### Post by foxmajik on 2009-03-08
I fixed it myself.

First I discovered that hd2 that was being referred to at boot was the USB stick, since drives are numbered starting with 0.

Then I setup Grub to use hd1,0 as the boot device because that is the hard drive where I have Ubuntu installed.

Finally, I used fdisk to set the bootable flag on the partition.

---

