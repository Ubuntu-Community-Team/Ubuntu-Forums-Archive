---
title: "Dual Booting Geexbox and 8.10"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by Jose Catre-Vandis on 2009-01-24
This all worked fine before, but apparently the file system ext3 on 8.10 is slightly different. After installation of Geexbox to the hard drive, it does not find the 8.10 installation at all nor put it into the menu.lst. If I manually add an entry to the geexbox grub's menu.lst file, it give me an Error 2 - bad file or directory type. I have tried both the normal menu.lst entries and the configfile approach.

I have tried it round the other way (8.10 grub and an entry for Geexbox) but this has never worked for me, and seems to require the specific settings of the geexbox grub to boot geexbox, but 8.10 does boot fine.

So this updated setup can give me one or the other, which ever way I try. can anyone help with any settings I might be able to use to overcome Error 2

EDIT

[COLOR="Sienna"]Have sorted this out now

For a dual boot situation where you have Ubuntu 8.10 and Geexbox (or perhaps other distros with older grub) installed on separate partitions, and you install GeexBox (or other older grub distro) second to use it's grub.

Ubuntu 8.10 formats partitions to an inode size of 256 (as opposed to 128 in previous versions) in preparation for ext4. This has implications for dual boot environments using older versions of grub, and can cause access issues from windows when using the ext2 drivers.

The workaround is to format the partitions prior to installation using an older version of Ubuntu/Gparted, then to carry out the normal installation BUT avoiding the formatting stage. Older grubs can then see this. I used the Ubuntu Hardy Heron (8.04.1) Live CD to action this requirement. (My PartedMagic 3 Live CD creates 256 inode sizes, grrr!)

A useful command to check your inode size, run as root/sudo

```
dumpe2fs /dev/sdaX | grep -i "inode size"
```
which will return either 128 or 256, you want 128 ![/COLOR]

---

### Post by Jose Catre-Vandis on 2009-01-24
Solved

---

