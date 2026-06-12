---
title: "WUSB600Nv2 Wireless Help!!!!"
date: 2010-11-10
forum: Hardware
---

### Post by qbanito on 2010-11-10
Hello, well I am a novice in Linux OS, I have a wireless card, it's a Linksys WUSB600N but it doesn't work in Ubuntu 10.10 Desktop Edition, which it is the one I have, 64 bits machine, so I read this [https://help.ubuntu.com/community/WifiDocs/Device/Linksys%20WUSB600N](https://help.ubuntu.com/community/WifiDocs/Device/Linksys%20WUSB600N) and I did all the steps,
I downloaded 2010_0915_RT3572_Linux_STA_v2.4.0.2.tar
 but in the last part, sudo make install I got this error 

alain@alain:~/t/2010_0915_RT3572_Linux_STA_v2.4.0.2$ sudo make install
make -C /home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3572sta.ko /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/
install: cannot stat `rt3572sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux'
make: *** [install] Error 2


and in the make part, i cut the whole code:

usb.c:34: note: expected â€˜VOID **â€™ but argument is of type â€˜struct __HTTX_BUFFER **â€™
/home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of â€˜RTMPAllocUsbBulkBufStructâ€™ from incompatible pointer type
/home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected â€˜VOID **â€™ but argument is of type â€˜struct __TX_BUFFER **â€™
/home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of â€˜RTMPAllocUsbBulkBufStructâ€™ from incompatible pointer type
/home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected â€˜VOID **â€™ but argument is of type â€˜struct __TX_BUFFER **â€™
/home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of â€˜RTMPAllocUsbBulkBufStructâ€™ from incompatible pointer type
/home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected â€˜VOID **â€™ but argument is of type â€˜UCHAR **â€™
make[2]: *** [/home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2

so i have no way to get connected to the internet, what is that error cannot stat `rt3572sta.ko': No such file or directory, I think thats why i can make the wireless card work. 
I just dont know what to do :(

Thank you

---

### Post by mod-u-lar on 2010-11-24
I have a similar problem, stuck at the compilation step. I have checked the the makefile and all paths to headers and sources are available. Really no idea what's missing and any help would be appreciated.

The only difference from the tutorials is the version of the driver on the Ralink website, but it's auto-download so I can't check if an older version would work.

```
xbmc@MediaPortal:~/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2$ make
make -C tools
make[1]: Entering directory `/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools'
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools/bin2h
cp -f os/linux/Makefile.6 /home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/Makefile
make -C /lib/modules/2.6.35-23-generic/build SUBDIRS=/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
  CC [M]  /home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocUsbBulkBufStruct’:
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function ‘usb_buffer_alloc’
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:52: warning: assignment makes pointer from integer without a cast
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeUsbBulkBufStruct’:
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:78: error: implicit declaration of function ‘usb_buffer_free’
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:234: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:241: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:278: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
make[2]: *** [/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/xbmc/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make: *** [LINUX] Error 2
```

---

### Post by mod-u-lar on 2010-11-26
Apparantly there is a problem with compiling the Ralink driver against kernel 2.6.35.22 and 2.6.35.23. Not sure if it's the driver or the kernel.

See also post 60 & 61 of the following thread [http://www.linuxquestions.org/questions/linux-wireless-networking-41/linksys-wusb600n-driver-and-dlink-dwl-ag132-driver-622449/page4.html](http://www.linuxquestions.org/questions/linux-wireless-networking-41/linksys-wusb600n-driver-and-dlink-dwl-ag132-driver-622449/page4.html)

Anyone knows where to report? Can't revert to 10.04 because of regular system freezes which I have not experienced in 10.10.

---

