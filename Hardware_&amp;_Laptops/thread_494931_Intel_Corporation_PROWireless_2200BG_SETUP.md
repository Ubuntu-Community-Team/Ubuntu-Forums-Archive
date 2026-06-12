---
title: "Intel Corporation PRO/Wireless 2200BG SETUP"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by gLa on 2007-07-07
Dear all,
   
       I have HP Pavilion ze2000 laptop, I can't setup my wireless adapter Intel Corporation PRO/Wireless 2200BG and search for wireless network . please can any body help me ?
   I'm using Kubuntu Feisty ,  

lspci | grep Wireless outputs

02:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

thanks

---

### Post by bukwirm on 2007-07-07
That wireless adapter should work fine.

What output do you get from
*iwconfig*
*iwlist scan*

---

### Post by gLa on 2007-07-07
ghaleb@ghaleb-laptop:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:""
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ghaleb@ghaleb-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
ghaleb@ghaleb-laptop:~$

---

### Post by bukwirm on 2007-07-08
It appears that your wireless card is turned off - try turning it on (usually a keyboard shortcut - it's Fn + F2 on my Dell Inspiron 6000).

Then try those commands again.

---

### Post by shaharudin on 2008-06-23
can we use this? :

```
sudo ifconfig eth1 up
```

---

