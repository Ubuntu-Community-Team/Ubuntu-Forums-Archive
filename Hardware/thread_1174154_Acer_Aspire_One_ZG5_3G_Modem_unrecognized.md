---
title: "Acer Aspire One ZG5 3G Modem unrecognized"
date: 2009-05-30
forum: Hardware
---

### Post by Chiapo on 2009-05-30
I have an Acer Aspire One ZG5 with 1GB RAM & 160GB hdd.
The machine came with WinXP pre-installed.
I installed UNR Jaunty to have a dual boot setup, which works fine... Except the internal 3G Qualcomm modem is not recognized as a modem by Ubuntu.
The modem only works in WinXP.
How can I get the 3G modem to work in Ubuntu?
I have read through the threads regarding the AA1 & Ubuntu, but apparently I'm one of the few people who have had an issue getting the AA1 online with the Qualcomm modem. 
In another thread, I was instructed to apt-get packages then recompile usbserial into the kernel, but if I can't get online how can I download packages?
Am I the only one having an issue with getting the Qualcomm modem to work with Ubuntu Netbook Remix 9.04?

---

### Post by amartz on 2009-07-20
No, unfortunately. I've got a ZG8, and UNR doesn't pick up the 3G modem either. Wifi works fine.

---

### Post by Chiapo on 2009-12-03
I just finished installing a freshly downloaded xubuntu 9.10 & the Qualcomm 9212 HS-USB modem works fine!

:popcorn:

---

### Post by amartz on 2009-12-03
> **Chiapo said:**
> I just finished installing a freshly downloaded xubuntu 9.10 & the Qualcomm 9212 HS-USB modem works fine!

:popcorn:

Do you still need to go to XP first?  I'll give you a couple of weeks to see if you still like it, then I'll get with you for the specifics for my ZG8.
Art

---

### Post by Chiapo on 2009-12-03
I downloaded xubuntu 9.10 in WinXP, then inatalled... The modem was recognized & assigned to /dev/ttyUSB0.

I downloaded kubuntu 9.10 Desktop .ISO last night using the Qualcomm 9212, then installed kubuntu 9.10. After that, no 3g connection.
I swear the 3g modem was working a few hours ago!

Now not even the Windows trick will let the modem be seen.

I saw somewhere to try the following:
```
route default /dev/ttyUSB0
```

or something like that, but when I tried it said something about /dev/ttyUSB0 unavailable, not sure, I'll boot into xubuntu 9.10 & see after I download gobi_loader & usb_modeswitch.

Feel free to laugh. :confused:

---

### Post by amartz on 2009-12-03
> **Chiapo said:**
> I downloaded xubuntu 9.10 in WinXP, then inatalled... The modem was recognized & assigned to /dev/ttyUSB0.

I downloaded kubuntu 9.10 Desktop .ISO last night using the Qualcomm 9212, then installed kubuntu 9.10. After that, no 3g connection.
I swear the 3g modem was working a few hours ago!
 :confused:

Type lsusb and see if you get "Bus 001 Device 004: ID 05c6:9212 Qualcomm, Inc."  If it comes back as something other than 9212, that means that the firmware is not getting loaded into the modem. That's what XP was doing for you. With 9.10, I guess there are commands and utilities to load the firmware from 9.10, without windows. I've been watching a thread at [http://ubuntuforums.org/showthread.php?t=1008200](http://ubuntuforums.org/showthread.php?t=1008200) about this, but haven't tried it yet myself. In particular the parts about the gobi.loader and qcserial.
Art

---

### Post by Chiapo on 2009-12-04
I'm posting from within xubuntu 9.10 Desktop using the Qualcomm 9212 3g modem right now.

The steps I made to get online are listed here: [http://ubuntuforums.org/showthread.php?t=1157846&page=6](http://ubuntuforums.org/showthread.php?t=1157846&page=6)

msignor says the gobi_loader works for him, so I'll be trying that next.

Cheers! & Thanks for your help! :KS

---

### Post by Chiapo on 2009-12-05
Update:

Evidently, the qcserial driver module is a bit buggy, as the modem is sometimes unavailable even when doing the Win > gobi shuffle.

When the modem is unavailable, the network icon on my xfce4 panel spins abnormally fast, and spins indefinitely.
Sometimes the system reports a connection has been made via the Mobile Broadband GSM connection, but no page will load, ping results in Host Not Found, or Unknown Host, and the connection information appears the same as when the connection is good.

I wonder if there is some authorization issue preventing the modem from being available from time to time? 

I'm currently posting from within xubuntu 9.10, which has been updated with the most recent updates.
The Qualcomm 9212 modem connects automatically, as specified in Network Manager, but not every time.


I did the make & make install of gobi_loader, but haven't noticed any difference in modem availability.

On the gobi_loader download page is three separate versions of gobi_loader. Since my firmware was found in a directory named "2" I downloaded the 2nd version of gobi_loader.

I shall test the other two.

On a side note, WiFi works wonderfully! I also believe the 3g modem is faster in *buntu than WinXP, but that may just be my own prejudice. :p

---

### Post by coljohnhannibalsmith on 2011-05-08
Hello,

I am working on this problem myself, and the following site is a good place to start:

[http://linmodems.org/](http://linmodems.org/)




Hannibal

---

