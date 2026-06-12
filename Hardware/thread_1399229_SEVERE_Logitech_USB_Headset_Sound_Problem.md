---
title: "SEVERE Logitech USB Headset Sound Problem"
date: 2010-02-05
forum: Hardware
---

### Post by thfz on 2010-02-05
I own a Logitech ClearChat Comfort USB headset, and I am having severe problems with it. I've managed to set up KDE so that it is the preferred audio card, and for a little while after plugging the device in everything works perfectly. However, once an application starts to play sound (Flash, Amarok, whatever), eventually a fuzzy noise sound starts playing through the headset and then the application will lock up along with any programs related to the sound system (pavucontrol, KDE System Settings Multimedia tab, and so on). If I unplug the device, those applications will resume their normal activity, or at least be able to be killed. If I try to plug the headset back in after this happens, the red power light on the device doesn't turn on, and the computer doesn't recognize it.

Sometimes, after plugging in or unplugging the headset, my USB mouse will freeze up. Just the mouse, not the keyboard. This does not unfreeze until after a reboot. Also, when this happens, **lsusb** does not display any information. The process locks up and can't be killed by CTRL+C or CTRL+Z; it just hangs.

I have no clue what's going on here, but I believe it is related to PulseAudio. If I try to play a sound file using aplay, I sometimes get an error about snd_pcm being unavailable. My mouse is currently frozen due to this error, so I can't post the output of any commands right now. I'll edit this after a reboot.

Thanks for any help you can give!

I should probably also mention that this issue can be replicated on Fedora 12 on this computer, but that this doesn't appear to occur on my laptop (currently running Ubuntu 9.10).

=========================
Ubuntu 9.10, Fedora 12
=========================

This is by far one of the strangest problems I've ever seen in Linux.

Here is lspci:
```

00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 SATA controller: nVidia Corporation MCP78S [GeForce 8200] AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200 (rev a2)
04:00.0 Communication controller: Agere Systems Device 0630 (rev 01)
05:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403

```

lsusb with the device plugged in:
```

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 04f2:0760 Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6363 Alcor Micro Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 046d:0a0c Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c054 Logitech, Inc.

```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


cat /var/log/messages | tail
```
Feb  5 12:33:15 localhost kernel: usb 4-4: Manufacturer: Logitech
Feb  5 12:33:15 localhost kernel: usb 4-4: configuration #1 chosen from 1 choice
Feb  5 12:33:15 localhost kernel: input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:04.0/usb4/4-4/4-4:1.3/input/input7
Feb  5 12:33:15 localhost kernel: generic-usb 0003:046D:0A0C.0005: input,hidraw3: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:04.0-4/input3
Feb  5 12:33:16 localhost kernel: usbcore: registered new interface driver snd-usb-audio
Feb  5 12:33:16 localhost rtkit-daemon[2096]: Sucessfully made thread 2178 of process 2094 (/usr/bin/pulseaudio) owned by '500' RT at priority 5.
Feb  5 12:33:16 localhost rtkit-daemon[2096]: Sucessfully made thread 2179 of process 2094 (/usr/bin/pulseaudio) owned by '500' RT at priority 5.
Feb  5 12:33:22 localhost kernel: ALSA sound/usb/usbaudio.c:934: timeout: still 3 active urbs..
Feb  5 12:33:28 localhost kernel: ALSA sound/usb/usbaudio.c:934: timeout: still 7 active urbs..
Feb  5 12:34:05 localhost kernel: usb 4-4: USB disconnect, address 3
```

This is the /var/log/messages when there is no error. I'll post the failure messages after I reboot to get my mouse back.

Here is the failure message:
```

Feb  5 12:39:14 localhost kernel: [<c066e3c0>] usb_disconnect+0xcc/0x16a
Feb  5 12:39:14 localhost kernel: [<c066f868>] hub_thread+0x547/0x1077
Feb  5 12:39:14 localhost kernel: [<c0430cde>] ? finish_task_switch+0xa4/0xbf
Feb  5 12:39:14 localhost kernel: [<c0449c21>] ? autoremove_wake_function+0x0/0x34
Feb  5 12:39:14 localhost kernel: [<c0449977>] kthread+0x70/0x75
Feb  5 12:39:14 localhost kernel: [<c066f321>] ? hub_thread+0x0/0x1077
Feb  5 12:39:14 localhost kernel: [<c066f321>] ? hub_thread+0x0/0x1077
Feb  5 12:39:14 localhost kernel: [<c0449977>] ? kthread+0x70/0x75
Feb  5 12:39:14 localhost kernel: [<c0449907>] ? kthread+0x0/0x75
Feb  5 12:39:14 localhost kernel: [<c04041c7>] kernel_thread_helper+0x7/0x10

```

---

### Post by labinnsw on 2010-02-12
Have you tried any of these yet?

[http://ubuntuforums.org/showthread.php?t=1135182](http://ubuntuforums.org/showthread.php?t=1135182)

[http://ubuntuforums.org/showthread.php?t=1002746](http://ubuntuforums.org/showthread.php?t=1002746) (number 14)

[http://ubuntuforums.org/showthread.php?t=543878](http://ubuntuforums.org/showthread.php?t=543878)

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

[http://ubuntuforums.org/showthread.php?t=1210812](http://ubuntuforums.org/showthread.php?t=1210812)

They are in no particular order.

---

### Post by two-sheds on 2010-03-01
I have the same chipset and the same problem. My system worked fine prior to 9.10 so there is no old fixes for previous versions of Ubuntu that are going to solve the problem.  

I haven't found any information on how to fix the problem but no USB devices work properly.

---

### Post by labinnsw on 2010-03-01
> **two-sheds said:**
> so there is no old fixes for previous versions of Ubuntu that are going to solve the problem.

Not necessarily. You won't know until you try.

---

