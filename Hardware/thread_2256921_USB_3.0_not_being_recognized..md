---
title: "USB 3.0 not being recognized."
date: 2014-12-15
forum: Hardware
---

### Post by gothrog on 2014-12-15
Hi All,

I'm working with a Sony FCB-MA130 camera.  It is a USB 3.0.  I've looked on the forums already and have run a set of commands.  I have listed the update below.  The camera seems to run with Android, but I have not been able to get it to recognize the camera on Ubuntu and I believe it is the USB 3.0 not being recognized.  This is a 32 bit armv7l.

```
mike@linaro-gnome:~$ uname -a
Linux linaro-gnome 3.4.0-g58e4014-00018-gfd56be5 #1 SMP PREEMPT Thu Oct 9 13:01:53 IST 2014 armv7l armv7l armv7l GNU/Linux

```
The device that appears and disappears when I unplug the USB is usbdev1.7.  However every time I unplug the USB it increments up the 1.X.
Example:  Was usbdev1.3 ... usbdev1.X

```
mike@linaro-gnome:~$ ls /dev/usb*
/dev/usb_accessory  /dev/usbdev1.1  /dev/usbdev1.7  /dev/usbdev2.1  /dev/usbmon0  /dev/usbmon1  /dev/usbmon2

```

In this code below you will see that their is no recognized root hub for USB 3.0.  Am I correct and is Ubuntu not recognizing it as a USB 3.0?  How do I get a USB 3.0 to be recognized on the device?  Does this require a kernel change or can I do something else?

The 007 device is supposed to be the USB 3.0 device and if I use the -v I can see it carrying information for a Video Camera.

```
mike@linaro-gnome:~$ sudo lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 2588:1d05
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mike@linaro-gnome:~$ sudo lsusb -s 007
Bus 001 Device 007: ID 2588:1d05

```


```
mike@linaro-gnome:~$ usb-devices


T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 1
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.04
S:  Manufacturer=Linux 3.4.0-g58e4014-00018-gfd56be5 ehci_hcd
S:  Product=Qualcomm EHCI Host Controller
S:  SerialNumber=msm_ehci_host.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.10 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=2588 ProdID=1d05 Rev=00.01
S:  Manufacturer=Infinitegra, Inc.
S:  Product=Infinitegra SW: This software has a time limitation.
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=200mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=(none)


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 1
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.04
S:  Manufacturer=Linux 3.4.0-g58e4014-00018-gfd56be5 ehci_hcd
S:  Product=Qualcomm EHCI Host Controller
S:  SerialNumber=msm_ehci_host.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub



```

---

### Post by mörgæs on 2014-12-16
> **gothrog said:**
> Does this require a kernel change or can I do something else?

Could be. Do you get the same results in a live boot of 14.10?

---

