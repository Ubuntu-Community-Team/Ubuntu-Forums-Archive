---
title: "USB problem: ThrustMaster HOTAS X &quot;device not accepting address&quot;"
date: 2013-12-03
forum: Hardware
---

### Post by Keith_Beef on 2013-12-03
I [posted about this very briefly]("http://ubuntuforums.org/showthread.php?t=1256191") way back in 2009 and then put the device to one side for a few years while I was busy with other things in my life.

Now I'm getting back into FlightGear, I'd really like to get this controller working. I've seen from other posts on FlightGear that some people have got it to work, but I have a specific problem with getting the device recognized in Ubuntu 12.04LTS.

My other controllers (Saitek and CH Products yokes, Saitek AV8R-01 stick, UltimARC stick etc.) work straight out of the box, but not this HOTAS X.

Before plugging in the HOTAS X, the usb tree looks like this:

```
lsusb -t
4-1.1:1.2: No such file or directory
4-1.1:1.3: No such file or directory
/:  Bus 11.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 10.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 09.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/3p, 12M
        |__ Port 1: Dev 3, If 0, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
        |__ Port 1: Dev 3, If 1, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
        |__ Port 1: Dev 3, If 2, Class=vend., Driver=, 12M
        |__ Port 1: Dev 3, If 3, Class=app., Driver=, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/4p, 480M
    |__ Port 4: Dev 3, If 0, Class=stor., Driver=usb-storage, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
    |__ Port 4: Dev 3, If 0, Class=hub, Driver=hub/4p, 480M
        |__ Port 1: Dev 4, If 0, Class=hub, Driver=hub/4p, 480M
            |__ Port 2: Dev 5, If 0, Class=HID, Driver=usbhid, 1.5M
            |__ Port 2: Dev 5, If 1, Class=HID, Driver=usbhid, 1.5M
            |__ Port 3: Dev 6, If 0, Class=HID, Driver=usbhid, 1.5M

```
After plugging in the HOTAS X (to a port integrated on the mainboard), the usb tree looks like this:

```
lsusb -t
4-1.1:1.2: No such file or directory
4-1.1:1.3: No such file or directory
/:  Bus 11.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 10.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 09.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/3p, 12M
        |__ Port 1: Dev 3, If 0, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
        |__ Port 1: Dev 3, If 1, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
        |__ Port 1: Dev 3, If 2, Class=vend., Driver=, 12M
        |__ Port 1: Dev 3, If 3, Class=app., Driver=, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/4p, 480M
    |__ Port 4: Dev 3, If 0, Class=stor., Driver=usb-storage, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
    |__ Port 4: Dev 3, If 0, Class=hub, Driver=hub/4p, 480M
        |__ Port 1: Dev 4, If 0, Class=hub, Driver=hub/4p, 480M
            |__ Port 2: Dev 5, If 0, Class=HID, Driver=usbhid, 1.5M
            |__ Port 2: Dev 5, If 1, Class=HID, Driver=usbhid, 1.5M
            |__ Port 3: Dev 6, If 0, Class=HID, Driver=usbhid, 1.5M
```

There is no change… 

The end of dmesg shows that there was a problem with the device.
```
[45360.980013] usb 9-1: new full-speed USB device number 2 using uhci_hcd
[45361.160014] usb 9-1: device descriptor read/64, error -71
[45361.384015] usb 9-1: device descriptor read/64, error -71
[45361.656012] usb 9-1: new full-speed USB device number 3 using uhci_hcd
[45361.832024] usb 9-1: device descriptor read/64, error -71
[45362.112013] usb 9-1: device descriptor read/64, error -71
[45362.384013] usb 9-1: new full-speed USB device number 4 using uhci_hcd
[45362.792010] usb 9-1: device not accepting address 4, error -71
[45362.960012] usb 9-1: new full-speed USB device number 5 using uhci_hcd
[45363.368015] usb 9-1: device not accepting address 5, error -71
[45363.368029] hub 9-0:1.0: unable to enumerate USB device on port 1
```

The HOTAS X has a switch with two positions: PC or PS3; the switch is in the PC position.

There are also buttons labelled SE, ST, PRESET and MAPPING.

So I'll use "watch tail /var/log/syslog" while I press these buttons to see if there is any change.

Pressing SE: no effect
Pressing ST: no effect
Pressing SE and ST together: no effect
Pressing PRESET: no effect
Pressing MAPPING: no effect
Pressing PRESET and MAPPING together: makes the system try to reconnect the device.

