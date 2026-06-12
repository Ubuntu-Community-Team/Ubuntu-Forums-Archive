---
title: "touchscreen works only if mouse attached"
date: 2011-10-14
forum: Hardware
---

### Post by spipe on 2011-10-14
I'm trying to get an all-in-one touchscreen PC working as a kiosk (no mouse or keyboard), using the new Ubuntu 11.10, and am almost there.

The touch screen works perfectly if there had been a USB mouse or keyboard attached at boot time.

If I boot without mouse or keyboard, the touchscreen responds randomly - clicking in one place will make the pointer appear somewhere else.  Tap the same spot a few times and the pointer will appear in a different place every time.

More info: if you boot with a mouse and then unplug it later, the touchscreen continues to work.  If you boot without and plug one in later, it does not help. Restarting the lightdm service (am I right that this is the replacement for gdm?) has no effect either.

In other words, whatever the difference is, it apparently happens at boot time, and as far as I can tell it can only be fixed with a reboot.

Any idea where to start troubleshooting?  I did try comparing lsmod output when it's happy vs. unhappy, and it has the same modules.

----------------------

Edit:

It did occur to me that it might be a lower-level quirk, like maybe USB support didn't get turned on in BIOS unless there was a device attached at boot; but as it turns out, you can plug in a mouse later and that mouse WILL work, although the touchscreen won't.  I think that eliminates the BIOS as a suspect.

The hardware is a Shuttle x50v2 running a 1.8GHz Atom processor, AMI BIOS 1.03.

The touchscreen appears in lsusb this way:

```

Bus 005 Device 002: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
```

---

### Post by spipe on 2011-10-14
Still poking and prodding at this.

Here's a chunk of dmesg after a happy startup (touchscreen works, because a keyboard had been attached at boot)

```
[    2.042333] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    2.083627] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.2
/usb4/4-1/4-1:1.0/input/input5
[    2.084472] generic-usb 0003:413C:2105.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.2-1/input0
[    2.084619] usbcore: registered new interface driver usbhid
[    2.084627] usbhid: USB HID core driver
[    2.168155] usb 5-2: new full speed USB device number 2 using uhci_hcd
[    2.251804] wmi: Mapper loaded
[    2.287741] [drm] Initialized drm 1.1.0 20060810
[    2.289181] jmb38x_ms 0000:01:00.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.289199] jmb38x_ms 0000:01:00.3: setting latency timer to 64
[    2.331690] type=1400 audit(1318608355.721:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=518 comm="apparmor_parser"
[    2.333247] type=1400 audit(1318608355.725:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=518 comm="apparmor_parser"
[    2.335256] type=1400 audit(1318608355.725:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=518 comm="apparmor_parser"
[b][    2.339407] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input6
[    2.340104] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input7
[    2.340524] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input8
[    2.340762] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input9
[    2.341208] generic-usb 0003:0EEF:0001.0002: input,hiddev0,hidraw1: USB HID v2.10 Pointer [eGalax Inc. USB TouchController] on usb-0000:00:1d.3-2/input0[/b]
[    2.363307] cfg80211: Calling CRDA to update world regulatory domain

```

Compare to an unhappy startup (no keyboard was attached at boot, and touchscreen is hosed):

```
[    2.065432] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    2.178686] [drm] Initialized drm 1.1.0 20060810
[    2.265767] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.265781] i915 0000:00:02.0: setting latency timer to 64
[    2.283909] cfg80211: Calling CRDA to update world regulatory domain
[    2.309715] jmb38x_ms 0000:01:00.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.309731] jmb38x_ms 0000:01:00.3: setting latency timer to 64
[    2.317642] i915 0000:00:02.0: irq 42 for MSI/MSI-X
[    2.317658] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.317665] [drm] Driver supports precise vblank timestamp query.
[    2.351649] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.384476] rtl8192se 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.384494] rtl8192se 0000:02:00.0: setting latency timer to 64
[    2.397552] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[    2.397558]            Loading firmware rtlwifi/rtl8192sefw.bin
[    2.398083] wmi: Mapper loaded
[    2.479986] type=1400 audit(1318607754.907:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=513 comm="apparmor_parser"
[    2.481489] type=1400 audit(1318607754.911:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=513 comm="apparmor_parser"
[    2.482399] type=1400 audit(1318607754.911:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=513 comm="apparmor_parser"
[    2.701279] [drm] initialized overlay support
[    2.729996] fbcon: inteldrmfb (fb0) is primary device
[    2.730156] Console: switching to colour frame buffer device 170x48
[    2.730259] fb0: inteldrmfb frame buffer device
[    2.730265] drm: registered panic notifier
[b][    2.732939] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input5
[    2.733221] usbcore: registered new interface driver usbtouchscreen[/b]
[    2.745229] usbcore: registered new interface driver usbhid
[    2.745238] usbhid: USB HID core driver
[    2.750674] acpi device:0c: registered as cooling_device4

```

:confused:

---

### Post by spipe on 2011-10-18
Can't really say I understand, but the problem has gone away.

I did a debian stable installation on another partition and left debian's bootloader on the MBR.  Turns out the touchscreen doesn't work at all with the debian installation; but after I set the grub default to boot ubuntu 11.10 again, the touchscreen started to work all the time regardless of whether any USB devices are detected during boot.

It's a riddle wrapped in a mystery wrapped in an enigma, but if I have to install-and-ignore debian on all these kiosks, I'll do it. :-\"

---

### Post by spipe on 2011-11-02
Followup and bump.  I configured a second kiosk, had the same problem with the touchscreen as expected, and tried the same trick of installing Debian and using its bootloader to launch Ubuntu.  This time it didn't help.

So my workaround isn't going to be reliable.  I still need to find out what makes the boot process different when a USB keyboard or mouse is plugged in (which makes the touchscreen work properly), versus when it isn't.  Any help out there?

---

### Post by spipe on 2011-11-04
Finally solved by downgrading the kernel from 3.0 to 2.6 (that is, by wiping Ubuntu 11.10 and installing Debian Squeeze) and downloading a canned touchscreen driver from EETI, [found here]("http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm").  The manufacturer only has drivers for 2.4.x and 2.6.x currently.

---

### Post by bryanagee on 2012-03-20
Have you done any more with this? I have a kiosk application that I'm hoping to use the X50 for, and a test run gave me similar issues. I'm trying 12.04, and the cursor is just wild.

Interestingly enough, the live cd that I used for install worked perfectly.

---

### Post by spipe on 2012-03-20
Nope, I just stuck with Debian, and the kiosks are working fine.

> *Interestingly enough, the live cd that I used for install worked perfectly.*

That is strange, yes. I wonder if the live CD uses a different kernel.

---

### Post by satart on 2012-05-31
confirmed. 

I have the same problem with 12.04.

Any new hint?

---

