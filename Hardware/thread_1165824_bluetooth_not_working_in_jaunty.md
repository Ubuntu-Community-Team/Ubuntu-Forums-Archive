---
title: "bluetooth not working in jaunty"
date: 2009-05-21
forum: Hardware
---

### Post by blakecraw on 2009-05-21
EDIT: Solution in post 6

Bluetooth is not working at all after I upgraded to 9.04 64-bit

It was working before the upgrade, but now, I get the following:

```
$ lsusb | grep Bluetooth
Bus 004 Device 002: ID 044e:300c Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)

$ ps aux | grep bluetooth
root      3350  0.0  0.0  31308  1904 ?        Ss   00:27   0:00 /usr/sbin/bluetoothd

```
but...
```
$ hcitool scan
Device is not available: No such device

$ hciconfig -a
<returns nothing>
```
There is a switch for the bluetooth/wireless on my computer, and it is on (the wireless is working), so I haven't been able to find anything else to try with hcitool/hciconfig failing. Any ideas?

---

### Post by pauna on 2009-05-21
> **blakecraw said:**
> Bluetooth is not working at all after I upgraded to 9.04 64-bit


Please check your BIOS that Bluetooth hasn't accidentally been disabled there. I know it should not happen, but I've had some really mysterious BIOS incidents with laptops.

BTW, I have bluetooth fully working in 32bit Jaunty so there should not be anything fundamentally wrong with BT support in Jaunty.

---

### Post by blakecraw on 2009-05-21
There's nothing in the (Phoenix) BIOS about bluetooth. I never changed any BIOS settings, but I did a reset to the factory settings. Still no bluetooth.

---

### Post by blakecraw on 2009-05-23
I still haven't made any progress, anybody else have a solution?

---

### Post by blakecraw on 2009-05-24
Update:

I booted the 8.10 (amd64) live cd, and bluetooth works fine there.

I've tried booting the 9.04 live cd, and although the md5sum is right, and I burned the disc slowly, it will not boot (goes to grub after waiting a little while, presumably looking at the cd).

EDIT: I made a 9.04 live dvd with the same image on it, and it booted; bluetooth worked fine.

I've also tried different versions of the bluetooth packages (including the one that was working with the live dvd), and reinstalling them, nothing.

This is starting to get very frustrating, any help would be much appreciated.

---

### Post by blakecraw on 2009-05-25
Ok, I figured it out: I had to `modprobe btusb` and now it's back to the way it should be.

---

