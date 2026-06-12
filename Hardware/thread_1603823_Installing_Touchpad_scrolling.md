---
title: "Installing Touchpad scrolling"
date: 2010-10-23
forum: Hardware
---

### Post by Astrophysiker on 2010-10-23
Hi,

I'm using Ubuntu 10.10 on a Lenovo G550 notebook. Actually, the touchpad is not detected by /proc/bus/input/devices. How can I get out, which touchpad is in and how to install the right modules?

Best regards,

Astro

---

### Post by Frantique on 2011-02-15
I am having the same problem. Trying to fix it, I will post the solution as soon as I will find it.

---

### Post by HankB on 2011-02-15
The Synaptics touchpad on my T500 works fine. I cannot find it in either 'lshw' output or 'lspci'.

I can see references to it in the Xorg log:

```
hbarta@cypress:/var/log$ grep touch Xorg.0.log
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) Synaptics touchpad driver version 1.2.2
(--) SynPS/2 Synaptics TouchPad: touchpad found
(--) SynPS/2 Synaptics TouchPad: touchpad found
hbarta@cypress:/var/log$ 
```

The 'hwinfo' command identifies the Synaptics touchpad:
```

  37: udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  input.device = '/dev/input/event6'
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  input.product = 'SynPS/2 Synaptics TouchPad'
  info.subsystem = 'input'
  info.product = 'SynPS/2 Synaptics TouchPad'
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input6/event6'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  info.category = 'input'
  info.capabilities = { 'input', 'input.touchpad' }
  linux.device_file = '/dev/input/event6'


```

I'm unsure what else to suggest.

---

### Post by Tedwin on 2011-02-15
I'm also running 10.10 on a lenovo g550 and have the same problem. The touchpad works fine except for scrolling, which is really a pain. I'm pretty sure it's an ALPS touchpad but I see no reference to it in /proc/bus/input/devices. Only PS/2 generic mouse is listed. I see no tab for touchpad in system-preferences-mouse.
Any help with enabling scrolling would be greatly appreciated. Thanks in advance.

---

### Post by Frantique on 2011-02-27
> **Tedwin said:**
> I'm also running 10.10 on a lenovo g550 and have the same problem. The touchpad works fine except for scrolling, which is really a pain. I'm pretty sure it's an ALPS touchpad but I see no reference to it in /proc/bus/input/devices. Only PS/2 generic mouse is listed. I see no tab for touchpad in system-preferences-mouse.
Any help with enabling scrolling would be greatly appreciated. Thanks in advance.

In 11.04 (Natty N.) the problem is still here, but in a funny way. The tp is detected normally, it appears everywhere as is, but it has no effect if I am setting the vscolling on or off. Not working at all. No error message, no nothing.

---

### Post by Slave2Metal on 2011-02-27
Might give this a try.
> **kongo09 said:**
> A goodie for those who tried two-finger scrolling in Ubuntu: it doesn't normall work!

However, if you're on the latest Ubuntu 10.10 (or above) you can get a  bleeding-edge driver from Launchpad. The details are discussed here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191)

Just download the latest .deb package (for me it was [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/+attachment/1771346/+files/synaptics-dkms_1.1.1_all.deb](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/+attachment/1771346/+files/synaptics-dkms_1.1.1_all.deb) )

It wouldn't install with the Software Center as expected, so use the command line:
```
sudo dpkg -i synaptics-dkms_1.1.1_all.deb
```It takes some time  and I had to reboot. The you can go to  System->Preferences->Mouse->Touchpad and enable the Two Finger  scrolling.

---

### Post by Frantique on 2011-02-27
> **Slave2Metal said:**
> Might give this a try.
Doesn't work.

---

### Post by Slave2Metal on 2011-02-27
So, you downloaded the deb, installed it and in system, preferences, mouse, there wasn't an option for two finger scrolling?
> **Frantique said:**
> Doesn't work.

---

### Post by Frantique on 2011-03-11
> **Slave2Metal said:**
> So, you downloaded the deb, installed it and in system, preferences, mouse, there wasn't an option for two finger scrolling?
It appears there, but does nothing.

---

### Post by szemy on 2011-10-19
Hi everyone!

I am facing the same problem...
Tried the patch, but still nothing.
The touchpad tab won't show up in settings.
This is interesting:
sudo tpconfig 
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).

I don't want fancy multi touch, but scrolling at least should work...

---

### Post by bigpenguin on 2011-10-22
I have Natty on an HP dv7 notebook.  The Touchpad tab is there right out of the gate and side scrolling works, but two-fingered scrolling doesn't.  Perhaps this is fixed in 11.10?  Does anyone know?

---

