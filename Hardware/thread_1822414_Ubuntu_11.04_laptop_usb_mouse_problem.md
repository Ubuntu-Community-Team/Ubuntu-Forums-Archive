---
title: "Ubuntu 11.04 laptop usb mouse problem"
date: 2011-08-10
forum: Hardware
---

### Post by sammer_wulf on 2011-08-10
Hy!

The situation is this : I have an older laptop (Fujtsu Siemens Amilo L7310W). The trackpad isn't working, so I need to use an USB mouse. I had XP on it (mouse working fine), then I deleted XP, and installed Ubuntu 11.04. Already in the installer, the mouse was like my laptop's cpu were used 100% (slow, laggy and all). But when I used the keyboard for the controlls, it worked very well, fast and all... I thought my laptop is too weak - so I installed Puppy Linux. Same problem. Mouse wont work normally, just very slow and laggy. If I used the keyboard, everything was working flawlessly...
So I reinstalled Ubuntu 11.04. The problem is there. I tried to change mouse settings (speed, etc.) but there was no noticeable change. Now I tried it with another USB mouse, and it's still not working well. (when I take a mouse off the USB, I have to restart  the system to get it to work again - maybe some USB problems?) 
What could I do?:confused:

---

### Post by matt_symes on 2011-08-10
Hi

Try another USB port first. If that does not fix it...

Plug the mouse in and type (from the terminal)

```
dmesg | tail -n30
```

```
lsusb
```

Post the results back here between code tags.

Kind regards

---

### Post by sammer_wulf on 2011-08-10
Tried with all usb ports, none was working. Tried connecting my Blackberry, it wouldn't recognize it. (USB problem?)

Here are the results:

```
wulf@SammerBook:~$dmesg | tail -n30
[   25.195201] cfg80211: Regulatory domain changed to country: AM
[   25.195204] cfg80211:  (start_freq - end_freq@bandwidth), (max_antenna_gain, max_eirp)
[   25.195208] cfg80211:     (2402000 KHz - 2482000KHz @ 40000 KHz), (N/A, 2000mBm)
[   25.195212] cfg80211:     (5170000 KHz - 5250000KHz @ 20000 KHz), (N/A, 1800 mBm)
[   25.195216] cfg80211:     (5250000 KHz - 5330000KHz @ 20000 KHz), (N/A, 1800mBm)
[   25.232725] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.553578] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
[   25.681610] VIA 82xx Audio 0000:00:11.5: power state changed by ACPI to D0
[   25.681619] VIA 82xx Audio 0000:00:11.5: power state changed by ACPI to D0
[   25.681639] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link [ALKC] -> GSI 22 (level, low)-> IRQ 22
[   25.681825] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   26.296003] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   26.296103] vesafb: scrolling: redraw
[   26.296103] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   26.297315] Console: switching to colour frame buffer device 80x30
[   26.297343] fb0: VESA VGA frame buffer device
[   26.358425] ppdev: user-space parallel port driver
[   26.724569] [drm] Initialized drm 1.1.0 20060810
[   27.228076] pci 0000:01:00.0: power state changed by ACPI to D0
[   27.228100] pci 0000:01:00.0: power state changed by ACPI to D0
[   27.228138] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   27.232443] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010)
[   27.232452] [drm] No driver support for vblank timestamp query
[   27.232458] [drm] Initialized via 2.11.1 20070202 for 0000:01:00.0 on minor 0
[   27.235319] agppart-via 0000:00:00.0: AGP 3.5 bridge
[   27.235349] agppart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
[   27.235358] agppart-via 0000:00:00.0: putting AGP V2 device into 0x mode
[   27.235452] pci 0000:01:00.0: putting AGP V2 device into 0x mode
[   34.037626] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
wulf@SammerBook:~$lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f3:0232 Elan Microelectronics Corp.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by matt_symes on 2011-08-11
Hi

There is no mention of the mouse at all from the dmesg command.

You ran the commands after plugging in the mouse ?

Have you tried a different mouse ?

What is the output (from a terminal) of

```
xinput --list
```

and 

```
gconftool-2 --get /desktop/gnome/peripherals/touchpad/touchpad_enabled
```

Kind regards

---

### Post by sammer_wulf on 2011-08-11
I had the mouse plugged in. I tried another usb mouse, that wasnt working. I tried both mouses on my normal PC, they were working fine.

The codes gave me something like this (I could just type in the text from the laptop's console on my PC)

```
wulf@SammerBook:~$ xinput --list
  Virtual core pointer                  id=2  [master pointer (3)]
