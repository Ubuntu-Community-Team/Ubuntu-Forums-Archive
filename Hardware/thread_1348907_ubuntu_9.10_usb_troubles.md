---
title: "ubuntu 9.10 usb troubles"
date: 2009-12-07
forum: Hardware
---

### Post by icd* on 2009-12-07
im using ubuntu 9.10 32bit (i think) on a toshiba laptop, and upgraded from 9.04. plugging my external hard drive and pendrives into the atop using 9.04 used to work; it would auto-mount and i would be able to see and access it.
since updating to karmic i've not been able to use any usb devices. typing "lsusb", i can see the device plugged in, and when i type "dmesg | tail" it tells me a removable disk has been attatched on/in sdb.
however, when i type in "sudo mount /dev/sdb1" im gien the message 
"mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"
ive made sure that udev is the latest version (147-61), ive also blacklisted uvcvideo but no avail. ive also "removed flush blah blah in the gnome registry. 
ive tried countless things but nothing seems to work. i know my way around linux ok but im sure i must just be missing something as i seem to be the only person still having problems (not many new posts about it anymore).

im still looking on ubuntu bugs website but i fear that this may be a slightly old laptop and a driver may not be available anymore or something, i dont know anymore =p help appeciated.

---

