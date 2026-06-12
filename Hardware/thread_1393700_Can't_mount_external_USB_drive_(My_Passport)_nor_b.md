---
title: "Can't mount external USB drive (My Passport) nor backup UDF volume"
date: 2010-01-29
forum: Hardware
---

### Post by ikjadoon on 2010-01-29
Hi. I'm new to Ubuntu. :)

I'm having some trouble with basically everything. To say this past week has been difficult would be an understatement. To sum it up: imagine you made an image of your hard drive, the next day you have software troubles that require a format, so you format the hard drive, and when you go back to put the image on your hard drive, Windows throws you a nasty unexplainable error with no troubleshooting help at all: the parameter is incorrect, 0x80070057. RIGHT, it's been a tough week.

I'm trying to hook up my external USB drive (Western Digital My Passport). It doesn't seem to do anything when I hook it up; the light on it turns on, though. I have no indication it even got plugged in. It works fine in all my other Windows' computers. :( I searched and some threads said one should mount the drive themselves, but I can't seem to figure that out, either! I was told to type "sudo fdisk -l", but that only showed my hard drive. :(

Second issue: my image backup was on a 50GB rewritable Blu-ray disk. Ubuntu correctly finds and identifies the drive. However, when I put the BD in, I get an error:

"Unable to mount UDF volume
Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sr0, missing codepage or helper program, or other error
In some cases useful info is found in syslog -try dmesg | tail or so"

Right. I installed UDFTOOLs (with sudo apt-get install udftools) and it seemed to install fine, but same issue.

Any help is SUPER APPRECIATED. :D :D :D

~Ibrahim~

---

