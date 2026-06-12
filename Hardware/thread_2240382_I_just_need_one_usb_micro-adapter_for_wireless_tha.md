---
title: "I just need one usb micro-adapter for wireless that works with 14.04"
date: 2014-08-19
forum: Hardware
---

### Post by sharon-talbot on 2014-08-19
I have a Lenovo T440s laptop.  It shipped with the ill-fated rtl8192ee driver that does not work.

I purchased a usb micro-adapter intended for the raspberry pi with "guaranteed" linux compatability.  It is also a realtek chipset.  The driver for it "works", but is completely unreliable.  I find better connectivity can be achieved by connecting my phone to the local wireless AP and then tethering to the phone with a usb cable, but this is obviously insane.  My coworker also has a device with a realtek chipset (slightly different), and it is also flakey.  Another coworker handed me a bag of usb micro-adapters that he had laying about, and I tested them all and they all had realtek chipsets according to lsusb.

I just need one micro-adapter that works with Ubuntu 14.04.  Please tell me which adapter you are using if it is available for purchase on Amazon, and you are currently using it with 14.04.  No realtek chipsets.  I'd prefer not to spend more than $50.

I should mention that I've seen the following, and they recommend cards, but I can't tell if they are up-to-date or if the chipset is the same as the device on Amazon.  It appears Realtek used to be acceptable in Ubuntu and no longer is, which rules out a lot of cards.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
[http://wireless.kernel.org/en/users/Devices/USB](http://wireless.kernel.org/en/users/Devices/USB)

That's why I'm looking for a link to purchase that someone here has definitely used with 14.04.

THANK YOU!

---

### Post by spjackson on 2014-08-21
I've got a few of these [http://www.amazon.com/Edimax-EW-7811Un-Adapter-Raspberry-Supports/dp/B003MTTJOY/]("http://www.amazon.com/Edimax-EW-7811Un-Adapter-Raspberry-Supports/dp/B003MTTJOY/ref=sr_1_1?ie=UTF8&qid=1408632591&sr=8-1&keywords=edimax") and I think they are wonderful. I've also bought a couple for other people. I don't use them in anger because currently all my internal adapters work with Linux. I've just tried one of my Edimax devices with Xubuntu 14.04 64bit on  my Lenovo Thinkpad Edge E520 and it worked just by plugging it in to the USB - no additional configuartion needed (apart from connecting to the right SSID). lsusb reports:
```

Bus 001 Device 003: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]

```
Despite being Realtek, it works fine. It connects to my Wifi at 65Mbps, whereas my internal Centrino Wireless-N 1000 connects at 121Mbps. They are cheap and I love them.

---

