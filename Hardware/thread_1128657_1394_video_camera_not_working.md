---
title: "1394 video camera not working"
date: 2009-04-17
forum: Hardware
---

### Post by keithclark on 2009-04-17
I can't seem to get my 1394 camcorder to work with 9.04.  I tried kino and when I try and capture it gives the following error:

Waring:  raw1394 kernel module not loaded or failure to read/write /dev/raw1394!

Keith

---

### Post by cariboo on 2009-04-17
There is a bug in the version of kino that is included with Jaunty. To solve the problem run Kino as root:

```
gksu kino
```

I edited the launcher in Sound & Video-->Kino to the same thing.

See [this]("http:///help.ubuntu.com/community/Firewire").

Jim

---

### Post by keithclark on 2009-04-18
Thanks Jim, perfect.

Keith

---

### Post by fantasmino on 2009-04-27
Another solution, just for not use Kino as root:

```
sudo gedit /etc/modules
```
add these 3 lines:
```
raw1394
dv1394
video1394
```
save and close.

```
sudo gedit /lib/udev/rules.d/50-udev-default.rules
```
in the section "# Firewire" add this line:
```
KERNEL=="raw1394", GROUP="video", MODE="0666"
```
save and close, reboot and Kino will work again with 1394 for users :P

---

### Post by lisati on 2009-04-30
Thanks. Now to learn Kino!!!!

---

