---
title: "usb mouse stops working at random times only reboot fixes"
date: 2010-04-15
forum: Hardware
---

### Post by strange on 2010-04-15
my usb mouse stops working after i boot my system it sometimes lasts a few minutes
sometimes an hour but in the end it stops working the optical light remains lit when i uplug it the light goes off when i plug it back in it stays off, only a reboot sorts it.

please ask which logs i should provide for additional info to possibly solve this problem

thanks in advance

---

### Post by Sonsum on 2010-04-15
Does this happen with other USB mouses? 

And what kind of mouse is it?

---

### Post by strange on 2010-04-15
yes it happens with other mouses as well its a logitech mx518
if i plug in another mouse after the mx518 failed that one wont start working either

---

### Post by Sonsum on 2010-04-15
That's odd. Which version of Ubuntu is it? 10.04? 9.10?

---

### Post by strange on 2010-04-15
9.10 and yes very weird :)

---

### Post by Sonsum on 2010-04-15
Here's something I found, hopefully it will solve your problem: [http://www.ubuntugeek.com/how-to-fix-usb-stops-working-problem-in-ubuntu.html](http://www.ubuntugeek.com/how-to-fix-usb-stops-working-problem-in-ubuntu.html)

Make sure to follow the instructions for GRUB 2 (in Karmic, that's what you have).

---

### Post by strange on 2010-04-15
yeah i googled before posting here
i've tried that already. no go :(

---

### Post by Sonsum on 2010-04-15
Well thats too bad. I don't have much experience on this sorta subject. It sounds like you've done your research and that's all I'm able to do. I'm sorry that I can't fix your problem, and I wish you the best of luck!

---

### Post by strange on 2010-04-15
thank you,

any other takers?

---

### Post by strange on 2010-04-15
bump

---

### Post by strange on 2010-04-18
i have tried changing acpi autosuspend to 0 this makes the mouse last a bit longer but it still dies.

i've googled for days no, no solutions anywhere :(

---

### Post by pi/roman on 2010-04-18
You could list your drivers when it works and when it doesn't and see if there is a diference:
modprobe -l | grep -i hid
will probably list your device driver. Mine is hid-logitech.

Then if it stops working try unloading and reloading it, so using mine as an example it would be:
sudo modprobe -r hid-logitech
to remove the driver and:
sudo modprobe hid-logitech
to start it up again

If your driver is not listed there then try grepping for "usb" or "mouse".

---

### Post by strange on 2010-04-18
below are the outputs for the commands you suggested to issue (ran as root)
i have a logitech mouse as well but it doesnt seem to show.

on a sidenote when the mouse failed i tried to run :
modprobe -r usbhid ; modprobe usbhid
but the -r did work (my keyboard stopped working)
but the modprobing itself just stalled.

hope this gives you more insight to pindown my problem

/strange


modprobe -l | grep -i mouse
kernel/drivers/usb/misc/idmouse.ko
kernel/drivers/input/mouse/appletouch.ko
kernel/drivers/input/mouse/bcm5974.ko
kernel/drivers/input/mouse/gpio_mouse.ko
kernel/drivers/input/mouse/inport.ko
kernel/drivers/input/mouse/logibm.ko
kernel/drivers/input/mouse/pc110pad.ko
kernel/drivers/input/mouse/psmouse.ko
kernel/drivers/input/mouse/sermouse.ko
kernel/drivers/input/mouse/synaptics_i2c.ko
kernel/drivers/input/mouse/vsxxxaa.ko

---


modprobe -l | grep -i hid
kernel/drivers/hid/hid-a4tech.ko
kernel/drivers/hid/hid-apple.ko
kernel/drivers/hid/hid-belkin.ko
kernel/drivers/hid/hid-cherry.ko
kernel/drivers/hid/hid-chicony.ko
kernel/drivers/hid/hid-cypress.ko
kernel/drivers/hid/hid-drff.ko
kernel/drivers/hid/hid-ezkey.ko
kernel/drivers/hid/hid-gyration.ko
kernel/drivers/hid/hid-kensington.ko
kernel/drivers/hid/hid-kye.ko
kernel/drivers/hid/hid-logitech.ko
kernel/drivers/hid/hid-microsoft.ko
kernel/drivers/hid/hid-monterey.ko
kernel/drivers/hid/hid-ntrig.ko
kernel/drivers/hid/hid-pl.ko
kernel/drivers/hid/hid-petalynx.ko
kernel/drivers/hid/hid-samsung.ko
kernel/drivers/hid/hid-sjoy.ko
kernel/drivers/hid/hid-sony.ko
kernel/drivers/hid/hid-sunplus.ko
kernel/drivers/hid/hid-gaff.ko
kernel/drivers/hid/hid-tmff.ko
kernel/drivers/hid/hid-topseed.ko
kernel/drivers/hid/hid-zpff.ko
kernel/drivers/hid/hid-wacom.ko
kernel/drivers/hid/usbhid/usbhid.ko
kernel/net/bluetooth/hidp/hidp.ko

---


modprobe -l | grep -i usb
kernel/drivers/net/wireless/at76c50x-usb.ko
kernel/drivers/net/wireless/libertas/usb8xxx.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
kernel/drivers/net/wireless/p54/p54usb.ko
kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
kernel/drivers/net/usb/catc.ko
kernel/drivers/net/usb/kaweth.ko
kernel/drivers/net/usb/pegasus.ko
kernel/drivers/net/usb/rtl8150.ko
kernel/drivers/net/usb/hso.ko
kernel/drivers/net/usb/asix.ko
kernel/drivers/net/usb/cdc_ether.ko
kernel/drivers/net/usb/cdc_eem.ko
kernel/drivers/net/usb/dm9601.ko
kernel/drivers/net/usb/smsc95xx.ko
kernel/drivers/net/usb/gl620a.ko
kernel/drivers/net/usb/net1080.ko
kernel/drivers/net/usb/plusb.ko
kernel/drivers/net/usb/rndis_host.ko
kernel/drivers/net/usb/cdc_subset.ko
kernel/drivers/net/usb/zaurus.ko
kernel/drivers/net/usb/mcs7830.ko
kernel/drivers/net/usb/usbnet.ko
kernel/drivers/net/usb/int51x1.ko
kernel/drivers/net/usb/cdc-phonet.ko
kernel/drivers/net/irda/irda-usb.ko
kernel/drivers/net/wimax/i2400m/i2400m-usb.ko
kernel/drivers/usb/otg/gpio_vbus.ko
kernel/drivers/usb/otg/twl4030-usb.ko
kernel/drivers/usb/otg/nop-usb-xceiv.ko
kernel/drivers/usb/host/whci/whci-hcd.ko
kernel/drivers/usb/host/oxu210hp-hcd.ko
kernel/drivers/usb/host/isp116x-hcd.ko
kernel/drivers/usb/host/xhci.ko
kernel/drivers/usb/host/sl811-hcd.ko
kernel/drivers/usb/host/sl811_cs.ko
kernel/drivers/usb/host/u132-hcd.ko
kernel/drivers/usb/host/r8a66597-hcd.ko
kernel/drivers/usb/host/isp1760.ko
kernel/drivers/usb/host/hwa-hc.ko
kernel/drivers/usb/storage/usb-storage.ko
kernel/drivers/usb/storage/ums-alauda.ko
kernel/drivers/usb/storage/ums-cypress.ko
kernel/drivers/usb/storage/ums-datafab.ko
kernel/drivers/usb/storage/ums-freecom.ko
kernel/drivers/usb/storage/ums-isd200.ko
kernel/drivers/usb/storage/ums-jumpshot.ko
kernel/drivers/usb/storage/ums-karma.ko
kernel/drivers/usb/storage/ums-onetouch.ko
kernel/drivers/usb/storage/ums-sddr09.ko
kernel/drivers/usb/storage/ums-sddr55.ko

kernel/drivers/usb/storage/ums-usbat.ko
kernel/drivers/usb/misc/adutux.ko
kernel/drivers/usb/misc/appledisplay.ko
kernel/drivers/usb/misc/berry_charge.ko
kernel/drivers/usb/misc/cypress_cy7c63.ko
kernel/drivers/usb/misc/cytherm.ko
kernel/drivers/usb/misc/emi26.ko
kernel/drivers/usb/misc/emi62.ko
kernel/drivers/usb/misc/ftdi-elan.ko
kernel/drivers/usb/misc/idmouse.ko
kernel/drivers/usb/misc/iowarrior.ko
kernel/drivers/usb/misc/isight_firmware.ko
kernel/drivers/usb/misc/usblcd.ko
kernel/drivers/usb/misc/ldusb.ko
kernel/drivers/usb/misc/usbled.ko
kernel/drivers/usb/misc/legousbtower.ko
kernel/drivers/usb/misc/rio500.ko
kernel/drivers/usb/misc/usbtest.ko
kernel/drivers/usb/misc/trancevibrator.ko
kernel/drivers/usb/misc/uss720.ko
kernel/drivers/usb/misc/usbsevseg.ko
kernel/drivers/usb/misc/vstusb.ko
kernel/drivers/usb/misc/sisusbvga/sisusbvga.ko
kernel/drivers/usb/c67x00/c67x00.ko
kernel/drivers/usb/wusbcore/wusbcore.ko
kernel/drivers/usb/wusbcore/wusb-wa.ko
kernel/drivers/usb/wusbcore/wusb-cbaf.ko
kernel/drivers/usb/class/cdc-acm.ko
kernel/drivers/usb/class/usblp.ko
kernel/drivers/usb/class/cdc-wdm.ko
kernel/drivers/usb/class/usbtmc.ko
kernel/drivers/usb/image/mdc800.ko
kernel/drivers/usb/image/microtek.ko
kernel/drivers/usb/serial/usbserial.ko
kernel/drivers/usb/serial/aircable.ko
kernel/drivers/usb/serial/ark3116.ko
kernel/drivers/usb/serial/belkin_sa.ko
kernel/drivers/usb/serial/ch341.ko
kernel/drivers/usb/serial/cp210x.ko
kernel/drivers/usb/serial/cyberjack.ko
kernel/drivers/usb/serial/cypress_m8.ko
kernel/drivers/usb/serial/usb_debug.ko
kernel/drivers/usb/serial/digi_acceleport.ko
kernel/drivers/usb/serial/io_edgeport.ko
kernel/drivers/usb/serial/io_ti.ko
kernel/drivers/usb/serial/empeg.ko
kernel/drivers/usb/serial/ftdi_sio.ko
kernel/drivers/usb/serial/funsoft.ko
kernel/drivers/usb/serial/garmin_gps.ko
kernel/drivers/usb/serial/hp4x.ko
kernel/drivers/usb/serial/ipaq.ko
kernel/drivers/usb/serial/ipw.ko
kernel/drivers/usb/serial/ir-usb.ko
kernel/drivers/usb/serial/iuu_phoenix.ko
kernel/drivers/usb/serial/keyspan.ko
kernel/drivers/usb/serial/keyspan_pda.ko
kernel/drivers/usb/serial/kl5kusb105.ko
kernel/drivers/usb/serial/kobil_sct.ko

kernel/drivers/usb/serial/mct_u232.ko
kernel/drivers/usb/serial/mos7720.ko
kernel/drivers/usb/serial/mos7840.ko
kernel/drivers/usb/serial/moto_modem.ko
kernel/drivers/usb/serial/navman.ko
kernel/drivers/usb/serial/omninet.ko
kernel/drivers/usb/serial/opticon.ko
kernel/drivers/usb/serial/option.ko
kernel/drivers/usb/serial/oti6858.ko
kernel/drivers/usb/serial/pl2303.ko
kernel/drivers/usb/serial/qcserial.ko
kernel/drivers/usb/serial/safe_serial.ko
kernel/drivers/usb/serial/siemens_mpi.ko
kernel/drivers/usb/serial/sierra.ko
kernel/drivers/usb/serial/spcp8x5.ko
kernel/drivers/usb/serial/symbolserial.ko
kernel/drivers/usb/serial/ti_usb_3410_5052.ko
kernel/drivers/usb/serial/visor.ko
kernel/drivers/usb/serial/whiteheat.ko
kernel/drivers/usb/atm/cxacru.ko
kernel/drivers/usb/atm/speedtch.ko
kernel/drivers/usb/atm/ueagle-atm.ko
kernel/drivers/usb/atm/usbatm.ko
kernel/drivers/usb/atm/xusbatm.ko
kernel/drivers/input/touchscreen/usbtouchscreen.ko
kernel/drivers/i2c/busses/i2c-tiny-usb.ko
kernel/drivers/media/video/cpia_usb.ko
kernel/drivers/media/video/usbvision/usbvision.ko
kernel/drivers/media/video/pvrusb2/pvrusb2.ko
kernel/drivers/media/video/dabusb.ko
kernel/drivers/media/video/usbvideo/usbvideo.ko
kernel/drivers/media/video/usbvideo/ibmcam.ko
kernel/drivers/media/video/usbvideo/ultracam.ko
kernel/drivers/media/video/usbvideo/konicawc.ko
kernel/drivers/media/video/usbvideo/vicam.ko
kernel/drivers/media/video/usbvideo/quickcam_messenger.ko
kernel/drivers/media/dvb/ttusb-dec/ttusb_dec.ko
kernel/drivers/media/dvb/ttusb-dec/ttusbdecfe.ko
kernel/drivers/media/dvb/ttusb-budget/dvb-ttusb-budget.ko
kernel/drivers/media/dvb/b2c2/b2c2-flexcop-usb.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-vp7045.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-vp702x.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-gp8psk.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-dtt200u.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-dibusb-common.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-a800.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-dibusb-mb.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-dibusb-mc.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-nova-t-usb2.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-umt-010.ko

kernel/drivers/media/dvb/dvb-usb/dvb-usb-m920x.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-gl861.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-au6610.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-digitv.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-cxusb.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-ttusb2.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-dib0700.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-opera.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-af9005.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-af9005-remote.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-anysee.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-dw2102.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-dtv5100.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-af9015.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-cinergyT2.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-ce6230.ko
kernel/drivers/media/dvb/siano/smsusb.ko
kernel/drivers/watchdog/pcwd_usb.ko
kernel/drivers/bluetooth/bfusb.ko
kernel/drivers/bluetooth/btusb.ko
kernel/drivers/isdn/hardware/mISDN/hfcsusb.ko
kernel/drivers/isdn/hisax/hfc_usb.ko
kernel/drivers/isdn/gigaset/usb_gigaset.ko
kernel/drivers/hid/usbhid/usbhid.ko
kernel/drivers/staging/go7007/go7007-usb.ko
kernel/drivers/staging/usbip/usbip_common_mod.ko
kernel/drivers/staging/usbip/vhci-hcd.ko
kernel/drivers/staging/usbip/usbip.ko
kernel/drivers/staging/wlan-ng/prism2_usb.ko
kernel/drivers/staging/at76_usb/at76_usb.ko
kernel/drivers/staging/comedi/drivers/usbdux.ko
kernel/drivers/staging/comedi/drivers/usbduxfast.ko
kernel/drivers/staging/rtl8192su/r8192s_usb.ko
kernel/drivers/staging/line6/line6usb.ko
kernel/drivers/staging/serqt_usb2/serqt_usb2.ko
kernel/drivers/staging/cpc-usb/cpc-usb.ko
kernel/drivers/uwb/i1480/dfu/i1480-dfu-usb.ko
kernel/drivers/usb/gadget/dummy_hcd.ko
kernel/drivers/usb/gadget/g_zero.ko
kernel/drivers/usb/gadget/g_audio.ko
kernel/drivers/usb/gadget/g_ether.ko
kernel/drivers/usb/gadget/gadgetfs.ko
kernel/drivers/usb/gadget/g_file_storage.ko
kernel/drivers/usb/gadget/g_serial.ko
kernel/drivers/usb/gadget/g_printer.ko
kernel/drivers/usb/gadget/g_midi.ko
kernel/drivers/usb/gadget/g_cdc.ko
kernel/sound/usb/snd-usb-audio.ko
kernel/sound/usb/snd-usb-lib.ko
kernel/sound/usb/usx2y/snd-usb-usx2y.ko
kernel/sound/usb/usx2y/snd-usb-us122l.ko
kernel/sound/usb/caiaq/snd-usb-caiaq.ko
kernel/ubuntu/lirc/lirc_atiusb/lirc_atiusb.ko
kernel/ubuntu/lirc/lirc_igorplugusb/lirc_igorplugusb.ko
kernel/ubuntu/lirc/lirc_mceusb/lirc_mceusb.ko
kernel/ubuntu/lirc/lirc_ttusbir/lirc_ttusbir.ko

---

### Post by pi/roman on 2010-04-18
Also try adding the verbose option to get a better idea what it's doing. So try:
sudo modprobe -r -v hid-logitech
sudo modprobe -v hid-logitech

---

### Post by strange on 2010-04-18
done. should i wait now untill it stops working again?

---

### Post by camdude on 2010-04-18
This has happened to me: You have 1 of 2 problems:
1. Hardware Conflicts
2. A Bad USB port somewhere, and when you plug a device in, it shorts out the USB plugs...

Try looking for HW conflicts, and perhaps trying to reinstall the device first, and if that doesn't work, buy a hub, and plu it in to a USB port that you know that does work. It could also be that you blocker (The black block in the usb port) fell out, that can cause some electrical shorts too

---

### Post by strange on 2010-04-18
well my keyboard keeps working all the time which is usb as well
and if i put the mouse in the port which my keyboard is in i have the same problem.

HW conflict im not sure how to test that i only have a usb keyboard and a usb mouse connected and the mouse stops working out of nowhere. where should i look for conflicts ?

---

### Post by strange on 2010-04-18
ok the mouse stopped functioning again and i ran the command i was told to:

-
strange@sodom:~$ sudo modprobe -r -v hid-logitech
[sudo] password for strange: 
rmmod /lib/modules/2.6.31-21-generic/kernel/drivers/hid/hid-logitech.ko
rmmod /lib/modules/2.6.31-21-generic/kernel/drivers/hid/usbhid/usbhid.ko
-

thats what it shows, it doesnt return to prompt and just stalls there. cant "modprobe -v hid-logitech" after that either

---

### Post by camdude on 2010-04-18
to get detailed hardware information, run 'hwinfo' (without quotes) in the terminal. That will give you connection information, the driver information, and etc.

---

### Post by strange on 2010-04-19
i've just installed hwinfo would you like me to post the output somewhere?

---

### Post by sithlordkyle on 2010-05-07
i have this same issue with 10.04 and it's not a hardware problem.  i say this because i have that system dual-booted with windows 7 and the mouse never stops working with it... just ubuntu.

does anyone know if this problem happens with any other linux distro?

---

### Post by strange on 2010-05-08
which motherboard do you have?

---

### Post by strange on 2010-05-25
i have stumbled upon:
[http://www.nvnews.net/vbulletin/showthread.php?t=135022](http://www.nvnews.net/vbulletin/showthread.php?t=135022)

i dont understand what they mean with the order thing, they dont explain how to fix it. 

if someone has any ideas please reply.

---

### Post by strange on 2010-05-25
i've upgraded to 10.04 the problem remains

---

### Post by strange on 2010-09-05
i found a fix its costly 
if i disable SMP i dont have any usb problems
but that means i use 1 out of 3 cores which destroys my performance

---

