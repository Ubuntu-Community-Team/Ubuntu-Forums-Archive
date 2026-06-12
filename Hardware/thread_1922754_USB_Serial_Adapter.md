---
title: "USB Serial Adapter"
date: 2012-02-09
forum: Hardware
---

### Post by Urumiko on 2012-02-09
Hi guys being a noob I have googled this as best I can but am getting out of my depth.

My laptop is a dell XPS 17 L02x
I am trying to install this [DIgitus usb serial adapter]("http://www.digitus.info/en/products/accessories/adapter-and-converter/usb-to-serial-adaptor-usb-20-da-70156/") on the latest 32bit ubuntu by using the instructions in the readme:[INDENT]> "Instructions for installing the D2XX shared lib 
As Linux distributions vary these instructions are a guide to installation and use. 
This setup works with Mandrake 9.2 but may require some investigation on other distributions. 
 
This library has been tested using kernel 2.6.32.  
 
D2XX documentation is available for the Windows DLL - some variations may occur between Linux and  
Windows implementation. We have endeavored to make the APIs appear the same on both platforms however some 
issues may slip and we would appreciate that you contact support if you observe this. 
 
D2XX for Linux was primarily developed to aid porting windows applications written with D2XX to Linux. 
Unfortunately the source code for D2XX is not freely available - however if you prefer to have the  
source and are starting a project from scratch you can try libftdi from Thomas Jarosch.  
 
 
libftd2xx uses an unmodified version of libusb ([http://libusb.wiki.sourceforge.net/](http://libusb.wiki.sourceforge.net/)).  Source code for libusb is included in the driver distribution in the libusb-1.0.8 directory. 
 
 
Installation: 
1. unzip and untar the file given to a suitable directory 
gunzip libftd2xx1.0.0.tar.gz 
tar -xvf libftd2xx1.0.0.tar 
 
2. Change directory to the required architecture subdirectory, build/i386 for 32-bit or build/x86_64 for 64-bit. 
 
3. As root user copy the following files to /usr/local/lib 
cp libftd2xx.so.1.0.0 /usr/local/lib 
 
3. Change directory to /usr/local/lib 
cd /usr/local/lib 
 
4. make symbolic links to these files using the following commands: 
ln -s libftd2xx.so.1.0.0 libftd2xx.so 
 
5. Change directory to /usr/lib 
cd /usr/lib 
 
6. make symbolic links to these files using the following commands: 
ln -s /usr/local/lib/libftd2xx.so.1.0.0 libftd2xx.so 
 
7. Add the following line to /etc/fstab: 
none /proc/bus/usb usbdevfs defaults,devmode=0666 0 0 
There have been reports that you may need to use the following command for some distros 
none /proc/bus/usb usbdevfs defaults,mode=0666 0 0 (use usbfs in 2.6 kernels) 
 
8. Remount all in the fstab file 
mount -a 
 
If you have problems with this check with usbview (search on the internet for application  
or it can be sent to you by ftdi) to check the usb file system is mounted properly. 
 
Other problems will be related to the ftdi_sio driver loading -  
1.you must unload this driver (and usbserial) if it is attached to your device ("rmmod ftdi_sio" and "rmmod usbserial" as root user).  
2.Your PID/VID has not been included in the distribution.A PID of 0x6006 and VID of 
0x0403 should work as a temporary workaround."[/INDENT]When I hit point 8 (sudo mount -a) i get an error telling me there is no entry point for "/proc/bus/usb"
I tried implementing the [following as suggested]("http://ubuntuforums.org/showthread.php?t=1493771").(not understanding what it does)
> sudo mount --bind /dev/bus /proc/bus sudo ln -s /sys/kernel/debug/usb/devices /proc/bus/usb/devicesThis results in a different error of "usbfs is not a recognised file system[I]"

Can anyone help?
or at least help explain the problem I am facing?

[/I]

---

### Post by Urumiko on 2012-02-11
Anyone?

---

