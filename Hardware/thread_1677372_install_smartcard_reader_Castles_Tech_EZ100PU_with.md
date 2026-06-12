---
title: "install smartcard reader Castles Tech EZ100PU with pcsc-lite on Ubuntu Maverick"
date: 2011-01-28
forum: Hardware
---

### Post by mister_tea on 2011-01-28
i read a few posts of users not being able to use this hardware with latests Ubuntu versions
so here the steps i used to make it work on Maverick together with pcsc-lite :

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

