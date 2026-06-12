---
title: "Maxtor onetouch3 not detected in 10.4"
date: 2010-09-18
forum: Hardware
---

### Post by ebbygonzo on 2010-09-18
I got a refurbed Maxtor onetouch3 external for cheap, but it can't be detected.  I get this this when I type:  ```
dmesg | tail
[10289.976122] usb 3-1: device descriptor read/64, error -71
[10290.204126] usb 3-1: device descriptor read/64, error -71
[10290.420126] usb 3-1: new full speed USB device using uhci_hcd and address 3
[10290.544156] usb 3-1: device descriptor read/64, error -71
[10290.772160] usb 3-1: device descriptor read/64, error -71
[10290.988119] usb 3-1: new full speed USB device using uhci_hcd and address 4
[10291.400114] usb 3-1: device not accepting address 4, error -71
[10291.512137] usb 3-1: new full speed USB device using uhci_hcd and address 5
[10291.928105] usb 3-1: device not accepting address 5, error -71
[10291.928157] hub 3-0:1.0: unable to enumerate USB device on port 1

``` The internet has not been helpful either.  I may not be able to use it.  Any ideas?

---

### Post by Manyette on 2010-09-18
Can't help much except to say that a Maxtor One-Touch 4 is my backup drive and works well with 10.4.

---

### Post by wilee-nilee on 2010-09-18
Did you look in gparted if it was showing?

Did you reboot with it plugged in to see if it shows?

Did you try to see if other OS could see it ie MS or Apple or any other Linux distros.

When you say refurbished could you tell us what that means, and where did you get the drive from?

---

### Post by ebbygonzo on 2010-09-18
Does not show in gparted.

Does not show on reboot.

No detect on windows (Even after installing maxtor software).

I thought it was new when I bought it (no description of it being repaired on the site I bought it from), but it has a sticker on it that says, "Maxtor Certified Repair" on it.

---

### Post by ebbygonzo on 2010-09-21
If the Drive makes a clicking noise while running, does this mean it might not be getting enough power to mount?  Could it mean something else as well, like it's dead?

---

### Post by wilee-nilee on 2010-09-21
> **ebbygonzo said:**
> If the Drive makes a clicking noise while running, does this mean it might not be getting enough power to mount?  Could it mean something else as well, like it's dead?

I have a maxtor one touch 4 mini. It came with a dual usb cord. When it doesn't get enough power it does make a clicking sort of sound. It does work with 1 rather short cord though, generally. Not sure if the single working is the length or quality, I'm not a electrical engineer. Other single cords I have create a low power click. When this happens it doesn't show on the computer.

---

### Post by ebbygonzo on 2010-09-21
> **wilee-nilee said:**
> I have a maxtor one touch 4 mini. It came with a dual usb cord. When it doesn't get enough power it does make a clicking sort of sound. It does work with 1 rather short cord though, generally. Not sure if the single working is the length or quality, I'm not a electrical engineer. Other single cords I have create a low power click. When this happens it doesn't show on the computer.

Mine has its own power supply.  I need to check if it is actually putting out what it says as well as if its using the right adapter to power it.  I think power is probably the issue. Thanks for the help.

---

