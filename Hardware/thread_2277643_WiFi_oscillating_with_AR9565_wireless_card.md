---
title: "WiFi oscillating with AR9565 wireless card"
date: 2015-05-10
forum: Hardware
---

### Post by adfelippe on 2015-05-10
Hi everyone,

I've just got a new laptop and installed Ubuntu 14.04 on it. Problem is: WiFi connection is terrible. It keeps oscillating, barely runs fast and sometimes it drops the connection.
lspci gives me:
```
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
```
lsmod gives me ath9k module:
```
ath9k                 137283  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
```
And I also noticed this messages on dmesg:
```
[ 1138.128124] ath: phy0: Failed to stop TX DMA, queues=0x002!
[ 1176.216746] ath: phy0: Failed to stop TX DMA, queues=0x002!
[ 1204.300726] ath: phy0: Failed to stop TX DMA, queues=0x002!
[ 1245.536628] ath: phy0: Failed to stop TX DMA, queues=0x002!
[ 1277.212100] ath: phy0: Failed to stop TX DMA, queues=0x002!
[ 1289.891579] ath: phy0: Failed to stop TX DMA, queues=0x002!
```

They keep showing up while the connection gets worse.

I've already try adding "options ath9k nohwcrypt=1" to the ath9k.conf file and changing my wifi router settings to AES encryption only.

Has anyone experienced the same issues? I just want to be sure it's not a driver issue (since I've had problems with ath9k module in the past - another laptop though) before sending my pc back to the manufacturer to be fixed :D

---

### Post by dino99 on 2015-05-10
that is how all internet connections are: the speed you get is the lowest rate against the sender/isp/you, the bandwidth is shared between the connected users. So its like a roller-coaster ;)

---

### Post by GrouchyGaijin on 2015-05-10
For what it's worth, I had a similar problem.  All the other devices in the house connected fine, it was just my Ubuntu laptop that was having trouble.  After a lot of reading and not having any luck, I changed the router's settings from Auto to only use 20mhz.  Since then my laptop has connected well.

---

### Post by DAVID_GREGORY_KERR on 2015-08-11
I have the same plug-in board in my Acer Aspire TC-220 and have no problem with Linux Mint Cinnamon 17 (Qiana) 64bit why not download the source code then while in root terminal do (chmod 0044 <ret>,make <ret>,make install <ret>) no need to do ./configure <ret> as I tried it and got the error no configure file associated with this file so the make install should install it for you do a reboot and see if this solves the problem but always look for the latest stable drives if you can.

---

