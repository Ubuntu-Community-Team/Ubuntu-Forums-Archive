---
title: "install freezes when detecting hardware"
date: 2006-01-16
forum: Installation &amp; Upgrades
---

### Post by Cereal2nd on 2006-01-16
ok,

when the installer start searching for an cdrom to install from it always freezes, i gave it over 25 minuts, but after 25 minuts its still at 0%

i tryed the folowing boot options:
mem=512m
framebuffer=off
usb probe=off

anything else i can try?

---

### Post by joft on 2006-01-16
Hi,

just some thoughts:

if the installer doesn't find your cdrom drive, perhaps some chipset driver module is not loaded.

Did you try an expert install? I think there you can chose which chipset driver will get loaded.

What does the logging console (Alt-F4 or was it F3?) say?

---

### Post by Sef on 2006-01-16
Questions:

A) Have you tried a Ubuntu Live CD? 

     -)Check and make sure Ubuntu is compatible with your hardware.

B) Do you have another computer you could start an install to check if the CD is good or bad? 

     1) The cd still may be bad.   
     2) If downloaded, did you md5sum it?
     3) If you do, just reboot it before you do any partitioning, so nothing will be                installed.

---

### Post by Cereal2nd on 2006-01-17
ok, i founbd the problem, i have an usb cardreader and it seems that ubuntu doesn't like it, the moment i unplugged this one, verything works fine.

---

