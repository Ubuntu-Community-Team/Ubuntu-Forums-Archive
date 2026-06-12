---
title: "How to know the commercial name of a device."
date: 2013-01-23
forum: Hardware
---

### Post by luquino on 2013-01-23
I have two video devices: KWorld TV card and Logitech web cam.
Is there any bash command or any system file that lets me know the commercial name of any single device?
i.e.: on /dev/vide0 there is the cam (sometimes) so I wish to make a query that returns me "Logitech HD 525 C" or something similar.
Thx for your help.

---

### Post by sanderj on 2013-01-23
Have you tried 

```
lsusb
```

---

### Post by matt_symes on 2013-01-23
Hi

...or 

```
lspci
```

Kind regards

---

### Post by luquino on 2013-01-23
yes but there is any reference to /dev/videox in lspci and lusb

```
luca@pc-sala:~$ lspci
00:00.0 RAM memory: NVIDIA Corporation MCP61 Host Bridge (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
02:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)
02:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
luca@pc-sala:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:0826 Logitech, Inc. 
luca@pc-sala:~$ 

```

and I need to prepare a little script that permits to choose the device in a human readable format

---

### Post by steeldriver on 2013-01-23
I don't know what you mean by "permits to choose the device" - but if you're trying to map /dev/xxx nodes to pluggable devices you might want to look at udev

```
udevadm info -a -n /dev/video0
```

---

### Post by luquino on 2013-01-24
yes, udevadm is the solution I was using in my script and I see that probably is the only one.

---

### Post by luquino on 2013-02-11
I was wrong, on Launchpad Answers they gave me the solution to the problem
[https://answers.launchpad.net/ubuntu/+question/221536]("https://answers.launchpad.net/ubuntu/+question/221536")


```
luca@pc-sala:~$ ls /sys/class/video4linux/video0/device/driver/module/drivers/
usb:uvcvideo
luca@pc-sala:~$ ls /sys/class/video4linux/video1/device/driver/module/drivers/
pci:saa7134
luca@pc-sala:~$ cat /sys/class//video4linux/video0/name
HD Webcam C525
luca@pc-sala:~$ cat /sys/class//video4linux/video1/name
saa7134[0] video (Kworld Plus T

```

---

