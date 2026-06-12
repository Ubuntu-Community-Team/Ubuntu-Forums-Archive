---
title: "Is my laptop compatible with ubuntu???"
date: 2020-07-17
forum: Hardware
---

### Post by erratic1stuff on 2020-07-17
My laptop is asus fx505dd
Is my laptop compatible with ubuntu???
If compatible please give me a drivers for my laptop

---

### Post by poorguy on 2020-07-17
A sure fire way to find out if your laptop is compatible with Ubuntu or any other Linux distro is to create a bootable DVD or USB media and give it a test run in Live mode without installing or touching your existing OS which is presently installed.

---

### Post by erratic1stuff on 2020-07-18
Im going to reinstall my laptop with ubuntu :)

---

### Post by guiverc on 2020-07-18
Try Ubuntu on your actual hardware and see for yourself
[https://ubuntu.com/tutorials/try-ubuntu-before-you-install](https://ubuntu.com/tutorials/try-ubuntu-before-you-install)
(which applies to all flavors, as @poorguy suggested)

It won't be exactly what you'll get (there are limitations to 'live' environments), but it's a huge clue, especially with regards hardware support (a huge reason it exists)

[https://ubuntu.com/tutorials/tutorial-install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/tutorial-install-ubuntu-desktop#1-overview)

[https://ubuntu.com/tutorials/tutorial-burn-a-dvd-on-macos#1-overview](https://ubuntu.com/tutorials/tutorial-burn-a-dvd-on-macos#1-overview)
[https://ubuntu.com/tutorials/tutorial-burn-a-dvd-on-windows#1-overview](https://ubuntu.com/tutorials/tutorial-burn-a-dvd-on-windows#1-overview)
[https://discourse.ubuntu.com/t/how-to-burn-a-dvd-on-ubuntu/14022](https://discourse.ubuntu.com/t/how-to-burn-a-dvd-on-ubuntu/14022)

[https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview)
[https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview)
[https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview)

To download Ubuntu
[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

For Ubuntu flavors, see
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

Validate the ISO using
[https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)

To validate the write to your install media, you can see
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
(this isn't required for Ubuntu 20.04 LTS (& flavors) or later, as it's now automatic)

---

### Post by kurt18947 on 2020-07-19
> **erratic1stuff said:**
> Im going to reinstall my laptop with ubuntu :)

Don't get too hasty. I'd first create a Windows restore USB or Windows iso.  Then create a live *buntu USB and make sure the important parts work, pointing devices, WiFi (big one, most likely problem) maybe see if any printers are recognized without adding drivers, things like that. I've had pretty good luck dual booting, the only problem I had was a Windows update overwriting GRUB. I was able to fix that with boot-repair. If you try dual booting, it's an excellent idea to resize your Windows partition using Windows tools then install *buntu in the newly freed up space.

---

### Post by oldfred on 2020-07-19
A few systems only update UEFI or SSD firmware from within Windows.
And you first need to update the firmware, anyway, but typically newer systems will have updates for several years.

You will need to add proprietary nVidia driver during install and probably have to boot with "nomodeset" boot parameter. If you do not install nVidia driver, you still need nomodeset to boot the install.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Should be similar:
Asus ROG Zephyrus GA502 Ryzen 7 3750H + Nvidia GTX 1660 Ti Set up Guide
[https://ubuntuforums.org/showthread.php?t=2440670](https://ubuntuforums.org/showthread.php?t=2440670)

---

