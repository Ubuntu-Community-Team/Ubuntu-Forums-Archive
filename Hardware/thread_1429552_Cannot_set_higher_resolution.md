---
title: "Cannot set higher resolution"
date: 2010-03-14
forum: Hardware
---

### Post by netizen99 on 2010-03-14
I Install Ubuntu 9.10 desktop on my Hasee Q540x laptop. Everything works fine except the LCD display can't display the higher resolution 1280x800. Any solution?

---

### Post by ssulaco on 2010-03-14
Just a thought,Is your Graphics driver enabled?
Go to System -> Administration -> Hardware drivers

---

### Post by zeroseven0183 on 2010-03-14
I also had that trouble when installing Ubuntu on my cousin's laptop. I had to find a third-party .deb for his graphic card since it's not automatically detected in the Hardware Drivers. Could you post the result of ```
**lspci**
```

In case you have a SiS graphic driver, check out [http://www.winischhofer.eu/linuxsispart1.shtml](http://www.winischhofer.eu/linuxsispart1.shtml) and download the appropriate driver.

I also uploaded a file in Mediafire that I used to upgrade the driver for my cousin's. It's in [http://www.mediafire.com/?xwogktm4zmm](http://www.mediafire.com/?xwogktm4zmm)

Higher resolution was added after the installation, however, the screen still has some problems like having some random vertical lines when playing videos.

---

### Post by netizen99 on 2010-03-16
Thanks all for your replies.

below is lspci output:
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

---

