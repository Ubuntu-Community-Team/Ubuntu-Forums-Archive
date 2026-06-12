---
title: "Hp/Compaq Presario V3000z"
date: 2006-08-25
forum: Hardware &amp; Laptops
---

### Post by ephesius on 2006-08-25
Does anyone have this laptop? I am strongly considering purchasing and am wondering if anyone has had any problems with it.

---

### Post by skeezicks on 2006-08-25
I have the v6030us. It's the bigger version of the v3000. I've had some probs. When I used Xubuntu the nic card would bug out. 

  It's a very nice laptop but it suffers from a lack of drivers right now. I have xp64 running to and there are no drivers. There is no linux support for HP/Compaq and definitely no 64 support. 

  If you see a good deal then go and buy it. But if you're like me and want everything to work NOW then I would hold off. It's only going to frustrate you.

Here's a list of things working:
video card (1280x800 with 'nv' driver - not official 'nvidia'    driver)
lan card (works fine in ubuntu, in xubuntu needed nvidia driver)
usb
sata

not working:
sound <--- frustrating conexant high def audio.
card reader
bluetooth
acpi support

  Hope that helps. We need to get some support going for users with this type of laptop. I hope we can get a thread started.

---

### Post by Melcar on 2006-08-25
The only thing that WILL cause you problems is the wireless chip.  I have a V2000Z and I presume Compaq uses the same wireless chips for most of their notebooks (in my case it's a Broadcom one).  Everything else works fine.

---

### Post by capnrick on 2006-09-26
We have a v3000 series here.  Audio works fine for me, right out of the box.  I am not certain if 3-d drivers are working, I don't have anything on here to test with(but I am uing the nvidia proprietary drivers no problem).  The wireless can be made to work with ndiswrapper, but mine is still a little buggy right now.

ACPI support is a little off, so I I haven't gotten suspend or hibernate to function 100%.

The card reader in this one works great, even automounts in KDE 3.5.4.  

don't havebluetooth on this version, so that I don't know.

---

