---
title: "Instant DigitalTV USB (DVB-T Stick)"
date: 2007-10-05
forum: Hardware &amp; Laptops
---

### Post by Kucki on 2007-10-05
Hello,

I have a Problem with my Instant DigitalTV USB Stick (ADS Technologies, Inc.), because he is not recognized. I installed the v4l from the website linuxtv.org (like it is described in this tutorial: [here]("http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers") <-2. Obtain latest v4l-dvb source code from LinuxTV). So after restarting, dmesg shows me this output:

usb 3-4: new high speed USB device using ehci_hcd and address 6
usb 3-4: configuration #1 chosen from 1 choice

//I think this shows that the driver for my usb stick isn't loaded successfully, isn't it?.

i looked for my device at page: [here]("http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices#DiB3000M-B_USB1.1_DVB-T_devices")
there was an entry "ADSTech Instant TV DVB-T USB2.0" I think this is my device, but on my device is written "Ads Tech Instant Digital TV USB" but i think it's the same, isn't it?
So i load the firmware for this entry on page: [here]("http://rpm.pbone.net/index.php3/stat/4/idpl/3597775/com/dvb-firmware-usb-20061120-1plf2007.0.noarch.rpm.html")
and i put it into folder /lib/firmware/2.6.20-16-generic (after extracting with "alien -g"), but it doesn't help.

extra infos:

lsusb -v

```
Bus 003 Device 004: ID 06e1:a338 ADS Technologies, Inc.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x06e1 ADS Technologies, Inc.
  idProduct          0xa338
  bcdDevice            0.00
  iManufacturer           1 ADS
  iProduct                2 Instant DigitalTV USB
  iSerial                 0
  bNumConfigurations      1
```

grep "dvb" /var/log/messages 

no output

Can you help me?
Srry for my bad English,hope you can understand.

PS. I have Ubuntu 7.04 Feisty 32bit Kernel 2.6.20-16-generic KDE 3.5.6

---

### Post by Jose Catre-Vandis on 2007-10-05
Have a look here
[http://ubuntuforums.org/showthread.php?t=417758&page=3](http://ubuntuforums.org/showthread.php?t=417758&page=3)

it is most likely that the cx88_dvb module is not being loaded

---

### Post by Kucki on 2007-10-06
thx, for your answer i tried to load the cx88_dvb module, with "modprobe"
I get the error:

FATAL: Error inserting cx88_dvb (/lib/modules/2.6.20-16-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

I also tried to load the modules given by the this site: [http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices#DiB3000M-B_USB1.1_DVB-T_devices]("http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices#DiB3000M-B_USB1.1_DVB-T_devices")

 - dib3000-common.ko
 - dib3000mb.ko
 - dvb-usb.ko
 - dvb-usb-dibusb-common.ko
 - dvb-usb-dibusb-mb.ko

I was able to load all modules, but only "dib3000-common.ko" wasn't found.
Are there other possibilties i can try?

---

### Post by Jose Catre-Vandis on 2007-10-07
Can you output your dmesg after boot, need to see if card is being recognised and what is being loaded up

at a terminal
```
dmesg > dmesg-output.txt
```

also an output of your lsmod would be helpful
```
lsmod > lsmod-output.txt
```

---

### Post by Kucki on 2007-10-07
Okay here are the files, which are containing the output.

---

### Post by Jose Catre-Vandis on 2007-10-08
OK I've been barking up the wrong tree! Sorry. it seems your card uses the saa7134 module, and linux is not able to automatically recognise it. To sort this out we need to know what card and tuner numbers your card runs on, and then to load the saa7134-dvb module. (I have a tv card that uses the same modules)

Try the following and see what you get:
```
sudo rmmod saa7134-alsa
```
```
sudo rmmod saa7134
```

If you have i2c installed try this
```
modprobe saa7134 i2c_scan=1
``` then 
```
dmesg
``` and see if card has loaded
if not
```
sudo modprobe saa7134 card=58 tuner=54
```
```
dmesg
```
is card registered now? if not, redo do above commands but try without tuner
```
sudo modprobe saa7134 card=58
```
```
sudo saa7134-dvb
```
```
dmesg
```
is frontend registered?

This could end up with a lot of trial and error on card and tuner numbers til you hit the spot, unless someone else pipes up with the info

another useful page
[http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)

---

