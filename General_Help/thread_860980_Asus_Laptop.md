---
title: "Asus Laptop"
date: 2008-07-16
forum: General Help
---

### Post by 133794m3r on 2008-07-16
Ok has anyonen on here ever Ran Ubuntu on an Asus Laptop I'm thinking about getting a G70S and then taking of the ever so ugly vista and then putting Ubuntu on it.... so my question to all of you is. Have any of you ever had any exp. w/ running Ubuntu on an Asus. And secondly how'd it go? I know that Asus Obviously doesn't lock the Processors on this rig since they give you a handy little program to overclock it w/. So yeah if you've used it before just tell me how it went.

---

### Post by Tomatz on 2008-07-16
Post the specs ;)

---

### Post by Canis familiaris on 2008-07-16
Let us know your hardware:

```
lspci
```

---

### Post by 133794m3r on 2008-07-16
> **Tomatz said:**
> Post the specs ;)
haven't bought yet.... looking to buy want to make sure it's ubuntu friendly b4 i do
ok... well here's everthing I think... It's kinda new... and this is all i can find about the X1 it's from the Bestbuy page
```

Processor:Intel&#65533; Core(TM)2 Duo Mobile
Processor Speed:2.1GHz
Display Type: WXGA+ widescreen display @ 1440 x 900 resolution
Screen Size:17.1"
System Bus:800MHz
Cache Memory: 3MB on die Level 2
RAM:4GB
Hard Drive Type:Serial ATA (7200 rpm)
Hard Drive Size:400GB
Optical Drive: Double-layer DVD±RW/CD-RW
Graphics: Dual NVIDIA GeForce Go 8700M GT graphics cards
Video Memory: 1GB
Modem: 56 Kbps* ITU V.92 *Capable of receiving 56 Kbps downloads. However, 
current regulations limit download speed to 53 Kbps.
Networking: Built-in 10/100/1000Base-T Ethernet LAN
Wireless Networking: Built-in Intel® PRO/Wireless 4965 network connection (802.11a/b/g/n)
Additional Audio/Video Connectors: 1 HDMI
Audio: Azalia audio chip
Speakers:Built-in
PCMCIA Slots: 1
USB 2.0 Ports: 4
IEEE 1394 FireWire Ports:1
Pointing Device:Touchpad
```
but here's the specs on an A1 same series not sure if this helps any
```

-17" WUXGA 1920X1200:
Monitor ID AUO2088
Manufacturer B170UW02 V0
Manufacture Date Week 1 / 2007
Max. Visible Display Size 37 cm x 23 cm (17.2")
Picture Aspect Ratio 16:10
Gamma 2.20
DPMS Mode Support None

-nVidia 8700M GT SLI 1GB (512x2) GDDR3
-T9500 Penryn 2.6GHz 800 FSB 6MB
-4GB DDR2 667 (2GX2)
-400GB (200X2) 7200rpm SATA
-2.0 MP webcam
-Built-in Bluetooth
-Intel 4965 Wireless a/b/g/n
-Battery: 8 cells 5200 mAh, 77 Whrs
-1 x Microphone-in jack
-1 x Headphone-out jack (S/PDIF)
-1 x VGA port/Mini D-sub 15-pin for external monitor
-4 x USB 2.0 ports
-1 x IEEE 1394 port 1 x RJ11 Modem jack for phone line
-1 x RJ45 LAN Jack for LAN insert
-1 x HDMI , support HDCP 1 x E-SATA
```
they both look identical to me... so yeah no clue

---

### Post by Tomatz on 2008-07-16
> **133794m3r said:**
> ok... well here's everthing I think... 
-17" WUXGA 1920X1200:
Monitor ID AUO2088
Manufacturer B170UW02 V0
Manufacture Date Week 1 / 2007
Max. Visible Display Size 37 cm x 23 cm (17.2")
Picture Aspect Ratio 16:10
Gamma 2.20
DPMS Mode Support None

-nVidia 8700M GT SLI 1GB (512x2) GDDR3
-T9500 Penryn 2.6GHz 800 FSB 6MB
-4GB DDR2 667 (2GX2)
-400GB (200X2) 7200rpm SATA
-2.0 MP webcam
-Built-in Bluetooth
-Intel 4965 Wireless a/b/g/n
-Battery: 8 cells 5200 mAh, 77 Whrs
-1 x Microphone-in jack
-1 x Headphone-out jack (S/PDIF)
-1 x VGA port/Mini D-sub 15-pin for external monitor
-4 x USB 2.0 ports
-1 x IEEE 1394 port 1 x RJ11 Modem jack for phone line
-1 x RJ45 LAN Jack for LAN insert
-1 x HDMI , support HDCP 1 x E-SATA


i hope this helps you guys out....:P

The only difficulty will be setting up your wifi. You will have to use ndiswrapper to install the drivers as there are no native linux drivers :(

But other than that, i would say its fully compatable ;)

---

### Post by 133794m3r on 2008-07-16
> **Tomatz said:**
> The only difficulty will be setting up your wifi. You will have to use ndiswrapper to install the drivers as there are no native linux drivers :(

But other than that, i would say its fully compatable ;)
a what huh? like the propriety driver thing? wear i connect through ethernet line and dl?

---

### Post by Tomatz on 2008-07-16
> **133794m3r said:**
> a what huh? like the propriety driver thing? wear i connect through ethernet line and dl?

Sorry but i was wrong. As of hardy the card works out of the box ;)

