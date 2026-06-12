---
title: "Asus A7u can't identify 3g Modem correctly"
date: 2009-02-16
forum: Hardware
---

### Post by Dezfor on 2009-02-16
A have 3G modem: Samsungh Z810 (with micro CD card)
My laptop: Asus A7U
I use Ubuntu 8.10: 
```
root@andrew-laptop:~# uname -a
Linux andrew-laptop 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64 GNU/Linux
```
So, i have really strange problem. If i connect modem to my laptop it displays as CD-Rom Disc and lsusb sees it like: ```
Bus 003 Device 004: ID 05c6:1000 Qualcomm, Inc. 
```
If i wanna my Ubuntu to see this device as modem i should firstly login into my Windows XP and connect modem via usb. Then launch internet connection and after it restart windows and login in Ubuntu(while doing this i don't disconnect 3G device) and after it it appears as Samsungh Z100 i can connet using Gnome-ppp and usb_modeswitch. Lsusb in such situation says: ```
Bus 001 Device 003: ID 04e8:6601 Samsung Electronics Co., Ltd Z100 Mobile Phone
```
But as u understand such system of turning on Momem isn't suitable for me. And i even can't delete XP because without it i couldn't launch internet on Linux :)
Really i don't know what to do. Can u suggest something?

P.S. when modem identifies correctly i see two USB devices and one CD-Rom if not correctly - only CD-Rom. In XP it looks like two CD-Roms and one USB device. On the Cd-rom are drivers for Windows. Using Linux i can't open them

---

### Post by Dezfor on 2009-03-05
My problem was solved. I don't know how, but now linux can see my 3g device without any problems. Today i only installed wine and some new updates. May be new updates helped me. But when i wrote this post i had all newest updates for those period :)

---

