---
title: "D-Link DWA-131 usb dongle doesn't work in Ubuntu Server 12.04.2"
date: 2013-06-11
forum: Hardware
---

### Post by ikerdobarro on 2013-06-11
I know that there are many threads related with these D-Link dongles with Realtek chips, but no one has solved my problem. I have this dongle in a Pentium 4 with Ubuntu Server 12.04.2 installed (lshhw output attached):

```
Linux cacharro 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:15:33 UTC 2013 i686 i686 i386 GNU/Linux
```

The specific dongle is:

```
Bus 004 Device 002: ID 0bda:8192 Realtek Semiconductor Corp. RTL8192U 802.11n Wireless Adapter
```

As you can see, the ID isn't the 07D1:3303 usual in threads mentioned above. It's some strange because in the Debian Wiki web this one is supported by r8712u module and corresponds to the rev. A1 which I have as stated in its commercial box, but ubuntu identifies it as ID 0bda:8192, which is supported by r8192u_usb, as stated in Debian Wiki. Whatever it was, the system loads automatically r8712u module and recognizes the dongle and assigns to it wlan0 interface. When I try to set essid and key parameters with iwconfig, either with wlan0 down or up, I can't and the interface remains without changes. The dmesg after extract and reinsert the dongle:

```
[  614.712054] usb 4-1: USB disconnect, device number 2
[  634.736041] hub 4-0:1.0: unable to enumerate USB device on port 1
[  640.956017] usb 4-1: new full-speed USB device number 4 using uhci_hcd
[  641.095046] usb 4-1: not running at top speed; connect to a high speed hub
[  641.118049] usb 4-1: New USB device found, idVendor=0bda, idProduct=8192
[  641.118053] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  641.118057] usb 4-1: Product: 802.11n WLAN Adapter
[  641.118060] usb 4-1: Manufacturer: Realtek
[  641.120186] r8712u: DriverVersion: v7_0.20100831
[  641.120226] r8712u: register rtl8712_netdev_ops to netdev_ops
[  641.120232] r8712u: USB_SPEED_LOW with 6 endpoints
[  641.123051] r8712u: Boot from EFUSE: Autoload Failed
[  641.123058] r8712u: MAC Address from efuse = 00:e0:4c:87:00:00
[  641.123061] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"

```
Thus, I tried with r8192u_usb module, but this module doesn't recognize the dongle neither assign any wireless interface. The dmesg:

```
sudo rmmod -f r8712u
sudo depmod -a
sudo modprobe r8192u_usb
[  824.121694] r8192u_usb: module is from the staging directory, the quality is unknown, you have been warned.
[  824.124050] ieee80211_crypt: registered algorithm 'NULL'
[  824.124057] ieee80211_crypt: registered algorithm 'TKIP'
[  824.124061] ieee80211_crypt: registered algorithm 'CCMP'
[  824.124064] ieee80211_crypt: registered algorithm 'WEP'
[  824.124067] 
[  824.124067] Linux kernel driver for RTL8192 based WLAN cards
[  824.124071] Copyright (c) 2007-2008, Realsil Wlan
[  824.124880] usbcore: registered new interface driver rtl819xU
```

I've tried also to use Realtek's drivers for Linux, but I allways obtained the following error when compiling: 

```
iker@cacharro:~/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405$ sudo make clean 

rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~ 
rm .tmp_versions -fr ; rm Module.symvers -fr 
cd cmd ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko  
cd crypto ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko  
cd debug ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko  
cd eeprom ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko  
cd hal/rtl8712 ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko  
cd io ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko  
cd ioctl ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko  
cd led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko  
cd mlme ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko  
cd mp ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko  
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko  
cd os_intf ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko  
cd os_intf/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko  
cd pwrctrl ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko  
cd recv ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko  
cd rf ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko  
cd sta_mgt ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko  
cd xmit; rm -fr *.mod.c *.mod *.o .*.cmd *.ko  
cd efuse; rm -fr *.mod.c *.mod *.o .*.cmd *.ko  

iker@cacharro:~/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405$ sudo make 

make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.5.0-23-generic/build M=/home/iker/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405  modules 
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-23-generic' 
  CC [M]  /home/iker/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o 
In file included from /home/iker/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:70:0, 
                 from /home/iker/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24: 
/home/iker/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_cmd.h:107:25: error: field ‘event_tasklet’ has incomplete type 
In file included from /home/iker/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:72:0, 
                 from /home/iker/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24: 
/home/iker/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_xmit.h:355:24: error: field ‘xmit_tasklet’ has incomplete type 
In file included from /home/iker/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:73:0, 
                 from /home/iker/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24: 
/home/iker/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_recv.h:205:24: error: field ‘recv_tasklet’ has incomplete type 
make[2]: *** [/home/iker/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o] Error 1 
make[1]: *** [_module_/home/iker/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-23-generic' 
make: *** [modules] Error 2 

```

Also with ndiswrapper and all the drivers in the dongle's CD and Realtek's web for Windows (XP,2K, 7, etc). Any idea? Thank you very much in advance.

---

### Post by Yellow Pasque on 2013-06-11
> usb 4-1: not running at top speed; connect to a high speed hub

Have you tried different USB ports?

Check lsusb to see which USB ports are 2.0:
```
sudo update-usbids
lsusb
```

---

### Post by ikerdobarro on 2013-06-11
Yes, I've tried in all the USB ports but nothing. Here you have them:

Bus 001 Device 002: ID 0424:223a Standard Microsystems Corp. 8-in-1 Card Reader
Bus 004 Device 002: ID 0bda:8192 Realtek Semiconductor Corp. RTL8192U 802.11n Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I can't update-usbsids because this machine isn't net-connected. Another thing I forgot to say is that the light of the dongle is off, but I've tried to make an ad-hoc connection with iwconfig and with that mode I could set essid and dongle started to blink but I could't ssh to it; later I found in the dongle manual that it doesn't support ad-hoc connections. Many weird things.

---

### Post by Yellow Pasque on 2013-06-11
Are there any USB settings in your BIOS that could make all those 1.1 ports 2.0?

---

### Post by ikerdobarro on 2013-06-12
Finally I downladed in other computer yesterday the usb.ids.gz file and decompressed into /var/lib/usbutils, reboot and nothing. Yes, the BIOS has 3 USB confs, USB support, USB 2.0 support and legacy support. I've tried enable and disabled every support with all possible conbinations but nothing, all remains the same, except with USB support disabled, which dissable the other two supports and doesn't allow the machine to detect USB hubs.

Thanks a lot for all your help, Temüjín

---

### Post by Yellow Pasque on 2013-06-12
Sorry I couldn't be of more help. The only other thing I could think of is trying a newer kernel, or just the wireless backports: [https://launchpad.net/ubuntu/precise/i386/linux-backports-modules-cw-3.8-precise-generic-pae](https://launchpad.net/ubuntu/precise/i386/linux-backports-modules-cw-3.8-precise-generic-pae)

---

### Post by ikerdobarro on 2013-06-14
It does the matter, Temüjin, thanks for your interest. I finally installed the backports with kernel 3.2.0-48.36-generic-pae and nothing.

---

