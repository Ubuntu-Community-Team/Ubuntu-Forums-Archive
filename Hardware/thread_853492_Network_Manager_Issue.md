---
title: "Network Manager Issue"
date: 2008-07-08
forum: Hardware
---

### Post by lacrosse_man16 on 2008-07-08
I have an HP dv6748us and I am trying to get my wireless card to work.  I have installed the drivers and ndiswrapper acknowledges that the hardware is present.  No errors are present when I use the trail command in the terminal.  The only problem that I am aware of is that the Network Manager does not have the wireless tab. Here is a picture of what I am talking about:


[CENTER][IMG]http://i264.photobucket.com/albums/ii175/mastahchef117/Screenshot-NetworkSettings.png[/IMG][/CENTER][/QUOTE]

---

### Post by stats on 2008-07-09
check if there are any hardware drivers listed in system->administration->restricted hardware
if not, look into installing ndiswrapper. there are a lot of howtos on the forums for that

---

### Post by Qinjuehang on 2008-07-09
If I'm not mistaken, you use a Atheros wireless chipset. It should "just work"...so maybe check your ristricted manager. Also, [https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi](https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi)
Try issuing modprobe on the module

---

### Post by lacrosse_man16 on 2008-07-11
Im pretty sure that I have a broadcom chipset, but I will still try the Atheros chipset since there is a driver for it.  As for the ndiswrapper installment I already have, and everything works until the last step.

---

### Post by Daelyn on 2008-07-11
> **lacrosse_man16 said:**
> I have an HP dv6748us and I am trying to get my wireless card to work.  I have installed the drivers and ndiswrapper acknowledges that the hardware is present.  No errors are present when I use the trail command in the terminal.  The only problem that I am aware of is that the Network Manager does not have the wireless tab. Here is a picture of what I am talking about:


Post outputs of:

```
lspci
```
```
lsusb
```
```
ifconfig
```
```
iwconfig
```

That way we can identify what NIC you have and if it is at all identified as a NIC by the system.

---

### Post by lacrosse_man16 on 2008-07-13
Ok sorry it took me so long the power was out.  I had gotten it to work I just had the wireless n driver and apparently you need the wireless g driver for ndiswrapper to work.  Thank you guys for helping!

---

