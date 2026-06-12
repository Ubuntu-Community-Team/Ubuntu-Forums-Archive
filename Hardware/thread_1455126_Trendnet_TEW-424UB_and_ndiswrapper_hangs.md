---
title: "Trendnet TEW-424UB and ndiswrapper hangs"
date: 2010-04-15
forum: Hardware
---

### Post by WA1DH on 2010-04-15
I'm trying to get a Trendnet TEW-424UB wireless adapter to work on my IBM T40 laptop. I installed ndiswrapper and the Windows 2000 driver per the instructions here: [http://ubuntuforums.org/showthread.php?t=529090](http://ubuntuforums.org/showthread.php?t=529090)  I checked ndiswrapper -l and the driver is installed. The device is visible with the lsusb command. The problem I have is when I run sudo modprobe ndiswrapper, the system hangs. When I do this, the light on the adapter comes on, but the system immediately hangs. On hard reboot, the device light does not come on and it does not load in network manager. I tried blacklisting free drivers per the instructions here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Disable%20Free%20Drivers](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Disable%20Free%20Drivers)  But no luck.

I am also running an internal wireless card on the laptop, which is based on the Atheros chipset. This internal card works fine and I would like to keep it enabled. I don't know if this is causing the conflict or not. Any ideas?

Thanks.

---

