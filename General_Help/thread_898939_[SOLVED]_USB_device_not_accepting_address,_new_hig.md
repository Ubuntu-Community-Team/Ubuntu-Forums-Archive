---
title: "[SOLVED] USB: device not accepting address, new high speed USB device using ehci_hcd."
date: 2008-08-23
forum: General Help
---

### Post by houdodu on 2008-08-23
I'm getting the following in a loop inside dmesg. What can I do? I have no idea where to start.


```
[  109.248889] usb 4-4: device descriptor read/64, error -71
[  109.464033] usb 4-4: device descriptor read/64, error -71
[  109.679679] usb 4-4: new high speed USB device using ehci_hcd and address 21
[  110.086994] usb 4-4: device not accepting address 21, error -71
[  110.199317] usb 4-4: new high speed USB device using ehci_hcd and address 22
[  110.607133] usb 4-4: device not accepting address 22, error -71
[  110.881679] usb 4-4: new high speed USB device using ehci_hcd and address 23
[  110.993818] usb 4-4: device descriptor read/64, error -71
[  111.209143] usb 4-4: device descriptor read/64, error -71
[  111.424775] usb 4-4: new high speed USB device using ehci_hcd and address 24
[  111.538083] usb 4-4: device descriptor read/64, error -71
[  111.752229] usb 4-4: device descriptor read/64, error -71
[  111.967892] usb 4-4: new high speed USB device using ehci_hcd and address 25
[  112.375194] usb 4-4: device not accepting address 25, error -71

```

---

### Post by Rocket2DMn on 2008-08-23
Try unloading the ehci_hcd module
```
sudo rmmod ehci_hcd
```
This sometimes happens with USB2, though I'm not sure why or when exactly.

---

### Post by houdodu on 2008-08-23
just switched it over to uhci:

```
[  225.574244] hub 4-0:1.0: cannot disable port 4 (err = -19)
[  225.574252] hub 4-0:1.0: cannot disable port 4 (err = -19)
[  225.574261] usb 4-6: USB disconnect, address 7
[  225.579303] ehci_hcd 0000:00:1a.7: USB bus 4 deregistered
[  225.580585] ACPI: PCI interrupt for device 0000:00:1a.7 disabled
[  225.857765] usb 3-2: new full speed USB device using uhci_hcd and address 2
[  226.025110] usb 3-2: configuration #1 chosen from 1 choice
[  226.028734] scsi9 : SCSI emulation for USB Mass Storage devices
[  226.028959] usb-storage: device found at 2
[  226.028961] usb-storage: waiting for device to settle before scanning
[  226.265088] usb 2-2: new full speed USB device using uhci_hcd and address 2
[  226.385887] usb 2-2: device descriptor read/64, error -71
[  226.608517] usb 2-2: device descriptor read/64, error -71
[  226.824163] usb 2-2: new full speed USB device using uhci_hcd and address 3
[  226.943963] usb 2-2: device descriptor read/64, error -71
[  227.168584] usb 2-2: device descriptor read/64, error -71

```

---

### Post by Rocket2DMn on 2008-08-23
What device are you trying to plug in here?  Is it a flash drive, an external hard disk, a printer?  Have you tried unplugging the device's cables and then reconnecting them (I know, sounds silly)?

---

### Post by houdodu on 2008-08-23
between messages i determined it was the 4 port hub on my dell screen. i unplugged it and the messages stopped. i plugged in back in and so far so good.

for anyone searching, this started when xwin crashed and ubuntu forced me into a reboot for an unknown reason. i turned the computer off and it had no effect on the problem. if this happens again, i'll try shutting the power to the screen off as well.

actual cause is still unknown, i guess?

---

### Post by The Dragon Master on 2008-08-24
Thanks Rocketman. I had the same problem, your ehci_hcd line has solved my usb woes. 

Rockon dude!:guitar:

---

### Post by lddm00 on 2008-09-25
Thanks a lot Rocket2DMn. I was having problem with a mp3 player and with your line its fixed now, really awesome!!

---

### Post by tardeevo on 2008-11-23
the same were here w/ kubuntu 8.04 athlon dual core 64, but not anymore thanks to your fix Rocket2DMn!
great hint tnx a lot!

---

### Post by jhoderd on 2008-12-09
I don't mean to be a party-pooper, but doesn't removing ehci_hcd also prevent you from using USB at high-speed?

Note that I have the exact same problem you guys have, and I had it already since Hardy.  I either have to choose between loading ehci_hcd (in which case some devices won't work), or limiting myself to uhci_hcd (where everything works but is limited to sloooow USB 1.1 speeds...)

I see lots of reports about this problem in the forums and in Launchpad.  I think the Ubuntu kernel devs should dignify us with a better answer than "wait for 9.10"  (because it seems the 9.04 alpha also suffers from this same problem).

Cheers,
A not so happy Ubuntero

---

### Post by wikirandy on 2008-12-18
I'm having the same problem as everyone else - mine is that I can't seem to get a webcam going (either Logitech 9000 or QuickCam Communicate Deluxe). I gave the 9000 back, hoping it would solve the problem.

Does anyone have a recommendation for a webcam that will work out of the box?

This is SO frustrating! 

Gee, maybe I should give some money to the development effort - maybe that will get their attention. 

- Randy

---

### Post by Calfaile on 2009-02-09
I was having the same problem and unloading ehci_hcd worked for me.  I'm not so excited by the lack of high speed USB though, has this issue been fixed in the newest distribution?

---

### Post by P86 on 2009-03-01
> **Calfaile said:**
> I was having the same problem and unloading ehci_hcd worked for me.  I'm not so excited by the lack of high speed USB though, has this issue been fixed in the newest distribution?

Not according to:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746?comments=all]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746?comments=all")

I'm hoping for a fix, because either it gets fixed or I'm heading back to Windows (not that I want to).

---

### Post by Mike.lifeguard on 2009-04-10
> **Rocket2DMn said:**
> Try unloading the ehci_hcd module
```
sudo rmmod ehci_hcd
```
This sometimes happens with USB2, though I'm not sure why or when exactly.

OK I did that, but after installing gnomad2 I think that was the real problem for me. How do I re-load that module?

---

### Post by Rocket2DMn on 2009-04-10
> **Mike.lifeguard said:**
> OK I did that, but after installing gnomad2 I think that was the real problem for me. How do I re-load that module?

Should be
```
sudo modprobe ehci_hcd
```
If that doesn't work, please start a new thread for your problem, I'm closing this one since it keeps getting necroposted.  Thanks and good luck.

---

