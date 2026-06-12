---
title: "LifeView L5Vt Deluxe + rtl2832u help"
date: 2010-05-07
forum: Hardware
---

### Post by drazen on 2010-05-07
I have bought USB TV Stick LifeView LV5T Deluxe and I have tried to install drivers and firmware for it on my Ubuntu 9.10 following next steps:

1. sudo apt-get install unrar build-essential mercurial
2. mkdir digivox; cd digivox
3. hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
4. wget [http://media.ubuntuusers.de/forum/attachments/2103272/090730_RTL2832U_LINUX_Ver1.1.rar](http://media.ubuntuusers.de/forum/attachments/2103272/090730_RTL2832U_LINUX_Ver1.1.rar)
5. unrar x -ep 090730_RTL2832U_LINUX_Ver1.1.rar ./v4l-dvb/linux/drivers/media/dvb/dvb-usb
6. cd v4l-dvb
7. for i in `find . -name *.pl`; do chmod +x $i ; done
8. gedit ./linux/drivers/media/dvb/dvb-usb/Makefile
 (Insertion nearly to the end of file)
dvb-usb-rtl2832u-objs = demod_rtl2832.o dvbt_demod_base.o  dvbt_nim_base.o foundation.o math_mpi.o nim_rtl2832_mxl5007t.o  nim_rtl2832_fc2580.o nim_rtl2832_mt2266.o  rtl2832u.o rtl2832u_fe.o rtl2832u_io.o tuner_mxl5007t.o tuner_fc2580.o  tuner_mt2266.o tuner_tua9001.o nim_rtl2832_tua9001.o
obj-$(CONFIG_DVB_USB_RTL2832U) += dvb-usb-rtl2832u.o
 gedit ./linux/drivers/media/dvb/dvb-usb/Kconfig
 (Insertion to the end of file:)
config DVB_USB_RTL2832U
        tristate "Realtek RTL2832U DVB-T USB2.0 support"
        depends on DVB_USB
        help
          Realtek RTL2832U DVB-T driver
 gedit ./linux/drivers/media/dvb/dvb-usb/rtl2832u.c
 (1. Remove // of line 12:)
//DVB_DEFINE_MOD_OPT_ADAPTER_NR(adapter_nr);
 (2. replace line 61-63 by:)
        if ( ( 0== dvb_usb_device_init(intf,&rtl2832u_1st_properties,THIS_MODULE,NULL,adapter_nr)  )||
                ( 0== dvb_usb_device_init(intf,&rtl2832u_2nd_properties,THIS_MODULE,NULL,adapter_nr)  ) ||
                ( 0== dvb_usb_device_init(intf,&rtl2832u_3th_properties,THIS_MODULE,NULL,adapter_nr)  ))
 gedit ./linux/drivers/media/dvb/dvb-usb/tuner_tua9001.c
 (search for 19.2 AND 20.48 and replace it by 19_2 AND 20_48:)
#elif defined(CRYSTAL_19.2_MHZ)   /*  Frequency 19.2 MHz */
#elif defined(CRYSTAL_19_2_MHZ)   /*  Frequency 19.2 MHz */
#elif defined(CRYSTAL_20.48_MHZ)   /*  Frequency 20,48 MHz */
#elif defined(CRYSTAL_20_48_MHZ)   /*  Frequency 20,48 MHz */
 9. make
 10. STRG^C after some secs.
 11. gedit ./v4l/.config
       (replace  FIREDTV=m by FIREDTV=n:) 
      CONFIG_DVB_FIREDTV=m 
      CONFIG_DVB_FIREDTV=n
 12. make clean
13. make
14. sudo make install


Problems occurred on step 13. while compiling ir-raw-event.c:
ir-raw-event.c:168: error: implicit declaration of function 'kfifo_out' and so on ...

I have noticed on [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) that 2 days ago v4l-dvb project had some changes with ir-core and ir-coomon files. 

Could this be the reason why my compiling process does not finished?
If so, which older revision of v4l-dvb can I use to properly install rtl2832u driver?

---

### Post by dino99 on 2010-05-07
[https://launchpad.net/ubuntu/+ppas?name_filter=v4l](https://launchpad.net/ubuntu/+ppas?name_filter=v4l)
[https://launchpad.net/~libv4l/+archive/ppa](https://launchpad.net/~libv4l/+archive/ppa)

---

### Post by dagokent on 2010-05-09
edit  ir-raw-event.c 

 replace "kfifo_in" with "kfifo_get" and "kfifo_out" with "kfifo_put".

---

### Post by meandubu on 2010-05-13
Hi [drazen]("http://ubuntuforums.org/member.php?u=1069447"). Did you finally manage to get it to work? I seem to have problem getting this to work...:confused:

---

### Post by drazen on 2010-05-15
Thanks dagokent, your tip helped me to compile v4l-dvb project, buth my problem still remains unsolved.
I have contact Realtek to help me to solve this problem. If I manage to solve problem  I will replay.

---

### Post by swlazlowski on 2010-05-16
It would be much appreciated - I have the same problem - managed to get the tuner recognized but can't tune in to any channel here in Birmingham uk

---

### Post by quequotion on 2010-05-18
> **dino99 said:**
> [https://launchpad.net/ubuntu/+ppas?name_filter=v4l](https://launchpad.net/ubuntu/+ppas?name_filter=v4l)
[https://launchpad.net/~libv4l/+archive/ppa](https://launchpad.net/~libv4l/+archive/ppa)

Since installing packages from that ppa, I no longer have any v4l devices available...

---

### Post by drazen on 2010-05-18
> **swlazlowski said:**
> It would be much appreciated - I have the same problem - managed to get the tuner recognized but can't tune in to any channel here in Birmingham uk

I also tried to install driver from this url: [http://www.turnovfree.net/~stybla/linux/v4l-dvb/lv5tdlx/](http://www.turnovfree.net/~stybla/linux/v4l-dvb/lv5tdlx/) , but no success. Also tuner is recognized but not able to tune. I am located in Zagreb,Croatia. Can you try to install driver from this site and tell me your experience ? 
If you still have the same problem can you send me your debug messages by setting driver in debug mode. Steps to do that:
1. Plug usb
2. Unload driver:
        # sudo rmmod dvb-usb-rtl2832u
3. Goto to dvb-usb diectory:
        # cd /lib/module/ kernel version/kernel/drivers/media/dvb/dvb-usb
4. Load module in debug mode:
        # sudo insmod dvb-usb-rtl2832u.ko debug=1
5. scan channels (you can use scan utility or w_scan).
6. Debug messages can be seen in file /var/log/messages

My message file contains this lines:
DVB: registering adapter 1 frontend 0 (Realtek RTL2832 DVB-T  RTL2836 DTMB)...
dvb-usb: USB DVB-T Device successfully initialized and connected.
usbcore: registered new interface driver dvb_usb_rtl2832u
rtl2832_ts_bus_ctrl : Do Nothing
+rtl2832_init
+usb_init_setting 
+usb_init_bulk_setting 
HIGH SPEED
-usb_init_bulk_setting 
+usb_epa_fifo_reset 
-usb_epa_fifo_reset 
-usb_init_setting 
+gpio3_out_setting 
-gpio3_out_setting 
+demod_ctl1_setting 
-demod_ctl1_setting 
+suspend_latch_setting 
-suspend_latch_setting 
+demod_ctl_setting 
-demod_ctl_setting 
+set_tuner_power 
-set_tuner_power 
+check_tuner_type
error!! read_rtl2832_tuner_register: ret=-32, DA=0xc0, len=1, offset=0x0, data=(0x2c,)
error!! read_rtl2832_tuner_register: ret=-32, DA=0xac, len=1, offset=0x1, data=(0x2c,)
error!! read_rtl2832_tuner_register: ret=-32, DA=0xc0, len=2, offset=0x7e, data=(0x2c,0xde,)
error try= 1!! write_rtl2832_stdi2c: ret=-32, DA=0xc0, len=2, data=(0xfb,0xd9,)
error try= 2!! write_rtl2832_stdi2c: ret=-32, DA=0xc0, len=2, data=(0xfb,0xd9,)
error try= 3!! write_rtl2832_stdi2c: ret=-32, DA=0xc0, len=2, data=(0xfb,0xd9,)
error try= 4!! write_rtl2832_stdi2c: ret=-32, DA=0xc0, len=2, data=(0xfb,0xd9,)
error try= 5!! write_rtl2832_stdi2c: ret=-32, DA=0xc0, len=2, data=(0xfb,0xd9,)
eroror try= 1!! read_rtl2832_stdi2c: ret=-32, DA=0xc0, len=1, data=(0x86,)
error try= 2!! read_rtl2832_stdi2c: ret=-32, DA=0xc0, len=1, data=(0x86,)
error try= 3!! read_rtl2832_stdi2c: ret=-32, DA=0xc0, len=1, data=(0x86,)
error try= 4!! read_rtl2832_stdi2c: ret=-32, DA=0xc0, len=1, data=(0x86,)
error try= 5!! read_rtl2832_stdi2c: ret=-32, DA=0xc0, len=1, data=(0x86,)
-check_tuner_type : FC0012 tuner on board...
+check_dtmb_support 
+set_demod_2836_power  onoff = 1
error!! read_rtl2832_demod_register: ret=-32, DA=0x3e, len=1, page=0, offset=0x1, data=(0xf2,)
-set_demod_2836_power  onoff = 1 fail
error!! read_rtl2832_demod_register: ret=-32, DA=0x3e, len=2, page=5, offset=0x10, data=(0x7a,0xf4,)
-check_dtmb_support  RTL2836 NOT FOUND.....
+set_demod_2836_power  onoff = 0
error!! read_rtl2832_demod_register: ret=-32, DA=0x3e, len=1, page=0, offset=0x1, data=(0xf2,)
-set_demod_2836_power  onoff = 0 fail
demod_type is 0
+build_nim_module
-build_nim_module

---

### Post by quequotion on 2010-06-06
> **quequotion said:**
> Since installing packages from that ppa, I no longer have any v4l devices available...

scratch that... I can't remember which I did first: purge the v4l-dvb module or install the ppa packages... that very likely was my fault.

---

### Post by mahdif62 on 2010-06-09
Guys I have a problem with installing the driver. I did everything as explained in the 090730_RTL2832U_LINUX_Ver1.1 readme file but I get the following error:
```
mahdi@mahdi-desktop:~/Desktop/v4l-dvb-82a9eead02b7$ make
make -C /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l 
make[1]: Entering directory `/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.32-22-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/firmware'
make[2]: Leaving directory `/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory `/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/firmware'
Kernel build directory is /lib/modules/2.6.32-22-generic/build
make -C /lib/modules/2.6.32-22-generic/build SUBDIRS=/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/tuner-xc2028.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/tuner-simple.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/tuner-types.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/mt20xx.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/tda8290.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/tea5767.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/tea5761.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/tda9887.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/tda827x.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/au0828-core.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/au0828-i2c.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/au0828-cards.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/au0828-dvb.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/au0828-video.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/au8522_dig.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/au8522_decoder.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/flexcop-pci.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/flexcop-usb.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/flexcop.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/flexcop-fe-tuner.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/flexcop-i2c.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/flexcop-sram.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/flexcop-eeprom.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/flexcop-misc.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/flexcop-hw-filter.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/flexcop-dma.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/bttv-driver.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/bttv-cards.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/bttv-if.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/bttv-risc.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/bttv-vbi.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/bttv-i2c.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/bttv-gpio.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/bttv-input.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/bttv-audio-hook.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cpia2_v4l.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cpia2_usb.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cpia2_core.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-alsa-main.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-alsa-pcm.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-driver.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-cards.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-i2c.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-firmware.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-gpio.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-queue.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-streams.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-fileops.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-ioctl.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-controls.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-mailbox.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-vbi.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-audio.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-video.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-irq.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-av-core.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-av-audio.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-av-firmware.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-av-vbi.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-scb.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-dvb.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx18-io.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx231xx-audio.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx231xx-video.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx231xx-i2c.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx231xx-cards.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx231xx-core.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx231xx-avcore.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx231xx-pcb-cfg.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx231xx-vbi.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx23885-cards.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx23885-video.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx23885-vbi.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx23885-core.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx23885-i2c.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx23885-dvb.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx23885-417.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx23885-ioctl.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx23885-ir.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx23885-input.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx23888-ir.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/netup-init.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cimax2.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/netup-eeprom.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx23885-f300.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx25840-core.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx25840-audio.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx25840-firmware.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx25840-vbi.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx88-video.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx88-vbi.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx88-mpeg.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx88-cards.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx88-core.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx88-i2c.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx88-tvaudio.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx88-dsp.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cx88-input.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dvbdev.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dmxdev.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dvb_demux.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dvb_filter.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dvb_ca_en50221.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dvb_frontend.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dvb_net.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dvb_ringbuffer.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dvb_math.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/av7110_hw.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/av7110_v4l.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/av7110_av.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/av7110_ca.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/av7110.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/av7110_ipack.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/av7110_ir.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/a800.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/af9005-remote.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/af9005.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/af9005-fe.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/af9015.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/anysee.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/au6610.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/az6027.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/ce6230.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cinergyT2-core.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cinergyT2-fe.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/cxusb.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dib0700_core.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dib0700_devices.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dibusb-common.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dibusb-mb.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dibusb-mc.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/digitv.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dtt200u.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dtt200u-fe.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dtv5100.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dw2102.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/ec168.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/friio.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/friio-fe.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/gl861.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/gp8psk.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/gp8psk-fe.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/m920x.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/nova-t-usb2.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/opera1.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/demod_rtl2832.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dvbt_demod_base.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dvbt_nim_base.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/foundation.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/math_mpi.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/nim_rtl2832_mxl5007t.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/nim_rtl2832_fc2580.o
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/nim_rtl2832_mt2266.o
/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/nim_rtl2832_mt2266.c: In function 'demod_pdcontrol':
/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/nim_rtl2832_mt2266.c:825: warning: passing argument 3 of 'MT2266_GetParam' from incompatible pointer type
/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/tuner_mt2266.h:990: note: expected 'UData_t *' but argument is of type 'u32t *'
/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/nim_rtl2832_mt2266.c:826: warning: passing argument 3 of 'MT2266_GetParam' from incompatible pointer type
/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/tuner_mt2266.h:990: note: expected 'UData_t *' but argument is of type 'u32t *'
/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/nim_rtl2832_mt2266.c:1082: warning: passing argument 3 of 'MT2266_GetParam' from incompatible pointer type
/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/tuner_mt2266.h:990: note: expected 'UData_t *' but argument is of type 'u32t *'
  CC [M]  /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/rtl2832u.o
In file included from /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/rtl2832u.c:5:
/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/rtl2832u.h:20:1: warning: "USB_VID_AZUREWAVE" redefined
In file included from /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dvb-usb.h:26,
                 from /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/rtl2832u.h:7,
                 from /home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/rtl2832u.c:5:
/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/dvb-usb-ids.h:67:1: warning: this is the location of the previous definition
/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/rtl2832u.c: In function 'rtl2832u_usb_probe':
/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/rtl2832u.c:61: error: too few arguments to function 'dvb_usb_device_init'
/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/rtl2832u.c:62: error: too few arguments to function 'dvb_usb_device_init'
/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/rtl2832u.c:63: error: too few arguments to function 'dvb_usb_device_init'
make[3]: *** [/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l/rtl2832u.o] Error 1
make[2]: *** [_module_/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/mahdi/Desktop/v4l-dvb-82a9eead02b7/v4l'
make: *** [all] Error 2
```

Please help me as I'm a newbie and have no idea what this error means.

---

### Post by cthlhu1987 on 2010-06-29
I'd did it like it's written in #1 and #3, but then I got the following error msg:
```
baruch@baruch-laptop:~/progs/tv_card_driver/digivox/v4l-dvb$ make 
make -C /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l 
make[1]: Entering directory `/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.32-23-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/firmware'
make[2]: Leaving directory `/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory `/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/firmware'
Kernel build directory is /lib/modules/2.6.32-23-generic/build
make -C /lib/modules/2.6.32-23-generic/build SUBDIRS=/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-23-generic'
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner-xc2028.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner-simple.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner-types.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/mt20xx.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tda8290.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tea5767.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tea5761.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tda9887.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tda827x.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/au0828-core.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/au0828-i2c.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/au0828-cards.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/au0828-dvb.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/au0828-video.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/au8522_dig.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/au8522_decoder.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/flexcop-pci.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/flexcop-usb.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/flexcop.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/flexcop-fe-tuner.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/flexcop-i2c.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/flexcop-sram.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/flexcop-eeprom.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/flexcop-misc.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/flexcop-hw-filter.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/flexcop-dma.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/bttv-driver.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/bttv-cards.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/bttv-if.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/bttv-risc.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/bttv-vbi.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/bttv-i2c.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/bttv-gpio.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/bttv-input.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/bttv-audio-hook.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cpia2_v4l.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cpia2_usb.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cpia2_core.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-alsa-main.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-alsa-pcm.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-driver.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-cards.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-i2c.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-firmware.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-gpio.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-queue.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-streams.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-fileops.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-ioctl.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-controls.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-mailbox.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-vbi.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-audio.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-video.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-irq.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-av-core.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-av-audio.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-av-firmware.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-av-vbi.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-scb.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-dvb.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx18-io.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx231xx-audio.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx231xx-video.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx231xx-i2c.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx231xx-cards.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx231xx-core.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx231xx-avcore.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx231xx-pcb-cfg.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx231xx-vbi.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx23885-cards.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx23885-video.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx23885-vbi.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx23885-core.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx23885-i2c.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx23885-dvb.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx23885-417.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx23885-ioctl.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx23885-ir.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx23885-input.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx23888-ir.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/netup-init.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cimax2.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/netup-eeprom.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx23885-f300.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx25840-core.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx25840-audio.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx25840-firmware.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx25840-vbi.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx88-video.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx88-vbi.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx88-mpeg.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx88-cards.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx88-core.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx88-i2c.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx88-tvaudio.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx88-dsp.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cx88-input.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dvbdev.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dmxdev.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dvb_demux.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dvb_filter.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dvb_ca_en50221.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dvb_frontend.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dvb_net.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dvb_ringbuffer.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dvb_math.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/av7110_hw.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/av7110_v4l.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/av7110_av.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/av7110_ca.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/av7110.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/av7110_ipack.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/av7110_ir.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/a800.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/af9005-remote.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/af9005.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/af9005-fe.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/af9015.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/anysee.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/au6610.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/az6027.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/ce6230.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cinergyT2-core.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cinergyT2-fe.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/cxusb.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dib0700_core.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dib0700_devices.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dibusb-common.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dibusb-mb.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dibusb-mc.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/digitv.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dtt200u.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dtt200u-fe.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dtv5100.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dw2102.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/ec168.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/friio.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/friio-fe.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/gl861.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/gp8psk.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/gp8psk-fe.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/m920x.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/nova-t-usb2.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/opera1.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/demod_rtl2832.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dvbt_demod_base.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dvbt_nim_base.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/foundation.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/math_mpi.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/nim_rtl2832_mxl5007t.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/nim_rtl2832_fc2580.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/nim_rtl2832_mt2266.o
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/nim_rtl2832_mt2266.c: In function 'demod_pdcontrol':
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/nim_rtl2832_mt2266.c:825: warning: passing argument 3 of 'MT2266_GetParam' from incompatible pointer type
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner_mt2266.h:990: note: expected 'UData_t *' but argument is of type 'u32t *'
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/nim_rtl2832_mt2266.c:826: warning: passing argument 3 of 'MT2266_GetParam' from incompatible pointer type
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner_mt2266.h:990: note: expected 'UData_t *' but argument is of type 'u32t *'
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/nim_rtl2832_mt2266.c:1082: warning: passing argument 3 of 'MT2266_GetParam' from incompatible pointer type
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner_mt2266.h:990: note: expected 'UData_t *' but argument is of type 'u32t *'
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/rtl2832u.o
In file included from /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/rtl2832u.c:5:
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/rtl2832u.h:20:1: warning: "USB_VID_AZUREWAVE" redefined
In file included from /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dvb-usb.h:26,
                 from /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/rtl2832u.h:7,
                 from /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/rtl2832u.c:5:
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dvb-usb-ids.h:67:1: warning: this is the location of the previous definition
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/rtl2832u_fe.o
In file included from /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/rtl2832u_fe.c:4:
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/rtl2832u.h:20:1: warning: "USB_VID_AZUREWAVE" redefined
In file included from /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dvb-usb.h:26,
                 from /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/foundation.h:17,
                 from /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dvbt_demod_base.h:278,
                 from /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/demod_rtl2832.h:73,
                 from /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/nim_rtl2832_tua9001.h:78,
                 from /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/rtl2832u_fe.h:5,
                 from /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/rtl2832u_fe.c:2:
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/dvb-usb-ids.h:67:1: warning: this is the location of the previous definition
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/rtl2832u_io.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner_mxl5007t.o
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner_mxl5007t.c: In function 'MxL_Soft_Reset':
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner_mxl5007t.c:1140: warning: unused variable 'Status'
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner_mxl5007t.c: In function 'MxL_Tuner_RFTune':
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner_mxl5007t.c:1224: warning: unused variable 'Status'
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner_mxl5007t.c: In function 'MxL5007_Init':
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner_mxl5007t.c:824: warning: 'myIRV' may be used uninitialized in this function
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner_fc2580.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner_mt2266.o
  CC [M]  /home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner_tua9001.o
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner_tua9001.c:951:25: error: missing ')' after "defined"
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner_tua9001.c:951:31: error: missing '(' in expression
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner_tua9001.c:957:25: error: missing ')' after "defined"
/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner_tua9001.c:957:32: error: missing '(' in expression
make[3]: *** [/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l/tuner_tua9001.o] Error 1
make[2]: *** [_module_/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/baruch/progs/tv_card_driver/digivox/v4l-dvb/v4l'
make: *** [all] Error 2
baruch@baruch-laptop:~/progs/tv_card_driver/digivox/v4l-dvb$ 
```
I haven't the slightest idea, what that means, can anyone help me with this, plz?

---

### Post by forcecore on 2010-09-26
xx

---

### Post by jurastublic on 2011-04-18
After many hours finaly I found the driver that WORKS with ubuntu 10.10 meerkat:
[http://hotfile.com/l/114615053/8b445d/20101202_linux_install_package.rar.html](http://hotfile.com/l/114615053/8b445d/20101202_linux_install_package.rar.html)
or 
[http://members.driverguide.com/driver/detail.php?driverid=1805766](http://members.driverguide.com/driver/detail.php?driverid=1805766)

The rar file contains installation script and simple instructions, you will probably have to install dvb-apps too.
Tested on Ubuntu 10.10 Maverick Meerkat, kernel is 2.6.35-28

Good luck!

---

### Post by s1hr on 2011-08-26
> **jurastublic said:**
> After many hours finaly I found the driver that WORKS with ubuntu 10.10 meerkat:
[http://hotfile.com/l/114615053/8b445d/20101202_linux_install_package.rar.html](http://hotfile.com/l/114615053/8b445d/20101202_linux_install_package.rar.html)
or 
[http://members.driverguide.com/driver/detail.php?driverid=1805766](http://members.driverguide.com/driver/detail.php?driverid=1805766)

The rar file contains installation script and simple instructions, you will probably have to install dvb-apps too.
Tested on Ubuntu 10.10 Maverick Meerkat, kernel is 2.6.35-28

Good luck!

hmmm, first link not work...
      second link ask to register and pay via paypal BEFORE download something what maybe will work...
      so,go to linuxtv, search google for that lsusb gives you,and ignore post like this! to pay for free driver????
damn!with this card i allready paid closed driver for windows7,and some closed software and get serial no,but that is not my OS...so for what to pay again? maker give drivers for linux fedora 6.0 but for older card..and till now noting else.
all other drivers are free! and exactly you can use some driver of Realtek 2832U  if you have LV32TDLX,even if chip is from VIA, that is power of linux&ubuntu...for more older card is more easy to find drivers.but for this dual head dvbt will diferent from singlehead version,but both can work in single mode for sure.
and that one is for free and is generic!(not connected just to one brand & model..to some people it work,to some work with some patch,and some never finish make command..
      ...  
and that pay before u even try have noting with spirit of sharing and ubuntu,shame on that.That is how i think.Specially when we allready paid drivers & software..in case of not only tv brand for sure!
Note that if u have that card,and on the box just xp and vista logo,maker will provide to you linux driver,and in some case upgrade to winn7..
Smell very bad,that card which have winn7 logo,not have(or for purpose makers are stopped in developing or just publishing on own pages linux drivers?-->brand=NotOnlyTv..[www.notonlytv.net](www.notonlytv.net) maybe such deal is expected from somebody who have micro and soft..something.

---

### Post by jurastublic on 2011-10-13
Thanx for the rant .
Anyway the hotfile link has a typo, tnx for noticing, this is the real one: 

 [http://hotfile.com/dl/114615053/a8b445d/20101202_linux_install_package.rar.html]("http://hotfile.com/dl/114615053/a8b445d/20101202_linux_install_package.rar.html")

It isn't obvious at first but on members.driverguide.com you don't have to pay if you register. You have free download quota so you can download it for free. Practically same as rapidshare only you have to register first. 

This driver is originally e-mailed to me from a friendly guy from Realtek.
And, what's most important, it works. 

I've noticed something regarding applications for watching TV on ubuntu.
After installation of the driver I installed Me-tv for watching. It needed channels.conf so I didn't want to bother with it and installed Kaffeine which has scanner in it.
It all went well, picture and sound and I removed Me-tv. After that, Kaffeine was unable to recognize the TV stick. Strange.  I reinstalled Me-tv and it was all good again. Maybe something to do with Me-tv removing dvb-apps. 
This strange thing happens only on Ubuntu, not on the Mint LXDE, on the Mint, after removing Me-tv, Kaffeine works OK.

---

### Post by zooey on 2011-10-29
Hi,

thanks a lot for that previous hotfile link :) :) saved my life, i couldn't run Gigabyte U7300 usb DVB-T until now, great thanks

---

### Post by s1hr on 2012-01-05
There is now very simple way to make RTL2832U driver working in  Ubuntu with kernel 3.0.0 ,kernel 3.1.0 and even kernel 3.2.0(with small edit),that means a lot of dvb-t cards USB and PCI  with this chip will work under Ubuntu 11.10 and even under Ubuntu 12.04 LTS which have to arive soon.
"Not Only TV" -LifeView LV5TDLX is just one of them.
Personally i test it with with "Not Only TV LV32TDLX" on Ubuntu 11.10 with kernel 3.0.0

Original Realtek RTL2832U chipset (DVB/DAB) Linux 2.6.x driver rel. 2.2.2 , "full" version
Thanks to Realtek (as company)
Thanks to Xgazza
Thanks to Skaman
Thanks to Gennar1
Thanks to Ambrosa

This procedure is for kernel 3.0.0 and kernel 3.1.0

```
sudo apt-get install build-essential
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install git
git clone https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0.git*
cd DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0
cd RTL2832-2.2.2_kernel-3.0.0
make clean
make
sudo make install
```

now its time to make restart of Your computer or just type in terminal
```
sudo reboot
```

thats it.

to check if driver is loaded type
```
lsmod | grep dvb
```
You should get someting like..
> dvb_usb_rtl2832u      341269  0 
dvb_usb                23788  1 dvb_usb_rtl2832u
dvb_core               94826  1 dvb_usb

what means that driver rtl2832u is loaded and working.
All your dvb-t aplication now will recognize your dvb-t card.
Next to do is to scan for available dvb-t chanels.
As player Kaffeine can use also your dvb-t card and have scan for dvb channels built in,i recommend it.
This driver depends of card will open fm radio and DAB radio if your card support it.Mine do.

Enjoy watching dvb-t..:popcorn: .. and listening FM radio or DAB radio if You are lucky and live in country where have DAB radio.



P.S. Sorry Mr. Jura Stublic,when i want to check that your link with early posted realtek older driver, it ask me to use paypal..page ask me, no rant,just fact..but now i understood that you have good intentions. ):P

---