[http://ubuntuforums.org/showthread.php?t=707573](http://ubuntuforums.org/showthread.php?t=707573)

---

### Post by 133794m3r on 2008-07-16
> **Tomatz said:**
> Sorry but i was wrong. As of hardy the card works out of the box ;)

[http://ubuntuforums.org/showthread.php?t=707573](http://ubuntuforums.org/showthread.php?t=707573)
wait.... so your saying evertything should work right out of the box? w/ 8.04.1? :D

---

### Post by Tomatz on 2008-07-16
> **133794m3r said:**
> wait.... so your saying evertything should work right out of the box? w/ 8.04.1? :D

It _should_ do ;)

This is linux rember...

:lolflag:

---

### Post by 133794m3r on 2008-07-16
> **Tomatz said:**
> It _should_ do ;)

This is linux rember...

:lolflag:
well yeah.... but I know that Nvidia makes Linux Drivers so I don't have to worry about that... and I was using ubuntu before and had to do a little work before i could run it smoothly... 
now all I have to do is convince parents that that's the best Laptop for the price 2099.99 USD

---

### Post by Tomatz on 2008-07-16
> **133794m3r said:**
> well yeah.... but I know that Nvidia makes Linux Drivers so I don't have to worry about that... and I was using ubuntu before and had to do a little work before i could run it smoothly... 
now all I have to do is convince parents that that's the best Laptop for the price 2099.99 USD

Good luck.... my dad would have laughed all the way down the street ;)

:lolflag:

---

### Post by 133794m3r on 2008-07-16
> **Tomatz said:**
> Good luck.... my dad would have laughed all the way down the street ;)

:lolflag:

yeah I hope it'll work out.... see this is going to be my college/work rig and since I'm going into Video Game Programming I think I'll be able to convince them that I need it b/c of my job field.... and plus I hoping that they'll let me have it since my last pc lasted me about 5.4 years... and I'll tell them this one should give me about 6 years... b/c of the specs.... so do you think if I go on about how I'll have to be running demos and stuff on my laptop for my classes that it'll help out any?
i mean just look at how beautiful this thing is! that's why i want it plus all of the crap that comes preloaded....
images below
-----------------------------------------
[IMG]http://images.bestbuy.com/BestBuy_US/images/products/8906/8906188_sa.jpg[/IMG][IMG]http://images.bestbuy.com/BestBuy_US/images/products/8906/8906188le.jpg[/IMG]
[IMG]http://images.bestbuy.com/BestBuy_US/images/products/8906/8906188_ta.jpg[/IMG][IMG]http://images.bestbuy.com/BestBuy_US/images/products/8906/8906188cv2a.jpg[/IMG]
[IMG]http://images.bestbuy.com/BestBuy_US/images/products/8906/8906188cv1a.jpg[/IMG][IMG]http://images.bestbuy.com/BestBuy_US/images/products/8906/8906188_sa.jpg[/IMG]

---

### Post by vjkeito on 2008-07-26
have you tried installing ubuntu on this yet?

I would really like to find out how you got on as I'm also interested in purchasing one of these!

cheers
keito

---

### Post by editrix on 2008-07-26
When it comes to hardware, I've always found the best way of learning if it will work with Linux is to search the brand and model number in Google Linux. There's also [http://www.linux-laptop.net/](http://www.linux-laptop.net/)

---

### Post by vjkeito on 2008-08-02
> **editrix said:**
> When it comes to hardware, I've always found the best way of learning if it will work with Linux is to search the brand and model number in Google Linux. There's also [http://www.linux-laptop.net/](http://www.linux-laptop.net/)

yeah, I've done that but its very new and hence there is not much available.

Tuxmobil is a good site for laptop compatibility too.

if the original poster has bought one of these then we should be able to get some info hopefully

---

### Post by triffle on 2008-08-02
Yeah boss... I am running Ubuntu 8.04 on my Asus f3ak-x2. Everything works out of the box. I am having a problem with skype, but i thinks its skype's problem.

Hardware:

AMD TL-58 1.9 GHZ
ATI RADEON HD 2600
2GB of 667 RAM
120GB SATA HD
Super Multi Drive (a little wonky, buts its wonky in windows as well)
Atheros b/g wireless
Realteck on board sound
Fantom Drive (500 GB external USB HD)
Webcam 

I am new to Ubuntu myself. But so far I am loving it on my ASUS. Compiz-fusion works well.

---

