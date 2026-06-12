---
title: "USB Install"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by vijay_wai on 2008-12-21
Hello,

I got my Ubuntu / Kubuntu Interpid discs today.
I want to do a USB install.
I have a 4 gb usb which I want to use for *all* Linux partitions (swap / boot / fs and all). I want the grub to stay only on USB.

Is this possible??
i.e. when I choose the USB install from Ubuntu disc, where does it install Grub?? On usb or on my laptop HDD??

My intention is use the laptop for Vista in normal boot ....
When my usb is plugged in it boots to Ubuntu...

Pleae advise

---

### Post by ibutho on 2008-12-21
When installing Ubuntu, there is an "Advanced" tab in the installer. Click on that tab and you will see an option that asks where you want to install the bootloader. If you do not do this, I thik grub will be installed to the MBR of your hard disk.

---

### Post by vijay_wai on 2008-12-21
If I follow the instructions ... (ie. advanced settings -> usb for grub) ... does it mean that my HDD MBR remains untouched and i still boot into vista as set in the factory settings??

Would you have a walkthrough for USB install??

---

### Post by ibutho on 2008-12-21
I don't have a walkthrough, but if you make sure that grub is installed on the USB device, it will leave the MBR of your Vista disk untouched.

---

### Post by vijay_wai on 2008-12-21
OK ... will give it a go ... thanks a tonne!

---

