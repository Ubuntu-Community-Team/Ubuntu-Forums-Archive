---
title: "VM on 11.4 freezes when using ActivIdentity via pcscd"
date: 2011-09-02
forum: Hardware
---

### Post by otto456 on 2011-09-02
Folks,
I'm a little desparate about this. I'm running 11.4 (64 Bit) with VmWare Workstation 7.1.4. I have a Windows 7 VM which needs to use a ActivIdentity USB Key. I used to have that setup working on 10.4, where (when the USB key is plugged) I got got a Virtual Activ SIM device, which i mapped to the VM.
Due to a new computer I needed to move to 11.4, where i struggle with the VM freezeing when it's using the ActivIdentity USB Key.
Here is the order of things :
0. Boot computer to 11.4
1. I plug in the USB Key to the computer
2. I start VMWare Workstation
3. I start the Virtual Machine
4. I map the ActivIdentity Virtual SIM to the VM (LED on Key turns green)
5. I try to open a VPN connection inside the VM (this requires to read data from the ActivIdentity USB Key)
6. After providing my PIN code, when the VPN setup tries to read info from the USB KEY, the VM freezes
7. Waiting a long time (>5 minutes), but nothing happens
8. Unplug USB Key from Host Computer : VM unfreezes

Appreciate any help !

Thanks a lot
Otto


I have gathered some log data and version info :

otto@8560w[11:10:57] ~ >uname -a
Linux 8560w 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


otto@8560w[11:10:09] ~ >sudo dpkg-query -l pcscd
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                     Version                                  Description
+++-========================================-========================================-================================================================================================
ii  pcscd                                    1.7.0-2ubuntu2                           Middleware to access a smart card using PC/SC (daemon side)



otto@8560w[11:10:03] ~ >sudo dpkg-query -l libccid
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                     Version                                  Description
+++-========================================-========================================-================================================================================================
ii  libccid                                  1.4.2-2                                  PC/SC driver for USB CCID smart card readers





