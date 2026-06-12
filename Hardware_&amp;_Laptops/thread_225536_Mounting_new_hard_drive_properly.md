---
title: "Mounting new hard drive properly"
date: 2006-07-29
forum: Hardware &amp; Laptops
---

### Post by Enigmatic on 2006-07-29
The drive is sda, and it has one partition on it, sda5 which is xfs and 300GB.

I mounted it with sudo mount -t xfs /dev/sda5 /media/Media (created the Media folder).

Now what I can't quite figure out is why it shows up as '300GB volume: Media' in the Computer browser, but it never appears on my Places menu.

Also, I should be editing fstab so it always appears on startup, correct? And, is there a way to make files deleted trigger the 'files present in recycle bin' icon? Right now they appear there, but the icon showing that there are files in there never appears.

---

