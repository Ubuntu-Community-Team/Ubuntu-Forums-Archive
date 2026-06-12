---
title: "[B]i Dont belive that there is no soluion for usb devices on ubuntu???[/B]"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by zorro26 on 2007-05-19
**i Dont belive that there is no soluion for usb devices on ubuntu???**

am i right, cause i have created few posts, but no solution. searched and found quite a few threads for the same subject but with no replays. there should be a way to make it work.

Right now my problem, my system wont detect my psp or cell phone(smasung i300) which used be detect by ubuntu dark drapper for few mins, but since i updated it to fiesty fawn that dosnt work aswell... what should i do???

without conecting my phone or psp this is my dmesg | tail

> kal@kal:~$ dmesg | tail
[ 1608.475179] usb 2-1: device descriptor read/8, error -110
[ 1610.802158] usb 2-1: device descriptor read/8, error -110
[ 1610.925472] usb 2-1: new full speed USB device using ohci_hcd and address 7
[ 1614.557079] usb 2-1: device descriptor read/8, error -110
[ 1618.005404] usb 2-1: device descriptor read/8, error -110
[ 1807.102210] Losing some ticks... checking if CPU frequency changed.
[ 1954.515322] usb 4-1: new high speed USB device using ehci_hcd and address 12
[ 1954.581147] usb 4-1: configuration #1 chosen from 1 choice
[ 1954.631594] usb 4-1: USB disconnect, address 12
[ 1954.730455] usbcore: registered new interface driver libusual


after i conect both

> kal@kal:~$ dmesg | tail
[ 1610.925472] usb 2-1: new full speed USB device using ohci_hcd and address 7
[ 1614.557079] usb 2-1: device descriptor read/8, error -110
[ 1618.005404] usb 2-1: device descriptor read/8, error -110
[ 1807.102210] Losing some ticks... checking if CPU frequency changed.
[ 1954.515322] usb 4-1: new high speed USB device using ehci_hcd and address 12
[ 1954.581147] usb 4-1: configuration #1 chosen from 1 choice
[ 1954.631594] usb 4-1: USB disconnect, address 12
[ 1954.730455] usbcore: registered new interface driver libusual
[ 2311.769203] usb 2-1: new full speed USB device using ohci_hcd and address 8
[ 2313.211546] usb 2-1: device descriptor read/64, error -110


to be honest it dosnt make any sense to me but to someone it might, so if you are that someone then, PLEASE PLEASE HELP...

---

### Post by zorro26 on 2007-05-20
**Still no replies** ok... i sreached USB in synaptic package manage, and istalled few stuff like ipod, and mass storage devices etc. reboot and tried to coneect again. now my psp is detected but as ipod..

> [  321.326270] usb 3-2: device descriptor read/64, error -110
[  321.453428] usb 3-2: new full speed USB device using ohci_hcd and address 3
[  322.895778] usb 3-2: device descriptor read/64, error -110
[  330.511223] usb 3-2: device descriptor read/64, error -110
[  330.638382] usb 3-2: new full speed USB device using ohci_hcd and address 4
[  332.918358] usb 3-2: device descriptor read/8, error -110
[  335.243480] usb 3-2: device descriptor read/8, error -110
[  335.370420] usb 3-2: new full speed USB device using ohci_hcd and address 5
[  337.650344] usb 3-2: device descriptor read/8, error -110
[  339.975468] usb 3-2: device descriptor read/8, error -110


phone still dosnt work... 
does anyone know to solve this problem and has no one came accross this problem... :(

---

