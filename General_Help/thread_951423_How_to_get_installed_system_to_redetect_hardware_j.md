---
title: "How to get installed system to redetect hardware just as liveCD does."
date: 2008-10-18
forum: General Help
---

### Post by brallan on 2008-10-18
I got kernelpanic on my desktop, and a bit of investigation revealed that it was a motherboard failure. 

Now I would like to remove my harddrives, install them in another desktop, but when i have done this in the past I have wound up needing to reinstall to get the hardware detection right. this seems kind of silly, since the liveCD detects everything wonderfully.

is there a simple command to do this reconfiguration at boot or reboot?

---

### Post by geirha on 2008-10-18
I don't think there is. However, it should handle most changes, but the GRUB boot loader may get confused, and if it has a different graphics card, you might need to reconfigure Xorg, especially if it's a graphics card that require a proprietary driver. Any hardware that requires proprietary drivers are problematic in fact.

For GRUB problems, it may be as easy as altering the boot order in the bios, or you may need to reinstall grub. The [SuperGrubDisk](http://www.supergrubdisk.org/) is apparently very easy to use for these kind of things (though I've never tried it myself, even people with little experience seem to be able to fix GRUB using it).

For the Xorg. If the new system has a graphics card that uses an open source driver, it is likely that it will just work, though you might need to change resolution. If it needs a proprietary driver, installing the driver should be enough. If you had such problems with previous releases, it is likely to work better with Hardy, as there have been great improvements in the Xorg that ships with Hardy. [https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy)

In general, if you do run into trouble, it's very likely you can get it fixed by asking for help at these forums. Just make sure you mention that you transferred the harddrives to a new system to avoid confusion.

If you boot the liveCD, does all the hardware work on that desktop?

---

### Post by brallan on 2008-10-18
> **geirha said:**
> If you boot the liveCD, does all the hardware work on that desktop?

Yes, it works great. Actually, most everything seems to work fine, I just need to redo the graphical setup, as you said. I have run into this issue several times and looked high and low for a simple solution. The thing is, answering the questions involved with a xorg reconfig when the liveCD just works seems like such a pain. It just seems like something that a liveCD should be able to DO, like boot up, and if you are happy with the hardware config, then overwrite your hardware config files in an existing install (even if its NOT ubuntu!) but then I suppose that is one of those things which is too much to ask from the already incredibly wonderful CD that we have....

brian

---

### Post by geirha on 2008-10-18
The liveCD relies on xorg's ability to automatically detect hardware. If you look inside /var/log/Xorg.0.log you should find the configuration it uses in xorg.conf-format, so it might work to just copy that to /etc/X11/xorg.conf on your new system. Also, not having an xorg.conf at all may work too.

---

### Post by brallan on 2009-06-15
ok, I have once again had a machine fail on me, and when swapping it into another laptop, which also runs ubuntu liveCD fine, I am having a similar problem. This time its not with xorg.conf, since its the ethernet card. does anyone know how to redetect the LAN card?

when I type ifconfig with the 9.04 liveCD:
```
eth0      Link encap:Ethernet  direcciónHW 00:08:02:2c:5d:69  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:11 Dirección base: 0x1400 

```
but this section is completely missing when I load up with the recently swapped hard drive.

any advice is greatly appreciated.

---

### Post by brallan on 2009-06-15
and both the liveCD and the disk have the same /etc/network/interfaces:

```
auto lo
iface lo inet loopback
```

---

### Post by brallan on 2009-06-15
boy do I feel stupid. I tried it again and it worked fine. I suppose the first time i booted up without the LAN cable in the machine, now it detected the network without problems.

amazing that it redetected all the hardware perfectly! gnu/linux ROCKS!

---

