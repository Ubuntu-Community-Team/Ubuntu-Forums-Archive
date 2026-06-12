---
title: "lcd4linux"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by peterthewolf on 2007-07-28
Am trying to run lcd4linux and get these messages

peter@peter-desktop:~$ lcd4linux
security error: owner and/or group of '/etc/lcd4linux.conf' don't match
security error: group or other have access to '/etc/lcd4linux.conf'

peter@peter-desktop:~$ sudo lcd4linux
Password:
security error: group or other have access to '/etc/lcd4linux.conf'

Both lcd4linux and lcd4linux.conf belong to root

What is wrong

---

### Post by [round] on 2007-10-07
chmod u+rwx /etc/lcd4linux.conf
chown root.root /etc/lcd4linux.conf

---

### Post by bartoni on 2007-12-08
Had these same errors, the above didn't work... but...

chmod 700 /etc/lcd4linux.conf

did

---

