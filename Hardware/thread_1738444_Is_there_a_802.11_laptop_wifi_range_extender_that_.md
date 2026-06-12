---
title: "Is there a 802.11 laptop wifi range extender that is known to work with Ubuntu 10.04?"
date: 2011-04-24
forum: Hardware
---

### Post by rocksockdoc on 2011-04-24
I bought the USB Amped UA600 Wireless Router/Antenna WiFi range extender but it is not supported on Linux. 

[LIST]
[*]Internal laptop WiFi radio is 50 mW with a 1 dBi antenna
[*]External USB WiFi radio is 600 mW with a 5 dBi antenna (better antennas can easily be hooked up)
[/LIST]
However, the one I bought just won't work; details here:
**- [How do we tell Ubuntu 10.04 to use a DIFFERENT wireless radio card?]("http://ubuntuforums.org/showthread.php?t=1737183")**

**So, may I ask if there is a KNOWN GOOD WiFi range extender that is known to work on Linux?**


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189813&stc=1&d=1303591188[/IMG]

---

### Post by Dutch70 on 2011-04-26
Without having a direct answer... I just wondered if either of these links might be of some use to you.
[[COLOR="RoyalBlue"]http://www.howtogeek.com/59152/boost-networking-performance-by-installing-tomato-on-your-router/[/COLOR]]("http://www.howtogeek.com/59152/boost-networking-performance-by-installing-tomato-on-your-router/")
[[COLOR="RoyalBlue"]http://www.howtogeek.com/56612/turn-your-home-router-into-a-super-powered-router-with-dd-wrt/[/COLOR]]("http://www.howtogeek.com/56612/turn-your-home-router-into-a-super-powered-router-with-dd-wrt/")

If so and you get your money back on that extender, you gotta split it with me. ;) ...lol j/k.

---

### Post by rocksockdoc on 2011-04-27
> **Dutch70 said:**
> wondered if either of these links might be of some use to you.

Here are the titles to the two links:
- [Boost Networking Performance by Installing Tomato on Your Router]("http://www.howtogeek.com/59152/boost-networking-performance-by-installing-tomato-on-your-router/")
- [Turn Your Home Router Into a Super-Powered Router with DD-WRT]("http://www.howtogeek.com/56612/turn-your-home-router-into-a-super-powered-router-with-dd-wrt/")


[LIST]
[*]The first article discusses installing the Tomato router OS firmware on my home router.
[LIST]
[*]You can download an updated version of Tomato from [http://tomatousb.org/](http://tomatousb.org/)
[/LIST]
 
[*]The second article discusses the DD-WRT router OS:
[LIST]
[*]My wifi extender isn't in the list of [supported routers]("http://www.dd-wrt.com/wiki/index.php/Supported_Devices") nor in the support [help files]("http://www.dd-wrt.com/site/support/router-database")
[*]But I might actually install it on my home router (but not on the laptop wifi extender)
[/LIST]
 
[/LIST]
Interestingly, I picked up another wifi extender yesterday:
- Enenius EUB9603 Wireless 11b/g/n Hight Power USB Adapter (2,000 mW, & a 5 dBi detachable antenna)
- $ lsusb ==> Bus 001 Device 006: ID 1740:9603 Senao

Like its predecessor (the Amped UA600 with the 0bda:8172 Realtek Semiconductor Corp. chipset), the Senao Enenius also came without any Linux drivers. 

Worse yet, the Senao Enenius too failed to operate on the Ubuntu 10.04 laptop, so I must be sailing in uncharted seas.

I'm sure in a few years this problem of Linux-compatible USB wifi extenders will be solved; but, for now, I ask anew:

Q: Are there any KNOWN Linux-compatible USB wifi extenders extant?

---

### Post by rocksockdoc on 2011-11-05
I just received a PM where the owner said this:

> I was successful with the **Amped Wireless UA600** only on MS Windows and Mac OS X. Too bad it will not cooperate with Linux.

Therefore, I just purchased a wireless N300 usb adapter from Monoprice. This works  with all 3 of the aforementioned OS. I had to install drivers for MS and  Mac, but not for Linux where it worked OOB for Linux.  I'm now happy with this N300 USB device. 

I'm still sad about  the Amped Wireless UA600 which is 2.5 months old now and cannot be returned to the CompUSA store that I had purchased it from.Next person to need WiFi extension on Ubuntu Linux, please write a quick review so we all benefit from knowing what works, and what doesn't work on Ubuntu.

---

### Post by rocksockdoc on 2012-01-29
I'm still searching for a Ubuntu-compatible WiFi solution to improve the range of my weak Lenovo X61t laptop (1dbi omni antenna, 17dBm, 50mW radio transmit power).

I just found [this $30]("http://www.wlanparts.com/product/AWUS036H/Alfa-Network-Wifi-USB-80211g-up-to-1000mW.html") Alfa Network Wifi USB, 802.11g up to 1000mW whose [datasheet]("http://static.zoovy.com/merchant/pnt/AWUS036H.pdf") lists Linux 2.6 as being supported even though the device uses the Realtek 8187L chipset  which I had previously found the bugs for in the Ubuntu 10.04 Lucid Lynx distribution:
- [USB drivers not found when plugging in a Senao/EnGenius USB device]("http://ubuntuforums.org/showthread.php?t=1740943")[B]
- [/B][How to tell Ubuntu 10.04 to use a DIFFERENT wireless radio card?]("http://ubuntuforums.org/showthread.php?t=1737183&highlight=USB+drivers+plugging+Senao%2FEnGenius") 			 		  		  		 
[LIST]
[*][Alfa Network AWUS036H]("http://static.zoovy.com/merchant/pnt/AWUS036H.pdf") ==>  $28, omni antenna, 2dBi omni antenna, 20dBm (100mW) radio
[/LIST]
Does anyone have experience with installing this AWUS036H on Ubuntu?

---

### Post by rocksockdoc on 2012-02-28
$16 [GSI High-Powered Ultra-Secure 500mW 150Mbps USB Wireless WIFI Long Range Network Adapter with Detachable External 5dBi Antenna]("http://www.amazon.com/GSI-High-Powered-Ultra-Secure-Wireless-Detachable/dp/tech-data/B003SHA79G")

---

