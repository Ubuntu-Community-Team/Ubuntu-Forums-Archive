---
title: "Hauppauge 878 (WinTV) and LIRC"
date: 2008-04-29
forum: Hardware
---

### Post by ububug on 2008-04-29
Hi,
I have an Hauppauge bttv 878 WinTV TV card which comes with a remote control. I want to use the remote with lirc to control MPlayer. I'm using Ubuntu 8.04.

I've installed lirc and used the install routine to configure lirc. But dmesg | grep lirc reports:
[   80.531777] lirc_pvr150: bt878 #0 [sw]: no devices found

This is pretty strange since the bttv driver is able to detect and find the card
[   45.623791] bttv: Bt8xx card found (0).
...
[   45.623861] bttv: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb

lircd starts but exits immediately with

lircd(userspace) ready
accepted new client on /dev/lircd
could not get file information for /dev/lirc
default_init(): No such file or directory
caught signal

What's wrong with my installation? How can I fix it?

Best Regards

---

