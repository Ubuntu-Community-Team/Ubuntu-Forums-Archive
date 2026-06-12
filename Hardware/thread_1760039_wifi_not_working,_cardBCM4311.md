---
title: "wifi not working, card:BCM4311"
date: 2011-05-16
forum: Hardware
---

### Post by hit.and.run on 2011-05-16
[LEFT]I'm using Natty.

I have a wifi card (as obtained from the command **lspci -v | less**)- 
```

03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
        Subsystem: Broadcom Corporation Device 0465
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at b4000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: ssb
```I also have the following packages installed:
1. bcmwl-kernel-source
2. broadcom-sta-common
3. broadcom-sta-source

Also, my laptop Lenovo 3000-Y500, has
1. a manual wifi switch (which glows properly in Windows, but not in Ubuntu) and also 
2. has a keyboard shortcut to enable/disable wifi (the keyboard shortcut works by pressing the Fn key + F4 key)

The output of **lspci -vnn | grep 14e4** -
```

03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0465]
```
Even after all this, ubuntu does not detect any wifi networks. **Wifi-radar** also does not detect my wifi card. what should I do?
[/LEFT]

---

### Post by shnutzer on 2011-05-16
Hey there!

I've got the same card!

I haven't yet managed to install a working driver other than ndiswrapper on Ubuntu from 10.04 to 11.04.

If you want to try ndiswrapper, keep reading:
Run in terminal:

> sudo rmmod b43
sudo rmmod ssb
sudo rmmod wlto remove conflicting modules

Then do a back-up:

> sudo cp /boot/initrd.img-`uname -r`  /path/to/somewheresafeAnd finally update initrd.img:

> sudo update-initramfs -uThen install the driver using ndiswrapper  (package is called ndis-gtk)

> sudo apt-get install ndis-gtk ndiswrapperDriver:
[http://ubuntuforums.org/attachment.php?attachmentid=192348&stc=1&d=1305568967](http://ubuntuforums.org/attachment.php?attachmentid=192348&stc=1&d=1305568967)

Another link:
[http://dl.dropbox.com/u/20414532/bcmwl.tar.gz](http://dl.dropbox.com/u/20414532/bcmwl.tar.gz)

(Be sure to unpack it first ;p )

Then add "ndiswrapper" (without quotation marks) to /etc/modules:

> gksu gedit /etc/modules
Ta-dah! You should have WiFi working! :p

---

### Post by dixonstalbert on 2011-05-16
thank you!!

this got my Acer Aspire 3680-2472 working when the STA driver that ubuntu automatically installed and the OEM Windows Vista Broadcomm driver from Acer did not.

---

### Post by hit.and.run on 2011-05-17
> **shnutzer said:**
> 
Ta-dah! You should have WiFi working! :p

It works !! You rock dude...

---

