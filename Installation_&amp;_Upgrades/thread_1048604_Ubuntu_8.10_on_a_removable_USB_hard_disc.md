---
title: "Ubuntu 8.10 on a removable USB hard disc"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by ClockworkPlum on 2009-01-23
Hello.

As I had Ubuntu and Windows XP installed on the same hard disc, partitioned, and as there is not much space on that hard disc (40GB) which made Windows boot really slow, I now want to try and install Ubuntu 8.10 on a removable hard disc. However, I couldn't find a proper tutorial for that (many of those just said "remove your main hard disc in order to assure you don't install it on the wrong one", it would have been easy only if I weren't using a laptop).

If someone can help me out, I want to install Ubuntu on a Verbatim USB hard disc, 120 GB (80GB free), File system FAT32. What do I need to do to prepare the disc for the installation, do I need to delete all files stored on it? 

And one more question, how do I configure dual boot afterwards? Will Windows XP be able to boot if I remove the removable hard disc? 

Thank you :D

---

### Post by Pumalite on 2009-01-23
Make sure you install Grub on the external drive: step 7 of the installation: 'Advanced Tab'; replace '(hd0)' for /dev/sdb1 (should be that if you have only one HH). Use the option: 'Use Entire Disk'
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)

---

### Post by ClockworkPlum on 2009-01-23
Thanks Pumalite for your reply but I can't access the link, is it operational? If you could fix it thanks :)

---

### Post by Pumalite on 2009-01-23
Maybe is too old. I'll give you this:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)
It's for Pendrives, but you can use it on your external drive.

---

### Post by ClockworkPlum on 2009-01-24
Thanks :)

---

