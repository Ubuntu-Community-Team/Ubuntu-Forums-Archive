---
title: "Firefox 5 crashes with CAC card"
date: 2011-07-02
forum: Hardware
---

### Post by aggiemarine07 on 2011-07-02
I followed the community documentation on installing my CAC in ubuntu just like I did with 9.04 to 10.10 and everything worked great.

However, after upgrading to 11.04 I installed it just as I always did but every time I start Firefox 5 it crashes. I have tried multiple ways of getting this to work (i.e. removing the module in FF, re-installing the pcsc_scan module, etc.) but to no avail.

My question is has anyone gotten FireFox 5 to work in Ubuntu 11.04? Thanks in advance.

---

### Post by An Sanct on 2011-07-02
Great .. this happens to me a lot :}

First I posted an answer to another thread, sorry for that!

The answer here would be: FF 5.0 the Canonical 1.0 build runs fine on Natty. Try the 'alpha' [nightly build]("http://nightly.mozilla.org/"), maybe your problem is already fixed.

---

### Post by lovinglinux on 2011-07-02
Try to disable the Global Menu Bar Integration Add-on and see if it starts properly. To do that, you can start Firefox in safe mode.

```
firefox -safe-mode
```

Although the global menu integration is a possible culprit, other add-ons might be causing the problem. If Firefox starts in safe mode, then is probably an add-on.

---

### Post by aggiemarine07 on 2011-07-02
> **An Sanct said:**
> Great .. this happens to me a lot :}

First I posted an answer to another thread, sorry for that!

The answer here would be: FF 5.0 the Canonical 1.0 build runs fine on Natty. Try the 'alpha' [nightly build]("http://nightly.mozilla.org/"), maybe your problem is already fixed.

------------------------------

Alright, so I downloaded the nightly build and ran firefox after extracting the archive. I then went to Edit--> Preferences-->Advanced-->Security Devices to add my CAC card.

Upon finding the module in /usr/lib/pkcs11/libcoolkeypk11.so it crashes and gives the following error in the terminal:


(firefox-bin:2516): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
firefox-bin: slot.cpp:2258: CKYStatus Slot::readCACCertificateAppend(CKYBuffer*, CKYSize): Assertion `mOldCAC' failed.

I sent the crash report to FireFox but the cac card still doesnt work. Any other suggestions? I really appreciate the response. Thanks!

---

### Post by aggiemarine07 on 2011-07-02
> **lovinglinux said:**
> Try to disable the Global Menu Bar Integration Add-on and see if it starts properly. To do that, you can start Firefox in safe mode.

```
firefox -safe-mode
```

Although the global menu integration is a possible culprit, other add-ons might be causing the problem. If Firefox starts in safe mode, then is probably an add-on.

-------------------

Upon running firefox (not the nightly build) in safe-mode I go through the steps to add the cac module to security devices in the advanced menu.

However, Firefox crashes again and is the same error message as with the nightly build. It is:

firefox-bin: slot.cpp:2258: CKYStatus Slot::readCACCertificateAppend(CKYBuffer*, CKYSize): Assertion `mOldCAC' failed.


Thanks for the responses! Any other ideas whats going on? Thanks.

---

### Post by jas- on 2011-07-06
Same problem. Firefox5, Kubuntu 11 (fully patched) coolkeypkcs (also latest).

(firefox-bin:2516): LIBDBUSMENU-GTK-CRITICAL **:  dbusmenu_menuitem_property_set_shortcut: assertion  `gtk_accelerator_valid(key, modifier)' failed
firefox-bin: slot.cpp:2258: CKYStatus Slot::readCACCertificateAppend(CKYBuffer*, CKYSize): Assertion `mOldCAC' failed.

This occurs only when the card is in the reader. If I open FF without the card in the reader I have not problem selecting the coolkeypkcs.so object and seeing the device.

---

### Post by Utah_Dave on 2011-07-20
Ubuntu 11.04 

Firefox crashes when inserting my CAC card. I ran firefox in safe mode (firefox -safe-mode) and disabled all plugins. Firefox still crashed when I inserted my CAC card. This time I got the following in my terminal:

