---
title: "Cannot adjust brightness on Vostro 3400"
date: 2014-06-01
forum: Hardware
---

### Post by JustinJS on 2014-06-01
Okay, I have looked around quite a bit and cannot figure our how to get my brightness to lower or raise. When i hit the keys to raise and lower the brightness it shows up on the screen, but does nothing.

Note: I have a **Nvidia 310m** on my laptop and am running **Ubuntu 14.04**

What i have tried. 
**Installed the Nvidia drivers**
***set my grub parameters as follows***
*acpi_osi=linux* attempt 1
*acpi_osi=windows* attempt 2
**Tried to install nvidiabl-dkms**

Nothing I seem to do works.
I previously had Linux Mint installed and was able to fix it by adding acpi_osi=linux to grub, but it did nothing on Ubuntu

Any ideas would be great

---

### Post by Toz on 2014-06-01
Lets get a good look at the current state of your system. Can you run the following commands below and post back the results?

1. Your current kernel boot line:
```
cat /proc/cmdline
```

2. Info about your video card and driver:
```
lspci -k | grep -A2 VGA
```

3. Info about your backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

4. Your currently loaded kernel modules:
```
lsmod
```

Have you tried the **Option "RegistryDwords" "EnableBrightnessControl=1"** hack? See [http://ubuntuforums.org/showthread.php?t=2221452&p=13011416&viewfull=1#post13011416]("http://ubuntuforums.org/showthread.php?t=2221452&p=13011416&viewfull=1#post13011416")

---

### Post by JustinJS on 2014-06-01
> **Toz said:**
> 

Have you tried the **Option "RegistryDwords" "EnableBrightnessControl=1"** hack? See [http://ubuntuforums.org/showthread.php?t=2221452&p=13011416&viewfull=1#post13011416]("http://ubuntuforums.org/showthread.php?t=2221452&p=13011416&viewfull=1#post13011416")

You are the man! Thanks! 
Creating that config file worked like a charm.

---

