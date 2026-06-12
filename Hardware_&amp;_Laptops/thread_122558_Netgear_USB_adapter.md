---
title: "Netgear USB adapter"
date: 2006-01-27
forum: Hardware &amp; Laptops
---

### Post by VirusScanner on 2006-01-27
Hi, I'm Parker and I'm new to linux/ubuntu. I ordered the CDs and they arrived, so I installed one on my laptop. It has a Netgear MA111 USB wireless adapter which works fine with windows but not with linux (of course).

To set it up I followed a tutorial on this website, getting the ndiswrapper installed and loading it. The Networking administration tool shows a wlan0 connection but it takes forever to enable and firefox gives me "x cannot be found" for website names and "connection was refused" for IP addresses.

So I'm hoping someone can tell me how to fix it. Thanks.

---

### Post by VirusScanner on 2006-01-28
I figured I'd post the output of iwconfig here too

```
wlan0     IEEE 802.11b  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:11 Mb/s
          RTS thr:-1034772768 B   Fragment thr:-1034772768 B
          Encryption key:off
          Power Management min timeout:0us  mode:All packets received
          Link Quality:100/100  Signal level:-68 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:39   Missed beacon:0

------------- Output from "iwconfig wlan0 channel 9"

Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Invalid argument.
```

Thanks to anyone who can help. I'm interested in doing some development on linux but I can't do much until I can download the gcc packages.

---

### Post by mips on 2006-01-28
Go have a look in the Hardware/Networking section. Maybe do a search for posts by Lambert and also check out his signature for helpfull info.

---

### Post by az on 2006-01-28
I think there are several revisions of this device and several chipsets.  I have gotten a prism2_usb chipset device to work like this:
[http://ubuntuforums.org/showpost.php?p=627259&postcount=5](http://ubuntuforums.org/showpost.php?p=627259&postcount=5)

I would assume you have a prism2 device (check the device manager when you have it plugged it, or check the /var/log/messages log)

---

### Post by VirusScanner on 2006-01-28
I tried the instructions in that post but it still isn't working :(

I have a feeling the device is being recognized as it shows up in the network tray icon (is it the "tray" in linux too?) as wlan0 having a signal strength of 100% but that it hasn't received any packets.

And it only recognizes it as an IPv6 device I think, since the IP address is listed as 00:00:00:00:00:00 instead of 0.0.0.0 and iwconfig and other internet tools only show it as having IPv6 properties. Is there a command that I can try that forces it into IPv4 mode?

Thanks everyone.

---

### Post by Jynx on 2006-02-02
I am having the same exact problem.

I install Ubuntu for the first time ever today.

I followed the instructions here for the MA111 v1 

[http://www.ubuntuforums.org/showthread.php?t=22995&highlight=ma111](http://www.ubuntuforums.org/showthread.php?t=22995&highlight=ma111)

Takes a long time to enabled, yet never pulls an IP.. I see the exact same things as VirusScanner, and I cannot figure it out.

---

### Post by martian643 on 2007-11-03
Ditto.  A Netgear WG111 is supposed to work "out of the box"
Not for me.

---

