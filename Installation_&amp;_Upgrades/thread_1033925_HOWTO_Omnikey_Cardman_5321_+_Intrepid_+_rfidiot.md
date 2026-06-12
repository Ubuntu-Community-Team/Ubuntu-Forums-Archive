---
title: "HOWTO: Omnikey Cardman 5321 + Intrepid + rfidiot"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by slipdipper on 2009-01-07
HOWTO: Omnikey Cardman 5321 + Intrepid + rfidiot

preface:
so ya, ubuntu has the pcscd package but it isnt compiled with to use libusb, so if you're using a omnikey cardman 5321, you're out of luck. there is also the pcscd-omnikey package, but that didnt work all to excellent for me. so here's what i did to get it all working. Some steps may or may not be needed. if someone else can do it more efficiently, please let me know, and that would be helpful

Install Prerequisite packages:
------------------------------------------------
```

sudo apt-get install build-essential python python-dev swig libpcsclite-dev python-crypto libusb-dev libusb

```



install pyscard:
------------------------------------------------
Download from: [http://pyscard.sourceforge.net/](http://pyscard.sourceforge.net/)

```

tar -zxvf pyscard-1.6.7.tar.gz
cd pyscard-1.6.7/
sudo python setup.py build_ext install

```

NOTE: If this doesnt compile, you may have to install some other python libs



install pyserial:
------------------------------------------------
Download from: [http://pyserial.wiki.sourceforge.net/pySerial](http://pyserial.wiki.sourceforge.net/pySerial) ([http://pypi.python.org/pypi/pyserial](http://pypi.python.org/pypi/pyserial))
```

tar -zxvf pyserial-2.4.tar.gz
cd pyserial-2.4/
sudo python setup.py build_ext install

```

NOTE: above may not be needed


Install pcsc-lite: 
------------------------------------------------
download from: [https://alioth.debian.org/frs/?group_id=30105](https://alioth.debian.org/frs/?group_id=30105)

```

wget https://alioth.debian.org/frs/download.php/2708/pcsc-lite-1.5.1.tar.bz2
tar -jxvf pcsc-lite-1.5.1.tar.bz2
cd pcsc-lite-1.5.1
./configure --enable-libusb --enable-extendedapdu  --disable-libhal --enable-usbdropdir=/usr/lib/pcsc/drivers --sysconfdir=/etc --prefix=/usr LDFLAGS="-lpthread"
make
sudo make install

```

Install Omnikey Driver:
------------------------------------------------
Download from: [http://omnikey.aaitg.com/index.php?id=69](http://omnikey.aaitg.com/index.php?id=69)
Select "Cardman RFID USB 5231" and "Linux"
Download: "CardMan 5x2x PC/SC for Linux 32Bit"

```

tar -zxvf ifdokrfid_lnx-2.6.0.tar.gz
cd ifdokrfid_lnx-2.6.0/
sudo ./install -p /usr/lib/pcsc/drivers

```

Note: Make sure the below file exists: 
```

/usr/lib/pcsc/drivers/ifdokrfid_lnx-2.6.0.bundle/Contents/Linux/ifdokrfid.so

```


Start pcscd
-----------------------------------------------
```

sudo /usr/sbin/pcscd -f -a -d

```

In the output you should see:
```

00000000 pcscdaemon.c:267:main() pcscd set to foreground with debug send to stderr
00000089 debuglog.c:239:DebugLogSetLevel() debug level=debug
00000025 debuglog.c:268:DebugLogSetCategory() Debug options: APDU
00001262 pcscdaemon.c:505:main() pcsc-lite 1.5.1 daemon ready.
00558536 hotplug_libusb.c:477:HPAddHotPluggable() Adding USB device: 002:007
00000313 readerfactory.c:1083:RFInitializeReader() Attempting startup of OMNIKEY CardMan 5x21 00 00 using /usr/lib/pcsc/drivers/ifdokrfid_lnx-2.6.0.bundle/Contents/Linux/ifdokrfid.so
00000908 readerfactory.c:950:RFBindFunctions() Loading IFD Handler 3.0
OK OMNIKEY CardMan RFID  IA32 v2.6.0 support@omnikey.com

```



Run RFIDIOt 
-----------------------------------------------
Download from: [http://rfidiot.org/](http://rfidiot.org/)

test with (in new window):
```

./cardselect.py -L

```

---

### Post by kajer on 2009-01-10
Thank you for the awesome writeup!! but I have one problem, I used to be able to hotplug the USB cardman5321, but not with this install...

:confused::confused:

---

### Post by complience on 2009-03-03
Im using Ubuntu 8.10

but apart from that I followed your instructions however Im getting a different output when I launch PCSC lite and RFIDIOT cant detect my card.
> ```

sudo /usr/sbin/pcscd -f -a -d

00000000 pcscdaemon.c:267:main() pcscd set to foreground with debug send to stderr
00000151 debuglog.c:268:DebugLogSetCategory() Debug options: APDU
00000054 debuglog.c:239:DebugLogSetLevel() debug level=debug
00002281 pcscdaemon.c:505:main() pcsc-lite 1.5.2 daemon ready.
00468931 hotplug_libusb.c:403:HPEstablishUSBNotifications() Driver ifd-ccid.bundle does not support IFD_GENERATE_HOTPLUG. Using active polling instead.
00002158 hotplug_libusb.c:412:HPEstablishUSBNotifications() Polling forced every 1 second(s)
11409952 hotplug_libusb.c:477:HPAddHotPluggable() Adding USB device: 002:004
00000125 readerfactory.c:999:RFInitializeReader() Attempting startup of OmniKey CardMan 5321 00 00 using /usr/lib/pcsc/drivers/ifd-ccid.bundle/Contents/Linux/libccid.so
00000588 readerfactory.c:873:RFBindFunctions() Loading IFD Handler 3.0
00000266 ifdhandler.c:1323:init_driver() Driver version: 1.3.8
00001108 ifdhandler.c:1336:init_driver() LogLevel: 0x0003
00001018 ifdhandler.c:1356:init_driver() DriverOptions: 0x0000
00000071 ifdhandler.c:81:IFDHCreateChannelByName() lun: 0, device: usb:076b/5321:libusb:002:004
00002888 ccid_usb.c:236:OpenUSBByName() Manufacturer: Ludovic Rousseau (ludovic.rousseau@free.fr)
00001029 ccid_usb.c:246:OpenUSBByName() ProductString: Generic CCID driver
00000975 ccid_usb.c:252:OpenUSBByName() Copyright: This driver is protected by terms of the GNU Lesser General Public License version 2.1, or (at your option) any later version.
00083366 ccid_usb.c:408:OpenUSBByName() Found Vendor/Product: 076B/5321 (OmniKey CardMan 5321)
00000061 ccid_usb.c:410:OpenUSBByName() Using USB bus/device: 002/004
00022688 ccid_usb.c:798:get_data_rates() Got 256 data rates but was expecting 106



```

---

### Post by dodgerdawg on 2009-03-12
The command "sudo apt-get install build-essential python python-dev swig libpcsclite-dev python-crypto libusb-dev libusb" gave me the following error:

E: Couldn't find package libusb

Replace "libusb" w/"libusb-0.1-4" instead.

Gerry

---

### Post by claudemonet on 2009-11-25
Awesome write up, thanks.  However, I can't get the RFIDIOt suite to work with contactless cards (it seems to only want to read inserted cards).

Any idea how to get this to actually read RFID cards?  Below is the output from cardselect.py -L

> 

:~/Downloads/RFIDIOt-0.1z$ ./cardselect.py -L
PCSC devices:
    No: 0        OMNIKEY CardMan 5x21 (USB iClass Reader) 00 00
    No: 1        OMNIKEY CardMan 5x21 (USB iClass Reader) 00 01


---

### Post by naht on 2010-09-23
Hi,

I seem to have exactly the same problem with this reader (under windows atm :oops:, will try linux in the next few days) using python and pyscard.
Maybe there is a problem with the reader?

---

### Post by suoko on 2011-02-28
many thanks for your guide
i have now access to 3121

[should i clone my own card now ? :D]

apologize: is this used for POS too ?
it could be the cheaper and smallest portable POS around

---

### Post by ctskin on 2011-10-24
I used    libusb-0.1-4
but now , in the last step,  I get

[COLOR=Blue]checking for LIBUSB... no
no
checking for libusb-config... yes
checking libusb.h usability... no
checking libusb.h presence... no
checking for libusb.h... no
configure: error: libusb.h not found, use ./configure LIBUSB_CFLAGS=...

[COLOR=Black]
nb I got this message
configure: error: You can't use libudev _and_ libusb. Select only one.
so I added  [COLOR=Blue]--disable-libudev [COLOR=Black]to the config

Indeed there is no libusb.h on my machine   ... do I have to get all source and build it??? say it aint so.

I have no idea what CFLAGS are
but this did NOT help:  (there is no libusb.h in /usr/include OR anywhere.....)

[COLOR=Blue]LIBUSB_CFLAGS=-I/usr/include/libusb-1.0  

[COLOR=Black]I want to NOT build from any source, if possible. How do I say "dont bother with any *.h"  ???[/COLOR]
[/COLOR] [/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by YoungJules on 2011-11-24
Normally the .h files are provided by the -dev packages, so for libusb I'd guess libusb-dev

Sorry if this is maybe 4 weeks too late for you :P

---

