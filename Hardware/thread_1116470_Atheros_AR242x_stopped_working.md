---
title: "Atheros AR242x stopped working"
date: 2009-04-04
forum: Hardware
---

### Post by nonsectarianblu on 2009-04-04
First off I am completely new to Ubuntu and any Unix system in general. Currently do not have access to non wireless internet but I do have two computers and an external harddrive. I have been having troubles with my Atheros ar242x winmodem. I attempted to install it with the madwifi patch but could not extract the file. I got the card to work using wireless network drivers. When installed updates the card will no longer send or receive packets. When I run iwconfig this is the script I get.

lo          no wireless extensions.

eth0        no wireless extensions.

wlan0       IEEE 802.11g  ESSID:off/any
            Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Assoicated
            Bit Rate: 54 Mb/s
            Power Management:off
            Link Quality:0  Signal level:0  Noise level:0
            Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0
            Tx excessive retries:0 Invalid misc:0 Missed beacon:0


any suggestions so I can get this working before I go to Iraq in less then 15 days? Again to reiterate without wireless this computer cannot get on the internet so all downloads must be put unto the computer via external hard drive from a xp computer. I am running Ubuntu 8.04 Hardy Heron 32 bit, and it is a Toshiba P205 laptop

---

### Post by Ceyx on 2009-04-05
I've had the same problem and this page helped alot...scroll down about half way.  I disabled the driver that Ubuntu defaulted to and used Synaptic to get the backport from my install CD...

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

Ciao

---

