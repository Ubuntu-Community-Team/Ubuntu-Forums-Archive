---
title: "PCI Express Card Reader not mounting"
date: 2013-03-19
forum: Hardware
---

### Post by ShadWolf on 2013-03-19
I'm having problem with the PCI Express Card Reader not working properly on Ubuntu, I inserted a SD Card into the slot and it doesn't mount, I tried removing and inserting over and over with nothing working, so I take a look over at Terminal to see what's up and I get this

sudo lspci -G
```
Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
```

Checked output with lsusb

```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching HubBus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 5986:0510 Acer, Inc 
Bus 001 Device 004: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 002 Device 005: ID 04d9:1133 Holtek Semiconductor, Inc. 

```

and also checked with dmesg

dmesg | tail

```
[509974.867988] usb 2-1.2: USB disconnect, device number 4
[515288.372101] UDP: bad checksum. From 94.66.223.65:56542 to 192.168.1.71:19116 ulen 38
[518005.163587] usb 2-1.2: new low-speed USB device number 5 using ehci_hcd
[518005.263947] usb 2-1.2: New USB device found, idVendor=04d9, idProduct=1133
[518005.263959] usb 2-1.2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[518005.272053] input: HID 04d9:1133 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input15
[518005.272481] hid-generic 0003:04D9:1133.0002: input,hidraw0: USB HID v1.10 Mouse [HID 04d9:1133] on usb-0000:00:1d.0-1.2/input0
[614051.912457] mmc0: error -110 whilst initialising SD card
[614053.207044] mmc0: error -110 whilst initialising SD card
[614054.405742] mmc0: error -110 whilst initialising SD card 

```

From inserting and removing SD Card.

It appears to have a problem initialising the SD Card with the mmc0 block. I've tried searching up the error, but I couldn't get any answers I was looking for. I tried reboots to see if it would fix, but the problem persists, so I figure this could be a bug in the driver or something, because before it was working perfectly fine, til suddenly this happens unexpectedly for no reason.


is there a way to fix the kernel module or something or atleast re-initialise the PCI Express Card Reader to make it work properly again?

---

### Post by ShadWolf on 2013-03-20
bump

---

### Post by ShadWolf on 2013-03-21
Bump

Looking to get help on fixing this, anybody with suggestions on what to do to fix this?
I've tried redownloading the drivers for linux from Realtek but I've had no luck with that there, when I try getting to make the install I just get a bunch of errors while trying to install it. –– I can't seem to initialise the PCI Express Card Reader through modprobe because it thinks the module doesn't exist for some reason.

---

### Post by ShadWolf on 2013-03-27
bump


No solutions to be able to fix this?

---

### Post by ShadWolf on 2013-03-30
bump again for the 3rd time....


still no answers? :/

---

### Post by ShadWolf on 2013-04-02
Kinda disappointed that nobody's replies with an answer solution to this problem. :/

---

### Post by ShadWolf on 2013-04-04
Final bump on this thread before I go to another forum site who can actually help answer this problem.

---

### Post by marcnarc on 2013-07-11
Hello ShadWolf,

I am having this exact same problem.  Unfortunately I have no solution.  :(

I did find this [Arch Linux thread]("https://bbs.archlinux.org/viewtopic.php?pid=1251408") that refers to[ Realtek's RTS5209 Linux driver]("http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false#2").

I downloaded the driver and tried to compile it, but had no luck (and I'm not about to go spelunking through the code to figure this out):

```
# make
cp -f ./define.release ./define.h
make -C /lib/modules/3.8.0-25-generic/build/ SUBDIRS=/home/marcnarc/temp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229 modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-25-generic'
  CC [M]  /home/marcnarc/temp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.o
/home/marcnarc/temp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:914:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtsx_probe’
/home/marcnarc/temp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:1069:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtsx_remove’
/home/marcnarc/temp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:1094:11: error: ‘rtsx_probe’ undeclared here (not in a function)
/home/marcnarc/temp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:1095:2: error: implicit declaration of function ‘__devexit_p’ [-Werror=implicit-function-declaration]
/home/marcnarc/temp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:1095:24: error: ‘rtsx_remove’ undeclared here (not in a function)
/home/marcnarc/temp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:262:34: warning: ‘rtsx_host_template’ defined but not used [-Wunused-variable]
/home/marcnarc/temp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:476:12: warning: ‘rtsx_control_thread’ defined but not used [-Wunused-function]
/home/marcnarc/temp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:585:12: warning: ‘rtsx_polling_thread’ defined but not used [-Wunused-function]
/home/marcnarc/temp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:739:13: warning: ‘quiesce_and_remove_host’ defined but not used [-Wunused-function]
/home/marcnarc/temp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:775:13: warning: ‘release_everything’ defined but not used [-Wunused-function]
/home/marcnarc/temp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:785:12: warning: ‘rtsx_scan_thread’ defined but not used [-Wunused-function]
/home/marcnarc/temp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:810:13: warning: ‘rtsx_init_options’ defined but not used [-Wunused-function]
cc1: some warnings being treated as errors
make[2]: *** [/home/marcnarc/temp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.o] Error 1
make[1]: *** [_module_/home/marcnarc/temp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-25-generic'
make: *** [default] Error 2

```

You'd think that since this reader is in [several Ubuntu-certified systems]("http://www.ubuntu.com/certification/catalog/component/pci/10ec:5209/") that it might actually work.  Sigh.

---