output from pcscd -df :
> 
pcscdaemon.c:230:main() pcscd set to foreground with debug send to stderr
configfile.l:245: DBGetReaderListDir() Parsing conf directory: /etc/reader.conf.d
configfile.l:287: DBGetReaderList() Parsing conf file: /etc/reader.conf.d/libccidtwin
pcscdaemon.c:550:main() pcsc-lite 1.7.0 daemon ready.
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0002, path: /dev/bus/usb/001/001
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0002, path: /dev/bus/usb/001/001
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x8087, PID: 0x0024, path: /dev/bus/usb/001/002
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x138A, PID: 0x003C, path: /dev/bus/usb/001/003
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x8087, PID: 0x0024, path: /dev/bus/usb/001/002
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0003, path: /dev/bus/usb/003/001
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0002, path: /dev/bus/usb/002/001
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0002, path: /dev/bus/usb/002/001
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x8087, PID: 0x0024, path: /dev/bus/usb/002/002
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x03F0, PID: 0x231D, path: /dev/bus/usb/002/003
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x03F0, PID: 0x231D, path: /dev/bus/usb/002/003
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x03F0, PID: 0x231D, path: /dev/bus/usb/002/003
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x03F0, PID: 0x231D, path: /dev/bus/usb/002/003
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x8087, PID: 0x0024, path: /dev/bus/usb/002/002
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x09C3, PID: 0x0014, path: /dev/bus/usb/002/018
hotplug_libudev.c:309:HPAddDevice() Adding USB device: Activkey Sim
readerfactory.c:934:RFInitializeReader() Attempting startup of Activkey Sim 00 00 using /usr/lib/pcsc/drivers/ifd-ccid.bundle/Contents/Linux/libccid.so
readerfactory.c:824:RFBindFunctions() Loading IFD Handler 3.0
ifdhandler.c:1732:init_driver() Driver version: 1.4.2
ifdhandler.c:1750:init_driver() LogLevel: 0x0003
ifdhandler.c:1771:init_driver() DriverOptions: 0x0000
ifdhandler.c:79:IFDHCreateChannelByName() lun: 0, device: usb:09c3/0014:libudev:0:/dev/bus/usb/002/018
ccid_usb.c:267:OpenUSBByName() ifdManufacturerString: Ludovic Rousseau (ludovic.rousseau@free.fr)
ccid_usb.c:268:OpenUSBByName() ifdProductString: Generic CCID driver
ccid_usb.c:269:OpenUSBByName() Copyright: This driver is protected by terms of the GNU Lesser General Public License version 2.1, or (at your option) any later version.
ccid_usb.c:502:OpenUSBByName() Found Vendor/Product: 09C3/0014 (Activkey Sim)
ccid_usb.c:504:OpenUSBByName() Using USB bus/device: 2/18
ccid_usb.c:941:get_data_rates() Wrong GET DATA RATES size: 1
ifdhandler.c:401:IFDHGetCapabilities() tag: 0xFB3, usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
readerfactory.c:295:RFAddReader() Using the reader polling thread
ifdhandler.c:401:IFDHGetCapabilities() tag: 0xFAE, usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
ifdhandler.c:489:IFDHGetCapabilities() Reader supports 1 slot(s)
ifdhandler.c:1151:IFDHPowerICC() action: PowerUp, usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
eventhandler.c:256:EHStatusHandlerThread() powerState: POWER_STATE_POWERED
Card ATR: 3B FD 18 00 FF 80 B1 FE 45 1F 07 80 73 00 21 13 57 4A 54 48 61 31 47 00 5F 
ifdhandler.c:1151:IFDHPowerICC() action: PowerDown, usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
eventhandler.c:446:EHStatusHandlerThread() powerState: POWER_STATE_UNPOWERED
winscard_msg_srv.c:202: ProcessEventsServer() Common channel packet arrival
winscard_msg_srv.c:214: ProcessEventsServer() ProcessCommonChannelRequest detects: 10
pcscdaemon.c:91:SVCServiceRunLoop() A new context thread creation is requested: 10
winscard_svc.c:297:ContextThread() Thread is started: dwClientID=10, threadContext @6B7F90
winscard_svc.c:315:ContextThread() Received command: CMD_VERSION from client 10
winscard_svc.c:327:ContextThread() Client is protocol version 4:2
winscard_svc.c:347:ContextThread() CMD_VERSION rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: ESTABLISH_CONTEXT from client 10
winscard.c:193:SCardEstablishContext() Establishing Context: 0x10307A8
winscard_svc.c:406:ContextThread() ESTABLISH_CONTEXT rv=0x0 for client 10
winscard_msg_srv.c:202: ProcessEventsServer() Common channel packet arrival
winscard_msg_srv.c:214: ProcessEventsServer() ProcessCommonChannelRequest detects: 11
pcscdaemon.c:91:SVCServiceRunLoop() A new context thread creation is requested: 11
winscard_svc.c:297:ContextThread() Thread is started: dwClientID=11, threadContext @6EA2B0
winscard_svc.c:315:ContextThread() Received command: CMD_VERSION from client 11
winscard_svc.c:327:ContextThread() Client is protocol version 4:2
winscard_svc.c:347:ContextThread() CMD_VERSION rv=0x0 for client 11
winscard_svc.c:315:ContextThread() Received command: ESTABLISH_CONTEXT from client 11
winscard.c:193:SCardEstablishContext() Establishing Context: 0x1035F0C
winscard_svc.c:406:ContextThread() ESTABLISH_CONTEXT rv=0x0 for client 11
winscard_msg_srv.c:202: ProcessEventsServer() Common channel packet arrival
winscard_msg_srv.c:214: ProcessEventsServer() ProcessCommonChannelRequest detects: 12
pcscdaemon.c:91:SVCServiceRunLoop() A new context thread creation is requested: 12
winscard_svc.c:297:ContextThread() Thread is started: dwClientID=12, threadContext @6EA490
winscard_svc.c:315:ContextThread() Received command: CMD_VERSION from client 12
winscard_svc.c:327:ContextThread() Client is protocol version 4:2
winscard_svc.c:347:ContextThread() CMD_VERSION rv=0x0 for client 12
winscard_svc.c:315:ContextThread() Received command: ESTABLISH_CONTEXT from client 12
winscard.c:193:SCardEstablishContext() Establishing Context: 0x103688E
winscard_svc.c:406:ContextThread() ESTABLISH_CONTEXT rv=0x0 for client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_WAIT_READER_STATE_CHANGE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CONNECT from client 10
winscard.c:235:SCardConnect() Attempting Connect to Activkey Sim 00 00 using protocol: 3
ifdhandler.c:1151:IFDHPowerICC() action: PowerUp, usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard.c:309:SCardConnect() power up complete.
Card ATR: 3B FD 18 00 FF 80 B1 FE 45 1F 07 80 73 00 21 13 57 4A 54 48 61 31 47 00 5F 
winscard.c:328:SCardConnect() powerState: POWER_STATE_INUSE
prothandler.c:127: PHSetProtocol() Attempting PTS to T=1
ifdhandler.c:700:IFDHSetProtocolParameters() protocol T=1, usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
ifdhandler.c:1868:extra_egt() Extra EGT patch applied
winscard.c:406:SCardConnect() Active Protocol: T=1
winscard.c:426:SCardConnect() hCard Identity: 1862d
winscard_svc.c:447:ContextThread() CONNECT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: BEGIN_TRANSACTION from client 10
winscard.c:1057:SCardBeginTransaction() Status: 0x00000000
winscard_svc.c:499:ContextThread() BEGIN_TRANSACTION rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 10
winscard_svc.c:315:ContextThread() Received command: STATUS from client 10
winscard_svc.c:555:ContextThread() STATUS rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_STOP_WAITING_READER_STATE_CHANGE from client 12
winscard_svc.c:387:ContextThread() CMD_STOP_WAITING_READER_STATE_CHANGE rv=0x0 for client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: END_TRANSACTION from client 10
winscard.c:1194:SCardEndTransaction() Status: 0x00000000
winscard_svc.c:515:ContextThread() END_TRANSACTION rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_WAIT_READER_STATE_CHANGE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: BEGIN_TRANSACTION from client 10
winscard.c:1057:SCardBeginTransaction() Status: 0x00000000
winscard_svc.c:499:ContextThread() BEGIN_TRANSACTION rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 10
winscard_svc.c:315:ContextThread() Received command: STATUS from client 10
winscard_svc.c:555:ContextThread() STATUS rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_STOP_WAITING_READER_STATE_CHANGE from client 12
winscard_svc.c:387:ContextThread() CMD_STOP_WAITING_READER_STATE_CHANGE rv=0x0 for client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_WAIT_READER_STATE_CHANGE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: END_TRANSACTION from client 10
winscard.c:1194:SCardEndTransaction() Status: 0x00000000
winscard_svc.c:515:ContextThread() END_TRANSACTION rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_STOP_WAITING_READER_STATE_CHANGE from client 12
winscard_svc.c:387:ContextThread() CMD_STOP_WAITING_READER_STATE_CHANGE rv=0x0 for client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_WAIT_READER_STATE_CHANGE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_STOP_WAITING_READER_STATE_CHANGE from client 12
winscard_svc.c:387:ContextThread() CMD_STOP_WAITING_READER_STATE_CHANGE rv=0x0 for client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_WAIT_READER_STATE_CHANGE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_STOP_WAITING_READER_STATE_CHANGE from client 12
winscard_svc.c:387:ContextThread() CMD_STOP_WAITING_READER_STATE_CHANGE rv=0x0 for client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_WAIT_READER_STATE_CHANGE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: BEGIN_TRANSACTION from client 10
winscard.c:1057:SCardBeginTransaction() Status: 0x00000000
winscard_svc.c:499:ContextThread() BEGIN_TRANSACTION rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 10
winscard_svc.c:315:ContextThread() Received command: STATUS from client 10
winscard_svc.c:555:ContextThread() STATUS rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_STOP_WAITING_READER_STATE_CHANGE from client 12
winscard_svc.c:387:ContextThread() CMD_STOP_WAITING_READER_STATE_CHANGE rv=0x0 for client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_WAIT_READER_STATE_CHANGE from client 12
winscard_svc.c:315:ContextThread() Received command: END_TRANSACTION from client 10
winscard.c:1194:SCardEndTransaction() Status: 0x00000000
winscard_svc.c:515:ContextThread() END_TRANSACTION rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_STOP_WAITING_READER_STATE_CHANGE from client 12
winscard_svc.c:387:ContextThread() CMD_STOP_WAITING_READER_STATE_CHANGE rv=0x0 for client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_WAIT_READER_STATE_CHANGE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_STOP_WAITING_READER_STATE_CHANGE from client 12
winscard_svc.c:387:ContextThread() CMD_STOP_WAITING_READER_STATE_CHANGE rv=0x0 for client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_WAIT_READER_STATE_CHANGE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_STOP_WAITING_READER_STATE_CHANGE from client 12
winscard_svc.c:387:ContextThread() CMD_STOP_WAITING_READER_STATE_CHANGE rv=0x0 for client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_WAIT_READER_STATE_CHANGE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_STOP_WAITING_READER_STATE_CHANGE from client 12
winscard_svc.c:387:ContextThread() CMD_STOP_WAITING_READER_STATE_CHANGE rv=0x0 for client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_WAIT_READER_STATE_CHANGE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_STOP_WAITING_READER_STATE_CHANGE from client 12
winscard_svc.c:387:ContextThread() CMD_STOP_WAITING_READER_STATE_CHANGE rv=0x0 for client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_WAIT_READER_STATE_CHANGE from client 12
winscard_svc.c:315:ContextThread() Received command: BEGIN_TRANSACTION from client 10
winscard.c:1057:SCardBeginTransaction() Status: 0x00000000
winscard_svc.c:499:ContextThread() BEGIN_TRANSACTION rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 10
winscard_svc.c:315:ContextThread() Received command: STATUS from client 10
winscard_svc.c:555:ContextThread() STATUS rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x0 for client 10
winscard_svc.c:315:ContextThread() Received command: TRANSMIT from client 10
winscard.c:1551:SCardTransmit() Send Protocol: T=1
ifdhandler.c:1280:IFDHTransmitToICC() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_STOP_WAITING_READER_STATE_CHANGE from client 12
winscard_svc.c:387:ContextThread() CMD_STOP_WAITING_READER_STATE_CHANGE rv=0x0 for client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_WAIT_READER_STATE_CHANGE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_STOP_WAITING_READER_STATE_CHANGE from client 12
winscard_svc.c:387:ContextThread() CMD_STOP_WAITING_READER_STATE_CHANGE rv=0x0 for client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
ccid_usb.c:618:WriteUSB() write failed (2/18 ): -9 Success
ccid_usb.c:618:WriteUSB() write failed (2/18 ): -9 Success
ccid_usb.c:618:WriteUSB() write failed (2/18 ): -9 Success
ccid_usb.c:618:WriteUSB() write failed (2/18 ): -9 Success
ccid_usb.c:618:WriteUSB() write failed (2/18 ): -9 Success
ccid_usb.c:618:WriteUSB() write failed (2/18 ): -9 Success
ifdwrapper.c:525:IFDTransmit() Card not transacted: 612
winscard.c:1576:SCardTransmit() Card not transacted: 0x80100016
winscard_svc.c:602:ContextThread() TRANSMIT rv=0x80100016 for client 10
winscard_svc.c:315:ContextThread() Received command: END_TRANSACTION from client 10
winscard.c:1194:SCardEndTransaction() Status: 0x00000000
winscard_svc.c:515:ContextThread() END_TRANSACTION rv=0x0 for client 10
ccid_usb.c:618:WriteUSB() write failed (2/18 ): -9 Success
ifdwrapper.c:346:IFDStatusICC() Card not transacted: 612
eventhandler.c:303:EHStatusHandlerThread() Error communicating to: Activkey Sim 00 00
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: DISCONNECT from client 10
winscard.c:826:SCardDisconnect() Active Contexts: 1
winscard.c:827:SCardDisconnect() dwDisposition: 1
ccid_usb.c:618:WriteUSB() write failed (2/18 ): -9 Success
ifdwrapper.c:346:IFDStatusICC() Card not transacted: 612
ifdhandler.c:1151:IFDHPowerICC() action: Reset, usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
ccid_usb.c:618:WriteUSB() write failed (2/18 ): -9 Success
ifdhandler.c:1204:IFDHPowerICC() PowerUp failed
winscard.c:901:SCardDisconnect() Error resetting card.
winscard.c:992:SCardDisconnect() powerState: POWER_STATE_GRACE_PERIOD
ifdhandler.c:401:IFDHGetCapabilities() tag: 0xFB2, usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard.c:1006:SCardDisconnect() Stoping polling thread
ifdhandler.c:366:IFDHStopPolling() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:484:ContextThread() DISCONNECT rv=0x0 for client 10
eventhandler.c:458:EHStatusHandlerThread() powerState: POWER_STATE_POWERED
ccid_usb.c:618:WriteUSB() write failed (2/18 ): -9 Success
ifdwrapper.c:346:IFDStatusICC() Card not transacted: 612
eventhandler.c:303:EHStatusHandlerThread() Error communicating to: Activkey Sim 00 00
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_WAIT_READER_STATE_CHANGE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
ccid_usb.c:618:WriteUSB() write failed (2/18 ): -9 Success
ifdwrapper.c:346:IFDStatusICC() Card not transacted: 612
ifdhandler.c:1151:IFDHPowerICC() action: PowerDown, usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
ccid_usb.c:618:WriteUSB() write failed (2/18 ): -9 Success
ifdhandler.c:1166:IFDHPowerICC() PowerDown failed
eventhandler.c:446:EHStatusHandlerThread() powerState: POWER_STATE_UNPOWERED
ccid_usb.c:618:WriteUSB() write failed (2/18 ): -9 Success
ifdwrapper.c:346:IFDStatusICC() Card not transacted: 612
eventhandler.c:303:EHStatusHandlerThread() Error communicating to: Activkey Sim 00 00
winscard_svc.c:729:MSGSignalClient() Signal client: 12
winscard_svc.c:732:MSGSignalClient() SIGNAL rv=0x0 for client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_WAIT_READER_STATE_CHANGE from client 12
ccid_usb.c:618:WriteUSB() write failed (2/18 ): -4 No such device
ifdwrapper.c:346:IFDStatusICC() Card not transacted: 617
utils.c:68:SendHotplugSignal() Send hotplug signal to pcscd (pid=9043)
hotplug_libudev.c:539:HPEstablishUSBNotifications() Device removed
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0002, path: /dev/bus/usb/001/001
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0002, path: /dev/bus/usb/001/001
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x8087, PID: 0x0024, path: /dev/bus/usb/001/002
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x138A, PID: 0x003C, path: /dev/bus/usb/001/003
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x8087, PID: 0x0024, path: /dev/bus/usb/001/002
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0003, path: /dev/bus/usb/003/001
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0002, path: /dev/bus/usb/002/001
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x1D6B, PID: 0x0002, path: /dev/bus/usb/002/001
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x8087, PID: 0x0024, path: /dev/bus/usb/002/002
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x03F0, PID: 0x231D, path: /dev/bus/usb/002/003
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x03F0, PID: 0x231D, path: /dev/bus/usb/002/003
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x03F0, PID: 0x231D, path: /dev/bus/usb/002/003
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x03F0, PID: 0x231D, path: /dev/bus/usb/002/003
hotplug_libudev.c:258:get_driver() Looking for a driver for VID: 0x8087, PID: 0x0024, path: /dev/bus/usb/002/002
hotplug_libudev.c:481:HPRescanUsbBus() Removing USB device[0]: /dev/bus/usb/002/018
eventhandler.c:148:EHDestroyEventHandler() Stomping thread.
ifdhandler.c:401:IFDHGetCapabilities() tag: 0xFB1, usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
ifdhandler.c:401:IFDHGetCapabilities() tag: 0xFB2, usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
eventhandler.c:173:EHDestroyEventHandler() Request stoping of polling thread
ifdhandler.c:366:IFDHStopPolling() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
eventhandler.c:303:EHStatusHandlerThread() Error communicating to: Activkey Sim 00 00
winscard_svc.c:729:MSGSignalClient() Signal client: 12
winscard_svc.c:732:MSGSignalClient() SIGNAL rv=0x0 for client 12
eventhandler.c:469:EHStatusHandlerThread() Die
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_WAIT_READER_STATE_CHANGE from client 12
eventhandler.c:188:EHDestroyEventHandler() Thread stomped.
readerfactory.c:985:RFUnInitializeReader() Attempting shutdown of Activkey Sim 00 00.
ifdhandler.c:293:IFDHCloseChannel() usb:09c3/0014:libudev:0:/dev/bus/usb/002/018 (lun: 0)
ccid_usb.c:618:WriteUSB() write failed (2/18 ): -4 No such device
readerfactory.c:861:RFUnloadReader() Unloading reader driver.
winscard_svc.c:729:MSGSignalClient() Signal client: 12
winscard_svc.c:732:MSGSignalClient() SIGNAL rv=0x0 for client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_WAIT_READER_STATE_CHANGE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_STOP_WAITING_READER_STATE_CHANGE from client 12
winscard_svc.c:387:ContextThread() CMD_STOP_WAITING_READER_STATE_CHANGE rv=0x0 for client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 12
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
pcscdaemon.c:676:signal_trap() Received signal: 2
pcscdaemon.c:681:signal_trap() Preparing for suicide
winscard_svc.c:315:ContextThread() Received command: CMD_GET_READERS_STATE from client 11
readerfactory.c:1254:RFCleanupReaders() entering cleaning function
winscard_svc.c:130:ContextsDeinitialize() remaining threads: 3
pcscdaemon.c:628:at_exit() cleaning /var/run/pcscd

---

