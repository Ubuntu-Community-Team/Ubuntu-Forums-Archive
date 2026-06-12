---
title: "USB MP3 player won't mount"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by mark2741 on 2006-06-06
I'm trying to get my USB mp3 player, a Thompson/RCA RD1080, to work with Ubuntu and am stuck.

I assumed, and it appears from what I've read online so far, that Ubuntu should have just recognized it when it was initially plugged in and then mounted it for me. However it won't mount. Sometimes it isn't even visible as a drive when the file system is viewed via Nautilus. RIght now it is listed as a drive but I can't access it. When I double-click on the drive I get this error message:

**************************************

UNABLE TO MOUNT THE SELECTED VOLUME. THE VOLUME IS PROBABLY A FORMAT THAT CANNOT BE MOUNTED. 

Then under the "Show more details" arrow, it says:

wrong fstype, bad option, bad superblock on dev/sda.
missing codepage or other error
in some cases useful info is found in syslog - try dmesg | tail or so

then it states the above again (in other words, it shows the above paragraph twice in the same error window), followed by:

error: could not execute pmount

**************************************

I'm a linux and Ubuntu newbie. I looked in the gnome system prefs and the checkbox to automount devices is selected. I have no idea what to do from here. Any ideas?

---

### Post by jazzmuzik on 2006-06-07
I wonder if this driver would help:

[http://usbat2.sourceforge.net/](http://usbat2.sourceforge.net/)

---

### Post by mark2741 on 2006-06-07
That page says that the driver was submitted, accepted, and included in the linux kernel beginning with version 2.6.12. Since Dapper is at 2.6.15 I believe, I would assume it's in there and just not working for me?

But this does seem like the right driver as the mp3 player in question is an RCA Lyra, which is listed on that page.

---

