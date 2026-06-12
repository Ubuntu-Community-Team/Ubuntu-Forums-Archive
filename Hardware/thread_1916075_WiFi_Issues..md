---
title: "WiFi Issues."
date: 2012-01-27
forum: Hardware
---

### Post by smileyboyblue on 2012-01-27
Hi all, I am hoping someone here will be able to help me out. Yesterday I ran sudo apt-get update/upgrade but didn't pay to much attention to what as in it (I know i probably should have) and now my wifi is broken. It will connect for about 10secs then disconnect, reconnect etc etc. I dual boot with Windows and that works ok so I don't think it's a hardware problem.
My laptop is an Acer Aspire 5810T, OS is Ubuntu 11.10 with Gnome shell and kernel version is 3.0.0-12

I am a relative noob so give to me easy!

Thanks in advance.

---

### Post by madvinegar on 2012-01-27
Open up a terminal, write:

```
lspci
```

and please post the results.

---

### Post by smileyboyblue on 2012-01-27
****@smileyboyblue:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
02:00.0 Network controller: Intel Corporation WiFi Link 5100

---

### Post by madvinegar on 2012-01-28
Go to system->administration->additional drivers and see if a proprietary driver regarding your wireless network is activated.

If it is, deactivate it, and activate it again (also do a reboot after each activation/deactivation) and see if your wireless will work.


Also you can try unloading and reloading the driver.

In terminal write:

```
rmmod iwlagn
modprobe iwlagn 
```

And see if this will work.

---

### Post by smileyboyblue on 2012-01-28
Well apparently I have  no proprietary drivers on my system at all, I've been with Ubuntu/Linux since 10.10 and have had no major wireless problems before. The terminal code didn't work either.

I'm now thinking this problem may actually be with my router though as I tried my laptop on two different networks today and had no issues. Still strange that everything else on my network works fine though. I'm going to try restoring my router to its factory settings and see how that goes. I will report back.

---

### Post by smileyboyblue on 2012-01-30
Ok a factory restore of my router seems to have fixed it. Thanks for your help anyway.

---

