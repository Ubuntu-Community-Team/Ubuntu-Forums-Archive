---
title: "ov518 webcam"
date: 2006-01-20
forum: Hardware &amp; Laptops
---

### Post by Virogenesis on 2006-01-20
I'm having problems with setting up my ov518 webcam.
I've used easycam to get it running in the past and well i've tried that but it won't get pass the gui so I've gone about manually doing it.

I've searched the forum and came across a user who has managed to get it working I've followed his guide but still no joy.

```
vir@Trouble:~/Desktop/ov511-2.30$ CC=gcc-3.4
vir@Trouble:~/Desktop/ov511-2.30$ export CC
vir@Trouble:~/Desktop/ov511-2.30$ sudo make
    Building OVCam drivers for 2.6 kernel.
    PLEASE IGNORE THE "Overriding SUBDIRS" WARNING
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/vir/Desktop/ov511-2.30 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/vir/Desktop/ov511-2.30/ov511_core.o
  CC [M]  /home/vir/Desktop/ov511-2.30/ov511_decomp.o
  CC [M]  /home/vir/Desktop/ov511-2.30/ov518_decomp.o
  CC [M]  /home/vir/Desktop/ov511-2.30/ovcamchip_core.o
  CC [M]  /home/vir/Desktop/ov511-2.30/ov6x20.o
  CC [M]  /home/vir/Desktop/ov511-2.30/ov6x30.o
  CC [M]  /home/vir/Desktop/ov511-2.30/ov7x10.o
  CC [M]  /home/vir/Desktop/ov511-2.30/ov7x20.o
  CC [M]  /home/vir/Desktop/ov511-2.30/ov76be.o
  LD [M]  /home/vir/Desktop/ov511-2.30/ovcamchip.o
  LD [M]  /home/vir/Desktop/ov511-2.30/ov511.o
  CC [M]  /home/vir/Desktop/ov511-2.30/ovfx2.o
  CC [M]  /home/vir/Desktop/ov511-2.30/saa7111-new.o
  CC [M]  /home/vir/Desktop/ov511-2.30/tuner.o
  CC [M]  /home/vir/Desktop/ov511-2.30/tda7313.o
  Building modules, stage 2.
  MODPOST
  CC      /home/vir/Desktop/ov511-2.30/ov511.mod.o
  LD [M]  /home/vir/Desktop/ov511-2.30/ov511.ko
  CC      /home/vir/Desktop/ov511-2.30/ovcamchip.mod.o
  LD [M]  /home/vir/Desktop/ov511-2.30/ovcamchip.ko
  CC      /home/vir/Desktop/ov511-2.30/ovfx2.mod.o
  LD [M]  /home/vir/Desktop/ov511-2.30/ovfx2.ko
  CC      /home/vir/Desktop/ov511-2.30/saa7111-new.mod.o
  LD [M]  /home/vir/Desktop/ov511-2.30/saa7111-new.ko
  CC      /home/vir/Desktop/ov511-2.30/tda7313.mod.o
  LD [M]  /home/vir/Desktop/ov511-2.30/tda7313.ko
  CC      /home/vir/Desktop/ov511-2.30/tuner.mod.o
  LD [M]  /home/vir/Desktop/ov511-2.30/tuner.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
vir@Trouble:~/Desktop/ov511-2.30$ sudo modprobe -r ov511
vir@Trouble:~/Desktop/ov511-2.30$ sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/ov51*
vir@Trouble:~/Desktop/ov511-2.30$ sudo make install
./do_install.sh *.ko
Detected 2.6 kernel
Creating install path: /lib/modules/2.6.12-9-386/kernel/drivers/usb/media/
Installing ov511.ko to /lib/modules/2.6.12-9-386/kernel/drivers/usb/media/
Installing ovcamchip.ko to /lib/modules/2.6.12-9-386/kernel/drivers/usb/media/
Installing ovfx2.ko to /lib/modules/2.6.12-9-386/kernel/drivers/usb/media/
Installing saa7111-new.ko to /lib/modules/2.6.12-9-386/kernel/drivers/usb/media/
Installing tda7313.ko to /lib/modules/2.6.12-9-386/kernel/drivers/usb/media/
Installing tuner.ko to /lib/modules/2.6.12-9-386/kernel/drivers/usb/media/
Finding module dependencies
All done!
vir@Trouble:~/Desktop/ov511-2.30$ sudo modprobe ov511
vir@Trouble:~/Desktop/ov511-2.30$ sudo modprobe ov518_decomp
FATAL: Module ov518_decomp not found.

vir@Trouble:~/Desktop/ov511-2.30$ dmesg | grep ov5
[4294719.000000] drivers/usb/media/ov511.c: USB OV518 video device found
[4294719.002000] drivers/usb/media/ov511.c: Device revision 9
[4294719.038000] drivers/usb/media/ov511.c: Compression required with OV518...enabling
[4294720.656000] drivers/usb/media/ov511.c: Sensor is an OV6630AE
[4294721.269000] drivers/usb/media/ov511.c: Device at usb-0000:00:02.0-1 registered to minor 0
[4294721.269000] usbcore: registered new driver ov511
[4294721.269000] drivers/usb/media/ov511.c: v1.64 for Linux 2.5 : ov511 USB Camera Driver
[4304886.324000] drivers/usb/media/ov511.c: USB OV518 video device found
[4304886.326000] drivers/usb/media/ov511.c: Device revision 9
[4304886.362000] drivers/usb/media/ov511.c: Compression required with OV518...enabling
[4304887.992000] drivers/usb/media/ov511.c: Sensor is an OV6630AE
[4304888.605000] drivers/usb/media/ov511.c: Device at usb-0000:00:02.0-1 registered to minor 0
[4315285.942000] drivers/usb/media/ov511.c: No decompressor available
[4316302.304000] usbcore: deregistering driver ov511
[4316302.345000] drivers/usb/media/ov511.c: driver deregistered
[4316373.078000] /home/vir/Desktop/ov511-2.30/ov511_core.c: USB OV518 video device found
[4316373.082000] /home/vir/Desktop/ov511-2.30/ov511_core.c: Device revision 9
[4316373.116000] /home/vir/Desktop/ov511-2.30/ov511_core.c: Compression required with OV518...enabling
[4316373.285000] /home/vir/Desktop/ov511-2.30/ov511_core.c: Device at usb-0000:00:02.0-1 registered to minor 0
[4316373.285000] usbcore: registered new driver ov511
[4316373.285000] /home/vir/Desktop/ov511-2.30/ov511_core.c: v2.30 : ov511 USB Camera Driver (V4L2 disabled)
[4316407.277000] /home/vir/Desktop/ov511-2.30/ov511_core.c: No sensor is detected yet

```

heres the url [http://www.linuxquestions.org/questions/showthread.php?s=&threadid=344887]("http://www.linuxquestions.org/questions/showthread.php?s=&threadid=344887")

Thank you for your time hope you can help

---

### Post by pgatrick on 2006-09-29
I'm having the same problem. I had it working (kinda) before on ubuntu 5, but now I've forgotten how.. I think I've done it the exact same way, just won't work.

---

### Post by blink on 2006-10-17
If you're getting the message "No sensor is detected yet", you
might check if the module "ovcamchip" is loaded. It does the legwork to determine your sensor and may not get autoloaded when the ov511 module gets loaded.

In short to try:

```

modprobe -r ov511
modprobe ovcamchip
modprobe ov511

```

good luck!
bk

---

