---
title: "Flash drive file corruption, cannot delete"
date: 2008-09-25
forum: General Help
---

### Post by zx6r1033 on 2008-09-25
I have a folder on my flash drive that was corrupted during the transfer from my hard drive, and neither Vista nor Ubuntu will allow me to remove it. I tried through terminal as well, and it says the file doesn't exist. How can I get rid of it?

---

### Post by prshah on 2008-09-25
> **zx6r1033 said:**
> I have a folder on my flash drive that was corrupted during the transfer from my hard drive, and neither Vista nor Ubuntu will allow me to remove it. I tried through terminal as well, and it says the file doesn't exist. How can I get rid of it?

Most likely a corrupt entry. Open a terminal (Applications-Accessories-Terminal), plug it in, find the device ID with the command ```
dmesg | tail
``` then unmount it ```
sudo unmount /dev/sdd1
``` and run a check on it ```
sudo fsck -a /dev/sdd1
``` (replace sdd1 with the partition/device id as shown in the dmesg output.)

When done, unplug, wait 5 seconds and replug it in: The entry would now have either disappeared or will be "deleteable".

---

