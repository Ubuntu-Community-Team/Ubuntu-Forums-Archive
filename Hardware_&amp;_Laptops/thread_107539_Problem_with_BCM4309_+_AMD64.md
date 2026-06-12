---
title: "Problem with BCM4309 + AMD64"
date: 2005-12-23
forum: Hardware &amp; Laptops
---

### Post by xMaximex on 2005-12-23
Hi,

I have an NX6125 HP Compaq notebook (PN: PZ222UA, the BIG one)

The output of "lspci" for the wifi adapter :
Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)

I installed BCMWL5A.inf windows driver with ndiswrapper, "modprobe ndiswrapper", "ndiswrapper -m". "Ndiswrapper -l" says that the driver and the hardware is present but "iwconfig" doesn't show wlan0 ..

EDIT: I use Breezy 64

Any help will be appreciated

Thanks, Max

---

### Post by Lambert on 2005-12-23
Do you have any of the other files such as .sys or .bin in the same folder as your .inf file on your drive?

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Troubleshooting](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Troubleshooting)

---

### Post by vivedekananda on 2006-01-12
could you post here your "dmesg" output after you do "modprobe ndiswrapper"?

---

### Post by hangfire on 2006-10-17
I have the same problem, any help here?

---

