---
title: "Incorrect Wifi regulatory domain &amp; unable to change"
date: 2011-10-06
forum: Hardware
---

### Post by Hymyly on 2011-10-06
I recently installed Ubuntu on an Acer Aspire TimelineX 4820TG, with several minor problems. One problem I have not been able to fix is that it often boots with the wrong Wifi regulatory domain.

Sometimes it boots with "SE" — which is correct — but often with "US" or "00" instead, which causes Wifi channels 12 and 13 to be disabled. The domain changes on suspend/wake-up as well.

I have attempted to correct this using "sudo iw reg set SE" in the terminal, but doing so causes a complete loss of Wifi functionality with dmesg outputting things like:

```

[  136.901022] wlan0: authenticate with [MAC address] (try 1)
[  137.099679] wlan0: authenticate with [MAC address] (try 2)
[  137.299349] wlan0: authenticate with [MAC address] (try 3)
[  137.499068] wlan0: authentication with [MAC address] timed out
[  147.863661] wlan0: direct probe to [MAC address] (try 1/3)
[  148.062682] wlan0: direct probe to [MAC address] (try 2/3)
[  148.262372] wlan0: direct probe to [MAC address] (try 3/3)
[  148.462092] wlan0: direct probe to [MAC address] timed out

```

So: is there any way to tell the Wifi-drivers to use a particular regulatory domain? Alternatively, is there a proper way to switch regulatory domains at runtime, that doesn't break things?

Moar info:
Ubuntu 11.04 with Linux 2.6.38-11-generic
Wireless adapter is a Broadcom Corporation BCM43225 802.11b/g/n

---

### Post by Hymyly on 2011-10-13
I have added "iw reg set SE" to my rc.local, but there has to be a better way to change the regulatory domain?

Despite this, it still doesn't work. If I try connecting to a network on channel 12 or 13, I get the "direct probe timed out" messages from the previous post. The hardware is Europe-compatible; I purchased the laptop in Europe and it worked fine with the preinstalled Windows 7. The problem must be in the driver.

What's even stranger is that my network sometimes appears twice in the list of found networks: one with WPA2 (correct) and one with WEP (incorrect). I don't know if this is related.

I have tried installing the proprietary driver for my adapter, but it appears to run under US regulations, and I have not found how to change this. ("iw" says "nl80211 not found.") Any suggestions?

This is a bit of a showstopper for me since I sometimes find myself unable to connect to the networks at the university. I am seriously thinking about going back to Windows 7 since students at uni can get licenses for free through MSDNAA. :p

---

### Post by Hymyly on 2011-10-19
I have now upgraded to Ubuntu 11.10, and the problem persists. (At least I think I have upgraded properly. It failed with bug #859373 at first, and I had to run some dpkg-commands to get it to complete. And Grub refused to boot Linux 3 initially, so hackety-hack grub-install.) So anyway, Linux 3.0.0-12-generic still cannot make any sense of this. The problem is the same as before. And seeing as how I am not getting any replies in this forum I guess I am the only one with this problem.

Is there any way to inhibit the buggy wireless regulatory agent altogether? The documentation I've found on this matter is scarce, possibly because it borders on illegal. (I wonder what Torvalds would have said if they'd told him in 1992 that his kernel one day would have a component called the "central regulatory domain agent" which made sure users obeyed the law. :))

Apart from that I can only hope that the problem will be fixed in Pendulous Penguin. Or Quarrelsome Quadruped.

---

### Post by NovHak on 2012-03-12
Hej from France !

I doubt you are the only one with this problem. I don't have the exact same one since I don't use a Broadcom NIC. Here it's just that the driver (iwl4965) ignores CRDA settings and does its choice using its own internal rules.

Eventually I didn't experience problems in practice, but iw list gives me the following about channels 12 and 13 :
                        * 2467 MHz [12] (15.0 dBm) (passive scanning, no IBSS)
                        * 2472 MHz [13] (15.0 dBm) (passive scanning, no IBSS)

... which means I can use them to connect to APs using this frequency, but neither do active scanning nor create an ad-hoc network. That's fine most of the time, but what if I want to create an ad-hoc network on channel 13 ? Or do an active scan ?

Anyway, back to your problem, which seems more annoying than mine, since you can't even connect to APs on channels 12 and 13... **I would advise that you first do an "iw reg set SE", then rmmod your wireless module, wait 15 seconds or so, and modprobe back your wireless module.** I said rmmod instead of modprobe -r because modprobe -r would remove all wireless-related modules, including cfg80211, and your custom regulatory information would be lost. With rmmod it would be retained, and your wireless module would start with the correct regulatory domain already set, contrary to what was probably the case before.

In the case it works, it will serve as a workaround until this issue is addressed.

Hope this helps !

---

