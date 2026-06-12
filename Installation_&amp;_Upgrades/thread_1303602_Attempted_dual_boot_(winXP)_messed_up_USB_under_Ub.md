---
title: "Attempted dual boot (winXP) messed up USB under Ubuntu"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by asynchronous13 on 2009-10-28
I've been using Ubuntu 8.10 64bit on this machine for ~1 year now. Out of necessity, I had winXP running as a virtual machine using VirtualBox. Recently, I had to go to a dual-boot setup because VirtualBox doesn't fully support OpenGL yet.

Not only was the winXP install a miserable experience (had to slipstream extra drivers onto the install cd....ugh), but now I have to wait a full 2 minutes when I boot into Ubuntu before my USB keyboard will function. dmesg shows lots of usb related errors:

```
dmesg | grep usb
[    2.363231] usbcore: registered new interface driver usbfs
[    2.363247] usbcore: registered new interface driver hub
[    2.363282] usbcore: registered new device driver usb
[    3.466088] usb usb1: configuration #1 chosen from 1 choice
[    3.848013] usb 1-3: new full speed USB device using ohci_hcd and address 2
[    3.860078] usb usb2: configuration #1 chosen from 1 choice
[    4.284012] usb 2-3: new high speed USB device using ehci_hcd and address 2
[    4.417316] usb 2-3: configuration #1 chosen from 1 choice
[    4.736010] usb 2-10: new high speed USB device using ehci_hcd and address 3
[   19.848015] usb 2-10: device descriptor read/64, error -110
[   35.072516] usb 2-10: device descriptor read/64, error -110
[   35.288514] usb 2-10: new high speed USB device using ehci_hcd and address 4
[   50.400011] usb 2-10: device descriptor read/64, error -110
[   65.616013] usb 2-10: device descriptor read/64, error -110
[   65.832010] usb 2-10: new high speed USB device using ehci_hcd and address 5
[   76.240008] usb 2-10: device not accepting address 5, error -110
[   76.352013] usb 2-10: new high speed USB device using ehci_hcd and address 6
[   86.760008] usb 2-10: device not accepting address 6, error -110
[   86.856181] usb 2-3.1: new high speed USB device using ehci_hcd and address 7
[   86.965037] usb 2-3.1: configuration #1 chosen from 1 choice
[   87.476010] usb 1-10: new full speed USB device using ohci_hcd and address 3
[  102.652012] usb 1-10: device descriptor read/64, error -110
[  117.932010] usb 1-10: device descriptor read/64, error -110
[  118.212010] usb 1-10: new full speed USB device using ohci_hcd and address 4
[  133.388010] usb 1-10: device descriptor read/64, error -110
[  148.668010] usb 1-10: device descriptor read/64, error -110
[  148.948010] usb 1-10: new full speed USB device using ohci_hcd and address 5
[  159.356009] usb 1-10: device not accepting address 5, error -110
[  159.532010] usb 1-10: new full speed USB device using ohci_hcd and address 6
[  169.940008] usb 1-10: device not accepting address 6, error -110
[  170.012241] usb 2-3.1.1: new high speed USB device using ehci_hcd and address 8
[  170.179285] usb 2-3.1.1: configuration #1 chosen from 1 choice
[  170.268376] usb 2-3.1.3: new full speed USB device using ehci_hcd and address 9
[  170.377258] usb 2-3.1.3: configuration #1 chosen from 1 choice
[  170.656573] usb 2-3.1.3.1: new full speed USB device using ehci_hcd and address 10
[  170.749544] usb 2-3.1.3.1: configuration #1 chosen from 1 choice
[  170.820664] usb 2-3.1.3.3: new low speed USB device using ehci_hcd and address 11
[  170.917418] usb 2-3.1.3.3: configuration #1 chosen from 1 choice
[  170.918790] usbcore: registered new interface driver libusual
[  170.919066] usbcore: registered new interface driver hiddev
[  170.920185] input: Dell Dell USB Keyboard Hub as /devices/pci0000:00/0000:00:0b.1/usb2/2-3/2-3.1/2-3.1.3/2-3.1.3.1/2-3.1.3.1:1.0/input/input4
[  170.928898] usb-storage: device found at 8
[  170.928901] usb-storage: waiting for device to settle before scanning
[  170.976108] input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard Hub] on usb-0000:00:0b.1-3.1.3.1
[  170.978411] input: Dell Dell USB Keyboard Hub as /devices/pci0000:00/0000:00:0b.1/usb2/2-3/2-3.1/2-3.1.3/2-3.1.3.1/2-3.1.3.1:1.1/input/input5
[  171.004063] input,hidraw1: USB HID v1.10 Device [Dell Dell USB Keyboard Hub] on usb-0000:00:0b.1-3.1.3.1
[  171.008351] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:0b.1/usb2/2-3/2-3.1/2-3.1.3/2-3.1.3.3/2-3.1.3.3:1.0/input/input6
[  171.052062] input,hidraw2: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:0b.1-3.1.3.3
[  171.052091] usbcore: registered new interface driver usb-storage
[  171.053053] usbcore: registered new interface driver usbhid
[  171.053055] usbhid: v2.6:USB HID core driver
[  175.933738] usb-storage: device scan complete
[  267.820012] usb 1-10: new full speed USB device using ohci_hcd and address 7
[  282.996010] usb 1-10: device descriptor read/64, error -110
[  298.276009] usb 1-10: device descriptor read/64, error -110
[  298.556009] usb 1-10: new full speed USB device using ohci_hcd and address 8
[  313.732013] usb 1-10: device descriptor read/64, error -110
[  329.012014] usb 1-10: device descriptor read/64, error -110
[  329.292010] usb 1-10: new full speed USB device using ohci_hcd and address 9
[  339.700009] usb 1-10: device not accepting address 9, error -110
[  339.876010] usb 1-10: new full speed USB device using ohci_hcd and address 10
[  350.284010] usb 1-10: device not accepting address 10, error -110
```


All USB devices were working normally before the attempted dual-boot.
 * 6x usb ports on the motherboard
 * 2x usb ports on front of case
 * 1x rosewill card reader + usb port (plugged into usb on motherboard)
 * usb passthrough on monitor
 * dell usb keyboard/hub
 * microsoft usb mouse (plugged in to keyboard)

Now, they usually work -- but I might have to wait 2minutes after a device is plugged in, which makes debugging difficult when I can't type any commands....

Steps I took for dual-boot:
 * Resized Ubuntu partition (shrank /dev/sda1)
 * Created new NTFS partition (/dev/sda2)
 * Installed WinXP on the new partition (/dev/sda2)
 * Updated Grub

I am also having troubles with the WinXP install -- driver, IRQ, or USB related -- not entirely sure yet. But I can't figure out how installing XP on a different partition could have affected the USB on my Ubuntu install. 

At the BIOS screen, the keyboard is working immediately. So something happens after that part of the boot process. Also, usb works fine when booting from Ubuntu live CD.

Any ideas on what to check?

---

### Post by asynchronous13 on 2009-10-28
ok, scratch that part about working from the Ubuntu Live CD -- I re-tested that and I get the same delay and problems as I do when booting from the hard drive. Similar errors in dmesg as well.

---