firefox-bin: slot.cpp:2258: CKYStatus Slot::readCACCertificateAppend(CKYBuffer*, CKYSize): Assertion `mOldCAC' failed.

Any ideas what could be causing this?

Thanks for any ideas!

---

### Post by lingenfr on 2011-10-23
This problem continues. I tried the nightly build and running the nightly build in safe mode with all add-ons disabled and still got the crash with the same error. Any updates or additional things to try?

---

### Post by CPUNeck on 2011-11-16
I've experienced the same problem ironically on a previously working system that I upgraded the HD on, then used a dpkg -selection list to reinstall all applications, and restore the backeup from Dejavu (SP).  I put the old drive back in, same configuration and it still works fine.  I can't remember how I got it to work :(  So I need your help to figure out what I did.

Platform:
Dell E6420 w/built in Broadcom 5880 card reader
Firefox 7.0.1
Ubuntu 11.10 x64
DoD CAC GEMALTO 144

Debug output from starting service, inserting card, then removing it... close to the end.

```
cpuneck@Field-DL6420:~$ ps -e | grep -i pcscd
cpuneck@Field-DL6420:~$ pcscd -fd
00000000 debuglog.c:277:DebugLogSetLevel() debug level=debug
00000361 configfile.l:245:DBGetReaderListDir() Parsing conf directory: /etc/reader.conf.d
00000069 configfile.l:287:DBGetReaderList() Parsing conf file: /etc/reader.conf.d/libccidtwin
00000151 pcscdaemon.c:550:main() pcsc-lite 1.7.2 daemon ready.
00002350 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0002, path: /dev/bus/usb/001/001
00000376 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0002, path: /dev/bus/usb/001/001
00000282 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x8087, PID: 0x0024, path: /dev/bus/usb/001/002
00000319 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0002, path: /dev/bus/usb/002/001
00000253 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0002, path: /dev/bus/usb/002/001
00000269 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x8087, PID: 0x0024, path: /dev/bus/usb/002/002
00000280 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x0A5C, PID: 0x5801, path: /dev/bus/usb/002/003
00000075 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x0A5C, PID: 0x5801, path: /dev/bus/usb/002/003
00000030 hotplug_libudev.c:309:HPAddDevice() Adding USB device: Broadcom 5880
00000111 readerfactory.c:934:RFInitializeReader() Attempting startup of Broadcom 5880 [Broadcom USH w/swipe sensor] (0123456789ABCD) 00 00 using /usr/lib/pcsc/drivers/ifd-ccid.bundle/Contents/Linux/libccid.so
00000335 readerfactory.c:824:RFBindFunctions() Loading IFD Handler 3.0
00000076 ifdhandler.c:1750:init_driver() Driver version: 1.4.4
00000899 ifdhandler.c:1767:init_driver() LogLevel: 0x0003
00000036 ifdhandler.c:1778:init_driver() DriverOptions: 0x0000
00000195 ifdhandler.c:79:IFDHCreateChannelByName() lun: 0, device: usb:0a5c/5801:libudev:0:/dev/bus/usb/002/003
00000792 ccid_usb.c:245:OpenUSBByName() ifdManufacturerString: Ludovic Rousseau (ludovic.rousseau@free.fr)
00000036 ccid_usb.c:246:OpenUSBByName() ifdProductString: Generic CCID driver
00000031 ccid_usb.c:247:OpenUSBByName() Copyright: This driver is protected by terms of the GNU Lesser General Public License version 2.1, or (at your option) any later version.
00124629 ccid_usb.c:484:OpenUSBByName() Wrong interface for USB device 2/3. Checking next one.
00000203 ifdhandler.c:101:IFDHCreateChannelByName() failed
00000021 readerfactory.c:965:RFInitializeReader() Open Port 0x200000 Failed (usb:0a5c/5801:libudev:0:/dev/bus/usb/002/003)
00000012 readerfactory.c:275:RFAddReader() Broadcom 5880 [Broadcom USH w/swipe sensor] (0123456789ABCD) init failed.
00000020 readerfactory.c:985:RFUnInitializeReader() Attempting shutdown of Broadcom 5880 [Broadcom USH w/swipe sensor] (0123456789ABCD) 00 00.
00000010 readerfactory.c:861:RFUnloadReader() Unloading reader driver.
00000586 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x0A5C, PID: 0x5801, path: /dev/bus/usb/002/003
00000058 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x0A5C, PID: 0x5801, path: /dev/bus/usb/002/003
00000013 hotplug_libudev.c:309:HPAddDevice() Adding USB device: Broadcom 5880
00000084 readerfactory.c:934:RFInitializeReader() Attempting startup of Broadcom 5880 [Contacted SmartCard] (0123456789ABCD) 00 00 using /usr/lib/pcsc/drivers/ifd-ccid.bundle/Contents/Linux/libccid.so
00000316 readerfactory.c:824:RFBindFunctions() Loading IFD Handler 3.0
00000055 ifdhandler.c:1750:init_driver() Driver version: 1.4.4
00001112 ifdhandler.c:1767:init_driver() LogLevel: 0x0003
00000019 ifdhandler.c:1778:init_driver() DriverOptions: 0x0000
00000158 ifdhandler.c:79:IFDHCreateChannelByName() lun: 0, device: usb:0a5c/5801:libudev:1:/dev/bus/usb/002/003
00000990 ccid_usb.c:245:OpenUSBByName() ifdManufacturerString: Ludovic Rousseau (ludovic.rousseau@free.fr)
00000025 ccid_usb.c:246:OpenUSBByName() ifdProductString: Generic CCID driver
00000017 ccid_usb.c:247:OpenUSBByName() Copyright: This driver is protected by terms of the GNU Lesser General Public License version 2.1, or (at your option) any later version.
00001687 ccid_usb.c:504:OpenUSBByName() Found Vendor/Product: 0A5C/5801 (Broadcom 5880)
00000019 ccid_usb.c:506:OpenUSBByName() Using USB bus/device: 2/3
00001089 ccid_usb.c:936:get_data_rates() IFD does not support GET_DATA_RATES request: 0
00108490 ifdhandler.c:401:IFDHGetCapabilities() tag: 0xFB3, usb:0a5c/5801:libudev:1:/dev/bus/usb/002/003 (lun: 0)
00000032 readerfactory.c:295:RFAddReader() Using the reader polling thread
00002377 ifdhandler.c:401:IFDHGetCapabilities() tag: 0xFAE, usb:0a5c/5801:libudev:1:/dev/bus/usb/002/003 (lun: 0)
00000029 ifdhandler.c:489:IFDHGetCapabilities() Reader supports 1 slot(s)
00000445 hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x8087, PID: 0x0024, path: /dev/bus/usb/002/002
00000076 readerfactory.c:1301:RFWaitForReaderInit() Waiting init for reader: Broadcom 5880 [Contacted SmartCard] (0123456789ABCD) 00 00
99999999 ifdhandler.c:1151:IFDHPowerICC() action: PowerUp, usb:0a5c/5801:libudev:1:/dev/bus/usb/002/003 (lun: 0)
00042782 eventhandler.c:372:EHStatusHandlerThread() powerState: POWER_STATE_POWERED
00000035 eventhandler.c:387:EHStatusHandlerThread() Card inserted into Broadcom 5880 [Contacted SmartCard] (0123456789ABCD) 00 00
00000025 Card ATR: 3B 7D 96 00 00 80 31 80 65 B0 83 11 17 D6 83 00 90 00 
05003982 ifdhandler.c:1151:IFDHPowerICC() action: PowerDown, usb:0a5c/5801:libudev:1:/dev/bus/usb/002/003 (lun: 0)
00002496 eventhandler.c:446:EHStatusHandlerThread() powerState: POWER_STATE_UNPOWERED
08165071 eventhandler.c:325:EHStatusHandlerThread() Card Removed From Broadcom 5880 [Contacted SmartCard] (0123456789ABCD) 00 00
^C05000882 pcscdaemon.c:676:signal_trap() Received signal: 2
00000032 pcscdaemon.c:681:signal_trap() Preparing for suicide
01000113 readerfactory.c:1254:RFCleanupReaders() entering cleaning function
00000037 readerfactory.c:1263:RFCleanupReaders() Stopping reader: Broadcom 5880 [Contacted SmartCard] (0123456789ABCD) 00 00
00000017 eventhandler.c:148:EHDestroyEventHandler() Stomping thread.
00000014 ifdhandler.c:401:IFDHGetCapabilities() tag: 0xFB1, usb:0a5c/5801:libudev:1:/dev/bus/usb/002/003 (lun: 0)
00000011 ifdhandler.c:401:IFDHGetCapabilities() tag: 0xFB2, usb:0a5c/5801:libudev:1:/dev/bus/usb/002/003 (lun: 0)
00000009 eventhandler.c:173:EHDestroyEventHandler() Request stoping of polling thread
00000010 ifdhandler.c:366:IFDHStopPolling() usb:0a5c/5801:libudev:1:/dev/bus/usb/002/003 (lun: 0)
00000106 eventhandler.c:469:EHStatusHandlerThread() Die
00000429 eventhandler.c:188:EHDestroyEventHandler() Thread stomped.
00000023 readerfactory.c:985:RFUnInitializeReader() Attempting shutdown of Broadcom 5880 [Contacted SmartCard] (0123456789ABCD) 00 00.
00000043 ifdhandler.c:293:IFDHCloseChannel() usb:0a5c/5801:libudev:1:/dev/bus/usb/002/003 (lun: 0)
00001233 commands.c:941:CmdPowerOff Card absent or mute
00000086 readerfactory.c:861:RFUnloadReader() Unloading reader driver.
00000097 winscard_svc.c:130:ContextsDeinitialize() remaining threads: 0
00000012 pcscdaemon.c:628:at_exit() cleaning /var/run/pcscd
cpuneck@Field-DL6420:~$ 

```

Tell me what file/version information I need to provide, so we can get this to work for everyone.  On my new HD, no matter what I've tried, FF crashes as soon as the card is placed in the reader.

****UPDATE****

I just figured out what I did!  I used this page [https://help.ubuntu.com/community/CommonAccessCard?highlight=%28%28CommonAccessCard%29%29]("https://help.ubuntu.com/community/CommonAccessCard?highlight=%28%28CommonAccessCard%29%29") where it talks about the rpm2cpio utility and the coolkey x64 driver.  All I did was rerun that and wala... it works:popcorn:

---

