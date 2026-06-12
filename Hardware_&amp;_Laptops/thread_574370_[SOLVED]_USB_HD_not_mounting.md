---
title: "[SOLVED] USB HD not mounting"
date: 2007-10-12
forum: Hardware &amp; Laptops
---

### Post by Fingers &amp; Thumbs on 2007-10-12
I have read through similar threads on this and other forums, but to no avail, whereas other people are getting messages like "Unable to mount volume" I don't get anything, no desktop icon, no message, seemingly Ubuntu appears completely unaware that I have connected my drive at all. 

  This was not always the case, I did have several weeks of use before things stopped working,  and to the best of my knowledge I have not changed any mount point settings.

  I am new to Linux, so I'm not sure quite what is going on.

Any help would be warmly recieved.

---

### Post by Greetings from mirth on 2007-10-12
I had a couple of problems with mounting a usb stick

I did this

[LIST=1]
[*]Open a terminal
[*]sudo mkdir /mnt/USB
[*]did an fdisk -l to find out of even the sda1 even exists! (special device. USB I guess)
[*]then the big one...sudo mount -t vfat /dev/sda1 /mnt/USB
[/LIST]
but today, it doesn't show. Can't add remove programs either. 

 I had to delete this file
/var/lib/apt/lists/lock
then sudo apt-get check
the computer then said to run dpkg --configure -a
so I sudo'd that.
It did a few "setting up..." one was java, and a few...

Then I re-ran my mount command (up there) and the drive showed up.

---

### Post by Fingers &amp; Thumbs on 2007-10-12
Thanks for the quick response, I've just tried it, but can't get beyond (2.)

"sudo: mkdir/mnt/USB: command not found"

It has been suggested on the Linux format forum that I may be able to access it using the Live CD, obviously this isn't ideal, but if it works it would allow me to backup my files while I try reinstalling ubuntu, although I may wait for Gutsy before I do that.

I'll return with news once I have tried that method

---

