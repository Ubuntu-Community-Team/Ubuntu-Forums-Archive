---
title: "Installed Ubuntu 11.04 HP Pavillion dv6000, No Internet"
date: 2012-07-16
forum: Hardware
---

### Post by jessemillwood on 2012-07-16
Hi there, 

I recently attempted to install Ubuntu 11.04 on my HP Pavilion dv6000 (dv6423om) and I cannot connect wirelessly to the internet. I have read through many threads on how to fix this. (I have a broadcom BCM4311 card in my laptop.)

My problem is: I cannot connect over Ethernet because my Ethernet port is physically damaged. 

I have gotten rid of vista and put xp on my laptop and was able to get drivers on it through the use of a memory stick with drivers on it.

I am new to linux and have been an avid windows user for a while, I would like to change over to being an avid linux user so please excuse me if this is a newbie question. I have a few books that I am trying to get up to speed with but I do not know where to find these driver files so that I can transport them from a computer with internet connection to my crippled laptop. 

Thank you for any information and help,

jesse

---

### Post by ahallubuntu on 2012-07-16
I'm sure it's possible to download everything manually to a USB flash drive and get it working, but I wouldn't be able to tell you off the top of my head.

However, here are a few practical alternative methods:

- buy a USB to ethernet adapter, like this one for $3 USD shipped from Asia:

