---
title: "Can't save new options file for SDcard fix in 10.10"
date: 2011-03-21
forum: Hardware
---

### Post by solutionorppt on 2011-03-21
So I successfully installed 10.10 UNR on an Acer Aspire One last night, and installed all of the Canonical repositories, updates, etc. and fixed the wireless issue... The only problem left was the well-known SD card reading problem... So I:

[FONT=courier new]sudo gedit /etc/modprobe.d/options

then entered into the text editor:

[/FONT][FONT=courier new]options sdhci debug_quirks=1

[FONT=Arial]And saved the file, then rebooted.  The SD card read the card on the next boot, but not the subsequent one.  I reopened modprobe.d/options and the file was blank.  I tried to re-enter the text and save the file, but recieved the message: "Could not find the file /home/mrnetbook/etc/modprobe.d/options."

FWIW, the file definitely exists:
~$ dir /etc/modprobe.d
alsa-base.conf        blacklist-firewire.conf     blacklist-oss.conf               options
blacklist-ath_pci.conf    blacklist-framebuffer.conf  blacklist-watchdog.conf
blacklist.conf        blacklist-modem.conf        intel-5300-iwlagn-disable11n.conf

[/FONT][/FONT]

---

