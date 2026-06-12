---
title: "How to tether HTC Touch Pro 2"
date: 2010-04-06
forum: Hardware
---

### Post by rreed96e on 2010-04-06
I am brand new to Ubuntu, and need help tethering my HTC Touch Pro 2 to my Dell Inspiron Mini with Ubuntu 8.04.  Any suggestions are better than what I have now.

---

### Post by The Flying Penguin on 2010-04-07
It's incredibly simple. In fact, I think its easier in Ubuntu than Windows.

Download a program called WMWiFi Router and install it to your phone. You have several options as to how you want to share your internet connection with your computer. The 3G-WiFi option will turn your TP2 into a wireless router and any wifi enabled device can connect to it. If you want to save on battery, just plug the phone into your computer via the usb cable and select the 3G-USB option. Ubuntu will automatically recognize it as a modem and you are ready to surf! I share my TP2's internet connection with my laptop all the time using this method.

And did you know that there is a currently a working Android rom for the TP2? Sadly some things don't work as they should but once the kinks are worked out, it will be finding its way to my phone.

---

### Post by tendo on 2010-11-24
This thread really helped me out, thanks!  :popcorn:

---

### Post by Elludium_Q-36 on 2012-06-15
Don’t do it!!!

Not unless you want to practice doing hard resets, wiping all data, other than that on the microSD/TF card!

I installed WMWifiRouter, from the website of the same name, TWICE and both times, I had to do a hard reset after a few days.  I noticed I had to do a bunch of soft resets too.

Without installing WMWifiRouter, I haven’t had such trouble.

I read elsewhere, of someone having the same experience, AFTER I had my issue.

I’ve tried everything, of which I can think, or found; to sync and share the internet connection, in either direction, tethered or bluetooth.  Everything WiFi, with which I’ve toyed, has the traditional computer as client only.

Firestarter won’t serve the connection sharing, at least with the phone as client.  One bluetooth front-end, “Blueman applet 1.21“, “a GTK based Bluetooth manager” [http://blueman-project.org](http://blueman-project.org)  offers NAP (Network Access Point) service, but I’m not sure how to get it going; beyond settings.

Bluetooth serial port registers on both ends, but won’t connect.

I’ve connected the phone, via bluetooth and transfered filed in both directions.  I’ve started up PAN (Personal Area Network), which only does the “blinking box” thing.  

Connecting via USB, has Network Manager labeling it another ethernet (eth1) (HTC Generic RNDIS) connection, but no connectivity with the phone as client, at least not via firestarter.

Starting the bluetooth networking, shows the network device, bnep0 and pan0 is always present, with the bluetooth dongle inserted.

When home, I don’t get reliable signal indoors.  It would be nice to still be able to use the phone, say on the nightstand.  I might be able to put the phone outside, for signal and tether or use it as a wifirouter/bluetooth pan/dun but I’m not sure how to proceed.

To sync and upgrade from Windows Mobile 6.1 to WM 6.5, I tried the Windows software, provided with the phone, on a virtual XP machine, but the USB would not work.  I also tried various SynCE type packages, to no avail...

I’ve looked at xda-developers.com and they have made Android work on the HTC Touch Pro 2 / Pro2 / Pro II,  but it seems that subsystems, including bluetooth and the camera have been problematic. 

I’ve heard about Ubuntu on phones and gpe/opie on old PDAs but it seems that the official Ubuntu smartphone releases will only be given to OEMs: 
[http://mobile.pcadvisor.co.uk/news/mobile-phone/3361738/ubuntu-os-for-smartphones-may-come-next-year/](http://mobile.pcadvisor.co.uk/news/mobile-phone/3361738/ubuntu-os-for-smartphones-may-come-next-year/)

Anyway, I’d avoid WMWifiRouter...

---

