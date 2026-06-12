---
title: "lirc setup and /dev/lirc problems"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by jc508 on 2007-09-14
Hi,

I am trying to install lirc but having all sorts of difficulty.

a) lots of posts refer to /dev/lirc or /dev/lirco I don't have these  when would I expect to see them? are they normally there but dormant or does the act of getting lirc to load create then ?

b) lots of posts refer to /etc/lirc/hardware.conf and mention only one of what look like three areas that need to be modified.  How do you know when to use which
currently running 
# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_dev lirc_mceusb"

Do I need a device or driver ??

The problem is the modules never load and the only advice I can find if this happens is to check dmesg output.  Alas my dmesg only returns 1900 lines of TV tuner junk

Help really needed
Thanks
JC

---

