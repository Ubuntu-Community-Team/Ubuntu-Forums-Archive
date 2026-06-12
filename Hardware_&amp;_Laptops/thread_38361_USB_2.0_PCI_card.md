---
title: "USB 2.0 PCI card?"
date: 2005-05-31
forum: Hardware &amp; Laptops
---

### Post by elatomo on 2005-05-31
First of all, excuse me for my poor english (i'm from Spain)

After buying a 4th gen ipod I'm planning on upgrading my old usb 1.1 ports with a usb 2.0 pci card and i'm looking for issues and recomendations about models etc. for full compatibility with muy ubuntu hoary.

Maybe it's a lame question, but, it's neccesary to load modules or something after installing it? My kernel version is 2.6.10-7

Thanks in advance!

---

### Post by Mez on 2005-05-31
Run the command

```
lsmod | grep ehci
```

if you get output similar to

```
root@apathy:/home/mez # lsmod | grep ehci
ehci_hcd               32772  0 
usbcore               119224  7 snd_usb_audio,snd_usb_lib,usbhid,usb_storage,ehci_hcd,ohci_hcd
```

Then no, you dont, as it already has ehci enabled

---

### Post by elatomo on 2005-05-31
Thank you a lot Mez, i've tested the command and it seems i'll have to load the ehci module manually.

---

### Post by Alpha_Maverick on 2006-02-27
what if I don't get that message?

how do I go about installing the ehci module?

---

### Post by GeeRoc on 2006-03-13
in terms of hardware i can say that i got a cheapo USB 2.0 / FW card with a VIA chipset for about 10 bucks and it works flawlessly with my Hedgehog  - although i can only say that for USB - haven't tried the FW connection yet.

---

