---
title: "EeePC Touchscreen easiest installation"
date: 2010-02-21
forum: Hardware
---

### Post by shihkster1015 on 2010-02-21
DO MIND THAT I ONLY TRIED THIS WITH 9.10 EEEPC 1000H and TOUCHSCREEN VERSION 3.0X WITH UBUNTU KERNEL 2.6.X

1. Go download the newest driver [http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm) and save it on the desktop



2. Extract the file onto desktop. If you dont know how to, type the following exactly as it is in Terminal  [COLOR=Red]{The stars is whatever version you downloaded}[/COLOR]
```
cd Desktop
tar -xzvf eGalaxTouch-*.**.****-****-***.tar.gz
```3. Now you want to create an xorg.conf file 
```
 sudo gedit /etc/X11/xorg.conf
```Then save as an empty document



4. now navigate to the folder first
```
 cd eGalaxTouch32 
```Then run the setup
```
 sudo sh setup.sh 
```5. when the setup gets to "which interface controller do you use?" enter "3" and press enter. 

6. Wait for a while for it to run, then restart your computer.

7. After your computer restarts, type the following
```
 sudo rm /etc/X11/xorg.conf~
sudo gedit /etc/X11/xorg.conf
```then you would want to type any random thing in the file. For example, i typed ```
#useless line
```8. Now remove the eGalax driver by typing 
```
 cd /Desktop/eGalaxTouch32
sudo sh setup.sh uninstall 
```9. Reboot


10. Go into terminal and reinstall eGalax driver
```
 cd Desktop/eGalaxTouch32/
sudo sh setup.sh 
```11. Restart one last time

12. To calibrate, go to SYSTEMS>ADMINISTRATION>CALIBRATE TOUCHSCREEN

13. Follow the onscreen instruction to calibrate the touchscreen

EASY ENOUGH EH?

[COLOR=Blue]NOTE: YOUR DEVICE SHOULD BE CALLED /dev/usb/hiddev0
          IF YOU CAN'T CLICK, GO TO THE XORG.CONF FILE AND CHANGE THE LINE "OPTION" "SKIPCLICK" "1"       TO      "OPTION" "SKIPCLICK" "0"
[/COLOR]

---

### Post by AMD-ATI-Fan on 2010-11-30
hello [I]shihkster1015,
i tryed to install the egalax driver on my EeePC901 but it seems not to work :(
the installation finished without errors but the calibration utility says "no touch controller found"

this iis the content of my xorg.conf file:
[/I]> ### Touch Configuration Beginning ###
Section "ServerLayout"
        Identifier "Default Layout"
        InputDevice "EETI" "SendCoreEvents"
EndSection

Section "InputDevice"
        Identifier "EETI"
        Driver "egalax"
        Option "Device" "usbauto"
        Option "Parameters" "/var/lib/eeti.param"
        Option "ScreenNo" "0"
EndSection
### Touch Configuration End ### 			 		
do you have any idea what to do?


david

---

### Post by shihkster1015 on 2010-12-01
Are you sure you're on 9.10?
i didn't test it on any other verisons.
and you need to make sure you've installed the touchscreen correctly. Plugging it in the wrong ports will cause it to malfunction.

---

### Post by AMD-ATI-Fan on 2010-12-01
ok.

im running ubuntu 10.10, thought it would work there too :(


i tested the touchscreen on WinXP and it worked fine!

---

### Post by decopeland on 2011-03-28
I am running Linux Mint (which is built on Ubuntu 10).  I am up to the step of calibrating and can't get to System>Administration>Calibrate.  The Users Guide is not much help to me as a novice Linux user.
My xorg.conf (/etc/X11) file is as follows:
### Touch Configuration Beginning ###
Section "ServerLayout"
        Identifier "Default Layout"
        InputDevice "EETI" "SendCoreEvents"
EndSection

Section "InputDevice"
        Identifier "EETI"
        Driver "egalax"
        Option "Device" "usbauto"
        Option "Parameters" "/var/lib/eeti.param"
        Option "ScreenNo" "0"
EndSection
### Touch Configuration End ###

I have used this machine (EeePC 900A running Winodows 7) and the eGalax software with the touchscreen that I installed but would prefer to run Linux with the SSD on this machine.
Any suggestions?

---

### Post by decopeland on 2011-03-31
The above does not work for Ubuntu 10.  After unpacking the downloaded file:
$ tar zxf eGalaxTouch-3.04.4912-32b-k26.tar.gz
and creating xorg.conf file, the utility file is unpacked from the eGalaxTouch32 folder:
$ tar zxf eGalaxTouch.tar.gz
Then go into the eGalaxTouch32 folder and there will be a second eGalaxTouch 32 folder.  Click on the eGalaxTouch file and the utility will launch.  Follow the GUI to calibrate.

---

