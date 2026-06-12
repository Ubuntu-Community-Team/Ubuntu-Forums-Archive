---
title: "Manually overriding a bluetooth device type"
date: 2011-03-04
forum: Hardware
---

### Post by Crazedpsyc on 2011-03-04
I have this new bluetooth keyboard, but every device I have tried to pair it with, with both linux and windows, it is recognised as a modem, and is therefore unusable. It is a Celluon keyboard, so there are no linux drivers or programs, and the only windows ones are xp-vista 32bit. I have 7-64bit, so those will not work. I also tried it in wine, and it did nothing. From the command line with "wine blah.exe" I got nothing at all either. No output. The keyboard works great with USB, without even installing anything or configuring it. But why in the world does everything think it is a MODEM!?!? 

I think there is probably a way to manually edit a /etc/bluetooth file or something (after all, it is linux!), but I need help finding that file (or whatever). I am using blueman, bluedevil, and the built in bluetooth indicator, but none seem to have a way to change the type. I did try blueman's virtual serial port connector, with no results. I've already googled and ducked around as much as I can, but there appears to be nothing on this. 

It is definitely not in /etc/bluetooth, but I am looking into /var/lib/bluetooth. Check it out on your system if you have bluetooth! It looks like there is a folder for each bluetooth adapter type thing connected to the computer (named with its mac address), plus one that consists of only 00 bytes. There is lots of useful information there, but I can't see any about connected devices right now :(

Thanks for any help offered!

---

### Post by Crazedpsyc on 2011-03-05
BUuump #1

---

### Post by Crazedpsyc on 2011-03-07
Bump #2

---

### Post by Crazedpsyc on 2011-03-08
3

---

### Post by Crazedpsyc on 2011-03-09
#4

---

### Post by Crazedpsyc on 2011-03-11
#5? Anybody?

---

### Post by Crazedpsyc on 2011-03-13
#6

---

### Post by Crazedpsyc on 2011-03-28
Might as well bump again.
I just had a thought... Could I just change the "ports" it uses?
The keyboard says to use port 5 for incoming and 6 for outgoing i think...

Any idea how to do that? I know BlueProximity can specify ports, but what about blueman or whatever?

---

### Post by Crazedpsyc on 2011-03-31
Bump again. Be sure to read that previous post.
Any ideas?

---

### Post by KegHead on 2011-03-31
Hi!

More info?

KegHead

---

### Post by Crazedpsyc on 2011-04-01
Anything specifically? The keyboard is the Celluon LaserKey CL850BT, I got it working on WinXP without any of the extra drivers that came on the CD, there are only CD drivers for winxp-vista...
My Bluetooth is internal in my laptop, here is some info that might be useful
```
(root@ubuntu-laptop) ~ > lshal | grep blue                                     9:15:04
udi = '/org/freedesktop/Hal/devices/usb_device_b05_1788_1C4BD60E9899_if0_bluetooth_hci_1c4bd60e9899'
  bluetooth_hci.address = 31112039405721  (0x1c4bd60e9899)  (uint64)
  bluetooth_hci.originating_device = '/org/freedesktop/Hal/devices/usb_device_b05_1788_1C4BD60E9899_if0'  (string)
  info.capabilities = {'bluetooth_hci'} (string list)
  info.category = 'bluetooth_hci'  (string)
  info.subsystem = 'bluetooth'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_b05_1788_1C4BD60E9899_if0_bluetooth_hci_1c4bd60e9899'  (string)
  linux.subsystem = 'bluetooth'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/bluetooth/hci0'  (string)
udi = '/org/freedesktop/Hal/devices/usb_device_b05_1788_1C4BD60E9899_if0_bluetooth_hci_1c4bd60e9899_rfkill_hci0_bluetooth'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_b05_1788_1C4BD60E9899_if0_bluetooth_hci_1c4bd60e9899'  (string)
  info.product = 'hci0 bluetooth Killswitch'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_b05_1788_1C4BD60E9899_if0_bluetooth_hci_1c4bd60e9899_rfkill_hci0_bluetooth'  (string)
  killswitch.type = 'bluetooth'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/bluetooth/hci0/rfkill0'  (string)

```

---

