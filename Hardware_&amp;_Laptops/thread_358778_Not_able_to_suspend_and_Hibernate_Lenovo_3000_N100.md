---
title: "Not able to suspend and Hibernate Lenovo 3000 N100"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by rune.evjen on 2007-02-11
Hi !

I have tested suspend and hibernate on my Lenovo 3000 N100 and it does not work.

If anyone has any tips or tricks please help!

**Testing conditions:**

_- Ubuntu 6.10 with regular kernel 2.6.17-10-generic and suspend2 patched kernel_
->Both testet with nvidia (ver 1.0 -9746) and nv driver
->wireless using wpa_supplicant

_- Ubuntu 7.04 herd 4 with 2.6.20-6-generic_
->tested with nv driver
-> wireless using wpa_supplicant and networkmanager
**Hardware:** 
Lenovo 3000 N100 (type 0768 BJG) - Dual Core 2 1,83Ghz, NVIDIA Geforce Go 7300, ICH7 Chipset for sound and SATA controller, intel 3495 wireless.

During suspend i get different results.
**With setup Ubuntu 6.10, nvidia driver + compiz (my normal setup)**
_From GNOME: Suspend with wireless activated _
- The screen fades to black but the laptop does not go into suspend mode.
- It is not possible to wake up, switch to text mode (CTRL-F1) or reset X (CTRL-ALT-BKSP)
- I have to do a hardware reset to reboot the computer.

X.org log reports the following after I initiated suspend:
SetGrabKeysState - disabled
Synaptics DeviceOff called
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event1
(**) Option "Device" "/dev/input/event1"
(--) Synaptics Touchpad touchpad found

_From GNOME: Suspend with wireless deactivated:_
Same as above

_From GDM with wireless_
Same as above

_From GDM w/o wireless_
Computer goes into suspend, but after waking it up I get a black screen and no disk activity

**Other setups:**
Similar problems with suspend2 kernel, and Feisty
(except with suspend2 I get a log entry saying that suspend2 was not able to unload module "nvidia", forcing it puts the computer in the same state as without suspend2)

Please help!

Btw: Has anoyone got the fingerprint reader (Authentec) or Webcam working ?

Regards,

Rune Evjen
Norway

---

### Post by hey560 on 2007-02-18
I'm having problems with suspend/hibernate as well.

If I suspend screen goes black but I can still hear the fan and the hard drive working.  If I push keys and move mouse to get back nothing happens. I have to hard reset.

Anyone know how to fix this?

---

### Post by Turmoyl on 2007-02-18
If the laptop is still running hot when you Suspend it then it is not unusual for the general and HDD fans to keep working.  Since you are using (a trickle of) power to hold the CPU and memory in this frozen state it is necessary to keep the laptop in working order.  The laptop could not maintain a Suspend if it had to shut things down due to thermal problems.

If hitting a key or moving the mouse doesn't wake it from Suspend mode then hit the Function key combination that corresponds to the sleep functions (on my ThinkPad X60s this is Fn + F4) .

When you enter the Hibernation state it can take up to a minute to finish caching to your swap partition before the laptop powers down.  To wake it up requires hitting the power button as Hibernation is, in effect, a true power-down.  Once you hit the power button it will look like you're booting regularly but half-way through it will load you right back to your Hibernation point rather than a fresh desktop (think of it as a stateful snapshot kept on your hard disk).

On a side note keep in mind that if your wifi was in use when you entered a Suspend or Hibernate state it will be off once you "wake it up", and will need to be reinstated manually by you (i.e. sudo 'ifup wlan0 && dhclient wlan0', or trade ath0, etc. for wlan0 as appropriate for your setup).

---

### Post by hey560 on 2007-02-18
I think I spoke too soon.  Suspend and Hibernate work as expected now.  I guess I was just unlucky the first time I tried it.

As a reference for others i have the lenovo 3000 n100 0768-6KU.

The function key plus f4 doesn't seem to put it into suspend.  I guess thats a different key mapping issue.  I can still suspend by using the quit menu.

---

### Post by aethralis on 2007-09-27
I'm having the same problem with my laptop. To be precise I can hibernate and suspend it (by closing the lid) all right, but it never starts up after that, and I have to power off. Looked at the [wiki]("https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768"), but was unable to figure out what to do. Any help would be much appreciated.

---

### Post by aethralis on 2007-10-01
I'm testing the Gutsy version now... and the suspend/hibernate problem is still there.

---

### Post by hey560 on 2007-10-01
Try this page on the gentoo wiki:

[http://gentoo-wiki.com/HARDWARE_Lenovo_3000_N100#black_screen_with_backlight_switched_off_after_a_wake_up_from_a_suspend_to_ram](http://gentoo-wiki.com/HARDWARE_Lenovo_3000_N100#black_screen_with_backlight_switched_off_after_a_wake_up_from_a_suspend_to_ram)

---

### Post by w0ei on 2007-10-02
> **hey560 said:**
> Try this page on the gentoo wiki:

[http://gentoo-wiki.com/HARDWARE_Lenovo_3000_N100#black_screen_with_backlight_switched_off_after_a_wake_up_from_a_suspend_to_ram](http://gentoo-wiki.com/HARDWARE_Lenovo_3000_N100#black_screen_with_backlight_switched_off_after_a_wake_up_from_a_suspend_to_ram)
I also have this laptop (0768-BLG) and this fix makes my hibernate work (again). But still no suspend...

---

