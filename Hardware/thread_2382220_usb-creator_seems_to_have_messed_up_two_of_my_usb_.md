---
title: "usb-creator seems to have messed up two of my usb thumb drives"
date: 2018-01-10
forum: Hardware
---

### Post by raphaell2 on 2018-01-10
Not sure if I should post this in Hardware, Installation & Upgrades, General Help, or Ubuntu, Linux & OS Chat. 

I used usb-creator to turn two of my usb thumb drives into bootable Xubuntu 16.04 live media. Now, when I try to use gparted to turn them back into regular thumb drives, I get a pop up saying "The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes." When I click on "ignore", gparted shows me the drives with way too large sizes in bytes. Any ideas? (After this had happened to me with the first drive, I thought perhaps it was a physical problem with that particular drive - that's why I tried the same procedure with a second drive.)

---

### Post by sudodus on 2018-01-10
There is a bug in gparted (except in the newest version of Ubuntu, where it is fixed). Gparted does not understand the partition structure and file system in a cloned boot drive. Other tools can manage it better. You can use the following commands,

```

sudo lsblk -f
sudo lsblk -m

```

You can use the tool mkusb to restore a USB thumb drive to a standard storage device. See the following links

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[help.ubuntu.com/community/mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

---

### Post by raphaell2 on 2018-01-10
So the drive is still fine, it just doesn't look like that to gparted. Thank you, good to know!

---

