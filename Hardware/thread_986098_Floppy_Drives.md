---
title: "Floppy Drives"
date: 2008-11-18
forum: Hardware
---

### Post by theozzlives on 2008-11-18
Ubuntu 8.10 isn't recognising my floppy drives on my older systems. They are setup in my CMOS and activate during post, bur Ubuntu just don't see them. I need to flash my BIOS and need to boot DOS to do ti. please help......

---

### Post by prshah on 2008-11-18
> **theozzlives said:**
> Ubuntu 8.10 isn't recognising my floppy drives on my older systems. They are setup in my CMOS and activate during post, bur Ubuntu just don't see them. I need to flash my BIOS and need to boot DOS to do ti.

Edit your /etc/fstab line, and comment out the line beginning with "/dev/fd0" by placing a # in front of it. 

From Intrepid onwards, removable devices no longer require an entry in the fstab file (which is for "static" filesystems).

Post back if you want more details.

---

### Post by theozzlives on 2008-11-18
Still no dice.

---

### Post by prshah on 2008-11-19
> **theozzlives said:**
> Still no dice.

I hope you've restarted the system... (No other suggestions to offer)

---

