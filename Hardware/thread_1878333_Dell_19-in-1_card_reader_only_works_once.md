---
title: "Dell 19-in-1 card reader only works once"
date: 2011-11-09
forum: Hardware
---

### Post by jdfoote on 2011-11-09
After a reboot, when I put an SD card in my card reader, it always works. However, after I remove the card (using safely remove in the unity menu), it doesn't work when I put it back in.

I never noticed this problem under 11.04.

I read some other posts about using modprobe to restart the reader, but I can't figure out what command I am supposed to use. When I run lspci I don't see the card reader on there anywhere.

---

### Post by palimmo on 2012-04-09
> **jdfoote said:**
> After a reboot, when I put an SD card in my card reader, it always works. However, after I remove the card (using safely remove in the unity menu), it doesn't work when I put it back in.

I never noticed this problem under 11.04.

I read some other posts about using modprobe to restart the reader, but I can't figure out what command I am supposed to use. When I run lspci I don't see the card reader on there anywhere.

Same problem with Ubuntu 11.10 e Ubuntu 12.04 beta2.
Packard Bell Easynote TJ65.

---

### Post by dandnsmith on 2012-04-09
Sounds like what has happened is that you've safely removed not the card, but the card reader. I've seen the same thing happen to Windows users.
What you have to do is to eject the card or unmount the filesystem on it, and then the card-reader will remain available for use.

---

### Post by kurt18947 on 2012-04-09
> **dandnsmith said:**
> Sounds like what has happened is that you've safely removed not the card, but the card reader. I've seen the same thing happen to Windows users.
What you have to do is to eject the card or unmount the filesystem on it, and then the card-reader will remain available for use.

This is the likely answer.  Eject unmounts/removes the card.  "Safely remove" removes the card and its reading device.  If I pick the wrong choice, logging out and logging back in may fix it without a full reboot.

---

### Post by palimmo on 2012-04-09
After the first use, if I use "Eject" or "Safe Remove" the result is the same: it doesn't mount my card anymore.
Only after 5 attempts (insert-remove, insert-remove,...), it works!

---

