---
title: "Can't mount usb hard drive"
date: 2013-03-19
forum: Hardware
---

### Post by chiparawe on 2013-03-19
I have a 160gb hard drive I pulled from my laptop after it died which has a lot of files I use occassionaly. In the past I have either unplugged my second HDD and plugged in the 2.5" drive or altenatively accessed it via a usb plugged into my cyclone media player. Today I bough a 2.5" HDD enclosure for convenience and plugged it in to access some photos. No problems. This evening I decided to copy the photos to my permanent HDD for easier access. On plugging in the usb drive it wouldn't mount. It is visible under disk drives and shows up as 160gb usb drive in the home folder but clicking it brings up "unable to mount location". I have done nothing with it since I accessed it earlier today and it has always mounted in the past. I am stumped. Help please

---

### Post by ahallubuntu on 2013-03-19
~

---

### Post by chiparawe on 2013-03-19
Thanks. I will give that a go and post results.

---

### Post by ajgreeny on 2013-03-19
How is the drive formatted; ext#, fat32, ntfs?

If it is ntfs and it was not unmounted or shutdown properly before being removed from the enclosure it may be flagged as still in use. What happens if you try to mount it in terminal; any errors which may help?

---

### Post by chiparawe on 2013-03-19
I honestly can't remember how the disk is formatted. It came out of my laptop which ran windows 7 until it crashed. I then reformatted it and started running ubuntu only so I assume it is FAT32. I unmounted it after the last session this afternoon. I have rebooted into windows where it shows up as a mass storage device but I can't open it and in ubuntu it shows up as a usb hard drive but won't open because it isn't mounted. Terminal says no ntfs system and nothing when I try and mount it as FAT32

---

### Post by chiparawe on 2013-03-20
Ok. Looks like it is ext#

---

