---
title: "Two graphics cards output to 4 monitors fine on live usb, but not after installation"
date: 2017-11-13
forum: Hardware
---

### Post by SalsaDoom on 2017-11-13
So yes. Everything works as expected during the installation, I have two radeon graphics cards with two monitors each. After installation, the second graphics card shows the bootsplash, but when X loads it just stays there. Xrandr doesn't show the monitors on the second card. Whats different here after the install??

Here are my video cards, I'm using good old Mesa here, no fglrx stuff.

```
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Turks PRO [Radeon HD 6570/7570/8550] [1002:6759]
03:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Barts PRO [Radeon HD 6850] [1002:6739]
```

I tried adding in a file in /usr/share/X11/xorg.conf.d/ containing this

```
Section "Device"
        Identifier  "Card1"
        Driver      "radeon"
        BusID       "PCI:2:0:0"
EndSection

Section "Device"
        Identifier  "Card2"
        Driver      "radeon"
        BusID       "PCI:3:0:0"
EndSection
```

But it does nothing. I'm doing something wrong here (and so is the installer, btw, if it breaks it) but I don't know what to look. Googling this is hard because I just get results for people with optimus laptops.

Any ideas?

EDIT: [Here is a link]("https://pastebin.com/cjQGe38L") to my Xorg.0.log, I see a lot of things that look bad but now sure whats going on with them and why it all works on the live usb.

---

### Post by SalsaDoom on 2017-11-13
On closer inspection, this appears to have been caused by sddm not receiving correct permissions to access /dev/dri/card0 and card1. I didn't have time to find a proper solution unfortunately, and had to move on. ;(

---

