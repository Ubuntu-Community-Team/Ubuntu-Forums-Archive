---
title: "Error 25: Disk Read error (boot)"
date: 2006-05-28
forum: Hardware &amp; Laptops
---

### Post by dresnu on 2006-05-28
When I try to boot I always get this error: "Error 25: Disk Read error", then I have to press a button and return to the grub selection list. If I boot the same kernel in recovery mode I have no problem and the system boots up normally. I'm using the 2.6.15-23-686 version. I tried a 386 kernel with the same result though.
Any ideas on what it might be?

---

### Post by Nathaniel on 2006-05-28
Let me guess... SATA-harddrive?

---

### Post by dresnu on 2006-05-28
Nope normal IDE drive on a compaq laptop. Eveything was working normally till yesterday and I didn't do anything particular myself.

---

### Post by dresnu on 2006-05-29
Sorry for bumping this one, but I still have this issue though.
I found out googling that it might be a physical problem with my drive. But how come I can perfectly boot in recovery mode and why can't I still boot if I install a different kernel(which I suppose gets installed in a different sector of the drive)?

---

### Post by frying_fish on 2006-05-29
It could be as you have hinted, a bad sector, and as such the data would be corrupt, best plan is to try and test the drive with any tools provided by its manufacturer.

---

### Post by dresnu on 2006-05-31
I tried the only hdd test I found provided by compaq, which was the boot setup self test and didn't find anything.
After messing around a little bit with grub's options I found out that if I comment out the "savedefault" line in the default's kernel part of menu.list I can boot up normally!
I did the same trick for the windows part, which gave me the same error before, and booted in windows too(not that I was really looking forward to or anything :p).
I'm a little puzzled now because I read out what that option is supposed to do in the grub manual and can't really figure what correlation it might have with error 25...

---

