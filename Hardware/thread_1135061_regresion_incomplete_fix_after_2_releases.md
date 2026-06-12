---
title: "regresion incomplete fix after 2 releases"
date: 2009-04-24
forum: Hardware
---

### Post by tulpina on 2009-04-24
Not MY dongle, I haven't tested yet in Jaunty, but this is from a bug report where I subscribed, someone wrote:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268502](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268502)

"Mine still does not work. This is a regression form 8.04 over two
releases 8.10 and 9.04. I wonder why the Bluez bug (filed more than six
month ago) is still considered New (through two releases), importance
undecided (decidedly important to me) and unassigned (I am not able to
fix it myself!)

uname -a
Linux library 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
dpkg -l | grep bluez
ii  bluez                                      4.35-0ubuntu1
lsusb
Bus 003 Device 002: ID 2001:f111 D-Link Corp. [hex] DBT-122 Bluetooth adapter
hciconfig -a
hci0:    Type: USB
    ...UP RUNNING 
    ...Can't read local name on hci0: Connection timed out (110)"

---

