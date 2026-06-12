---
title: "pcsc &amp; libccid"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by 0cool on 2007-07-22
Hi, I tried to bring my USB Smart Card Reader oz776 to work without success.
I installed pcscd, pcsc-tools and libccid (installed in /usr/lib/pcsc/drivers/ifd-ccid.bundle/Contents/Linux/libccid.so.1.2.1) but it seems that pcscd doesn't recognize the reader or the libccid.
Do I need to install or load a kernel module for the reader itself?

Can somebody help me getting it to work?

> # lsusb
Bus 005 Device 004: ID 0b97:7772 O2 Micro, Inc.
Bus 005 Device 002: ID 0b97:7761 O2 Micro, Inc.

> # cat /var/log/messages
Jul 22 11:47:21 ubuntu pcscd: readerfactory.c:1363:RFCleanupReaders() entering cleaning function
Jul 22 11:47:21 ubuntu pcscd: pcscdaemon.c:558:at_exit() cleaning /var/run
Jul 22 11:47:21 ubuntu pcscd: pcscdaemon.c:533:main() pcsc-lite 1.3.3 daemon ready.

---

### Post by jens.h on 2007-07-28
I have a Dell Latitude D630 and observe exactly the same problem :(

---

### Post by LudovicRousseau on 2007-08-01
> # lsusb
Bus 005 Device 004: ID 0b97:7772 O2 Micro, Inc.
Bus 005 Device 002: ID 0b97:7761 O2 Micro, Inc.

The only O2 micro device supported by the CCID driver is 0x0b97:0x7762:O2 Micro Oz776.

---

### Post by 0cool on 2007-08-01
It seems the new reader from O2Micro with the ProductID 0x7772 has the same problem as the reader 0x7762. It still uses the wrong usb endpoint for the "extra" field.

I made some quick&dirty hacks to the current source code of ccid-1.3.0 to add this smart card reader with the already existing patch for the old one.

It works on my machine pretty well with my homebanking application and gnupg+pcsc.

Download the source code from [http://alioth.debian.org/frs/download.php/1970/ccid-1.3.0.tar.gz]("ccid-1.3.0.tar.gz") and the attached patch file to **/usr/src/**.

```

mark@ws01:~# sudo -i
root@ws01:~# /etc/init.d/pcscd stop
root@ws01:~# cd /usr/src
root@ws01:/usr/src# tar -xvzf ccid-1.3.0.tar.gz 
root@ws01:/usr/src# bunzip2 oz7772.patch.bz2
root@ws01:/usr/src# cd ccid-1.3.0
root@ws01:/usr/src/ccid-1.3.0# ./configure --enable-udev
root@ws01:/usr/src/ccid-1.3.0# make
root@ws01:/usr/src/ccid-1.3.0# make install
root@ws01:/usr/src/ccid-1.3.0# /etc/init.d/pcscd start

```

If you look into /var/log/messages you should see the following output and the *italic text when inserting and removing a smart card*.
> 
Aug  1 18:43:08 ws01 pcscd: pcscdaemon.c:533:main() pcsc-lite 1.3.3 daemon ready.
Aug  1 18:43:09 ws01 pcscd: hotplug_libusb.c:446:HPAddHotPluggable() Adding USB device: 005:004
Aug  1 18:43:09 ws01 pcscd: readerfactory.c:1108:RFInitializeReader() Attempting startup of O2 Micro Oz776 SmartCard Reader 00 00 using /usr/lib/pcsc/drivers/ifd-ccid.bundle/Contents/Linux/libccid.so.1.3.0-r1
Aug  1 18:43:09 ws01 pcscd: readerfactory.c:977:RFBindFunctions() Loading IFD Handler 3.0
Aug  1 18:43:09 ws01 pcscd: ifdhandler.c:1239:init_driver() LogLevel: 0x0003
Aug  1 18:43:09 ws01 pcscd: ifdhandler.c:1249:init_driver() DriverOptions: 0x0000
Aug  1 18:43:09 ws01 pcscd: ifdhandler.c:77:IFDHCreateChannelByName() lun: 0, device: usb:0b97/7772:libusb:005:004
Aug  1 18:43:09 ws01 pcscd: ccid_usb.c:229:OpenUSBByName() Manufacturer: Ludovic Rousseau (ludovic.rousseau@free.fr)
Aug  1 18:43:09 ws01 pcscd: ccid_usb.c:239:OpenUSBByName() ProductString: Generic CCID driver v1.3.0-r1
Aug  1 18:43:09 ws01 pcscd: ccid_usb.c:245:OpenUSBByName() Copyright: This driver is protected by terms of the GNU Lesser General Public License version 2.1, or (at your option) any later version.
Aug  1 18:43:09 ws01 pcscd: ccid_usb.c:393:OpenUSBByName() Found Vendor/Product: 0B97/7772 (O2 Micro Oz776 SmartCard Reader)
Aug  1 18:43:09 ws01 pcscd: ccid_usb.c:395:OpenUSBByName() Using USB bus/device: 005/004
Aug  1 18:43:09 ws01 pcscd: ccid_usb.c:782:get_data_rates() declared: 9600 bps
Aug  1 18:43:09 ws01 pcscd: ifdhandler.c:271:IFDHGetCapabilities() lun: 0, tag: 0xFAE
Aug  1 18:43:09 ws01 pcscd: ifdhandler.c:313:IFDHGetCapabilities() Reader supports 1 slots
[I]Aug  1 18:43:09 ws01 pcscd: ifdhandler.c:841:IFDHPowerICC() lun: 0, action: PowerUp
Aug  1 18:43:10 ws01 pcscd: Card ATR: 3B FA 13 00 FF 81 31 80 45 00 31 C1 73 C0 01 00 00 90 00 B1
Aug  1 18:43:13 ws01 pcscd: eventhandler.c:350:EHStatusHandlerThread() Card Removed From O2 Micro Oz776 SmartCard Reader 00 00[/I]


---

### Post by soul_rebel on 2007-11-22
package for gutsy here:
[http://andrearatto.homeunix.org/index.php/2007/dell-laptops-smart-card-reader-driver-for-ubuntu/]("http://andrearatto.homeunix.org/index.php/2007/dell-laptops-smart-card-reader-driver-for-ubuntu/")

---

