---
title: "'fdisk -l' is not listing a connected hard drive"
date: 2008-04-28
forum: Hardware
---

### Post by cheatcountry on 2008-04-28
I'm not sure what to do. Suddenly one of my hard drives just stopped working and didn't let me access anything in it and now I also don't see it listed when I do the fdisk -l command and it also doesn't show up in the computer area for the connected hard drives and the connected cd-roms. What can I do to fix this and find out what went wrong?

EDIT: I have also tried to run fsck to check the hard drive and it gives me the following error when I try to run the command:

*********@#######:~$ fsck /media/FreeAgent\ Drive_
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Is a directory while trying to open /media/FreeAgent Drive_

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


I also tried to run the above e2fsck command and got the same error as the above

---

### Post by coolaj86 on 2008-04-28
It may have died or the cable may have gradually become loose over time.

Try powering off the box, opening it up and unplugging / replugging the drive.

If that doesn't work you might want to try checking to see if it shows up in the the bios and perhaps putting it in a different computer.

---

### Post by cheatcountry on 2008-04-28
> **coolaj86 said:**
> It may have died or the cable may have gradually become loose over time.

Try powering off the box, opening it up and unplugging / replugging the drive.

If that doesn't work you might want to try checking to see if it shows up in the the bios and perhaps putting it in a different computer.

I have tried that already and its an external seagate hard drive. Also I haven't been able to access the bios ever since I got the grub boot loader on my computer. I don't know why...

---

### Post by Yellow Pasque on 2008-04-28
Is it a USB device? Try this and see if lsusb sees it:
```
sudo update-usbids
sudo lsusb
```

---

### Post by coolaj86 on 2008-04-28
Hmm... if you can't access the BIOS, I'd most certainly recommend taking the CMOS battery out or resseting it by the jumper because that's never a good sign.

Just about any time my computer has the plug pulled on it I have to reset the BIOS before it will recognize my SATA drives.

---

### Post by cheatcountry on 2008-04-29
> **Temüjin said:**
> Is it a USB device? Try this and see if lsusb sees it:
```
sudo update-usbids
sudo lsusb
```

I tried that command and it didn't work. It didn't list the hard drive.

---

