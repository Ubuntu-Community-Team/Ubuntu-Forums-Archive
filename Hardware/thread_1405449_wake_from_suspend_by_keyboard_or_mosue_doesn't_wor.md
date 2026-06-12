---
title: "wake from suspend by keyboard or mosue doesn't work"
date: 2010-02-12
forum: Hardware
---

### Post by froff on 2010-02-12
hello
Maybe somebody will be so kind and help me (please :) with my problem.

I found information about enabling devices for wakeup and then tried to configure all usb devices to be enabled. My /proc/acpi/wakeup:

```

Device    S-state      Status   Sysfs node
P0P2      S4     disabled  pci:0000:00:01.0
P0P1      S4     disabled  pci:0000:00:1e.0
UAR1      S4     disabled  pnp:00:06
PS2K      S4     disabled  pnp:00:0c
EUSB      S4     disabled  pci:0000:00:1d.7
USBE      S4     disabled  pci:0000:00:1a.7
P0P4      S4     disabled  pci:0000:00:1c.0
P0P5      S4     disabled  
P0P6      S4     disabled  
P0P7      S4     disabled  
P0P8      S4     disabled  pci:0000:00:1c.4
P0P9      S4     disabled  pci:0000:00:1c.5
USB0      S4     enabled   pci:0000:00:1d.0
USB1      S4     enabled   pci:0000:00:1d.1
USB2      S4     enabled   pci:0000:00:1d.2
USB3      S4     disabled  
USB4      S4     disabled  pci:0000:00:1a.0
USB5      S4     enabled   pci:0000:00:1a.1

```It is impossible to enable USB3 nor 4 - operation gives no effect.

After enabling devices I still can't wake up machine from suspend by keyboard or mouse.
My motherbard is asus p5b-e plus.
My mouse is connected to usb port while keyboard to ps2 port.

My questions:
1) Why doesn't it work?
2) How to match my devices with usb port numbers listed in /proc/acpi/wakeup?
    Listing from lsusb gives me no idea.
3) Is ps2 keyboard represented in system by USBx or another device (what device?) ?
    Listing from lsusb suggests that answer is "no" and I don't know how to find proper
    device and enable it.

Best regards for all.

---

### Post by froff on 2010-02-13
ping; anybody?

---

### Post by froff on 2010-02-13
> **froff said:**
> ping; anybody?

ping!!!

---

### Post by efflandt on 2010-02-14
Linux apparently does not monitor keyboard/mouse during suspend.  Just press the power button and it should wake up if it is functioning properly.  I only have one old laptop that does not wake properly from suspend.

Even in Windows, it depends.  My desktop at home wakes with keyboard input or mouse movement, but at work it does not work with mouse movement.  Maybe the difference is whether it is USB or PS/2, or S1 vs. S3 power save mode in BIOS.

If USB is powered down during suspend, you would not get any input from USB human interface devices (hid).

---

### Post by froff on 2010-02-14
> **efflandt said:**
> Linux apparently does not monitor keyboard/mouse during suspend.  Just press the power button and it should wake up if it is functioning properly.  I only have one old laptop that does not wake properly from suspend.

Even in Windows, it depends.  My desktop at home wakes with keyboard input or mouse movement, but at work it does not work with mouse movement.  Maybe the difference is whether it is USB or PS/2, or S1 vs. S3 power save mode in BIOS.

If USB is powered down during suspend, you would not get any input from USB human interface devices (hid).

Hello
I'm sure it is possible to keep devices powered during suspend. My motherboard can wakeup when powered off with key combination, mouse movement, network etc - it works.
But I don't know what to do to make it work when suspended :(

BTW
How to match USB numbers with devices?
What is device/port name for PS/2 keyboard and mouse?

best regards

---

