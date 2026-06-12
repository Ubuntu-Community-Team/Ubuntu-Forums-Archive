---
title: "Load module with parameters"
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by Hushpuppy on 2006-02-04
Hi,
I am having trouble with my Firewire hard disk.  It worked great under Red Hat 9 (kernel 2.4.18 or so).  Works great under Windows XP.  It is not working under Ubuntu 5.10, or 6.04 (currently running, with kernel 2.6.15).

I want to start the module   "sbp2"  with some failsafe parameters, but I don't know how to interject these params in the proper place.  After the machine starts, I can't rmmod and modprobe because by that time there's some sync error or something.

Anyway, where can I put the parameters so that the system will load sbp2 properly?  I'd think /etc/modules but I don't think that's right, because sbp2 is not even in there yet somehow- via a hotplug mechanism or whatnot- the system is loading the module when it discovers my ieee1394 device.

BTW, I'm running on a laptop, if that matters, but assume that the ieee1394 device is in the machine upon bootup.

Thanks for the help.

---

### Post by joft on 2006-02-05
Hi,

to set options you have to add a file to the directory /etc/modprobe.d . Add one new line to this file, which looks like:

```
options sbp2 <option>,<option>
```

Note: I think, this only works, if sbp2 isn't loaded by the initrd. If it's loaded by the initrd you have to change that.

---

### Post by thoffland on 2006-02-05
I'm just taking a stab at it here, but have you tried 
```
ivman
```
I came across it one day and it's been great for my PCMCIA card when I lose a connection... just unplug, and type that and replug it. Should work with USB/Firewire too I think. It's supposed to recognize any "plug and play" type of devise.

---

