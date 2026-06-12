---
title: "Broadcom WIFI Activated and Not Working"
date: 2012-08-07
forum: Hardware
---

### Post by rpwstuff on 2012-08-07
Hi, 

I have installed Ubuntu 12.04 on my laptop - Gateway MX6453 and the wifi is not working.  I had Ubuntu 11 on it before and the Broadcom Wifi worked fine. (I tried to reinstall Ubuntu 11 and it still does not work)  The wifi is on and works with the other two boot partitions - Windows 8 and Windows XP (although I did have to manually load the driver for Windows XP) so I know the Wifi works.

I have a Broadcom BCM4311 wireless card.

When I did the install the driver did not show up in System Settings - Additional Drivers so I did the following:

sudo apt-get purge bcmwl-kernel-source
(rebooted)
(put install disk in drive)
sudo apt-cdrom add
sudo apt-get install bcmwl-kernel-source
(rebooted)

and the driver showed up as activated in System Settings - Additional Drivers

I don't know what else to do.  I click the Network Icon at the upper left and nothing is showing for Wifi.  I just have the following:

Wired Network (greyed out)
disconnected (greyed out)
VPN Connections
(check)Enable Networking
Connection Information (greyed out)
Edit Connections...

Any suggestions would be appreciated.

Richard

---

### Post by Bucky Ball on 2012-08-07
Check you have b43-fwcutter and firmware-b43-installer installed. Reboot and try again.

There is a catch 22 with the Broadcom cards, even though they are well supported. Have you plugged in an ethernet cable and gotten update? Try that then Additional Drivers. ;)

---

### Post by rpwstuff on 2012-08-07
I don't have an internet connection on this laptop.  I downloaded b43-fwcutter and firmware-b43-installer and installed b43-fwcutter but when I installed firmware-b43-installer it said:

(Reading database ... 140043 files and directories currently installed.)
Preparing to replace b43-fwcutter 1:015-9 (using b43-fwcutter_015-14_amd64.deb) ...
Unpacking replacement b43-fwcutter ...
Setting up b43-fwcutter (1:015-14) ...
Processing triggers for man-db ...
richard@richard-MX6448:~$ sudo dpkg -i firmware-b43-installer*
Selecting previously unselected package firmware-b43-installer.
(Reading database ... 140044 files and directories currently installed.)
Unpacking firmware-b43-installer (from firmware-b43-installer_015-14_all.deb) ...
Setting up firmware-b43-installer (1:015-14) ...
No chroot environment found. Starting normal installation
This card work with newer 5.100.138 firmware. Trying to install it.
--2012-08-06 14:54:46--  [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2)
Resolving [www.lwfinger.com](www.lwfinger.com) ([www.lwfinger.com](www.lwfinger.com))... failed: Name or service not known.
wget: unable to resolve host address `[www.lwfinger.com](www.lwfinger.com)'
dpkg: error processing firmware-b43-installer (--install):
 subprocess installed post-installation script returned error exit status 4
Errors were encountered while processing:
 firmware-b43-installer

---

### Post by rpwstuff on 2012-08-07
You were right.  I installed the b43 driver using the instructions at the following link for No Internet steps 2 and 3: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access")

the following is a recap of steps 2 and 3

---------------

downloaded
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
and
[http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

and put them in home directory then ran the following
~$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2 
~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o 
~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
-----------------------
rebooted - still no wifi

went to System Settings Additional Drivers and removed Broadcom STA wireless drive.  There was an error but I rebooted anyway and the Wifi started working.  I checked the Additional Drivers and Broadcom STA wireless driver was not activated.  Everything is working now.

Thank you for pointing me in the right direction.

Richard :)

---

### Post by Bucky Ball on 2012-08-07
Great news. Enjoy! ;)

---

