---
title: "Removing command line from GRUB for all boots"
date: 2010-03-01
forum: Hardware
---

### Post by lukekirstein on 2010-03-01
Hello, I recently installed Ubuntu on my Dell Inspiron 6000, and after a couple of hiccups, I got it to boot.

After installing Ubuntu, I could not get it to boot into the first hard disk (the primary hard drive I use) because of a "Device not found" error. After some investigating, I discovered I had to edit a command in Grub in order to get it to boot past this error (something about the search -- no floppy command) by editing with 'e' and then 'Ctrl+X'. Got it to boot.

Now I have to manually remove this line in order to get Ubuntu to boot on restarts, regular boots, coming up from hibernation, anything. How can I remove this line indefinitely? Thanks!

---

### Post by lukekirstein on 2010-03-01
Bump. Help please?

---

### Post by meierfra. on 2010-03-01
Have a look at this How-To

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

Also, please do not bump your thread more than once every 24 hours.

---