Virtual core XTEST pointer          id=4  [slave pointer (2)]                     
OM                                  id=10  [slave pointer (2)]
PS/2 Generic Mouse                   id=12  [slave pointer (2)]
  Virtual core keyboard               id=3  [master keyboard (2)] 
Virtual core XTEST keyboard            id=5   [slave keyboard (3]
Power Button                          id=6   [slave keyboard (3)]
Video Bus                              id=7   [slave keyboard (3)]
Power Button                          id=8   [slave keyboard (3)]
Sleep Button                           id=9  [slave keyboard (3)]
AT Translated Set 2 keyboard             id=11  [slave keyboard (3)]

wulf@SammerBook:~$ gconftool-2 --get /desktop/gnome/peripherals/touchpad/touchpad_enabled
true
```

---

### Post by matt_symes on 2011-08-11
Hi

What is the output of 

```
xinput --list-props 2 4 10 12
```

Use copy and paste from the terminal to post the results back here. It is much easier and less error prone.

Kind regards

---

### Post by sammer_wulf on 2011-08-11
The problem is, that i have no internet connection atm on the laptop. And if i save it in a document, i cant copy it to my bbry, cause it wont recognize it.

```
Device 'Virtual core pointer'
  Device enabled (120):     1
  Coordinate Transformation Matrix (122):   1.000000, 0.000000, 
 0.000000, 0.000000, 1.000000, 0.00000, 0.000000, 0.000000, 
 1.000000
  Device 'Virtual core XTEST pointer':
  Device enabled (120):     1
  Coordinate Transformation Matrix (122):   1.000000, 0.000000, 
 0.000000, 0.000000, 1.000000, 0.00000, 0.000000, 0.000000, 
 1.000000
  XTEST Device(236):        1
Device 'OM'
  Device Enabled (120):     1
  Coordinate Transformation Matrix (122):   1.000000, 0.000000, 
 0.000000, 0.000000, 1.000000, 0.00000, 0.000000, 0.000000, 
 1.000000
  Device Accel Profile (241): 0
  Device Accel Constant Deceleration (242): 1.000000
  Device Accel Adaptive Deceleration (243): 1.000000
  Devicel Accel Velocity Scaling (244):     10.000000
  Evdev Axis Inversion (245): 0, 0
  Evdev Axes Swap (247):      0
  Axis Labels (248): "Rel X" (130), "Rel Y" (131)
  Button Labels (249): "Button Left" (123), "Button Middle" (124), 
 "Button Right" (125), "Button Wheel Up" (126), "Button Wheel 
 Down" (127), "Button Horiz Wheel Left" (128), "Button Horiz  Wheel 
 Right" (129)
  Evdev Middle Button Emulation (250):   0
  Evdev Middle Button Timeout (251):     50
  Evdev Wheel Emulation (252):     0
  Evdev Wheel Emulation Axes (253):0, 0, 4, 5
  Evdev Wheel Emulation Inertia (254):   10
  Evdev Wheel Emulation Timeout (255):   200
  Evdev Wheel Emulation Button (256):    4 
  Evdev Drag Lock Buttons (257):   0
Device 'PS/2 Generic Mouse'
  Device Enabled (120):      1
  Coordinate Transformation Matrix (122):   1.000000, 0.000000,  0.000000, 0.000000, 1.000000, 0.00000, 0.000000, 0.000000,  1.000000
  Device Accel Profile (241): 0
  Devicel Accel Constant Deceleration (242): 1.000000
  Device Accel Adaptive Deceleration (243):  1.000000
  Evdev Axis Inversion (245): 0, 0
  Evdev Axes Swap (247):      0
  Axis Labels (248): "Rel X" (130), "Rel Y"(131)
  Button Labels (249): "Button Left" (123), "Button Middle"  
(124), "Button Right" (125), "Button Wheel Up" (126), 
"Button Wheel Down" (127)
  Evdev Middle Button Emulation (250):   0
  Evdev Middle Button Timeout (251):     50
  Evdev Wheel Emulation (252):     0
  Evdev Wheel Emulation Axes (253):0, 0, 4, 5
  Evdev Wheel Emulation Inertia (254):   10
  Evdev Wheel Emulation Timeout (255):   200
  Evdev Wheel Emulation Button (256):    4
  Evdev Drag Lock Buttons (257):   0
```

---

### Post by sammer_wulf on 2011-08-11
I think there must be some problems with the USB-s. I tried all of them, and they are not recognizing my iPod, neither my phone, nor my pendrive.

---

### Post by matt_symes on 2011-08-11
Hi

> **sammer_wulf said:**
> I think there must be some problems with the USB-s. I tried all of them, and they are not recognizing my iPod, neither my phone, nor my pendrive.

You may well be right. 

I was very surprised that nothing was displayed in dmesg when you connected the USB mouse.

Try it with other USB devices and check the output of dmesg. You will be looking for something like this.

```
matthew@matthew-laptop:~$ dmesg | tail -n20
[151795.555724] hda-intel: spurious response 0x0:0x0, last cmd=0x15f0900
[151795.555728] hda-intel: spurious response 0x0:0x0, last cmd=0x15f0900
[151795.555733] hda-intel: spurious response 0x0:0x0, last cmd=0x15f0900
[151795.555738] hda-intel: spurious response 0x0:0x0, last cmd=0x1470740
[153937.040673] usb 1-1: new high speed USB device using ehci_hcd and address 8
[153937.195082] usb 1-1: configuration #1 chosen from 1 choice
[153937.196683] scsi7 : SCSI emulation for USB Mass Storage devices
[153937.197045] usb-storage: device found at 8
[153937.197052] usb-storage: waiting for device to settle before scanning
[153942.191206] usb-storage: device scan complete
[153942.192658] scsi 7:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  4.05 PQ: 0 ANSI: 2
[153942.195301] sd 7:0:0:0: Attached scsi generic sg2 type 0
[153942.201292] sd 7:0:0:0: [sdb] 8027789 512-byte logical blocks: (4.11 GB/3.82 GiB)
[153942.202022] sd 7:0:0:0: [sdb] Write Protect is off
[153942.202031] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[153942.202038] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[153942.207533] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[153942.207547]  sdb: sdb1
[153942.212967] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[153942.212981] sd 7:0:0:0: [sdb] Attached SCSI removable disk
matthew@matthew-laptop:~$ 

```

Kind regards.

---

### Post by sammer_wulf on 2011-08-11
I tried again this code:

```
dmesg | tail -n30
```

And these are some of the lines i got (i think these are the important lines)

```
usb 1-3: device not accepting address 5, error -110
usb 1-3: new high speed USB device using ehci_hcd and address 6
usb 1-3: device not accepting address 6, error -110
hub 1-0:1.0: unable to enumerate USB device on port 3
usb 2-2: new low speed USB device using uhci_hcd and address 2
input: OM as /devices/pci0000:00/0000:00:10.0/usb2/2-2/2-2:1.0/input/input7
generic-usb 0003:04F3:0232.0001: input, hidraw0: USB HID v1.11 Mouse [OM] on usb-0000:00:10.0-2/input0
usbcore: registered new interface driver usbhid
usbhid: USB HID core driver
```

I had an iPod and the mouse connected.

---

### Post by sammer_wulf on 2011-08-11
Now I dont know, what happened. I was just watching what I had connected with lsusb. And after the scan the laptop recognized my iPod. Apple Inc... And it's working, I can see the files on it, and all. But the mouse is still not working, neither does my blackberry, or usb stick.

---

### Post by sammer_wulf on 2011-08-11
Now I did some research about this error -110. I don't know if I'm right but in a lot of forums ehci_hcd and uhci_hcd were mentioned. I read i could try the following commands: 

```
rmmod ehci_hcd

rmmod uhci_hcd
```

Both showed me the same: 

```
ERROR: Module ehci_hcd does not exist in /proc/modules

ERROR: Module uhci_hcd does not exist in /proc/modules
```

I'm not really good in this topic (Linux) but what I read now is that these modules need to be there for the USB to work well. 

The other thing I found:
[Unable to enumerate usb device disabling ehci_hcd]("http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/")

I tried these things (Have I done something bad?), but they weren't working.

As I already mentioned, I'm not really into Linux. But as this thing gets slowly clearer (usb 1.1 instead of 2.0?) it just get's weirder to me.

---