```
Dec  3 10:12:52 saturn kernel: [46072.648011] usb 9-1: new full-speed USB device number 6 using uhci_hcd
Dec  3 10:12:52 saturn kernel: [46072.768008] usb 9-1: device descriptor read/64, error -71
Dec  3 10:12:52 saturn kernel: [46072.992019] usb 9-1: device descriptor read/64, error -71
Dec  3 10:12:53 saturn kernel: [46073.264009] usb 9-1: new full-speed USB device number 7 using uhci_hcd
Dec  3 10:12:53 saturn kernel: [46073.440013] usb 9-1: device descriptor read/64, error -71
Dec  3 10:12:53 saturn kernel: [46073.664016] usb 9-1: device descriptor read/64, error -71
Dec  3 10:12:53 saturn kernel: [46073.880012] usb 9-1: new full-speed USB device number 8 using uhci_hcd
Dec  3 10:12:54 saturn kernel: [46074.288011] usb 9-1: device not accepting address 8, error -71
Dec  3 10:12:54 saturn kernel: [46074.456012] usb 9-1: new full-speed USB device number 9 using uhci_hcd
Dec  3 10:12:54 saturn kernel: [46074.864012] usb 9-1: device not accepting address 9, error -71
Dec  3 10:12:54 saturn kernel: [46074.864022] hub 9-0:1.0: unable to enumerate USB device on port 1
Dec  3 10:12:56 saturn kernel: [46076.624010] usb 9-1: new full-speed USB device number 10 using uhci_hcd
Dec  3 10:12:56 saturn kernel: [46076.744009] usb 9-1: device descriptor read/64, error -71
Dec  3 10:12:56 saturn kernel: [46077.024014] usb 9-1: device descriptor read/64, error -71
Dec  3 10:12:57 saturn kernel: [46077.296009] usb 9-1: new full-speed USB device number 11 using uhci_hcd
Dec  3 10:12:57 saturn kernel: [46077.472010] usb 9-1: device descriptor read/64, error -71
Dec  3 10:12:57 saturn kernel: [46077.752009] usb 9-1: device descriptor read/64, error -71
Dec  3 10:12:57 saturn kernel: [46078.024006] usb 9-1: new full-speed USB device number 12 using uhci_hcd
Dec  3 10:12:58 saturn kernel: [46078.432036] usb 9-1: device not accepting address 12, error -71
Dec  3 10:12:58 saturn kernel: [46078.600009] usb 9-1: new full-speed USB device number 13 using uhci_hcd
Dec  3 10:12:58 saturn kernel: [46079.008010] usb 9-1: device not accepting address 13, error -71
Dec  3 10:12:58 saturn kernel: [46079.008021] hub 9-0:1.0: unable to enumerate USB device on port 1
Dec  3 10:13:00 saturn kernel: [46080.992043] usb 9-1: new full-speed USB device number 14 using uhci_hcd
Dec  3 10:13:00 saturn kernel: [46081.172009] usb 9-1: device descriptor read/64, error -71
Dec  3 10:13:01 saturn kernel: [46081.452013] usb 9-1: device descriptor read/64, error -71
Dec  3 10:13:01 saturn kernel: [46081.724009] usb 9-1: new full-speed USB device number 15 using uhci_hcd
Dec  3 10:13:01 saturn kernel: [46081.900014] usb 9-1: device descriptor read/64, error -71
Dec  3 10:13:01 saturn kernel: [46082.180016] usb 9-1: device descriptor read/64, error -71
Dec  3 10:13:02 saturn kernel: [46082.452012] usb 9-1: new full-speed USB device number 16 using uhci_hcd
Dec  3 10:13:02 saturn kernel: [46082.860013] usb 9-1: device not accepting address 16, error -71
Dec  3 10:13:02 saturn kernel: [46083.028026] usb 9-1: new full-speed USB device number 17 using uhci_hcd
Dec  3 10:13:03 saturn kernel: [46083.440014] usb 9-1: device not accepting address 17, error -71
Dec  3 10:13:03 saturn kernel: [46083.440025] hub 9-0:1.0: unable to enumerate USB device on port 1
```

So I'll try it in a different USB port, on the case.

```
Dec  3 10:23:35 saturn kernel: [46715.412009] usb 8-2: new full-speed USB device number 2 using uhci_hcd
Dec  3 10:23:35 saturn kernel: [46715.588017] usb 8-2: device descriptor read/64, error -71
Dec  3 10:23:35 saturn kernel: [46715.812016] usb 8-2: device descriptor read/64, error -71
Dec  3 10:23:35 saturn kernel: [46716.028047] usb 8-2: new full-speed USB device number 3 using uhci_hcd
Dec  3 10:23:35 saturn kernel: [46716.152035] usb 8-2: device descriptor read/64, error -71
Dec  3 10:23:36 saturn kernel: [46716.376015] usb 8-2: device descriptor read/64, error -71
Dec  3 10:23:36 saturn kernel: [46716.592027] usb 8-2: new full-speed USB device number 4 using uhci_hcd
Dec  3 10:23:36 saturn kernel: [46717.008011] usb 8-2: device not accepting address 4, error -71
Dec  3 10:23:36 saturn kernel: [46717.176011] usb 8-2: new full-speed USB device number 5 using uhci_hcd
Dec  3 10:23:37 saturn kernel: [46717.584014] usb 8-2: device not accepting address 5, error -71
Dec  3 10:23:37 saturn kernel: [46717.584023] hub 8-0:1.0: unable to enumerate USB device on port 2

```

So it looks like the same problem: "device descriptor read/64, error -71" and "device not accepting address".

Any ideas what's going on, here?

Try switching from PC to PS3 mode while it's still on that USB port; this does nothing at all.
Switch back to PC mode, still nothing.
Press PRESET and MAPPING together, and I get the same result as before.
Dec  3 10:25:57 saturn kernel: [46858.008018] usb 8-2: new full-speed USB device number 6 using uhci_hcd
Dec  3 10:25:57 saturn kernel: [46858.132018] usb 8-2: device descriptor read/64, error -71
Dec  3 10:25:58 saturn kernel: [46858.356011] usb 8-2: device descriptor read/64, error -71
Dec  3 10:25:58 saturn kernel: [46858.572012] usb 8-2: new full-speed USB device number 7 using uhci_hcd
Dec  3 10:25:58 saturn kernel: [46858.692009] usb 8-2: device descriptor read/64, error -71
Dec  3 10:25:58 saturn kernel: [46858.976008] usb 8-2: device descriptor read/64, error -71
Dec  3 10:25:59 saturn kernel: [46859.248009] usb 8-2: new full-speed USB device number 8 using uhci_hcd
Dec  3 10:25:59 saturn kernel: [46859.656007] usb 8-2: device not accepting address 8, error -71
Dec  3 10:25:59 saturn kernel: [46859.824011] usb 8-2: new full-speed USB device number 9 using uhci_hcd
Dec  3 10:25:59 saturn kernel: [46860.232011] usb 8-2: device not accepting address 9, error -71
Dec  3 10:25:59 saturn kernel: [46860.232019] hub 8-0:1.0: unable to enumerate USB device on port 2

