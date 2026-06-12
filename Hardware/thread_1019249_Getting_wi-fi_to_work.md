---
title: "Getting wi-fi to work"
date: 2008-12-22
forum: Hardware
---

### Post by kedarm on 2008-12-22
Hey,

I use a six year old Dell Inspiron 600m with the Broadcomm chipset. My wi-fi always gave me lots of problems, till Ubuntu 8.04 came around, where it suddenly began detecting wireless connections.

Now, after installing Ubuntu 8.10, the detection of wireless networks stopped. I tried the following -

1) Installing b43-cutter
(a) Installed b43-cutter
(b) Installed wi-fi radar, which I can run only hrough terminal with sudo privileges
(c) Restarted the machine
(d) Started wi-fi radar
But, it does not detect any network. I entered the SSID of the network too, but still it does not show any network at all.

2) Windows Wireless Drivers
I went to System --> Administration --> Windows Wireless Drivers
It gave me the 'install new driver' option, but it requires an .inf file. All drivers on the Dell website are .exe files, so no success there either.

I have done the following checks already -
1. Checked that the wireless network was present (connected through another laptop)
2. The driver is in place now, for it shows me a wlan and wmaster0 specs when I give the ifconfig command in the terminal.

Anyone has faced similar problems? Help needed!

---

