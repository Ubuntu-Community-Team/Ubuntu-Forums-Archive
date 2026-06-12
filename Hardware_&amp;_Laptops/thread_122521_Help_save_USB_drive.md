---
title: "Help save USB drive"
date: 2006-01-27
forum: Hardware &amp; Laptops
---

### Post by plexi50 on 2006-01-27
This is a tough one, but I think it is possible. I have a 1 gig usb HDD that I tried to install PSL to boot for a project. Long story short, I f*** the drive and it cannot be recognized. However, Ubuntu will still see it in the drive list, just cannot mount. Also gparted cannot open the drive, says "Error: Unable to open /dev/sda - unrecognised disk label." Thought I could get it back by deleting partitions and starting from scratch. It still powers up and works. Just got to force the my way in and clean it up. Any ideas, cause otherwise, its dust.

---

### Post by plexi50 on 2006-01-28
Solved it. Seems as though MS cannot read more than one partion on a USB device....so.....
[COLOR=#000000]sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
sync
cfdisk /dev/sda

and create new 16bit partion, had to reformat from Windoze :cry: but it works now

Ya learn something new everyday
[/COLOR]

---

