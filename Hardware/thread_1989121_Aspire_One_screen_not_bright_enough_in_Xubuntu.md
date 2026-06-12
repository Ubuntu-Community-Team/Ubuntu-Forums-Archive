---
title: "Aspire One screen not bright enough in Xubuntu"
date: 2012-05-28
forum: Hardware
---

### Post by NekoMaster on 2012-05-28
I'm running Xubuntu 10.04 on my Acer Aspire One D257 and even at full brightness, its not as bright as it should be. It's really making my eyes hurt when my surroundings are bright like when the lights are on in the room, or when it's daytime. My screen can get brighter then the max Xubuntu can do, as I've had windows on here and it gets much more brighter then Xubuntu.

Is there anyway to fix this? Just so people know, I have tried going through the power settings and theres nothing in there that helps, and yes i've tried the Fn+Left or Right keys (the keys for changing brightness), they work but like I said, the max Xubuntu imposes is half the brightness that I can get in Windows.

---

### Post by smcgrath1111 on 2012-06-25
> **NekoMaster said:**
> I'm running Xubuntu 10.04 on my Acer Aspire One D257 and even at full brightness, its not as bright as it should be. It's really making my eyes hurt when my surroundings are bright like when the lights are on in the room, or when it's daytime. My screen can get brighter then the max Xubuntu can do, as I've had windows on here and it gets much more brighter then Xubuntu.

Is there anyway to fix this? Just so people know, I have tried going through the power settings and theres nothing in there that helps, and yes i've tried the Fn+Left or Right keys (the keys for changing brightness), they work but like I said, the max Xubuntu imposes is half the brightness that I can get in Windows.

I observe the same problem on my Aspire One D257, running Ubuntu 12.04.  Despite the Ubuntu brightness being all the way up, the screen backlight is obviously not at it's known potential.  Here are some values from /sys/class/backlight/acpi_video0 when the brightness is all the way up:


root@scott-aspire:/sys/class/backlight/acpi_video0# cat brightness 
9
root@scott-aspire:/sys/class/backlight/acpi_video0# cat max_brightness 
9
root@scott-aspire:/sys/class/backlight/acpi_video0# cat actual_brightness 
9
root@scott-aspire:/sys/class/backlight/acpi_video0# cat bl_power 
0
root@scott-aspire:/sys/class/backlight/acpi_video0#

---

### Post by Seb71 on 2012-06-25
I had this problem on a Acer Aspire One Happy 2 (identical with D257, except the case color) with Ubuntu 12.04. It appeared right after I installed *Jupiter*. Fortunately, in my case it solved itself after another reboot.

---

### Post by Régis B. on 2012-07-18
Same problem here. My laptop is an Asus 1005-P (netbook).

---

### Post by Régis B. on 2012-07-18
I managed to solve this problem by adding an option to grub: edit the /etc/default/grub file and add "acpi_backlight=vendor" to the GRUB_CMDLINE_LINUX_DEFAULT option. On my computer, the option now looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
```

Then I rebooted grub: ```
sudo update-grub
```

Then I rebooted. Brightness was back to normal.

---

### Post by JuanChanKane on 2012-08-21
Same problem here with an Asus eee on xubuntu 12.04. Maximum screen / desktop brightnees needed a boost. proposed solution worked like a charm.
Thanks!

---

