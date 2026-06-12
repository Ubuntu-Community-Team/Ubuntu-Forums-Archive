---
title: "Help with Imon Pad and Lirc for Xbmc"
date: 2009-09-06
forum: Hardware
---

### Post by bogoliubov on 2009-09-06
I can't get my Imon Pad to work under Ubuntu (9.04 32 bit). Please help. I am at wits end with this!

In gnome-lirc-properties, is it detected correctly and, after having made the fix suggested on [https://bugs.launchpad.net/ubuntu/+source/gnome-lirc-properties/+bug/350825](https://bugs.launchpad.net/ubuntu/+source/gnome-lirc-properties/+bug/350825) ) it can also apply and save settings.

Also, I put "options lirc_imon pad2keys_active=1" in /etc/modprobe.d/lirc_imon.conf to get the pad keys working (though I'd like to use it both as keys and mouse)

However, I can't get the remote to work, and irw doesn't report any keypresses.

Here's some info:

```
ls /dev/lirc*
crw-rw---- 1 root root 61, 0 2009-09-06 08:07 /dev/lirc0
srw-rw-rw- 1 root root     0 2009-09-06 08:07 /dev/lircd

```

```
lsusb
Bus 003 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller

```

```
lsmod | grep lirc
lirc_imon              22924  0 
lirc_dev               19892  1 lirc_imon

```


Now if I stop lirc:
```
sudo /etc/init.d/lirc stop
 * Stopping remote control daemon(s): LIRC                                                   [ OK ]
```

and the execute these commands I found on [http://ubuntuforums.org/showthread.php?t=865356](http://ubuntuforums.org/showthread.php?t=865356) :
```
sudo /usr/sbin/lircd --driver=default --device=/dev/lirc0 --pidfile=/var/run/lirc0.pid --listen=8765
sudo /usr/sbin/lircd --driver=default --device=/dev/lirc1 --pidfile=/var/run/lirc1.pid --output=/dev/lircd --connect=localhost 8765

```
I still have the same devices in /dev, but now irw reports all keypresses except the directional keys and the shutdown key...!?!

So it seems I should be able to get it working, but I want it to work correctly by itself and I need the directional keys!

I desperately need it working!

Btw; if I get it working, what do I need to do to have it working under XBMC?

---

### Post by bogoliubov on 2009-09-06
bump....

---

### Post by bogoliubov on 2009-09-06
I really, really need some help with this...!

---

### Post by bogoliubov on 2009-09-08
No one?

---

### Post by bogoliubov on 2009-09-08
Ah, I solved it by purging all lirc related packages and reinstalling _withou_ gnome-lirc-properties. Now after some hacking of Lircmap.xml it kindof works... Except the directional keys.

---

