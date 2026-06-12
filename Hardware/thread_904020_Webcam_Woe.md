---
title: "Webcam Woe"
date: 2008-08-28
forum: Hardware
---

### Post by victor9098 on 2008-08-28
Hi All,

I have just installed ubuntu onto an Advent 4211 but I seem to be having webcam problems. Ekiga & Skype detect it, even using lsusb lists it but I can not get a picture and Ekiga reports a fault.

Any advice?

lsusb output:
Bus 005 Device 013: ID 5986:0203 Bison 
Bus 005 Device 005: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c402 Logitech, Inc. Marble Mouse (2-button)
Bus 001 Device 001: ID 0000:0000  

lspci output:
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Unknown device 8199 (rev 22)

---

### Post by Crafty Kisses on 2008-08-28
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by victor9098 on 2008-08-28
Thanks for the reply,

I just get the bouncing logo. I have tried different combinations (static picture / video / v4l / v4l2) but not getting anything.

---

### Post by IntuitiveNipple on 2008-08-29
Assuming the device is present at **/dev/video** this command should give some clues as to which kernel driver is in use, and from that there may be kernel-module options that will help get the camera working correctly.

Please report the output of:
```

udevinfo --query=all --name=/dev/video0 --attribute-walk

```

---

