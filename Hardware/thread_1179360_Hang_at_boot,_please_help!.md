---
title: "Hang at boot, please help!"
date: 2009-06-05
forum: Hardware
---

### Post by AlexKpow on 2009-06-05
What happens is, after GRUB, I go to a screen that has the line "Starting up..." For about 20-25 seconds, and then finally going to the splash loading screen. As I switch between my Windows partition and Ubuntu partition often, this can be very annoying. Especially when Windows boots up faster than Ubuntu!

Here's my dmesg: 
[http://freetexthost.com/0yxvl6mcee](http://freetexthost.com/0yxvl6mcee)

Here's the lines that might be of interest:

I don't know what to make of this one, my mobo is this right here: [http://www.evga.com/products/moreInfo.asp?pn=123-YW-E175-A1&family=Motherboard%20Family]("http://www.evga.com/products/moreInfo.asp?pn=123-YW-E175-A1&family=Motherboard%20Family") (NVIDIA nForce 750i Chipset chipset)
```

[    1.358694] pci 0000:00:03.0: Disabling HT MSI mapping<6>pci 0000:00:07.0: Disabling HT MSI mapping<6>pci 0000:00:09.0: Disabling HT MSI mapping<4>pci 0000:00:0b.0: OHCI: BIOS handoff failed (BIOS bug?) 00000784
[   10.156015] pci 0000:00:0b.1: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[   10.156147] pci 0000:00:0e.0: Disabling HT MSI mapping<6>pci 0000:00:0f.0: Disabling HT MSI mapping<6>pci 0000:00:10.0: Disabling HT MSI mapping<6>pci 0000:00:10.1: Disabling HT MSI mapping<7>pci 0000:03:00.0: Boot video device

```
With this one, I don't even have a parallel port, so not sure why it would be hanging there. And how can I disable it checking for IPv6 all together?
```

[   21.839697] type=1505 audit(1244182489.179:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2157
[   24.578478] ppdev: user-space parallel port driver
[   39.248517] eth0: no IPv6 routers present

```
Thanks!

Update: [link to bootchart](http://i40.tinypic.com/o5ox3s.png)

---

### Post by AlexKpow on 2009-06-06
shameless bump
[IMG]http://media.photobucket.com/image/bump/oughtumn/Bump.jpg[/IMG]

---

### Post by blazemore on 2009-06-07
THis is the bootchart you sent over MSN. It seems to me that khubd is causing the delay.

---

### Post by blazemore on 2009-06-07
Try disabling your parallel port in the BIOS of your computer.
Also try disabling Legacy USB Support, if that's an option.
Since dmesg says "Bios Bug?", check for a BIOS update on the manufacturers website.

---

