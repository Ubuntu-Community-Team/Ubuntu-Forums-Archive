---
title: "Wireless mouse recognised in lsusb, but not working"
date: 2017-11-10
forum: Hardware
---

### Post by Oinos on 2017-11-10
I recently bought a new wireless mouse - not any one of its actions are recognised by the system. Lsusb output:

Bus 004 Device 003: ID 145f:020c Trust 

dmesg | grep -i trust output:

```
[    1.481780] Initialise system trusted keyring
[    1.578358] Key type trusted registered
[  210.551333] usb 4-1: Product: Trust Ergo Mouse
[  210.780897] input: Compx Trust Ergo Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/0003:145F:020C.0001/input/input11
[  210.837257] hid-generic 0003:145F:020C.0001: input,hidraw0: USB HID v1.10 Keyboard [Compx Trust Ergo Mouse] on usb-0000:00:1d.2-1/input0
[  210.841876] input: Compx Trust Ergo Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1/0003:145F:020C.0002/input/input12
[  210.897452] hid-generic 0003:145F:020C.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [Compx Trust Ergo Mouse] on usb-0000:00:1d.2-1/input1
[  278.257175] usb 5-1: Product: Trust Ergo Mouse
[  278.263972] input: Compx Trust Ergo Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/0003:145F:020C.0003/input/input13
[  278.316840] hid-generic 0003:145F:020C.0003: input,hidraw0: USB HID v1.10 Keyboard [Compx Trust Ergo Mouse] on usb-0000:00:1d.3-1/input0
[  278.326368] input: Compx Trust Ergo Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.1/0003:145F:020C.0004/input/input14
[  278.380519] hid-generic 0003:145F:020C.0004: input,hiddev0,hidraw1: USB HID v1.10 Mouse [Compx Trust Ergo Mouse] on usb-0000:00:1d.3-1/input1
[  293.936226] usb 4-2: Product: Trust Ergo Mouse
[  293.942759] input: Compx Trust Ergo Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/0003:145F:020C.0005/input/input15
[  293.997440] hid-generic 0003:145F:020C.0005: input,hidraw0: USB HID v1.10 Keyboard [Compx Trust Ergo Mouse] on usb-0000:00:1d.2-2/input0
[  294.008981] input: Compx Trust Ergo Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/0003:145F:020C.0006/input/input16
[  294.071219] hid-generic 0003:145F:020C.0006: input,hiddev0,hidraw1: USB HID v1.10 Mouse [Compx Trust Ergo Mouse] on usb-0000:00:1d.2-2/input1
[  926.592488] input: Compx Trust Ergo Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/0003:145F:020C.0007/input/input17
[  926.649762] hid-generic 0003:145F:020C.0007: input,hidraw0: USB HID v1.10 Keyboard [Compx Trust Ergo Mouse] on usb-0000:00:1d.2-2/input0
[  926.661687] input: Compx Trust Ergo Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/0003:145F:020C.0008/input/input18
[  926.716546] hid-generic 0003:145F:020C.0008: input,hiddev0,hidraw1: USB HID v1.10 Mouse [Compx Trust Ergo Mouse] on usb-0000:00:1d.2-2/input1
```

dmesg | grep -i error output:
```
[   40.040209] systemd-udevd[338]: Error calling EVIOCSKEYCODE: Invalid argument
[   41.654402] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
```

dmesg | grep -i warning output:
```
[    2.624934] WARNING: CPU: 1 PID: 6 at /build/linux-lts-xenial-9XOGix/linux-lts-xenial-4.4.0/drivers/gpu/drm/i915/intel_fbdev.c:406 intel_fb_initial_config+0x2cc/0x5e0 [i915]()
[    2.860022] WARNING: CPU: 0 PID: 159 at /build/linux-lts-xenial-9XOGix/linux-lts-xenial-4.4.0/drivers/gpu/drm/drm_atomic_helper.c:723 drm_atomic_helper_update_legacy_modeset_state+0x221/0x250 [drm_kms_helper]()
[  174.812453] systemd-hostnamed[3101]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 1325.221554] systemd-hostnamed[4003]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
```

xinput output:

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad            id=10    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint Stick               id=11    [slave  pointer  (2)]
&#9116;   &#8627; Compx Trust Ergo Mouse                      id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=12    [slave  keyboard (3)]
    &#8627; Compx Trust Ergo Mouse                      id=13    [slave  keyboard (3)]
```

xev doesn't recognise any of the mouse actions.

There's no package nss-myhostname. I tried some of the advices I found online, to no avail.

I'm on dell latitude d430, ubuntu 14.04

---

### Post by efflandt on 2017-11-10
Does the mouse work on any other computer or OS? Are its batteries good? I am not familiar with that brand of mouse. Linux usually has no problems using multiple mouse devices (mousepad & mouse) simultaneously or multiple keyboard devices.

Don't worry about nss-myhostname, that is not essential.

---

### Post by Oinos on 2017-11-11
> **efflandt said:**
> Does the mouse work on any other computer or OS? Are its batteries good? I am not familiar with that brand of mouse. Linux usually has no problems using multiple mouse devices (mousepad & mouse) simultaneously or multiple keyboard devices.

Don't worry about nss-myhostname, that is not essential.

I haven't been able to test it on other computers or OSes yet - will do so later today. Yes, its batteries are good, just unpackaged. I should also say it's a 9 button mouse.

---

### Post by Holger_Gehrke on 2017-11-11
The first dmesg dump shows the receiver reconnecting on USB (and getting assigned a new address and name) several times in under one minute. You might want to try putting it in a different USB-port or putting it in a port on the laptop itself if you've put it in a port on a hub.

Holger

---

### Post by Oinos on 2017-11-11
> **Holger_Gehrke said:**
> The first dmesg dump shows the receiver reconnecting on USB (and getting assigned a new address and name) several times in under one minute. You might want to try putting it in a different USB-port or putting it in a port on the laptop itself if you've put it in a port on a hub.

Holger

I think that was me, unplugging and replugging it multiple times. I tried all the usb ports and none works. I also just tried it on win XP, MSI laptop, and it doesn't work there either. I should say at this point that I have another wireless mouse that works on both. Probably a silly try, but it doesn't work on a usb hub either. The windows also recognises the mouse, although it does say it's plugged in at location 0, instead of some port.

I'm wondering, at this point what's the chance of this being an issue on my side vs. the mouse being a faulty model? On its bottom side it writes 'QC PASS 2017' with a tick on 4 out of 12 point scale - I'm wondering if 1 or 12 is the highest quality...

---

### Post by Oinos on 2017-11-12
Status update: RTFM. It turns out it's only windows 7/8/10/vista compatible. Unless there's some sneaky way to go around that sans installing VMs, I think I'll just return it.

---