[http://www.ebay.com/itm/Ethernet-External-USB-to-Lan-RJ45-Network-Card-Adapter-10-100-Mbps-for-Laptop-PC-/251108073466](http://www.ebay.com/itm/Ethernet-External-USB-to-Lan-RJ45-Network-Card-Adapter-10-100-Mbps-for-Laptop-PC-/251108073466)

then in the future, you'll at least have the option to get wired ethernet again without wireless.  Of course, this will probably take 2-3 weeks to arrive shipped from Asia.  You can find the same thing in the US for a few bucks more, maybe even on your local Craigslist.  Handy to have one around for this laptop in any case.

- buy a USB wireless dongle for about $5 on eBay.  Same idea:

[http://www.ebay.com/itm/150M-Mini-USB-Wireless-Adapter-WiFi-802-11n-150Mbps-Network-Card-For-Laptop-PC-/221043918275](http://www.ebay.com/itm/150M-Mini-USB-Wireless-Adapter-WiFi-802-11n-150Mbps-Network-Card-For-Laptop-PC-/221043918275)

(Someone dug up one on Amazon that cost only slightly more, looks to be the same chipset:

[http://www.amazon.com/Bl-lw05-5r-802-11n-Wireless-Adapter-Chipset/dp/B004LPY204](http://www.amazon.com/Bl-lw05-5r-802-11n-Wireless-Adapter-Chipset/dp/B004LPY204)

)
I have a couple of these.  This will work in 11.04 but not without downloading the 8192CU Linux driver from Realtek's website (you have to build it in a terminal).  They work natively in 12.04 LTS.  These dongles are extremely handy.

Of course, 12.04 LTS may solve your problem as well without doing anything, and it will be supported for years.  Support for 11.04 ends in a few months.

---

### Post by Bucky Ball on 2012-07-16
Support life:

12.04 LTS = April 2017 (yes, five years support)
10.04 LTS = April 2013
11.10 = April 2013
11.04 = October 2012

In other words, you have just on three months until 11.04 reaches end of life, i.e. no more updates, including security ones, although still usable.

I would advise attempting to install a release that has more support left. ;)

BTW, I had the exact same machine and this card now works virtually 'out of the box'. You need to get online with a cable, do an update, check 'Additional Drivers'. You are looking for B43. If this doesn't work try installing:

b43-fwcutter
firmware-b43-installer

You may or may not be aware that this model was recalled by HP because of a major manufacturing flaw, repaired and/or replaced worldwide. This first sign of the issue was a dead card (nothing wrong with it, though, because it is actually the motherboard dying). I hope this is not the case for you as the recall period would have ended (unless you still have warranty). What worries me is that this card should be recognised and installed the moment you get online with a cable. Maybe you could provide us with the output of this command in a terminal:

```
sudo lshw -C network
```@[ahallubuntu]("http://ubuntuforums.org/member.php?u=32392"): Advising the purchase of a new card is not good advice about fixing this one. This one works fine in 10.04 LTS (and did in 8.04 LTS with the advent of the b43 drivers), just sounds like it needs some tweaking (unless of course it is the manufacturing fault and the machine is on the way out, in which case a dongle ain't gonna achieve much). I used a dongle when mine died and the dongle worked for a day before that died too. ;)

---

### Post by robtygart on 2012-07-16
I have a dv6000 too. Did you go into your additional drivers and actavate it? I had to on mine.

System Settings>Additional Drivers

Also I agree try out 12.04, I am using both Ubuntu and Kubuntu.

---

### Post by ahallubuntu on 2012-07-16
> **Bucky Ball said:**
> @[ahallubuntu]("http://ubuntuforums.org/member.php?u=32392"): Advising the purchase of a new card is not good advice about fixing this one.

You are welcome to your opinion - don't let anyone try to take that away from you.  I am also entitled to mine; just because you disagree doesn't make it "not good advice."

Suggesting someone spend a whopping $5 USD on a spare wireless card he could also use in the future for other things doesn't seem like such a bad idea vs. perhaps spending hours trying to get his existing card to work.  (If he installs the USB dongle and gets online, he could then easily use one of the posted solutions to get his existing card to work.)  These cheap little USB dongles are extremely useful to have around in a pinch.

The OP is welcome to disregard my advice.

---

### Post by jessemillwood on 2012-07-16
@allhallubuntu: 
I did try buying a usb/ethernet dongle at a local mom and pops computer store (I try going to big stores like bestbuy as a last resort) but I forgot to check the compatibility and it appears that it is only compatible with windows and mac. I will try and order one soon if I cant figure anything else out. Thank you for the links though!

@Bucky Ball:
I do realize that there was a recall, I actually did send mine in about 3 years ago because it wouldn't turn on. They replaced the mother board for about $450. But I'm trying to work with what I have. 
The output to "sudo lshw -C network" is:
```
PCI (sysfs)  
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:b6000000-b6003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:63:46:76
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
```

It seems that I should either update to 12.04 or get a dongle that is compatible with linux?

Thank you both for your responses

---

### Post by jessemillwood on 2012-07-16
@robtygart:
I did try that but I need an internet connection to do that

---

### Post by robtygart on 2012-07-16
Sorry Brain fart...

---

### Post by robtygart on 2012-07-16
:oops: Double post.......

---

### Post by techvish81 on 2012-07-16
try connecting with a phone usb tethering,  and i also suggest you to try out 12.04

---

### Post by ahallubuntu on 2012-07-17
Not all USB wireless dongles are the same.  Inside, they use a wide variety of chipsets.  In my experience, the "name" brands like Cisco/Linksys, D-Link, and Netgear have proprietary firmwares that have trouble with Linux and may not be supported at all.  Generic "no-name" cards tend to work best in Linux in my experience; you can usually get the driver directly from the chipset manufacturer (e.g. Realtek).

If you get the specific USB dongle I mentioned above from eBay or Amazon, you can compile a Realtek driver yourself that will work.  And you can probably use it to get online and get your internal card working, then unplug the USB dongle and have it as a spare or use it for something else besides your laptop.

---

### Post by Bucky Ball on 2012-07-17
Have you actually gotten online with a cable, updated and checked 'Additional Drivers' (as suggested in two posts)? Have you gone to Software Centre or Synaptics and installed 'b43-fwcutter' and 'firmware-b43-installer' if that didn't work for you, as suggested earlier?

Repeating; that card has worked (virtually) out of the box since the advent of b43 (about four years). It is extremely common and buying a dongle would be a waste of money (even if it is $3) before spending a little time on this because you have a perfectly good, compatible card in the machine already (not opinion, fact). Good luck. ;)

PS: Looks like the b43 driver has automatically installed (it is now part of the kernel, as you can see from your output). You can see it where it says 'driver' in the read out. You are just missing the firmware-b43-installer as it reads 'N/A' in the output thus the card is 'DISABLED'. Read in bold:

```
*-network **DISABLED**        description: Wireless interface         physical id: 1        logical name: wlan0        serial:  00:1a:73:63:46:76        capabilities: ethernet physical wireless         configuration: broadcast=yes **driver=b43** driverversion=2.6.38-8-generic **firmware=N/A** link=no multicast=yes wireless=IEEE 802.11bg
```PS: Not sure why the code is on one line but it's all there. ;)

You are basically a step away from getting this card up. If you can't get online I think the firmware is on the install CD (could be wrong). Chuck it in and have a look if you can't get online.

---

