---
title: "Bluetooth in Aspire 5920G"
date: 2008-09-11
forum: Hardware
---

### Post by rvm4000 on 2008-09-11
Does anyone know how to use the bluetooth in this laptop?

I run kbluetooth, but it just says "No bluetooth adapter". I think the device is off, but I don't know how to turn it on. The bluetooth key doesn't work, dmesg says this when I press it:
```

[  989.687117] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[  989.687125] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.

```

And this is what dmesg says about bluetooth:
```

$ dmesg | grep -i bluetooth
[   36.697004] Bluetooth: Core ver 2.11
[   36.697421] Bluetooth: HCI device and connection manager initialized
[   36.697425] Bluetooth: HCI socket layer initialized
[   36.714855] Bluetooth: L2CAP ver 2.9
[   36.714860] Bluetooth: L2CAP socket layer initialized
[   36.847465] Bluetooth: RFCOMM socket layer initialized
[   36.847488] Bluetooth: RFCOMM TTY layer initialized
[   36.847491] Bluetooth: RFCOMM ver 1.8

```

**Edit:** Well, it seems this computer doesn't include a bluetooth device after all. I tried to use it in Windows but it says "No device" when I press the bluetooth key.

---

