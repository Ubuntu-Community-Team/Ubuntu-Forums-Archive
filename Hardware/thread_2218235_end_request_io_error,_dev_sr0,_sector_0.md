---
title: "end_request: i/o error, dev sr0, sector 0"
date: 2014-04-19
forum: Hardware
---

### Post by vanquishedangel on 2014-04-19
I ran into this error while trying to move tmp directory to ram, which is odd because usually sr0 is for the cd/dvd drive. I also tried to look this up online and as I feared many people in threads have said that the hard drive is failing. My hard drive is about 6 years old and it is a refurbished on at that that has failed before.

This is not what cause the error, it was actually moving tmp directory to ram!

I had edited the /etc/fstab file and included the line below:

tmpfs /tmp tmpfs defaults,noatime,mode=1777,nosuid,size=512M 0 0

This is what caused the error however once this line was added simply deleting it from fstab will not fix the issue. I had to reboot the computer and hold the "shift" key while grub was booting and select the option for "safe mode". while in that safe mode I had to select the option "fsck". This solved the error.

This error also cause longer boot times and slower loading of things like desktop wall paper. hope this helped someone.

---

