---
title: "ASUS Zenbook 14 UM425UA"
date: 2021-03-11
forum: Hardware
---

### Post by nadro on 2021-03-11
Hello,
I have ASUS Zenbook 14 UM425UA (Ryzen 5 5500U + 16GB RAM version), but builtin keyboard doesn't work in both GDM and Gnome session (both X11 and Wayland) after cold power on, but works properly after reboot. GRUB menu works properly all the time. During problematic boots I see "Can't read CTR while initializing i8042" kernel error. I tried tricks with ignore "Asus WMI hotkeys" and blacklist Intel Virtual Button driver (this model has AMD APU however), but nothing seems to work. I tried to run Ubuntu 20.04 (HWE enabled), Ubuntu 20.10n Ubuntu 21.04 and even Fedora 33, however all distributions have the same problem. I tried Kernel 5.11.3 and 5.12.0rc2 for Ubuntu kernel PPA without success too. Touchpad works properly all the time. Did you have similar problems with your laptops?
BTW. Hibernation doesn't work too even on kernel 5.11+ (this kernel has AMD SoC PMC driver), but this is a topic for another thread. Keyboard is more problematic from my point of view.
Best regards,
Patryk

---

### Post by CelticWarrior on 2021-03-11
Please update UEFI before anything else.

---

### Post by nadro on 2021-03-11
I have the latest UEFI version (there is no newer version of UEFI for this model yet than this preinstalled). In UEFI there is no options related for keyboard too (just lock FN key, but I tried to disable/enable it).

---

### Post by CelticWarrior on 2021-03-11
If there's a "legacy USB support" make sure it's enabled.

---

### Post by nadro on 2021-03-11
Thanks, but there is no option for that. USB section in UEFI has just one option for enable Mass Storage support, UEFI in this model is really basic (I just see 2 nice options: SVM and EZ Flash, so I will be able to update UEFI without Windows).

---

### Post by danb0b on 2021-08-24
I was having this problem when trying to unlock LUKS on the llvm-encrypted hard disk on my ASUS UM425U laptop at startup. Keyboard works during GRUB but doesn't work at the LUKS screen or after. A usb keyboard-mouse combo does the trick, or booting a lower kernel (5.8.18 works but other ASUS features do not)

reinstalling xserver-xorg-input-all did not work. Neither did preloading i2c_hid, hid_multitouch and hid_generic in /etc/initramfs-tools/modules/

I first noticed this when upgrading from kernel 5.8 to 5.11. When running initramfs it has a couple warnings about missing amdgpu drivers. Checking the lspci -k output from each kernel, amdgpu is present in 5.11 but not 5.08 "lspci -k" outputs

I subsequently blacklisted the amdgpu drivers by adding "blacklist amdgpu" to /etc/modprobe.d/blacklist.conf and subsequently running "sudo update-initramfs -u". Worked at restoring the keyboard, but killed hdmi output. Restoring the amdgpu driver and rerunning initramfs did not generate errors and got the keyboard working, but am I right back where I started?

---

### Post by danb0b on 2021-09-25
yes it put me right back to where I started.  Here is some more recent info.  I don't know how to recompile a kernel...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1943832](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1943832)

---

