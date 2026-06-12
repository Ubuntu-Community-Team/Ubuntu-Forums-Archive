---
title: "Problems installing lirc on dapper"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by gavinb on 2006-10-09
I am installing mythtv 0.20 from source on my Ubuntu Dapper computer.  I was able to get everything to work except lirc.

I am trying to get a Haugpage PVR-150 remote to work.  I followed these instructions.
[http://www.mythtv.org/wiki/index.php/Lirc_on_Ubuntu_Dapper](http://www.mythtv.org/wiki/index.php/Lirc_on_Ubuntu_Dapper)

When I do the following it works.

from the lirc-0.8.0 src
sudo make install
sudo modeprobe lirc_i2c
sudo lircd
irw

but once I reboot and try to get the drivers to load it doesn't work.

Any ideas?
Brian

---

### Post by gavinb on 2006-10-09
Ok I found a little bit more info.

After I run the install it creates
/dev/lirc

but after it reboots it is
/dev/lirc0

Does lircd always look for /dev/lirc?

Could I use a symbolic link?

Brian

---

### Post by gavinb on 2006-10-10
I got my system working, but I wanted to share what I did in case any one else has this problem.

Basically lircd was looking for a device at either /dev/lirc or /dev/lirc/0 instead of /dev/lircd0 which is where mine is.

I changed my lircd dameon to point to the correct device path.

---

### Post by gavinb on 2006-10-10
opps

---

### Post by OldGaf on 2006-10-26
> **gavinb said:**
> I got my system working, but I wanted to share what I did in case any one else has this problem.

Basically lircd was looking for a device at either /dev/lirc or /dev/lirc/0 instead of /dev/lircd0 which is where mine is.

I changed my lircd dameon to point to the correct device path.

Thanks for posting this...... I am having the same problem. I will try this tomorrow.

---

