---
title: "No USB 2.0 on ASRock K7S41GX since update?"
date: 2009-06-04
forum: Hardware
---

### Post by subway.cookie on 2009-06-04
Hi everyone,

searching for K7S41 and K7S41GX didn't really help, so here is my problem:

Since the update to 9.04 my printer takes 2 minutes to print a picture. When I was looking for the issue, I did lspci and it returned
```

# lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

```Maybe you see the USB 1.1 controller. I assume this is the problem, since linux thinks that all rear USB connectors are attached to the USB 1.1 Controllers (which I found out by plugging the printer in every connector and do a lsusb, it alway said something like
```

# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f9:01ce Brother Industries, Ltd DCP-135C
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```The printer never was on bus 001. Funny thing is, that the board's manual states, that it has 6 USB 2.0 connectors, 4 of which are on the rear of the computer and two are on headers.
To me it looks like a weird driver issue, but I actually can't really remember having seen a "Linux Foundation 2.0 root hub" before, but that might be my bad memory :)

Do you have any idea how to make it USB 2.0 again? Because, well, USB 1.1 is kinda lame...

Thanks in advance, 
subway.cookie

---

### Post by subway.cookie on 2009-06-08
bump

---

### Post by simohell on 2009-10-02
> **subway.cookie said:**
> Hi everyone,

Since the update to 9.04 my printer takes 2 minutes to print a picture. 

[...]

Do you have any idea how to make it USB 2.0 again? Because, well, USB 1.1 is kinda lame...



Hi,

Sorry I can't help, except by telling that your probably looking at a wrong issue. My lspci looks the same, but I have 8.04 - so that I guess wouldn't be an upgrade issue. Did you check your lspci output before the upgrade?

I did have some USB-trouble with that motherboard at some point... don't know why, it's not an important system for me, so I didn't really look into it in detail.

---

