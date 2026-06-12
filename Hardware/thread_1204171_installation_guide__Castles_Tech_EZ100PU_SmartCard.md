---
title: "installation guide : Castles Tech EZ100PU SmartCard Reader USB &amp; PCSC-Lite on Jaunty"
date: 2009-07-04
forum: Hardware
---

### Post by mister_tea on 2009-07-04
i read a few posts on Linux forums about users having some troubles installing the EZ100PU SmartCard reader & PCSC-Lite on Linux

so here just a guide i wrote for installation on Ubuntu Jaunty :
(i don't work for Castle Tech or anything but just hope this can help some users dealing with this reader)

note : the manufacturer provided lately some texts for installation on Linux , but if you follow these steps below the good point is you only install & run standard packages (no executables from the manufacturer)

/*
	Linux Ubuntu V9.04 - installation guide for :
	hardware PCSC SmartCard Reader USB <CASTLES TECHNOLOGY EZ100PU> & PCSC-Lite
*/

- install Linux packages :
	sudo apt-get install pcscd pcsc-tools libusb-dev libusb-0.1-4

- download PCSC-Lite Linux package (here version 1.5.4) :
	(for ex from [http://pcsclite.alioth.debian.org/](http://pcsclite.alioth.debian.org/) )
	pcsc-lite-1.5.4.tar.bz2

- mount usbfs (to use EZ100PU on USB) :
	sudo mount -t usbfs usbfs /proc/bus/usb

- install & build PCSC-Lite binaries :
	in dir /usr/local/ : sudo tar x -v -o -f pcsc-lite-1.5.4.tar.bz2
	in dir /usr/local/pcsc-lite-1.5.4/ : sudo mkdir drivers (to install driver files later)
	sudo ./configure --disable-libhal --enable-libusb --enable-usbdropdir=/usr/local/pcsc-lite-1.5.4/drivers
	sudo make
	sudo make install

- download Castles Tech EZ100PU driver-package :
	(for ex from [http://www.casauto.com.tw/en/in-download.aspx](http://www.casauto.com.tw/en/in-download.aspx) )
	200962419433781450.gz

- install EZ100PU driver files into PCSC-Lite directory :
	extract files from EZ100PU driver-package :
		/EZUSB_Linux_x86_v1.4.7_For_Ubuntu/driver_ezusb_v1.4.7/drivers/ezusb.so
		/EZUSB_Linux_x86_v1.4.7_For_Ubuntu/driver_ezusb_v1.4.7/drivers/Info.plist
	move these files to PCSC-Lite directories (use <sudo mkdir> to create the new directories in /drivers) :
		/usr/local/pcsc-lite-1.5.4/drivers/EZ100usb.bundle/Contents/Linux/ezusb.so
		/usr/local/pcsc-lite-1.5.4/drivers/EZ100usb.bundle/Contents/Info.plist

- run pcsc_scan & test the EZ100PU reader access :
	type <pcsc_scan>
	it should detect the EZ100PU reader :
		Scanning present readers
		0: CASTLES EZ100PU 00 00
		Reader 0: CASTLES EZ100PU 00 00
		Card state: Card removed,
        then you can try when inserting a SmartCard

- debugging :
	type <lsusb> & check that the EZ100PU reader is detected
	kill pcscd (daemon) process & relaunch using : <sudo pcscd -f -d &>
	then insert the EZ100PU USB reader & should get display of PCSC-Lite info/error messages

---

### Post by droopycom on 2010-08-06
Good guide.

This unfortunately does not work on a 64 bit install. (The library provided by the manufacturer is 32 bits only,  and no sources found...)

---

### Post by olzi on 2010-08-23
> **droopycom said:**
> Good guide.

This unfortunately does not work on a 64 bit install. (The library provided by the manufacturer is 32 bits only,  and no sources found...)

Well, I got it to work on 64-bit install under linux32 compatibility. Here is a small howto:

Add extra lib32 sources:
> add-apt-repository ppa:falk-t-j/lucid

> apt-get update

Install 32-bit compat libs:
> apt-get install libc6-dev-i386
> apt-get install lib32usb

Compile pcscd:
> export CFLAGS="-m32"
> linux32 ./configure --enable-usbdropdir=/usr/lib/pcsc/drivers --disable-libhal
> linux32 make
> linux32 make install

Now it works:
> linux32 pcscd -f -d &
00000000 debuglog.c:224:DebugLogSetLevel() debug level=debug
00000447 pcscdaemon.c:505:main() pcsc-lite 1.5.3 daemon ready.
00174419 hotplug_libusb.c:477:HPAddHotPluggable() Adding USB device: 002:014
00000024 readerfactory.c:1024:RFInitializeReader() Attempting startup of CASTLES EZ100PU 00 00 using /usr/lib/pcsc/drivers/ezusb.bundle/Contents/Linux/ezusb.so
00000073 readerfactory.c:877:RFBindFunctions() Loading IFD Handler 3.0
00002651 readerfactory.c:249:RFAddReader() Using the pcscd polling thread
00000242 hotplug_libusb.c:403:HPEstablishUSBNotifications() Driver ifd-ccid.bundle does not support IFD_GENERATE_HOTPLUG. Using active polling instead.
00000014 hotplug_libusb.c:412:HPEstablishUSBNotifications() Polling forced every 1 second(s)

> pcsc_scan
PC/SC device scanner
V 1.4.16 (c) 2001-2009, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.5.3
16610131 winscard_msg_srv.c:239:SHMProcessEventsServer() Common channel packet arrival
00000041 winscard_msg_srv.c:248:SHMProcessEventsServer() SHMProcessCommonChannelRequest detects: 6
00000011 pcscdaemon.c:147:SVCServiceRunLoop() A new context thread creation is requested: 6
00000134 winscard_svc.c:133:ContextThread() Thread is started: 6
00000041 winscard_msg_srv.c:317:SHMProcessEventsContext() command CMD_VERSION received by client 6
00000011 winscard_svc.c:189:ContextThread() Client is protocol version 3:0
00000080 winscard_msg_srv.c:317:SHMProcessEventsContext() command ESTABLISH_CONTEXT received by client 6
00000031 winscard.c:242:SCardEstablishContext() Establishing Context: 17017064
Scanning present readers...
0: CASTLES EZ100PU 00 00

Mon Aug 23 13:30:33 2010
 Reader 0: CASTLES EZ100PU 00 00
  Card state: Card removed, 

And it is a 64-bit install:
> uname -a
Linux spacewalker 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64 GNU/Linux

---

### Post by spitjo on 2010-09-29
I'm getting mad with that reader and ubuntu 10.04
Starting from impossible usbfs mount (/proc/bus/usb does not exist)
Lucid comes with pcsclite 1.5.3 wich i need to replace with at least 1.5.4 compiled with libusb but i can't remove existing version (it force me to rmove another 6 or 7 useful packages like network manager and others)

Please update that fantastic guide and make it good for lucid, please...

---

### Post by File_ on 2011-01-15
> **spitjo said:**
> I'm getting mad with that reader and ubuntu 10.04
Starting from impossible usbfs mount (/proc/bus/usb does not exist)
Lucid comes with pcsclite 1.5.3 wich i need to replace with at least 1.5.4 compiled with libusb but i can't remove existing version (it force me to rmove another 6 or 7 useful packages like network manager and others)

Please update that fantastic guide and make it good for lucid, please...

BUMP ](*,)
 I also can't get it to work on lucid...

---

### Post by mister_tea on 2011-01-28
hi ... hope this helps ...

steps for installing the device :
smartcard reader CASTLES TECHNOLOGY EZ100PU
on OS : GnuLinux Ubuntu Maverick (10.10) 
-------------------------------------------


- connect the reader to usb port
- type command :
>>lsusb 
check the device appears correctly as :
Castles Technology Co., Ltd EZUSB PC/SC Smart Card Reader


- install some usefull packages :
>>sudo apt-get install opensc openct pcscd pcsc-tools
>>sudo apt-get install libusb-dev libusb-0.1-4


- download the driver package from the manufacturer :
go to [http://www.casauto.com.tw](http://www.casauto.com.tw) , select english
section Downloads
select PCSC smart card reader , ez100 series
download package : Linux(USupp... libusb...)


- download the pcsc-lite package :
[https://alioth.debian.org](https://alioth.debian.org)
get pcsclite 1.5.5 (this version)


- create a local directory "EZ100" 
- unpack pcsc-lite & driver packages in this directory 


- install pcsc-lite : move to the directory you created : pcsc-lite-1.5.5 , then type :
>>./configure --disable-libhal --enable-libusb
(maybe an additional option can be used : --enable-usbdropdir= , and after the = sign you paste the directory path where you will install the manuf drivers , see below)
>>sudo ./make
>>sudo ./make install


- in the manufacturer package find the files :
ezusb.so
Info.plist


- in the pcsc-lite directory created before , create directories & copy files :
/pcsc-lite-1.5.5/drivers/
- (DIR) EZ100usb.bundle
---     (DIR) Contents
------        Info.plist
------        (DIR) Linux
---------           ezusb.so
---------           Info.plist


- at this point normally pcsc-lite should have the needed files to access your EZ100PU smartcard reader hardware , so now let's try it :


- launch the pcsc-lite daemon :
for example to launch the daemon including debugging messages (so you can see live what is going on while you insert the reader / smart card etc) :
>>pcscd -f -d &


- launch the scan of pcsc-lite :
>>pcsc_scan
then if it is working , you should get :

Scanning present readers...
0: CASTLES EZ100PU 
Card state: Card inserted, etc etc ...


- if there is a problem , read the messages displayed from the pcsc-lite daemon

---

### Post by File_ on 2011-01-29
@mister_tea:  Thank you very much!! It worked! 

Now to use it with Firefox you just need to add a device to Firefox like this:
```

Open Firefox:
 1) Edit->Preferences->Advanced->Encryption->Security Devices
 2) Than click Load
 3) Enter arbitrary (descriptive) name under Module Name
 4) Under Module Filename enter: /usr/lib/opensc-pkcs11.so
 5) Wait a second and your card is good to go

```This worked for me on Maverick (Ubuntu 10.10)

---

### Post by tester100 on 2012-01-24
Hi guys

Any news on this

i have one of them readers and i am having some trouble with those readers, as apparently they seem to have problems in working on a x64 bit machine

i am running ubuntu 10.04 LTS server i have followed the examples shown here and this is as far as i could get

i have created the drivers folders inside the pcsc-lite-1.5.5 with all the other files and folders inside and compiled version 1.5.5 correclty but when i run pcsc_scan or pcscd -f -d &

i get the following errors....

root@tv01:~# pcsc_scan
PC/SC device scanner
V 1.4.16 (c) 2001-2009, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.5.3
SCardEstablishContext: Service not available.
root@tv01:~# pcscd -f -d &
[1] 17597
root@tv01:~# 00000000 debuglog.c:230:DebugLogSetLevel() debug level=debug
00000388 pcscdaemon.c:512:main() pcsc-lite 1.5.5 daemon ready.
00218202 hotplug_libusb.c:477:HPAddHotPluggable() Adding USB device: 002:002
00000051 readerfactory.c:1024:RFInitializeReader() Attempting startup of CASTLES                                                             EZ100PU 00 00 using /usr/local/pcsc-lite-1.5.5/drivers/EZ100usb.bundle/Contents                                                            /Linux/ezusb.so
00000165 readerfactory.c:877:RFBindFunctions() Loading IFD Handler 3.0
00006049 readerfactory.c:249:RFAddReader() Using the pcscd polling thread
00000095 hotplug_libusb.c:403:HPEstablishUSBNotifications() Driver EZ100usb.bund                                                            le does not support IFD_GENERATE_HOTPLUG. Using active polling instead.
00000014 hotplug_libusb.c:412:HPEstablishUSBNotifications() Polling forced every                                                             1 second(s)
02198142 eventhandler.c:292:EHStatusHandlerThread() Error powering up card: -214                                                            6435050 0x80100016
root@tv01:~#

---

