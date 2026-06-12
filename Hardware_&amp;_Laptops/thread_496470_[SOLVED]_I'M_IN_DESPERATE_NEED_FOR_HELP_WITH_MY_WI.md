---
title: "[SOLVED] I'M IN DESPERATE NEED FOR HELP WITH MY WIRELESS!!! Please help me."
date: 2007-07-09
forum: Hardware &amp; Laptops
---

### Post by ~~Tito~~ on 2007-07-09
It wont connect. I restarted the computer 3 times and it wont work. Anyone have any problems like this? I need my wireless to work. Do I reset the wireless modem??? (Its a linksys WCG200). Its a modem wireless/Ethernet router G gateway. It was working all day until after I ran DoD:Source a couple of times.
Wireless card info :
Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


I already did this BTW.

tito@TITOS-LAPTOP:~$ sudo apt-get install bcm43xx-fwcutter
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
bcm43xx-fwcutter is already the newest version.
The following packages were automatically installed and are no longer required:
libgnucrypto-java liblog4j1.2-java libswt3.2-gtk-java libseda-java
libcommons-cli-java libgtk-jni libcairo-java libbcprov-java libglib-java
libgtk-java libswt3.2-gtk-jni
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
tito@TITOS-LAPTOP:~$

sudo iwconfig =

tito@TITOS-LAPTOP:~$ sudo iwconfig
Password:
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11b/g ESSID:off/any Nickname:"Broadcom 4306"
Mode:Managed Frequency=2.484 GHz Access Point: Invalid
Bit Rate=1 Mb/s Tx-Power=15 dBm
RTS thr:off Fragment thr:off
Encryption key:off
Link Quality=0/100 Signal level=-256 dBm Noise level=-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

vmnet1 no wireless extensions.

vmnet8 no wireless extensions.

tito@TITOS-LAPTOP:~$

---

### Post by ~~Tito~~ on 2007-07-09
Can I uninstall the driver then reinstall it????

---

### Post by Cuppa-Chino on 2007-07-09
tito, have you considered using NDISWRAPPER -- it has proven quite sucessful for Broadcom ships. I am currently using it for my Broadcom 4326 chipset and it works fine with WPA and all, a bit disappointing to have to use it but it works well at least.

have a look at this thread [Broadcom with NDISWRAPPER]("http://ubuntuforums.org/showthread.php?t=297092")

ignore the fact that is says Dell everywhere, it works fine on my HP as well. Just find the right Windows driver for you card and use that

---

### Post by ~~Tito~~ on 2007-07-09
Find the right driver where? What site? for 4306?

---

### Post by ~~Tito~~ on 2007-07-09
Ok, i ad to reinstall, a lot of things got messed up also.

---

