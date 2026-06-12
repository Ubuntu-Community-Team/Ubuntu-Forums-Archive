---
title: "SanDisk Extreme 500 Portable SSD not detected in Ubuntu 16.04"
date: 2017-07-01
forum: Hardware
---

### Post by johndallyroxx on 2017-07-01
Hi Everyone,

I feel like a douche, for making my first post here a request for assistance...   I just picked up a SanDisk Extreme 500 Portable SSD drive, 250 GB edition (need it for editing 4k movies... my standard backup drive just can't handle editing 4k files).  Anyway, I had no idea there might be some conflict or incompatibility issue (I am a Linux newb... but a stubborn one, determine to stick with Linux after using Windows for 20+ years).  Anyway, as soon as I plug in the drive into the USB slot, I see this message:

[ATTACH=CONFIG]275824[/ATTACH]

Unable to access “Extreme 500”

Error mounting /dev/sdb1 at /media/pj/Extreme 500: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdb1" "/media/pj/Extreme 500"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'



The drive does show in the file/window, as "Extreme 500" right under Computer, and above Connect to Server... but clicking on it in order to access it, I instantly get the above error message.

I just picked the drive up earlier today in Bangkok, and already at the airport, trying to get it to work.  I'd love to return it if it can't be made to work as a backup/USB drive on my laptop, but... that's not an option as I'm flying to Europe soon.

Any help?  CAn these be made to work on an Ubuntu system?  Anyone who can help me out, I'll gladly offer you a 1000 yen gift certificate on my site (one of the largest marketplaces online of Japanese products: games, electronics, music, toys... you name it). I just don't want something for nothing.  If anyone can help, I'll be happy to offer something in return.  Thank you in advance.

---

### Post by CatKiller on 2017-07-01
My understanding is that exFAT is patent-encumbered, so cannot be used in the same way that FAT32 could be. If you format your drive as FAT32 instead, it will work largely the same as exFAT but can't handle individual files larger than 4 GB. Otherwise you can install exfat-fuse and exfat-utils to get userspace file mounting support. Information from [here]("https://www.howtogeek.com/235655/how-to-mount-and-use-an-exfat-drive-on-linux/").

---

### Post by efflandt on 2017-07-01
Note that the error says "mount: unknown filesystem type 'exfat'". I don't know how or why it was formatted as exfat, but to access exfat you just need to add support for it:```
sudo apt update
sudo apt install exfat-utils
```Which I think should include exfat-fuse for automounting (or at least it did when using synaptic to install exfat-utils).

exFAT is the default file system for SD/microSD cards larger than 32 GB (SDXC). You could always use a Linux file system like ext4 if only accessing it from Linux. But even though my Android phone uses ext4 for its internal storage it will not allow that on microSD, so I had to reformat that back to exFAT.

---

