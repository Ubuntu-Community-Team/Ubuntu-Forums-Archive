---
title: "No Bluetooth Adapter Present"
date: 2010-07-22
forum: Hardware
---

### Post by ansary on 2010-07-22
guys can u help me or give me some steps how to detect my bluetooth??

im using Bluetooth 2.1+EDR

---

### Post by SpyderBite on 2010-07-22
I've had the same problem myself since upgrading from Karmic. Never seemed important until I went to setup some new bluetooth noise reduction headphones. :/

---

### Post by IcarusR on 2010-07-23
Does dmesg have say anything about it ? In terminal type...

```
dmesg
```

I assume this is usb ?

Is it listed when you type in terminal..

```
lsusb
```

---

### Post by hansdown on 2010-07-23
Hi ansary.

You probably need to use an external bluetooth adaptor, like these, to access your bluetooth devices.

[http://www.google.com/products?client=ubuntu&channel=fs&oe=utf-8&q=usb+bluetooth+adaptors&um=1&ie=UTF-8&ei=1IFJTOSjMYaWsgPdkMVI&sa=X&oi=product_result_group&ct=title&resnum=3&ved=0CEIQrQQwAg](http://www.google.com/products?client=ubuntu&channel=fs&oe=utf-8&q=usb+bluetooth+adaptors&um=1&ie=UTF-8&ei=1IFJTOSjMYaWsgPdkMVI&sa=X&oi=product_result_group&ct=title&resnum=3&ved=0CEIQrQQwAg)

---

### Post by SpyderBite on 2010-07-23
> **hansdown said:**
> Hi ansary.

You probably need to use an external bluetooth adaptor, like these, to access your bluetooth devices.

That is what I do on another box that doesn't have a built in bluetooth adapter and it works fine. But, that's not really a solution for a system that has built in bluetooth. Especially, when it previously worked fine prior to the Lucid release.

**Edit:** Don't have time to mess with it further so I bought a $13 bluetooth adapter from Target today. That's the cheapest variety that works w/o buying additional software btw. Amazon and eBay have them for virtually free plus shipping.. but those require a Windows only software package for $30 to function.

Anyways.. Hope I'll get a chance to use my built in adapter after a later upgrade sometime. Cause this is just a band-aid on a flesh wound for what should be one of the most basic functions since it is an onboard hardware option.

---

### Post by fi2 on 2010-08-29
Same problem with my Toshiba A100-811 and Lucid. 

This old-fashioned machine has a switch on the side to turn wireless on/off. After reboot I couldn't see BT icon. I turned it off-on. BT icon appeared, and worked fine till next reboot.

I know this is not much, but it may give a hint to those who know.

---

### Post by numnuts on 2011-02-21
hello every body im new to ubuntu, when i installed a few days ago i thought it was great how it instantly found my bluetooth and wirelss network, straiaght away i paired up my phone with no problems, since then it does not see my adapter, its the usb type and even removing and replacing doesnt help, is there a simple cure for this yet?

---

