---
title: "Linksys wusb54g v.4 Cannot connect, ubuntu 12.04"
date: 2012-07-01
forum: Hardware
---

### Post by gkffjcs on 2012-07-01
I'm reinstalling a system which has attached to it an old Linkys wusb54g v.4 USB wireless adapter. After the install I can "connect" to the network, but then the network manager freezes at "Setting network address!" A few moments later, maybe 30 seconds or a minute, the system disconnects and then retrys. It repeates this forever, never connecting. 

During this process the following message is printed on pty0:
"phy0 -> rt2500usb_set_device_state: Error failed to enter state 3 (-16)"
"phy0 -> rt2x00lib_autowakeup: Error device failed to wake up" 

I have found several instances of people encountering this problem with previous versions of ubuntu. However, all threads make note that the probelm was fixed in later kernel versions, however, I am having the problem with 12.04!

Any help would be greatly appreciated!

---

### Post by ahallubuntu on 2012-07-01
If you google a little, you see lots of people have had issues with this adapter.  I've seen a lot of problems with name-brand adapters from Linksys (Cisco), D-Link, Netgear and have had much better luck with no-name adapters that are supported by the chip manufacturer, not a wireless company that focuses on Windows support.

Personally, I wouldn't waste much time on this old adapter.  I've been buying cheap mini-dongle USB wireless cards that are 150MHZ wireless N and work really well - for about $5 on eBay.  (They may come from Hong Kong or China so be prepared to wait 2-3 weeks at that price.)  I buy them as spares - they are so handy for little projects.  

The one I like to buy has the Realtek, not the Ralink, chipset.  I did have to build a kernel module for it with Ubuntu 11.04 and earlier but it worked solidly after that.  I imagine 12.04 has support built in.

The most recent ones I've bought are the smallest you can buy - not the ones that have "WiFi n" on the sticker or the long white ones.  They say "802.11n" on the end in white type.  These have been Realtek not Ralink for me; sometimes the chipset is noted in the description sometimes not.  The vendors vary.

---

### Post by Mazate on 2012-07-01
Then can you recommend a wireless adapter that is known to work with 12.04?  I have a computer sitting in my bedroom as a paper weight because I can't find a wireless adapter that will work with Ubuntu.  There has to be one _***KNOWN***_  to work with Ubuntu somewhere.  Of all of the wireless adapters and all of the chipsets out there, one has to work out of the box.  I find it hard to believe that anyone that wants to use Ubuntu is automatically stuck with a wired internet connection because there are NO wireless adapters that work with it.

---

### Post by ahallubuntu on 2012-07-02
I still use 10.04 LTS on my Dell laptop.  But I am at this moment booted into the Live CD of 12.04 LTS.  I'm trying some random USB wireless cards I have laying around for you - tested connecting via WPA2/WPA security:

0. Intel Internal WiFilink 5100: works automatically.

1. Generic Realtek USB mini-dongle 802.11n 150MHZ (under $5 shipped via eBay): **_works automatically_**

(rtl8192cu module used by kernel; lsusb shows it as "RTL8188CUS")


2. Tenda W311U Ralink USB 802.11n 150MHZ (standard USB size): **_works automatically._**
(Ralink RT2870/RT3070; rt2800usb modeule used).


3. Airlink 101 USB 802.11g Card model AWLL3028 - Realtek RTL8187B chipset - **_works automatically_**.  (but quite old).  This adapter has worked automatically in every distro of Ubuntu since 10.04 LTS - a very handy adapter to have around when debugging various distros.

So there are three USB cards that work out of the box in 12.04.  (The Airlink card is old and not recommended unless someone basically gives it to you.)  Any card that uses one of those chipsets mentioned should work as well.

---

### Post by Mazate on 2012-07-02
> **ahallubuntu said:**
> I still use 10.04 LTS on my Dell laptop.  But I am at this moment booted into the Live CD of 12.04 LTS.  I'm trying some random USB wireless cards I have laying around for you - tested connecting via WPA2/WPA security:

0. Intel Internal WiFilink 5100: works automatically.

1. Generic Realtek USB mini-dongle 802.11n 150MHZ (under $5 shipped via eBay): **_works automatically_**

(rtl8192cu module used by kernel; lsusb shows it as "RTL8188CUS")


2. Tenda W311U Ralink USB 802.11n 150MHZ (standard USB size): **_works automatically._**
(Ralink RT2870/RT3070; rt2800usb modeule used).


3. Airlink 101 USB 802.11g Card model AWLL3028 - Realtek RTL8187B chipset - **_works automatically_**.  (but quite old).  This adapter has worked automatically in every distro of Ubuntu since 10.04 LTS - a very handy adapter to have around when debugging various distros.

So there are three USB cards that work out of the box in 12.04.  (The Airlink card is old and not recommended unless someone basically gives it to you.)  Any card that uses one of those chipsets mentioned should work as well.


Does this appear to be the same thing?

[http://www.amazon.com/Bl-lw05-5r-802-11n-Wireless-Adapter-Chipset/dp/B004LPY204/ref=sr_1_2?ie=UTF8&qid=1341236435&sr=8-2&keywords=rtl8188cus](http://www.amazon.com/Bl-lw05-5r-802-11n-Wireless-Adapter-Chipset/dp/B004LPY204/ref=sr_1_2?ie=UTF8&qid=1341236435&sr=8-2&keywords=rtl8188cus)

---

### Post by ahallubuntu on 2012-07-02
It does *appear* to be the same as the mini-dongle I have - yes - except mine does not have that little WPS button on the end.  (I usually turn WPS off on my routers.)  For $6, it's not a huge gamble.

---

### Post by Mazate on 2012-07-02
> **ahallubuntu said:**
> It does *appear* to be the same as the mini-dongle I have - yes - except mine does not have that little WPS button on the end.  (I usually turn WPS off on my routers.)  For $6, it's not a huge gamble.

I just ordered it.  thanks for the info

---

