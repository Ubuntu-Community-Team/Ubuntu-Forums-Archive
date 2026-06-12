---
title: "AT&amp;T dongle not fliping"
date: 2010-12-14
forum: Hardware
---

### Post by DJBearocks on 2010-12-14
First sorry for such a long read

I have been trying for a while with help from Josh at .draisberghof.de to get my AT&T usb turbo device working

The device shows in terminal running a lsusb

Bus 001 Device 009: ID 1004:613f LG Electronics, Inc.

I have installed usb-modeswitch-data_20100826-1_all.deb and usb-modeswitch_1.1.4-1_amd64.deb both which insalled fine which
can be seen here

dave@ubuntu:~$ cd Downloads
dave@ubuntu:~/Downloads$ sudo bash
[sudo] password for dave:
root@ubuntu:~/Downloads# dpkg -i usb-modeswitch-data_20100826-1_all.deb
(Reading database ... 165037 files and directories currently installed.)
Preparing to replace usb-modeswitch-data 20100826-1 (using usb-modeswitch-data_20100826-1_all.deb) ...
Unpacking replacement usb-modeswitch-data ...
Setting up usb-modeswitch-data (20100826-1) ...
root@ubuntu:~/Downloads#

root@ubuntu:~/Downloads# dpkg -i usb-modeswitch_1.1.4-1_amd64.deb
(Reading database ... 165037 files and directories currently installed.)
Preparing to replace usb-modeswitch 1.1.4-1 (using usb-modeswitch_1.1.4-1_amd64.deb) ...
Unpacking replacement usb-modeswitch ...
Setting up usb-modeswitch (1.1.4-1) ...
Processing triggers for man-db ...
root@ubuntu:~/Downloads# 


This is what I am getting in terminal running a dmesg

[ 1258.084835] sr: Sense Key : Hardware Error [current] 
[ 1258.084845] sr: Add. Sense: No additional sense information
[ 1258.175310] usb-storage: device scan complete
[ 1258.176453] scsi 10:0:0:0: Direct-Access     Multi    Flash Reader     1.00 P



I have also at the request of Josh enabled logging to /etc/usb_modeswitch.con

As of yet I do not have any logs related to the device or any other new logs for that matter

I would really like to get this running as I am dual booting with windows just so I can use the dongle
at work.

---

