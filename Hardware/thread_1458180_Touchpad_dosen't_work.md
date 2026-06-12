---
title: "Touchpad dosen't work"
date: 2010-04-19
forum: Hardware
---

### Post by knua on 2010-04-19
Hy there 
I do have a problem with my touchpad i used an external wifi mouse and  now when i unplug it the Touch pad dosen 't work I had a look in the Settings but it says everything is working probably!:(

Is there anybody how has a solution for this problem dose I have to reinstall the driver for the mouse pad?

Help Please :guitar:

---

### Post by anglican on 2010-04-20
> **knua said:**
> Hy there 
I do have a problem with my touchpad i used an external wifi mouse and  now when i unplug it the Touch pad dosen 't work I had a look in the Settings but it says everything is working probably!:(

Is there anybody how has a solution for this problem dose I have to reinstall the driver for the mouse pad?

Help Please :guitar:

There's probably a function key for activating/deactivating your touchpad. Usually the key has a rectange with a pointing hand in it. On my netbook (AA1) it is Fn F7 but this is not universal - you don't say which laptop you have. If you can't work out which key to try (or if this doesn't fix it), let us know the model of laptop.

H

---

### Post by epitaph123 on 2010-04-30
Dual boot Vista SP2 & Ubuntu 10.04

If the touchpad is disabled in Vista, when i reboot into Ubuntu it does not recognize that windows has it disabled. So if i hit Fn+F7 to enable it, it shows disabling touchpad when it is already disabled and hitting Fn+F7 again shows re-enabling it but it still doesn't work until i reboot into vista and enable it there.

So if the touchpad is enabled in Vista and i reboot into Ubuntu the touchpad works fine, i am able to enable/disable perfectly. But if its disabled in Vista then Ubuntu can't enable or disable it at all.

This didn't happen in any other version of Ubuntu, only in 10.04

Does anyone know how to make Ubuntu 10.04 recognize that Vista has the touchpad disabled?

---

### Post by anglican on 2010-05-01
> **epitaph123 said:**
> Dual boot Vista SP2 & Ubuntu 10.04

If the touchpad is disabled in Vista, when i reboot into Ubuntu it does not recognize that windows has it disabled. So if i hit Fn+F7 to enable it, it shows disabling touchpad when it is already disabled and hitting Fn+F7 again shows re-enabling it but it still doesn't work until i reboot into vista and enable it there.

So if the touchpad is enabled in Vista and i reboot into Ubuntu the touchpad works fine, i am able to enable/disable perfectly. But if its disabled in Vista then Ubuntu can't enable or disable it at all.

This didn't happen in any other version of Ubuntu, only in 10.04

Does anyone know how to make Ubuntu 10.04 recognize that Vista has the touchpad disabled?

OK, the Vista dual boot bit changes things a bit. Take a look at:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727)

In other words try:

```
sudo modprobe psmouse proto=imps
```H

---

### Post by liutszho on 2010-05-05
> **anglican said:**
> OK, the Vista dual boot bit changes things a bit. Take a look at:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727)

In other words try:

```
sudo modprobe psmouse proto=imps
```H

I have tried that along with.

```
gconftool -s /desktop/gnome/peripherals/touchpad/touchpad_enabled -t boolean TRUE
```

Although my touchpad now works, scroll is disabled and I can't access touchpad configurations,

It says "Gysnaptics couldn't initialize. You have to set 'SHMConfig' 'true' in xorg.conf or XF86config to use Gsynpatics."

Then I tried this tutorial here: [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)

and did "gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi" and pasted those values in the file. But Touchpad config still won't open!

Help!

---

