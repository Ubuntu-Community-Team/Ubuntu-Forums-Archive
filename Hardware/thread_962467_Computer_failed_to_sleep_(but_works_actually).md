---
title: "Computer failed to sleep (but works actually)"
date: 2008-10-29
forum: Hardware
---

### Post by sircam on 2008-10-29
Hello,

Often, when my computer is back from sleep mode, a message "**Computer failed to sleep**" is displayed in the bottom right corner of the screen. However, everything seems to work fine, from sleep mode to wake up state.

Other people have reported similar issues, but I didn't find any actual solution, or even a clue on the possible origin (HAL, gnome bug, ...):

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/195095](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/195095)
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/199088](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/199088)

I could certainly disable the error notification, but out of curiosity and to avoid masking a possible real problem (when battery runs out unexpectedly for instance), I was wondering if the problem could be fixed.

More details below.

Would anybody have a pointer to provide me with? Logs to check or some monitoring to perform?

Thanks a bunch

sircam


**Acer Aspire 5680**.

_lshal_ shows nothing suspicious:

```
$ script -f -c "lshal -m" halout
```

Closing the lid:

```
19:33:30.746: computer_logicaldev_input_3 property button.state.value = true
19:33:30.750: computer_logicaldev_input_3 condition ButtonPressed = lid
19:33:33.350: net_00_16_d4_d0_d0_a0 removed
19:33:33.548: net_00_19_d2_3b_3e_70 removed
19:33:33.583: net_00_19_d2_3b_3e_70_0 removed
```

Reopened the lid the next day:

```
10:08:06.040: computer_power_supply_battery_BAT1 property battery.voltage.current = 16480 (0x4060)
10:08:06.054: computer_logicaldev_input_3 property button.state.value = false
10:08:06.063: usb_device_46d_c30e_noserial_if0_logicaldev_input removed
10:08:06.063: computer_logicaldev_input_3 condition ButtonPressed = lid
```

_syslog_ :

```
Oct 24 19:33:30 karkass gnome-power-manager: (sircam) Suspending computer. Reason: The lid has been closed on ac power.
```

So far so good, but on wake up:

```
Oct 25 10:08:06 karkass NetworkManager: <debug> [1224922086.046921] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c30e_noserial_if0_logicaldev_input'). 
Oct 25 10:08:06 karkass gnome-power-manager: (sircam) Resuming computer
Oct 25 10:08:06 karkass NetworkManager: <debug> [1224922086.051539] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c30e_noserial_if0'). 
Oct 25 10:08:06 karkass NetworkManager: <debug> [1224922086.055183] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c30e_noserial_if1_logicaldev_input'). 
Oct 25 10:08:06 karkass NetworkManager: <debug> [1224922086.062309] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c30e_noserial_if1'). 
Oct 25 10:08:06 karkass NetworkManager: <debug> [1224922086.062383] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c30e_noserial'). 
Oct 25 10:08:06 karkass gnome-power-manager: (sircam) suspend failed
```
Something a wee bit suspicious; don't know if it's relevant:

```
Oct 24 19:33:34 karkass NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - hal-ipw-killswitch-linux returned 255
```


```
$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
```

---

### Post by sircam on 2008-11-01
Looks like the upgrade from 8.04 to 8.10 fixed the issue...

---

