---
title: "How to enable the Wlan hardware by the terminal ? (fn keys don t work) Toshiba NB200"
date: 2012-01-06
forum: Hardware
---

### Post by solocan on 2012-01-06
Hi,

i have got this known problem of the toshiba laptops, so that the fn keys (fn+F8 ) dont work and i cant enable the wlan hardware.. Since 2 days i m looking for a solution to get the fn keys working properly but i gave this now up...so now im searching for an alternative solution to get the wlan hardware enabled by sending a signal from terminal.. 

i am sure that the wlan driver works right because on the installation it detects and asks the password..but on the connection table always : disabled by the hardware..

my question is:** How do i enable the wlan hardware by the terminal?**

---

### Post by solocan on 2012-01-06
**Response of the rfkill list:**
reiner@NB200:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
[B]
Response of the iwconfig[/B]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power= off   
          Retry  long limit:7   RTS thr: off   Fragment thr off
          Power Management: off

---

### Post by LinuxNubian on 2012-01-09
I have the same problem with Toshiba Satellite M35x-S309. 
$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

Cheers

---