---

### Post by Keith_Beef on 2013-12-04
I searched fot this "device descriptor read/64, error -71" and found nothing, though I read on [AskUbuntu]("http://askubuntu.com/questions/341241/ubuntu-wont-start-with-device-descriptor-read-64-error-32-what-this-messag"") that error -32 is about power supply. 

I plugged the HOTAS X into an external USB hub with a 5V power supply.

Dec  3 16:27:23 saturn kernel: [20219.780326] usb 1-4.2: new full-speed USB device number 11 using ehci_hcd
Dec  3 16:27:23 saturn kernel: [20219.860320] usb 1-4.2: device descriptor read/64, error -32
Dec  3 16:27:23 saturn kernel: [20220.044321] usb 1-4.2: device descriptor read/64, error -32
Dec  3 16:27:23 saturn kernel: [20220.220322] usb 1-4.2: new full-speed USB device number 12 using ehci_hcd
Dec  3 16:27:23 saturn kernel: [20220.296321] usb 1-4.2: device descriptor read/64, error -32
Dec  3 16:27:23 saturn kernel: [20220.476320] usb 1-4.2: device descriptor read/64, error -32
Dec  3 16:27:24 saturn kernel: [20220.652320] usb 1-4.2: new full-speed USB device number 13 using ehci_hcd
Dec  3 16:27:24 saturn kernel: [20221.060013] usb 1-4.2: device not accepting address 13, error -32
Dec  3 16:27:24 saturn kernel: [20221.132320] usb 1-4.2: new full-speed USB device number 14 using ehci_hcd
Dec  3 16:27:24 saturn kernel: [20221.540014] usb 1-4.2: device not accepting address 14, error -32
Dec  3 16:27:24 saturn kernel: [20221.540339] hub 1-4:1.0: unable to enumerate USB device on port 2

Right, so I can now get either error -32 or error -71 for this device.

But that AskUbuntu page referred to [another site]("http://paulphilippov.com/articles/how-to-fix-device-not-accepting-address-error") where errors -32, -71 and -101 are mentioned, and the declared cause is "over-current protection"; the proposed cure is to disconnect all other other USB devices, switch off and back on again. So I tried that.

Now, with the receiver for the wireless keyboard and mouse plugged into the car reader's USB port, the only other thing connected to the computer's USB is the powered external hub.

The computer refused to boot, the POST complained about there being no keyboard present, so I had to plug the receiver for the keyboard into the powered hub again.

Plugging the HOTAS X into the powered USB hub gets error -32, plugging it into the mainboard gets error -71, so there is no improvement at all.

Elsewhere, I have seen people mention USB devices that work under Windows but which fail with these -32, -71 or -101 error codes. I'll try to find those again.

---

### Post by r-senior on 2013-12-04
It was two or three years ago, but I had a problem similar to this with a digital audio workstation. These were my logs:

```
[   90.540060] usb 6-1: device descriptor read/64, error -71
[   90.780070] usb 6-1: device descriptor read/64, error -71
[   91.010047] usb 6-1: new full speed USB device using uhci_hcd and address 3
[   91.140045] usb 6-1: device descriptor read/64, error -71
[   91.380070] usb 6-1: device descriptor read/64, error -71
[   91.610078] usb 6-1: new full speed USB device using uhci_hcd and address 4
[   92.030046] usb 6-1: device not accepting address 4, error -71
[   92.150071] usb 6-1: new full speed USB device using uhci_hcd and address 5
[   92.570068] usb 6-1: device not accepting address 5, error -71
[   92.570122] hub 6-0:1.0: unable to enumerate USB device on port 1
```

I reported it as a bug to the kernel mailing list and it was fixed within a week. The fix made its way into the Ubuntu kernel eventually.

If you do report the bug this way, you should be prepared to

a. Compile and install a kernel. If this used to work and now doesn't, they will ask you to do a git bisect to track down the commit. If it's not a regression, they will want the bug report from a very recent kernel, unadorned by Ubuntu customizations. No VMs.

b. Turn on enhanced logging in the kernel. They might tell you what they want but not how to do it.

c. Spend quite a bit of your own time helping track down the bug. Once I'd isolated the offending commit in Git, the USB maintainer had a fix within a few hours and it worked first time.

---

### Post by Keith_Beef on 2013-12-04
[StackExchange]("http://unix.stackexchange.com/questions/72625/why-is-usb-not-working-in-linux-when-it-works-in-uefi-bios") seems to have a possible solution, since syslog shows that the computer is trying to use ehci_hcd.

> cd /sys/bus/pci/drivers/ehci_hcd
ls

You will see a file with 0000:00:xx.x format. Execute the following command:

sudo sh -c 'echo -n "0000:00:xx.x" > unbind'

Replace the xx.x with the numbers displayed on your file. It should disable the ehci_hcd.

You can now use the following script to disable ehci_hcd.

cd /sys/bus/pci/drivers/ehci_hcd/
sudo sh -c 'find ./ -name "0000:00:*" -print| sed "s/\.\///">unbind'

[http://www.geekdevs.com/2010/04/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/](http://www.geekdevs.com/2010/04/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/)



So I tried that.

```
cd /sys/bus/pci/drivers/ehci_hcd

ls
0000:00:1a.7  0000:00:1d.7  0000:05:01.2  bind  module  new_id  remove_id  uevent  unbind

lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 006: ID 04b8:0005 Seiko Epson Corp. Printer

lsusb -t
/:  Bus 11.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 10.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 09.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 6, If 0, Class=print, Driver=usblp, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/4p, 480M
    |__ Port 4: Dev 2, If 0, Class=stor., Driver=usb-storage, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
    |__ Port 2: Dev 2, If 0, Class=hub, Driver=hub/4p, 480M
        |__ Port 1: Dev 3, If 0, Class=hub, Driver=hub/4p, 480M
        |__ Port 4: Dev 4, If 0, Class=HID, Driver=usbhid, 1.5M
        |__ Port 4: Dev 4, If 1, Class=HID, Driver=usbhid, 1.5M
```

Now plug in the HOTAS X and look again
```
ls
0000:00:1a.7  0000:00:1d.7  0000:05:01.2  bind  module  new_id  remove_id  uevent  unbind

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 006: ID 04b8:0005 Seiko Epson Corp. Printer

lsusb -t
/:  Bus 11.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 10.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 09.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 6, If 0, Class=print, Driver=usblp, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/4p, 480M
    |__ Port 4: Dev 2, If 0, Class=stor., Driver=usb-storage, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
    |__ Port 2: Dev 2, If 0, Class=hub, Driver=hub/4p, 480M
        |__ Port 1: Dev 3, If 0, Class=hub, Driver=hub/4p, 480M
        |__ Port 4: Dev 4, If 0, Class=HID, Driver=usbhid, 1.5M
        |__ Port 4: Dev 4, If 1, Class=HID, Driver=usbhid, 1.5M
```

No difference… still 0000:00:1a.7  0000:00:1d.7  0000:05:01.2, so how do I know which of those values to send to unbind?

Syslog shows the usual error message.
```
Dec  4 11:22:40 saturn kernel: [66501.436321] usb 1-2.3: new full-speed USB device number 11 using ehci_hcd
Dec  4 11:22:40 saturn kernel: [66501.508316] usb 1-2.3: device descriptor read/64, error -32
Dec  4 11:22:41 saturn kernel: [66501.684319] usb 1-2.3: device descriptor read/64, error -32
Dec  4 11:22:41 saturn kernel: [66501.860321] usb 1-2.3: new full-speed USB device number 12 using ehci_hcd
Dec  4 11:22:41 saturn kernel: [66501.932328] usb 1-2.3: device descriptor read/64, error -32
Dec  4 11:22:41 saturn kernel: [66502.108320] usb 1-2.3: device descriptor read/64, error -32
Dec  4 11:22:41 saturn kernel: [66502.284318] usb 1-2.3: new full-speed USB device number 13 using ehci_hcd
Dec  4 11:22:42 saturn kernel: [66502.692012] usb 1-2.3: device not accepting address 13, error -32
Dec  4 11:22:42 saturn kernel: [66502.764319] usb 1-2.3: new full-speed USB device number 14 using ehci_hcd
Dec  4 11:22:42 saturn kernel: [66503.172010] usb 1-2.3: device not accepting address 14, error -32
Dec  4 11:22:42 saturn kernel: [66503.172333] hub 1-2:1.0: unable to enumerate USB device on port 3
```

Well, syslog has a line telling me it set up communication with the printer.
```
Dec  4 08:53:52 saturn udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:1a.0/usb4/4-1
```

So that identifies the value 0000:00:1a.7. I can grep for the other values, and should find the receiver for the wireless keyboad on the external hub, which is where I plugged the HOTAS X… so maybe that is the value to send to unbind.

```
grep "add \/devices\/pci" /var/log/syslog
Dec  4 08:50:39 saturn udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb4/4-1/4-1:1.0
Dec  4 08:50:39 saturn udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb4/4-1/4-1:1.0/usb/lp0
Dec  4 08:50:41 saturn udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb4/4-1/4-1:1.0/usb/lp0
Dec  4 08:53:52 saturn udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb4/4-1/4-1:1.0/usb/lp0
```

No, it only finds the printer.

But if I unplug the printer and plug it into the hub, that should work.


But no… the printer is reconnected with the same value 0000:00:1a.7, but the end is different, no doubt identifying the USB port.
```
Dec  4 11:32:13 saturn udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.1/1-2.1.2/1-2.1.2:1.0
```

This is the part of lsusb -t that changed:

The second line of
```
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 6, If 0, Class=print, Driver=usblp, 12M
```

has gone, because 
```
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
    |__ Port 2: Dev 2, If 0, Class=hub, Driver=hub/4p, 480M
        |__ Port 1: Dev 3, If 0, Class=hub, Driver=hub/4p, 480M
        |__ Port 4: Dev 4, If 0, Class=HID, Driver=usbhid, 1.5M
        |__ Port 4: Dev 4, If 1, Class=HID, Driver=usbhid, 1.5M
```

has become:
```
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
    |__ Port 2: Dev 2, If 0, Class=hub, Driver=hub/4p, 480M
        |__ Port 1: Dev 3, If 0, Class=hub, Driver=hub/4p, 480M
            |__ Port 2: Dev 15, If 0, Class=print, Driver=usblp, 12M
        |__ Port 4: Dev 4, If 0, Class=HID, Driver=usbhid, 1.5M
        |__ Port 4: Dev 4, If 1, Class=HID, Driver=usbhid, 1.5M
```

Well, what are the other two values, 0000:00:1d.7 and 0000:05:01.2?
```
grep "0000\:00\:1a\.7" /var/log/syslog
Dec  4 11:32:13 saturn mtp-probe: checking bus 1, device 15: "/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.1/1-2.1.2"
Dec  4 11:32:13 saturn udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.1/1-2.1.2/1-2.1.2:1.0
Dec  4 11:32:13 saturn udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.1/1-2.1.2
Dec  4 11:32:13 saturn udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.1/1-2.1.2/1-2.1.2:1.0/usb/lp0
Dec  4 11:32:14 saturn udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.1/1-2.1.2
Dec  4 11:32:15 saturn udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.1/1-2.1.2/1-2.1.2:1.0/usb/lp0
Dec  4 11:32:15 saturn udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.1/1-2.1.2

grep "0000\:00\:1d\.7" /var/log/syslog
```
Nothing… maybe the event is in an older file, like /var/log/syslog.1 or /var/log/syslog.2.gz

```
zgrep "0000\:00\:1d\.7" /var/log/syslog*
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.360603] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.360617] pci 0000:00:1d.7: reg 10: [mem 0xfa204000-0xfa2043ff]
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.403556] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.403578] pci 0000:00:1d.7: PCI INT A disabled
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.776239] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.776249] ehci_hcd 0000:00:1d.7: setting latency timer to 64
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.776251] ehci_hcd 0000:00:1d.7: EHCI Host Controller
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.776307] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.780210] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.780221] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfa204000
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.796014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.360582] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.360596] pci 0000:00:1d.7: reg 10: [mem 0xfa204000-0xfa2043ff]
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.404424] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.404442] pci 0000:00:1d.7: PCI INT A disabled
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.784232] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.784241] ehci_hcd 0000:00:1d.7: setting latency timer to 64
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.784243] ehci_hcd 0000:00:1d.7: EHCI Host Controller
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.784276] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.788177] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.788187] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfa204000
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.804013] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00

zgrep "0000\:05\:01\.2" /var/log/syslog*
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.362135] pci 0000:05:01.2: [1106:3104] type 0 class 0x000c03
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.362150] pci 0000:05:01.2: reg 10: [mem 0xfa10d000-0xfa10d0ff]
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.362212] pci 0000:05:01.2: supports D1 D2
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.362213] pci 0000:05:01.2: PME# supported from D0 D1 D2 D3hot D3cold
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.362217] pci 0000:05:01.2: PME# disabled
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.403661] pci 0000:05:01.2: PCI INT C -> GSI 16 (level, low) -> IRQ 16
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.403678] pci 0000:05:01.2: PCI INT C disabled
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.796227] ehci_hcd 0000:05:01.2: PCI INT C -> GSI 16 (level, low) -> IRQ 16
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.796236] ehci_hcd 0000:05:01.2: EHCI Host Controller
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.796294] ehci_hcd 0000:05:01.2: new USB bus registered, assigned bus number 3
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.796320] ehci_hcd 0000:05:01.2: irq 16, io mem 0xfa10d000
/var/log/syslog.1:Dec  3 10:50:51 saturn kernel: [    0.808015] ehci_hcd 0000:05:01.2: USB 2.0 started, EHCI 1.00
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.362113] pci 0000:05:01.2: [1106:3104] type 0 class 0x000c03
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.362127] pci 0000:05:01.2: reg 10: [mem 0xfa10d000-0xfa10d0ff]
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.362190] pci 0000:05:01.2: supports D1 D2
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.362191] pci 0000:05:01.2: PME# supported from D0 D1 D2 D3hot D3cold
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.362195] pci 0000:05:01.2: PME# disabled
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.404521] pci 0000:05:01.2: PCI INT C -> GSI 16 (level, low) -> IRQ 16
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.404537] pci 0000:05:01.2: PCI INT C disabled
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.804214] ehci_hcd 0000:05:01.2: PCI INT C -> GSI 16 (level, low) -> IRQ 16
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.804223] ehci_hcd 0000:05:01.2: EHCI Host Controller
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.804258] ehci_hcd 0000:05:01.2: new USB bus registered, assigned bus number 3
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.804284] ehci_hcd 0000:05:01.2: irq 16, io mem 0xfa10d000
/var/log/syslog.1:Dec  3 16:54:47 saturn kernel: [    0.816013] ehci_hcd 0000:05:01.2: USB 2.0 started, EHCI 1.00
```

There were a total of 83 entries for 0000:00:1d.7 and 90 for 0000:05:01.2, but those from Dec 3 at 10:50 and 16:54 are the most likely to be the HOTAS X.

So let's try sending those values to unbind, to see what happens. It shouldn't do any permanent harm, since the change is lost after a reboot.

```
sudo sh -c 'echo -n "0000:00:1d.7" > unbind'
```

New entries appear in syslog.
```
Dec  4 11:56:13 saturn kernel: [68513.639428] ehci_hcd 0000:00:1d.7: remove, state 4
Dec  4 11:56:13 saturn kernel: [68513.639436] usb usb2: USB disconnect, device number 1
Dec  4 11:56:13 saturn kernel: [68513.643596] ehci_hcd 0000:00:1d.7: USB bus 2 deregistered
Dec  4 11:56:13 saturn kernel: [68513.643695] ehci_hcd 0000:00:1d.7: PCI INT A disabled
```

Unplug the HOTAS and plug it back in.
```
 Dec  4 11:56:43 saturn kernel: [68544.572305] usb 1-2.3: new full-speed USB device number 16 using ehci_hcd
Dec  4 11:56:44 saturn kernel: [68544.652301] usb 1-2.3: device descriptor read/64, error -32
Dec  4 11:56:44 saturn kernel: [68544.836302] usb 1-2.3: device descriptor read/64, error -32
Dec  4 11:56:44 saturn kernel: [68545.012303] usb 1-2.3: new full-speed USB device number 17 using ehci_hcd
Dec  4 11:56:44 saturn kernel: [68545.092303] usb 1-2.3: device descriptor read/64, error -32
Dec  4 11:56:44 saturn kernel: [68545.276303] usb 1-2.3: device descriptor read/64, error -32
Dec  4 11:56:44 saturn kernel: [68545.452314] usb 1-2.3: new full-speed USB device number 18 using ehci_hcd
Dec  4 11:56:45 saturn kernel: [68545.860011] usb 1-2.3: device not accepting address 18, error -32
Dec  4 11:56:45 saturn kernel: [68545.932302] usb 1-2.3: new full-speed USB device number 19 using ehci_hcd
Dec  4 11:56:45 saturn kernel: [68546.340010] usb 1-2.3: device not accepting address 19, error -32
Dec  4 11:56:45 saturn kernel: [68546.340316] hub 1-2:1.0: unable to enumerate USB device on port 3
```

So no change.

```
sudo sh -c 'echo -n "0000:05:01.2" > unbind'

Dec  4 11:59:08 saturn kernel: [68689.148620] usb 3-4: USB disconnect, device number 2
Dec  4 11:59:08 saturn kernel: [68689.157158] ehci_hcd 0000:05:01.2: USB bus 3 deregistered
Dec  4 11:59:08 saturn kernel: [68689.157249] ehci_hcd 0000:05:01.2: PCI INT C disabled
Dec  4 11:59:08 saturn kernel: [68689.416015] usb 11-2: new full-speed USB device number 2 using uhci_hcd
Dec  4 11:59:08 saturn kernel: [68689.555037] usb 11-2: not running at top speed; connect to a high speed hub
Dec  4 11:59:08 saturn mtp-probe: checking bus 11, device 2: "/sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.1/usb11/11-2"
Dec  4 11:59:08 saturn mtp-probe: bus: 11, device: 2 was not an MTP device
Dec  4 11:59:08 saturn kernel: [68689.586189] scsi11 : usb-storage 11-2:1.0
Dec  4 11:59:09 saturn kernel: [68690.588054] scsi 11:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Dec  4 11:59:09 saturn kernel: [68690.591044] scsi 11:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Dec  4 11:59:09 saturn kernel: [68690.594045] scsi 11:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Dec  4 11:59:09 saturn kernel: [68690.597045] scsi 11:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Dec  4 11:59:09 saturn kernel: [68690.597728] sd 11:0:0:0: Attached scsi generic sg2 type 0
Dec  4 11:59:09 saturn kernel: [68690.597894] sd 11:0:0:1: Attached scsi generic sg3 type 0
Dec  4 11:59:09 saturn kernel: [68690.598037] sd 11:0:0:2: Attached scsi generic sg4 type 0
Dec  4 11:59:09 saturn kernel: [68690.598753] sd 11:0:0:3: Attached scsi generic sg5 type 0
Dec  4 11:59:10 saturn kernel: [68690.663039] sd 11:0:0:2: [sde] Attached SCSI removable disk
Dec  4 11:59:10 saturn kernel: [68690.790040] sd 11:0:0:1: [sdd] Attached SCSI removable disk
Dec  4 11:59:10 saturn kernel: [68690.820056] sd 11:0:0:0: [sdc] Attached SCSI removable disk
Dec  4 11:59:10 saturn kernel: [68690.865057] sd 11:0:0:3: [sdf] Attached SCSI removable disk
```

Ah, so this is the card reader that is connected to USB headers on the mainboard. Maybe if I use plug the HOTAS into the USB connector on that card reader, I'll see something…

```
Dec  4 12:01:38 saturn kernel: [68838.992013] usb 11-1: new full-speed USB device number 3 using uhci_hcd
Dec  4 12:01:38 saturn kernel: [68839.112009] usb 11-1: device descriptor read/64, error -71
Dec  4 12:01:38 saturn kernel: [68839.336010] usb 11-1: device descriptor read/64, error -71
Dec  4 12:01:38 saturn kernel: [68839.552008] usb 11-1: new full-speed USB device number 4 using uhci_hcd
Dec  4 12:01:39 saturn kernel: [68839.672009] usb 11-1: device descriptor read/64, error -71
Dec  4 12:01:39 saturn kernel: [68839.896010] usb 11-1: device descriptor read/64, error -71
Dec  4 12:01:39 saturn kernel: [68840.112010] usb 11-1: new full-speed USB device number 5 using uhci_hcd
Dec  4 12:01:39 saturn kernel: [68840.520008] usb 11-1: device not accepting address 5, error -71
Dec  4 12:01:40 saturn kernel: [68840.632009] usb 11-1: new full-speed USB device number 6 using uhci_hcd
Dec  4 12:01:40 saturn kernel: [68841.040011] usb 11-1: device not accepting address 6, error -71
Dec  4 12:01:40 saturn kernel: [68841.040023] hub 11-0:1.0: unable to enumerate USB device on port 1
```

No, still the same old error -71.

---

### Post by Keith_Beef on 2013-12-04
> **r-senior said:**
> It was two or three years ago, but I had a problem similar to this with a digital audio workstation. These were my logs:

```
[   90.540060] usb 6-1: device descriptor read/64, error -71
[   90.780070] usb 6-1: device descriptor read/64, error -71
[   91.010047] usb 6-1: new full speed USB device using uhci_hcd and address 3
[   91.140045] usb 6-1: device descriptor read/64, error -71
[   91.380070] usb 6-1: device descriptor read/64, error -71
[   91.610078] usb 6-1: new full speed USB device using uhci_hcd and address 4
[   92.030046] usb 6-1: device not accepting address 4, error -71
[   92.150071] usb 6-1: new full speed USB device using uhci_hcd and address 5
[   92.570068] usb 6-1: device not accepting address 5, error -71
[   92.570122] hub 6-0:1.0: unable to enumerate USB device on port 1
```

I reported it as a bug to the kernel mailing list and it was fixed within a week. The fix made its way into the Ubuntu kernel eventually.

If you do report the bug this way, you should be prepared to

a. Compile and install a kernel. If this used to work and now doesn't, they will ask you to do a git bisect to track down the commit. If it's not a regression, they will want the bug report from a very recent kernel, unadorned by Ubuntu customizations. No VMs.

b. Turn on enhanced logging in the kernel. They might tell you what they want but not how to do it.

c. Spend quite a bit of your own time helping track down the bug. Once I'd isolated the offending commit in Git, the USB maintainer had a fix within a few hours and it worked first time.

Thanks for your reply, r-senior. I see that your log entries refer to **uhci**_hcd, while mine are **ehci**_hcd.

I've not recompiled a kernel in years… certainly not since switching from Mandriva to Ubuntu, but I'm willing to give it a go. I don't know anything, yet, about how to identify an "offending commit in Git", though.

---

### Post by Keith_Beef on 2013-12-04
Ah, I just found [this page]("https://www.kernel.org/doc/Documentation/kernel-parameters.txt"), which lists a kernel parameter that looks promising (just about all the pages I've seen so far claim that all these -32 and -71 errors are "over-current protection").

```

	uhci-hcd.ignore_oc=
			[USB] Ignore overcurrent events (default N).
			Some badly-designed motherboards generate lots of
			bogus events, for ports that aren't wired to
			anything.  Set this parameter to avoid log spamming.
			Note that genuine overcurrent events won't be
			reported either.
```

My syslog entries are for ehci, not uhci, so maybe there is an equivalent parameter like ehci-hcd.ignore_oc=?

I tried looking at the kernel symbols, using the file I linked to above as a guide to possible parameter names. There is a parameter listed as "usbcore.usbfs_snoop", so I looked for parameters ending in "_snoop" first.

```
cat /proc/kallsyms | grep _snoop$
0000000000000000 r __param_str_usbfs_snoop
0000000000000000 r __param_usbfs_snoop
0000000000000000 b usbfs_snoop
```

Now looking for parameters ending in "ignore_oc":
```
cat /proc/kallsyms | grep ignore_oc$
0000000000000000 r __param_str_ignore_oc
0000000000000000 r __param_str_ignore_oc
0000000000000000 r __param_ignore_oc
0000000000000000 r __param_ignore_oc
0000000000000000 b ignore_oc
0000000000000000 b ignore_oc
```


So it looks like the first part of the parameter name is the module name, but I don't have a loaded module named usbcore.

```
sudo lsmod | grep -i usb
usblp                  18307  0 
usbhid                 47238  1 hid_logitech
hid                    99636  2 hid_logitech,usbhid
usb_storage            49198  0
```

---

### Post by r-senior on 2013-12-04
> **Keith_Beef said:**
> Thanks for your reply, r-senior. I see that your log entries refer to **uhci**_hcd, while mine are **ehci**_hcd.

Some of your logs do refer to uhci_hcd ...

```
...
Dec  4 12:01:40 saturn kernel: [68840.632009] usb 11-1: new full-speed USB device number 6 using [color="red"]uhci_hcd[/color]
Dec  4 12:01:40 saturn kernel: [68841.040011] usb 11-1: device not accepting address 6, error -71

```

---

### Post by Keith_Beef on 2013-12-04
> **r-senior said:**
> Some of your logs do refer to uhci_hcd ...

```
...
Dec  4 12:01:40 saturn kernel: [68840.632009] usb 11-1: new full-speed USB device number 6 using [color="red"]uhci_hcd[/color]
Dec  4 12:01:40 saturn kernel: [68841.040011] usb 11-1: device not accepting address 6, error -71

```

That's true, but that particular device is my card reader (SD, Memory Stick, etc.) that is connected to a header on the mainboard.

Plugging the HOTAS X into a USB port generates events that mention ehci_hcd.

---

### Post by Keith_Beef on 2013-12-04
I found that there is an ignore_oc parameter for  ehci_hcd, but I can't change it.

```
ls -al /sys/module/ehci_hcd/parameters/
total 0
drwxr-xr-x 2 root root    0 Dec  4 14:19 .
drwxr-xr-x 4 root root    0 Dec  4 11:18 ..
-r--r--r-- 1 root root 4096 Dec  4 14:19 hird
-r--r--r-- 1 root root 4096 Dec  4 14:21 ignore_oc
-r--r--r-- 1 root root 4096 Dec  4 14:19 log2_irq_thresh
-r--r--r-- 1 root root 4096 Dec  4 14:19 park

cat /sys/module/ehci_hcd/parameters/ignore_oc
N

sudo echo -n Y > /sys/module/ehci_hcd/parameters/ignore_oc
bash: /sys/module/ehci_hcd/parameters/ignore_oc: Permission denied
```

I can't do that? OK, I'll change the permissions.

```
sudo chmod u+rwx /sys/module/ehci_hcd/parameters/ignore_oc
ls -al /sys/module/ehci_hcd/parameters/
total 0
drwxr-xr-x 2 root root    0 Dec  4 14:19 .
drwxr-xr-x 4 root root    0 Dec  4 11:18 ..
-r--r--r-- 1 root root 4096 Dec  4 14:19 hird
-rwxr--r-- 1 root root 4096 Dec  4 14:21 ignore_oc
-r--r--r-- 1 root root 4096 Dec  4 14:19 log2_irq_thresh
-r--r--r-- 1 root root 4096 Dec  4 14:19 park

sudo echo -n Y > /sys/module/ehci_hcd/parameters/ignore_oc
bash: /sys/module/ehci_hcd/parameters/ignore_oc: Permission denied
```

I **still** can't do that. This must be one of those parameters that cannot be modified while the system is running.

I found [a page]("http://t5869.codeinpro.us/q/5152c26ce8432c04268dd1ad") that explains how to set this as a boot option in GRUB, so I followed those to update a line in /etc/default/grub.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ehci_hcd.ignore_OC=1"
```

Then I ran update-grub.

But still no change in this parameter.
```
cat /sys/module/ehci_hcd/parameters/ignore_oc
N
```

Ah, the instructions on that page are slightly wrong&#8230; it should be ehci_hcd.ignore_**oc** (lower case). I updated and rebooted again, and now:

```
cat /sys/module/ehci_hcd/parameters/ignore_oc
Y
```

The error messages are still there, though.

```
Dec  4 16:06:26 saturn kernel: [  127.420264] usb 1-2.1.1: new full-speed USB device number 11 using ehci_hcd
Dec  4 16:06:26 saturn kernel: [  127.492226] usb 1-2.1.1: device descriptor read/64, error -32
Dec  4 16:06:27 saturn kernel: [  127.668262] usb 1-2.1.1: device descriptor read/64, error -32
Dec  4 16:06:27 saturn kernel: [  127.844302] usb 1-2.1.1: new full-speed USB device number 12 using ehci_hcd
Dec  4 16:06:27 saturn kernel: [  127.916264] usb 1-2.1.1: device descriptor read/64, error -32
Dec  4 16:06:27 saturn kernel: [  128.092302] usb 1-2.1.1: device descriptor read/64, error -32
Dec  4 16:06:27 saturn kernel: [  128.268336] usb 1-2.1.1: new full-speed USB device number 13 using ehci_hcd
Dec  4 16:06:28 saturn kernel: [  128.676008] usb 1-2.1.1: device not accepting address 13, error -32
Dec  4 16:06:28 saturn kernel: [  128.748348] usb 1-2.1.1: new full-speed USB device number 14 using ehci_hcd
Dec  4 16:06:28 saturn kernel: [  129.156011] usb 1-2.1.1: device not accepting address 14, error -32
Dec  4 16:06:28 saturn kernel: [  129.156282] hub 1-2.1:1.0: unable to enumerate USB device on port 1
```

---

### Post by Keith_Beef on 2014-03-18
I did a BIOS firmware update yesterday, from F06 to F12, hoping to cure a minor annoyance (my CPU name wasnot reported for /proc/cpuinfo) and this problem&#8230; but no, I still get the errors.
Plugged into a port on the computer:
```
Mar 18 15:21:48 saturn kernel: [26261.288013] usb 7-1: new full-speed USB device number 3 using uhci_hcd
Mar 18 15:21:48 saturn kernel: [26261.412013] usb 7-1: device descriptor read/64, error -71
Mar 18 15:21:49 saturn kernel: [26261.636012] usb 7-1: device descriptor read/64, error -71
Mar 18 15:21:49 saturn kernel: [26261.908012] usb 7-1: new full-speed USB device number 4 using uhci_hcd
Mar 18 15:21:49 saturn kernel: [26262.320013] usb 7-1: device not accepting address 4, error -71
Mar 18 15:21:50 saturn kernel: [26262.488012] usb 7-1: new full-speed USB device number 5 using uhci_hcd
Mar 18 15:21:50 saturn kernel: [26262.896011] usb 7-1: device not accepting address 5, error -71
Mar 18 15:21:50 saturn kernel: [26262.896024] hub 7-0:1.0: unable to enumerate USB device on port 1
```

Plugged into an external, powered hub:
```
Mar 18 15:22:51 saturn kernel: [26324.436331] usb 1-2.2: new full-speed USB device number 10 using ehci_hcd
Mar 18 15:22:52 saturn kernel: [26324.516327] usb 1-2.2: device descriptor read/64, error -32
Mar 18 15:22:52 saturn kernel: [26324.700329] usb 1-2.2: device descriptor read/64, error -32
Mar 18 15:22:52 saturn kernel: [26324.876330] usb 1-2.2: new full-speed USB device number 11 using ehci_hcd
Mar 18 15:22:52 saturn kernel: [26324.956329] usb 1-2.2: device descriptor read/64, error -32
Mar 18 15:22:52 saturn kernel: [26325.140330] usb 1-2.2: device descriptor read/64, error -32
Mar 18 15:22:52 saturn kernel: [26325.316331] usb 1-2.2: new full-speed USB device number 12 using ehci_hcd
Mar 18 15:22:53 saturn kernel: [26325.724011] usb 1-2.2: device not accepting address 12, error -32
Mar 18 15:22:53 saturn kernel: [26325.796343] usb 1-2.2: new full-speed USB device number 13 using ehci_hcd
Mar 18 15:22:53 saturn kernel: [26326.204015] usb 1-2.2: device not accepting address 13, error -32
Mar 18 15:22:53 saturn kernel: [26326.204350] hub 1-2:1.0: unable to enumerate USB device on port 2

```

---

### Post by Keith_Beef on 2014-03-22
I had a problem with an eReader (a cheap Pan Digital PRD06 bought a few years ago) that would freeze up my keyboard and mouse whenever I plugged it in. 
Searching around, I found [another thread about USB problems]("http://ubuntuforums.org/showthread.php?t=797789").

Setting the old_scheme_first parameter cured that problem, so I started thinking that this might cure my HOTAS problem as well.

It didn't, and setting autosuspend to -1 did not fix the problem either; I'm still getting device descriptor read/64, error -32 in syslog.

---

### Post by Keith_Beef on 2014-03-22
[This thread]("https://bbs.archlinux.org/viewtopic.php?id=149708") set me on the path of looking in header files to decipher the error codes.

I eventually found two files containing lists.
```
/linux-source-3.2.0/include/asm-generic/errno.h
/linux-source-3.2.0/include/asm-generic/errno-base.h
```

Does it make sense that "device descriptor read/64, error -32" means "Broken pipe", as the line below from errno-base.h implies?

```

#define	EPIPE		32	/* Broken pipe */
```

---

