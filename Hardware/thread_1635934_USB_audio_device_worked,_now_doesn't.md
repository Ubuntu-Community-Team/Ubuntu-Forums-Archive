---
title: "USB audio device worked, now doesn't"
date: 2010-12-02
forum: Hardware
---

### Post by dolson on 2010-12-02
Hi.. I bought something called the Ion Tape Express. It's a cassette tape player with a USB port. I could return it if it didn't work with my OS, so I figured I may as well try it. My mom lent me her USB turntable, which I think was the same brand, and it worked fine. So, I got the thing home and plugged it in and Linux picked it up. I opened Audacity, selected the recording device, it worked fine.

But I went into the Sound configuration thing in Ubuntu 10.10, to see if I could get it to play through to my speakers (probably shoulda just enabled software playthrough in Audacity... hindsight, 20/20, all that...).

Something happened. I don't know what. I unplugged it and replugged it in, and it doesn't work anymore. I rebooted, same thing.

Now, here's the relevant sections from my log files from when it DID work:

> Dec  2 12:57:38 digory kernel: [1874067.916357] usb 3-2: new full speed USB device using uhci_hcd and address 2
Dec  2 12:57:38 digory kernel: [1874068.462496] usbcore: registered new interface driver hiddev
Dec  2 12:57:38 digory kernel: [1874068.466101] input: C-Media Electronics Inc. USB PnP Audio Device as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.2/input/input4
Dec  2 12:57:38 digory kernel: [1874068.466178] generic-usb 0003:0D8C:0121.0001: input,hidraw0: USB HID v1.00 Device [C-Media Electronics Inc. USB PnP Audio Device] on usb-0000:00:1d.1-2/input2
Dec  2 12:57:38 digory kernel: [1874068.466195] usbcore: registered new interface driver usbhid
Dec  2 12:57:38 digory kernel: [1874068.466197] usbhid: USB HID core driver
Dec  2 13:01:04 digory kernel: [1874274.542402] 2:1:1: usb_set_interface failed


Dec  2 12:57:38 digory kernel: [1874067.916357] usb 3-2: new full speed USB device using uhci_hcd and address 2
Dec  2 12:57:38 digory kernel: [1874068.462496] usbcore: registered new interface driver hiddev
Dec  2 12:57:38 digory kernel: [1874068.466101] input: C-Media Electronics Inc. USB PnP Audio Device as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.2/input/input4
Dec  2 12:57:38 digory kernel: [1874068.466178] generic-usb 0003:0D8C:0121.0001: input,hidraw0: USB HID v1.00 Device [C-Media Electronics Inc. USB PnP Audio Device] on usb-0000:00:1d.1-2/input2
Dec  2 12:57:38 digory kernel: [1874068.466195] usbcore: registered new interface driver usbhid
Dec  2 12:57:38 digory kernel: [1874068.466197] usbhid: USB HID core driver
Dec  2 12:57:39 digory rtkit-daemon[1674]: Successfully made thread 14494 of process 1921 (n/a) owned by '1000' RT at priority 5.
Dec  2 12:57:39 digory rtkit-daemon[1674]: Supervising 9 threads of 2 processes of 2 users.
Dec  2 13:01:04 digory kernel: [1874274.542402] 2:1:1: usb_set_interface failed
Dec  2 13:01:04 digory kernel: [1874274.543395] 2:1:1: usb_set_interface failed
Dec  2 13:01:04 digory pulseaudio[1921]: alsa-source.c: Failed to set hardware parameters: Input/output error


[1874068.549] (II) config/udev: Adding input device C-Media Electronics Inc. USB PnP Audio Device (/dev/input/event4)
[1874068.647] (II) No input driver/identifier specified (ignoring)

I believe that is messages, syslog, and Xorg, in that order.

Anyhow, as you can see, I did something at 13:01 that messed it up and it doesn't work anymore.

When I plug it in now, this is what I see in dmesg:

> [ 2582.988522] usb 5-2: new full speed USB device using uhci_hcd and address 6
[ 2583.112018] usb 5-2: device descriptor read/64, error -71
[ 2583.340013] usb 5-2: device descriptor read/64, error -71
[ 2583.556019] usb 5-2: new full speed USB device using uhci_hcd and address 7
[ 2583.680018] usb 5-2: device descriptor read/64, error -71
[ 2583.908020] usb 5-2: device descriptor read/64, error -71
[ 2584.124515] usb 5-2: new full speed USB device using uhci_hcd and address 8
[ 2584.532019] usb 5-2: device not accepting address 8, error -71
[ 2584.644019] usb 5-2: new full speed USB device using uhci_hcd and address 9
[ 2585.052017] usb 5-2: device not accepting address 9, error -71
[ 2585.052036] hub 5-0:1.0: unable to enumerate USB device on port 2

Anyone know what to do? I'm lost.. Is there something to do with ALSA or Pulse or whatever Ubuntu's using these days, or HAL or whatever the hardware stuff is? It's frustrating that I had it working, basically out of the box, and then I adjusted the input volume in the GUI and something broke..

I am using Ubuntu 10.10 32-bit on a Pentium Dual-Core E6600 system. Not sure what other info would be relevant here..

Any help is greatly appreciated.

Edit:

I found some advice to unplug all USB devices, power down, unplug the power supply, and this should "reset" something in the motherboard. I don't know that this is true, it sounds odd to me, but I tried it. When I started back up and plugged it in, the thing worked for a couple minutes, and I was looking in pavucontrol this time, and when I tried to increase the record level from the default of 35% to "unamplified" or whatever the label was, I got this in dmesg:

> [  361.003914] 2:1:1: usb_set_interface failed
[  361.004910] 2:1:1: usb_set_interface failed
[  361.005909] 2:1:1: usb_set_interface failed
[  361.006912] 2:1:1: usb_set_interface failed
[  361.007911] 2:1:1: usb_set_interface failed
[  361.008911] 2:1:1: usb_set_interface failed
[  361.009906] 2:1:1: usb_set_interface failed
[  361.010906] 2:1:1: usb_set_interface failed
[  361.011908] 2:1:1: usb_set_interface failed
[  361.012042] hub 3-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[  361.012046] usb 3-1: USB disconnect, address 2
[  361.012105] 2:1:1: usb_set_interface failed
[  361.012646] 2:1:1: usb_set_interface failed
[  361.012708] 2:1:1: usb_set_interface failed

I don't understand why the "hub" disabled the port and then tried to re-enable it... This is a relatively brand new PC (got it a couple months ago new from Acer - work-supplied machine), no other USB devices I've used exhibited any issues.

Thanks for any help.

Edit 2:

I tried it on another PC, same problem, but it didn't even show up when I plugged it in... Took it back to my other PC, found a regular stereo cable to try recording from the headphone out and was going to return the player tomorrow. I plugged it in USB (for power), and the damn PC recognized it no problem, and it is working right now with Audacity through USB... Since I had decided I'd return it tomorrow if I couldn't get the thing solved in 24 hours, I figured, may as well set the record level - that worked fine, too! I DON'T GET IT. If anyone knows what's going on, please let me know. I'm scared to unplug it, for fear it will stop working again..

---

