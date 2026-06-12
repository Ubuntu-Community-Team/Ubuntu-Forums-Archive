---
title: "Memory Card Reader Driver"
date: 2006-07-04
forum: Hardware &amp; Laptops
---

### Post by IDeus on 2006-07-04
I am looking for a driver for my laptops memory card reader. Its a RICOH RC5832/843 Flash Media Driver I need (Based on the install of the windows version)

---

### Post by tturrisi on 2006-07-04
The card reader just uses generic firmware on the device chip & generic drivers in the kernel.  What happens when you stick in a memory card?  It should auto-mount and open a window w/ the pic thumbnails in anywhere from 5-30 seconds depending on your system.  It won't appear as a drive in Computer window until it has a card in in and it is then mounted.  On windows, the "drives" show up in My Computer whether a card is inserted or not.

---

### Post by vitaliyn on 2008-03-25
I also have a memory card reader in my laptop, but when i insert a memory card, nothing happens.  It doesn't mount or do anything at all. It shows up in device manager but thats it. Can anyone help?

---

### Post by akwatve on 2008-03-25
I am facing the same problem. I have to type ```
mount /dev/mmcblk0p1 /foo/bar
``` to manually mount the card, Is there any way to mount it automatically. I am using Kubuntu gutsy

---

