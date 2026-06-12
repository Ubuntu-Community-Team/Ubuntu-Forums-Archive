---
title: "can't get splashy!"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by Nokes on 2009-04-27
okay, i'm trying to remaster Ubuntu Jaunty NBR, and i want to make my own bootsplash, so apt-get splashy and i get this
```
pkg: error processing /var/cache/apt/archives/splashy_0.3.13-3ubuntu1_i386.deb (--unpack):
 trying to overwrite `/etc/lsb-base-logging.sh', which is also in package lsb-base
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/splashy_0.3.13-3ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
can someone tell me what's going on? did i break break something?

---

### Post by Nokes on 2009-04-28
nevermind, got it!

---

### Post by digitalsushi on 2009-05-07
That's more useless than saying nothing at all :(

---

### Post by aj1140 on 2009-06-09
how did you fix it. im having the same problem

---

### Post by PhrankDaChickenGeek on 2009-06-19
Fix by:

```
 
sudo apt-get install -d splashy
sudo dpkg --force-overwrite -i /var/cache/apt/archives/splashy_0.3.13-3ubuntu1_i386.deb
sudo nano /boot/grub/menu.lst

```

Find the kernel line and add 'vga=791' to it
```

kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 [COLOR="Red"]vga=791[/COLOR] ro quiet splash

```

Save and exit using 'CTRL + X' & 'Y'

---

