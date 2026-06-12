---
title: "Tata Indicom Photon not working"
date: 2009-05-19
forum: Hardware
---

### Post by mayank.gulia on 2009-05-19
Dear all

I have recently migrate to Ubuntu 9.04 and my compliments to all relevant people for making the installation process so user friendly. 
I use Tata Indicom Photon to connect to the internet at home. I need to know how to make this work on Ubuntu.
Please note: Though I have been a fan of Ubuntu for over 4 years now, my technical knowledge still remains minimal. Please walk me through how I can use the Photon on Ubuntu.

Thanks for your help.

---

### Post by gopakumar.s on 2011-05-17
[FONT=Verdana, sans-serif][SIZE=2]There are different devices on market from TATA for the Photon service. You have to first verify your device type. It can be Huawei EC1260, EC1261, AC8710, EC168C and so on.[/SIZE][/FONT]
 
[FONT=Verdana, sans-serif][SIZE=2]If your device belongs to EC1260 or EC1261 (in my case it is) you can make it run well on Ubuntu 9.04 or 10.04.[/SIZE][/FONT]
 
[FONT=Verdana, sans-serif][SIZE=2]Usually WAN dongles, when plugged for the first time, will act like a USB storage and will start installing the driver from there. If the driver is already there, the storage device vanishes and the device then acts as a USB modem. Such devices can be called 'ZeroCD' enabled.[/SIZE][/FONT]
 
[FONT=Verdana, sans-serif][SIZE=2]But in Ubuntu or Linux in general, the OS expects the driver as a kernel module, not as a software in USB storage. The device should have used the module 'usbserial' instead of 'usb-storage' to successfully use the device as a USB modem.[/SIZE][/FONT]
 
[FONT=Verdana, sans-serif][SIZE=2]To make this possible, install the packaage 'usb-modswitch' which can perform a switching of the device from 'usb-storage' to 'usbserial'.[/SIZE][/FONT]
 
```
 
sudo apt-get install usb-modeswitch

```
 
[FONT=Verdana, sans-serif][SIZE=2]Install usb-modswitch-data package which consists of commands data needed for usb-modeswitch[/SIZE][/FONT]
 
```
 
sudo apt-get install usb-modswitch-data

```
 
[FONT=Verdana, sans-serif][SIZE=2]Now get your exact product and vendor code from the output of the following command (Your device must be plugged to pull out this information). [/SIZE][/FONT]
 
```
 
sudo lsusb
 
Bus 006 Device 007: ID 12d1:140b Huawei Technologies Co., Ltd.

```
 
[FONT=Verdana, sans-serif][SIZE=2]Edit the usb-modeswitch config to support your device[/SIZE][/FONT]
 
```
 
sudo gedit /etc/usb_modeswitch.d/12d1:1446

```
 
[FONT=Verdana, sans-serif][SIZE=2]In the line TargetProductList, add 140b.[/SIZE][/FONT]
 
 
```
 
TargetProductList=&#8221;1001,1406,140c,14ac, 140b&#8221;

```
 
[FONT=Verdana, sans-serif][SIZE=2]Save and close the file. [/SIZE][/FONT]
 
[FONT=Verdana, sans-serif][SIZE=2]Remove and re-plug your device and go to the 'Network Manager' and right click. Click on 'Edit Connection'.[/SIZE][/FONT]
 
[FONT=Verdana, sans-serif][SIZE=2]Go to the 'Mobile Broadband' tab and click on 'Add'.[/SIZE][/FONT]
 
[FONT=Verdana, sans-serif][SIZE=2]There you can see your device detected and listed. Click 'Forward' and select the 'Country' and the 'Provider'. Again click 'Forward' and 'Apply'.[/SIZE][/FONT]
 
[FONT=Verdana, sans-serif][SIZE=2]Enter your username and password. Usually the device number is your username.[/SIZE][/FONT]
 
[FONT=Verdana, sans-serif][SIZE=2]Check the option 'Available to all users' and click 'Apply'.[/SIZE][/FONT]
 
[FONT=Verdana, sans-serif][SIZE=2]Now use the 'Network Manager' to connect to the internet. You're done![/SIZE][/FONT]
 
[SIZE=2]Hope this will help those who are having problems with Photon USB modems on Ubuntu.[/SIZE]

---

