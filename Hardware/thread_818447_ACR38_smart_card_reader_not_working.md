---
title: "ACR38 smart card reader not working"
date: 2008-06-04
forum: Hardware
---

### Post by DoDoENT on 2008-06-04
Hello everyone!

I can't get my ACR38 smart card reader running. Sometimes it works, but most of the time it doesn't. Here is a pcscd log (reader was connected at the time of starting the deamon, and I reconnected it):

```
dodo@2nd-of-12:~$ sudo pcscd --foreground --debug
00000000 pcscdaemon.c:295:main() pcscd set to foreground with debug send to stderr
00000031 debuglog.c:236:DebugLogSetLevel() debug level=debug
00000310 pcscdaemon.c:513:main() pcsc-lite 1.4.99 daemon ready.
00078856 hotplug_libusb.c:478:HPAddHotPluggable() Adding USB device: 003:009
00000061 readerfactory.c:1116:RFInitializeReader() Attempting startup of ACS ACR38U 00 00 using /usr/lib/pcsc/drivers/ACR38UDriver.bundle/Contents/Linux/ACR38UDriver.so
00000301 readerfactory.c:949:RFBindFunctions() Loading IFD Handler 2.0
00000149 ifdwrapper.c:494:IFDStatusICC() Card not transacted: 612
00000011 eventhandler.c:164:EHSpawnEventHandler() Initial Check Failed on ACS ACR38U 00 00
00000007 hotplug_libusb.c:402:HPEstablishUSBNotifications() Driver ACR38UDriver.bundle does not support IFD_GENERATE_HOTPLUG. Using active polling instead.
00000006 hotplug_libusb.c:411:HPEstablishUSBNotifications() Polling forced every 1 second(s)
03099664 hotplug_libusb.c:538:HPRemoveHotPluggable() Removing USB device[0]: 003:009
00000018 eventhandler.c:105:EHDestroyEventHandler() Thread never started (reader init failed?)
00000007 readerfactory.c:1167:RFUnInitializeReader() Attempting shutdown of ACS ACR38U 00 00.
00000029 readerfactory.c:1028:RFUnloadReader() Unloading reader driver.
05002258 hotplug_libusb.c:478:HPAddHotPluggable() Adding USB device: 003:010
00000025 readerfactory.c:1116:RFInitializeReader() Attempting startup of ACS ACR38U 00 00 using /usr/lib/pcsc/drivers/ACR38UDriver.bundle/Contents/Linux/ACR38UDriver.so
00000195 readerfactory.c:949:RFBindFunctions() Loading IFD Handler 2.0
00000116 ifdwrapper.c:494:IFDStatusICC() Card not transacted: 612
00000008 eventhandler.c:164:EHSpawnEventHandler() Initial Check Failed on ACS ACR38U 00 00

```Additionaly, if I run "pcsc_scan", daemon prints the following:
```
05452134 winscard_msg_srv.c:217:SHMProcessEventsServer() Common channel packet arrival
00000028 winscard_msg_srv.c:226:SHMProcessEventsServer() SHMProcessCommonChannelRequest detects: 5
00000008 pcscdaemon.c:175:SVCServiceRunLoop() A new context thread creation is requested: 5
00000046 winscard_svc.c:131:ContextThread() Thread is started: 5
00000031 winscard_msg_srv.c:288:SHMProcessEventsContext() correctly processed client: 5
00000007 winscard_svc.c:179:ContextThread() Client is protocol version 3:0
00000050 winscard_msg_srv.c:288:SHMProcessEventsContext() correctly processed client: 5
00000025 winscard.c:242:SCardEstablishContext() Establishing Context: 16989544

``````
dodo@2nd-of-12:~$ pcsc_scan
PC/SC device scanner
V 1.4.11 (c) 2001-2007, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.4
Scanning present readers
Waiting for the first reader...

```And pscs_scan keeps waiting for a reader to appear and does nothing.

Is something wrong with the driver, or I just have the wrong configuration?

---

