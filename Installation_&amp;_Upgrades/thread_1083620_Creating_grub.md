---
title: "Creating grub"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by elliotn on 2009-03-01
How can I create a Dual boot as i have 2 harddisk, one has Ubuntu 8.10 and the other has win xp, they dont dual boot and I have uo always change in the BIOS to choose the needed OS, HOW can i create grub to load both without formating or reinstalling

---

### Post by lha on 2009-03-01
Set bios to boot from Ubuntu drive and add the following lines to the end of your /boot/grub/menu.lst:
```

title		Windows XP
root		(hd1,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by elliotn on 2009-03-01
Thanks m8 gotta try that.

---

### Post by elliotn on 2009-03-01
It aint working, do i add it on the bottom of everything or  what

---

### Post by lha on 2009-03-02
> **elliotn said:**
> It aint working, do i add it on the bottom of everything or  what

Yes, you add it in the bottom. What error(s) are you getting?

---

