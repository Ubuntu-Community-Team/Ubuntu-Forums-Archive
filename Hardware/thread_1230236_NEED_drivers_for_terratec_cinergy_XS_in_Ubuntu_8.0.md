---
title: "NEED drivers for terratec cinergy XS in Ubuntu 8.04"
date: 2009-08-03
forum: Hardware
---

### Post by stefboombastic on 2009-08-03
Hi all!
 Some time ago I managed to make my terratec Cinergy XS work fine with Kaffeine by using Mcentral drivers ( [http://mcentral.de/wiki/index.php5/Main_Page](http://mcentral.de/wiki/index.php5/Main_Page) ).
Unluckily I had to format my Hard Disk, and when installed again my Ubuntu I found out that the project was discontinued and I can't download the drivers anymore :( and when I begged the developer for old drivers, he posted this:

	@echo the em28xx-new driver project has been discontinued, in order to provide 
	@echo optimal Linux support you can have a look at [http://shop.sundtek.de](http://shop.sundtek.de) 
	@echo for fully supported Linux based TV devices.
	@echo ""
	@echo Support for Sundtek devices is provided at [http://support.sundtek.de](http://support.sundtek.de)
	@echo ""

So am I supposed to buy a new card for Ubuntu when ALL Windows versions from Win98 to Windows7 work fine with my device???
Is there anybody who can kindly send me the old drivers?
THANK YOU VERY VERY VERY MUCH in advance!

P.S. Video for linux does not support my device: 
[http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_USB_XS](http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_USB_XS)

---

### Post by LubosD on 2009-09-05
Hello, I've uploaded the driver for you: [http://www.dolezel.info/download/em28xx-new.tar.bz2](http://www.dolezel.info/download/em28xx-new.tar.bz2)

It has a patch for Linux 2.6.30 applied. If you're using an older version, unapply the included patch (fix-2.6.30.patch).

---

### Post by stefboombastic on 2009-09-06
Thank You very much!
 How to unapply the patch?
I tried simply to rename the patch file befor running make, but I've got only errors running the make, both in Ubuntu 8.04 (last update) and Ubuntu 9.04 (last updates)
I post here the results of the make:

```
stefano@stefano-VPC:~/em28xx-new$ sudo make

running ./build.sh build

make[1]: ingresso nella directory «/home/stefano/em28xx-new»
rm -rf Module.symvers; 
make -C /lib/modules/`if [ -d /lib/modules/2.6.21.4-eeepc ]; then echo 2.6.21.4-eeepc; else uname -r; fi`/build SUBDIRS=`pwd` modules
make[2]: ingresso nella directory «/usr/src/linux-headers-2.6.28-15-generic»
  CC [M]  /home/stefano/em28xx-new/em2880-dvb.o
/home/stefano/em28xx-new/em2880-dvb.c:149: warning: missing initializer
/home/stefano/em28xx-new/em2880-dvb.c:149: warning: (near initialization for ‘DRX3973DData_g.currentChannel.frequency’)
/home/stefano/em28xx-new/em2880-dvb.c:159: warning: missing initializer
/home/stefano/em28xx-new/em2880-dvb.c:159: warning: (near initialization for ‘DRX3973DData_g.channelCache’)
/home/stefano/em28xx-new/em2880-dvb.c: In function ‘mt352_pinnacle_init’:
/home/stefano/em28xx-new/em2880-dvb.c:584: warning: missing initializer
/home/stefano/em28xx-new/em2880-dvb.c:584: warning: (near initialization for ‘zlconf[23].reg’)
  CC [M]  /home/stefano/em28xx-new/em28xx-video.o
/home/stefano/em28xx-new/em28xx-video.c: In function ‘em28xx_v4l2_ioctl’:
/home/stefano/em28xx-new/em28xx-video.c:2920: warning: passing argument 5 of ‘video_usercopy’ from incompatible pointer type
/home/stefano/em28xx-new/em28xx-video.c: At top level:
/home/stefano/em28xx-new/em28xx-video.c:2947: error: variable ‘em28xx_v4l_fops’ has initializer but incomplete type
/home/stefano/em28xx-new/em28xx-video.c:2948: error: unknown field ‘owner’ specified in initializer
/home/stefano/em28xx-new/em28xx-video.c:2948: warning: excess elements in struct initializer
/home/stefano/em28xx-new/em28xx-video.c:2948: warning: (near initialization for ‘em28xx_v4l_fops’)
/home/stefano/em28xx-new/em28xx-video.c:2949: error: unknown field ‘open’ specified in initializer
/home/stefano/em28xx-new/em28xx-video.c:2949: warning: excess elements in struct initializer
/home/stefano/em28xx-new/em28xx-video.c:2949: warning: (near initialization for ‘em28xx_v4l_fops’)
/home/stefano/em28xx-new/em28xx-video.c:2950: error: unknown field ‘release’ specified in initializer
/home/stefano/em28xx-new/em28xx-video.c:2950: warning: excess elements in struct initializer
/home/stefano/em28xx-new/em28xx-video.c:2950: warning: (near initialization for ‘em28xx_v4l_fops’)
/home/stefano/em28xx-new/em28xx-video.c:2951: error: unknown field ‘ioctl’ specified in initializer
/home/stefano/em28xx-new/em28xx-video.c:2951: warning: excess elements in struct initializer
/home/stefano/em28xx-new/em28xx-video.c:2951: warning: (near initialization for ‘em28xx_v4l_fops’)
/home/stefano/em28xx-new/em28xx-video.c:2952: error: unknown field ‘read’ specified in initializer
/home/stefano/em28xx-new/em28xx-video.c:2952: warning: excess elements in struct initializer
/home/stefano/em28xx-new/em28xx-video.c:2952: warning: (near initialization for ‘em28xx_v4l_fops’)
/home/stefano/em28xx-new/em28xx-video.c:2953: error: unknown field ‘poll’ specified in initializer
/home/stefano/em28xx-new/em28xx-video.c:2953: warning: excess elements in struct initializer
/home/stefano/em28xx-new/em28xx-video.c:2953: warning: (near initialization for ‘em28xx_v4l_fops’)
/home/stefano/em28xx-new/em28xx-video.c:2954: error: unknown field ‘mmap’ specified in initializer
/home/stefano/em28xx-new/em28xx-video.c:2954: warning: excess elements in struct initializer
/home/stefano/em28xx-new/em28xx-video.c:2954: warning: (near initialization for ‘em28xx_v4l_fops’)
/home/stefano/em28xx-new/em28xx-video.c: In function ‘em28xx_init_dev’:
/home/stefano/em28xx-new/em28xx-video.c:3217: warning: assignment from incompatible pointer type
/home/stefano/em28xx-new/em28xx-video.c:3304: warning: assignment from incompatible pointer type
/home/stefano/em28xx-new/em28xx-video.c:3343: warning: assignment from incompatible pointer type
make[3]: *** [/home/stefano/em28xx-new/em28xx-video.o] Errore 1
make[2]: *** [_module_/home/stefano/em28xx-new] Errore 2
make[2]: uscita dalla directory «/usr/src/linux-headers-2.6.28-15-generic»
make[1]: *** [default] Errore 2
make[1]: uscita dalla directory «/home/stefano/em28xx-new»

```

I tried with fresh installations of Ubuntu though with last updates, and I've installed kernel headers and G++ before running the make.
Any idea?

Thank You in adavnce!
Stefano B.

---

### Post by LubosD on 2009-09-06
```
patch -p1 -R < fix-2.6.30.patch
```
(I'm not an Ubuntu user, so I can't tell you what will and what will not work for you.)

---

### Post by stefboombastic on 2009-09-07
Thank You so much!!!
That worked perfectly after unapplying the patch, both in Ubuntu 8.04 and Ubuntu 9.04 (tested with VMWare)!
If You agree I will link the drivers and the procedure I used for installing them in Ubuntu here:
[http://ubuntuforums.org/showthread.php?p=7752781#post7752781](http://ubuntuforums.org/showthread.php?p=7752781#post7752781)
where I had already posted another solution for making the cinergy XS work in Ubuntu!
By the way is the link with drivers disappearing soon or not?
Thank You again,
best regards,
Stefano B.

---

### Post by LubosD on 2009-09-07
You're absolutely welcome and free to post links to it anywhere. 
The file doesn't contain anything illegal, so unless something unusual happens (such as me cleaning up mess and accidentally taking down useful stuff too), I'm not planning on removing it.

---

### Post by maxter on 2009-09-17
hi LubosD,

i tried your drivers with jaunty with kernel 2.6.28-15-generic;
after reboot, inserting the key gives me only these errors:

Sep 17 13:25:44 max-desktop kernel: [  299.084025] usb 1-7: new high speed USB device using ehci_hcd and address 5
Sep 17 13:25:44 max-desktop kernel: [  299.224431] usb 1-7: configuration #1 chosen from 1 choice
Sep 17 13:25:45 max-desktop kernel: [  299.274348] em28xx: Unknown symbol v4l_compat_translate_ioctl
Sep 17 13:25:45 max-desktop kernel: [  299.274545] em28xx: Unknown symbol v4l2_video_std_construct
Sep 17 13:25:45 max-desktop kernel: [  299.274977] em28xx: Unknown symbol v4l2_type_names
Sep 17 13:25:45 max-desktop kernel: [  299.275161] em28xx: Unknown symbol v4l_printk_ioctl
Sep 17 13:25:45 max-desktop kernel: [  299.275687] em28xx: Unknown symbol video_unregister_device
Sep 17 13:25:45 max-desktop kernel: [  299.275870] em28xx: Unknown symbol video_device_alloc
Sep 17 13:25:45 max-desktop kernel: [  299.275963] em28xx: Unknown symbol video_register_device
Sep 17 13:25:45 max-desktop kernel: [  299.276494] em28xx: Unknown symbol video_usercopy
Sep 17 13:25:45 max-desktop kernel: [  299.276590] em28xx: Unknown symbol video_device_release
Sep 17 13:27:22 max-desktop kernel: [  396.859245] em28xx: Unknown symbol v4l_compat_translate_ioctl
Sep 17 13:27:22 max-desktop kernel: [  396.859463] em28xx: Unknown symbol v4l2_video_std_construct
Sep 17 13:27:22 max-desktop kernel: [  396.859898] em28xx: Unknown symbol v4l2_type_names
Sep 17 13:27:22 max-desktop kernel: [  396.860090] em28xx: Unknown symbol v4l_printk_ioctl
Sep 17 13:27:22 max-desktop kernel: [  396.860616] em28xx: Unknown symbol video_unregister_device
Sep 17 13:27:22 max-desktop kernel: [  396.860797] em28xx: Unknown symbol video_device_alloc
Sep 17 13:27:22 max-desktop kernel: [  396.860889] em28xx: Unknown symbol video_register_device
Sep 17 13:27:22 max-desktop kernel: [  396.861672] em28xx: Unknown symbol video_usercopy
Sep 17 13:27:22 max-desktop kernel: [  396.861837] em28xx: Unknown symbol video_device_release


during compilation i obtained the following errors:

make[2]: ingresso nella directory «/usr/src/linux-headers-2.6.28-15-generic»
  CC [M]  /home/max/em28xx-new/em2880-dvb.o
/home/max/em28xx-new/em2880-dvb.c:149: warning: missing initializer
/home/max/em28xx-new/em2880-dvb.c:149: warning: (near initialization for ‘DRX3973DData_g.currentChannel.frequency’)
/home/max/em28xx-new/em2880-dvb.c:159: warning: missing initializer
/home/max/em28xx-new/em2880-dvb.c:159: warning: (near initialization for ‘DRX3973DData_g.channelCache’)
/home/max/em28xx-new/em2880-dvb.c: In function ‘mt352_pinnacle_init’:
/home/max/em28xx-new/em2880-dvb.c:584: warning: missing initializer
/home/max/em28xx-new/em2880-dvb.c:584: warning: (near initialization for ‘zlconf[23].reg’)
  CC [M]  /home/max/em28xx-new/em28xx-video.o
  CC [M]  /home/max/em28xx-new/em28xx-i2c.o
/home/max/em28xx-new/em28xx-i2c.c:681: warning: ‘inc_use’ defined but not used
/home/max/em28xx-new/em28xx-i2c.c:688: warning: ‘dec_use’ defined but not used
  CC [M]  /home/max/em28xx-new/em28xx-cards.o
/home/max/em28xx-new/em28xx-cards.c:2842: warning: missing initializer
/home/max/em28xx-new/em28xx-cards.c:2842: warning: (near initialization for ‘em28xx_id_table[67].match_flags’)
  CC [M]  /home/max/em28xx-new/em28xx-core.o
  CC [M]  /home/max/em28xx-new/em28xx-input.o
  CC [M]  /home/max/em28xx-new/em28xx-webcam.o
  CC [M]  /home/max/em28xx-new/em28xx-keymaps.o
  LD [M]  /home/max/em28xx-new/em28xx.o
  CC [M]  /home/max/em28xx-new/em28xx-aad.o
/home/max/em28xx-new/em28xx-aad.c: In function ‘em28xx_aad_register’:
/home/max/em28xx-new/em28xx-aad.c:358: warning: format not a string literal and no format arguments
  CC [M]  /home/max/em28xx-new/em28xx-audio.o
  CC [M]  /home/max/em28xx-new/em28xx-audioep.o
/home/max/em28xx-new/em28xx-audioep.c:42: warning: missing initializer
/home/max/em28xx-new/em28xx-audioep.c:42: warning: (near initialization for ‘em28xx_audio_id_table[7].match_flags’)
  LD [M]  /home/max/em28xx-new/em28xx-dvb.o
  CC [M]  /home/max/em28xx-new/adimtv102/adimtv102.o
  CC [M]  /home/max/em28xx-new/cx25843/em28xx-cx25843.o
  CC [M]  /home/max/em28xx-new/drx3973d/drx3973d_demod.o
  CC [M]  /home/max/em28xx-new/drx3973d/drx3973d_core.o
/home/max/em28xx-new/drx3973d/drx3973d_core.c:6059:8: warning: "COMPILE_FOR_QT" is not defined
/home/max/em28xx-new/drx3973d/drx3973d_core.c:6068:7: warning: "COMPILE_FOR_QT" is not defined
/home/max/em28xx-new/drx3973d/drx3973d_core.c:6085:8: warning: "COMPILE_FOR_QT" is not defined
/home/max/em28xx-new/drx3973d/drx3973d_core.c:7726:8: warning: "COMPILE_FOR_QT" is not defined
/home/max/em28xx-new/drx3973d/drx3973d_core.c: In function ‘DRX3973D_Open’:
/home/max/em28xx-new/drx3973d/drx3973d_core.c:7799: warning: enumeration value ‘DRX3973D_SPIN_UNKNOWN’ not handled in switch
/home/max/em28xx-new/drx3973d/drx3973d_core.c:7915:8: warning: "COMPILE_FOR_QT" is not defined
/home/max/em28xx-new/drx3973d/drx3973d_core.c:7927:8: warning: "COMPILE_FOR_QT" is not defined
/home/max/em28xx-new/drx3973d/drx3973d_core.c:7933:8: warning: "COMPILE_FOR_QT" is not defined



any suggestion?

many thanks

Max

---

### Post by stefboombastic on 2009-09-17
Please always report Ubuntu version and precise card version!
Follow this:
[http://ohioloco.ubuntuforums.org/showthread.php?p=7912116](http://ohioloco.ubuntuforums.org/showthread.php?p=7912116)
Or if You are Italian:
[http://forum.ubuntu-it.org/index.php?topic=310711.msg2332058](http://forum.ubuntu-it.org/index.php?topic=310711.msg2332058)

It is my guide on how to install Terratec Cinergy Hybrid T USB XS (non FM) in Ubuntu 9.04. There is also how I did install it by using Mr LobosD drivers step by step ;)

Regards,
Stefano B.

---

### Post by bobbob1016 on 2009-09-17
If your problem was solved, mark the thread as solved.

---

### Post by pIII on 2010-10-10
hi all, has anyone upgraded to maverick? i don't seem to get my cinergy XS to properly work, it shows up via ucview (unicap) but i can't see the image coming in via composite.

even though dmesg shows me a log where everything seems to be good:

> 
[ 3961.315938] em28xx: New device TerraTec Electronic GmbH Cinergy Hybrid T USB XS @ 480 Mbps (0ccd:0042, interface 0, class 0)
[ 3961.316095] em28xx #0: chip ID is em2882/em2883
[ 3961.508304] em28xx #0: i2c eeprom 00: 1a eb 67 95 cd 0c 42 00 50 12 5c 03 6a 32 9c 34
[ 3961.508320] em28xx #0: i2c eeprom 10: 00 00 06 57 46 07 00 00 00 00 00 00 00 00 00 00
[ 3961.508333] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 31 00 b8 00 14 00 5b 00 00 00
[ 3961.508346] em28xx #0: i2c eeprom 30: 00 00 20 40 20 6e 02 20 10 01 00 00 00 00 00 00
[ 3961.508358] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 3961.508370] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 3961.508383] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 32 03 43 00 69 00
[ 3961.508395] em28xx #0: i2c eeprom 70: 6e 00 65 00 72 00 67 00 79 00 20 00 48 00 79 00
[ 3961.508408] em28xx #0: i2c eeprom 80: 62 00 72 00 69 00 64 00 20 00 54 00 20 00 55 00
[ 3961.508420] em28xx #0: i2c eeprom 90: 53 00 42 00 20 00 58 00 53 00 00 00 34 03 54 00
[ 3961.508433] em28xx #0: i2c eeprom a0: 65 00 72 00 72 00 61 00 54 00 65 00 63 00 20 00
[ 3961.508445] em28xx #0: i2c eeprom b0: 45 00 6c 00 65 00 63 00 74 00 72 00 6f 00 6e 00
[ 3961.508457] em28xx #0: i2c eeprom c0: 69 00 63 00 20 00 47 00 6d 00 62 00 48 00 00 00
[ 3961.508470] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 3961.508482] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 3961.508494] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 3961.508508] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x41d0bf96
[ 3961.508511] em28xx #0: EEPROM info:
[ 3961.508514] em28xx #0:	AC97 audio (5 sample rates)
[ 3961.508516] em28xx #0:	500mA max power
[ 3961.508520] em28xx #0:	Table at 0x06, strings=0x326a, 0x349c, 0x0000
[ 3961.509901] em28xx #0: Identified as Terratec Hybrid XS (card=11)
[ 3961.512367] tvp5150 4-005c: chip found @ 0xb8 (em28xx #0)
[ 3961.516549] tuner 4-0061: chip found @ 0xc2 (em28xx #0)
[ 3961.516829] xc2028 4-0061: creating new instance
[ 3961.516835] xc2028 4-0061: type set to XCeive xc2028/xc3028 tuner
[ 3961.519198] xc2028 4-0061: Error: firmware xc3028-v27.fw not found.
[ 3961.519464] Registered IR keymap rc-terratec-cinergy-xs
[ 3961.519646] input: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/rc/rc0/input10
[ 3961.519744] rc0: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/rc/rc0
[ 3961.520079] em28xx #0: Config register raw data: 0x50
[ 3961.520855] em28xx #0: AC97 vendor ID = 0x83847652
[ 3961.521204] em28xx #0: AC97 features = 0x6a90
[ 3961.521209] em28xx #0: Sigmatel audio processor detected(stac 9752)
[ 3961.655727] tvp5150 4-005c: tvp5150am1 detected.
[ 3961.768694] em28xx #0: v4l2 driver version 0.1.2
[ 3961.852172] em28xx #0: V4L2 video device registered as video3
[ 3961.852175] em28xx #0: V4L2 VBI device registered as vbi0




the kernel is: 
Linux 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux

anyother software i could use to understand how to select the source one wants from the cinergy XS?

thanks,
/pIII

---

### Post by tomsimmons on 2010-10-15
> **pIII said:**
> hi all, has anyone upgraded to maverick? i don't seem to get my cinergy XS to properly work, it shows up via ucview (unicap) but i can't see the image coming in via composite.

even though dmesg shows me a log where everything seems to be good:




the kernel is: 
Linux 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux

anyother software i could use to understand how to select the source one wants from the cinergy XS?

thanks,
/pIII

I can't help you solve the problem I'm afraid, but 12 lines up in your output there is an error saying the firmware can't be found.

Tom

---

