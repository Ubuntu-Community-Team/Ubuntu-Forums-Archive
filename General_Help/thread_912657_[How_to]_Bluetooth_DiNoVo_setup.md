---
title: "[How to] Bluetooth DiNoVo setup"
date: 2008-09-06
forum: General Help
---

### Post by webnub on 2008-09-06
I had problems with my logitech diNovo keyboard and mouse, which went dead when computer went into sleep mode.. I managed to fix it like this 
(the keyboard and mouse are supposed to be installed and bonded properly already-there are several threads which describe how to do this-):

I typed  ```
gksudo gedit /etc/default/bluetooth
``` in terminal and then in the bluetooth file, in the HIDD part , I added 

```

sudo hciconfig hci0 down
sudo hciconfig hci0 up
```

(Apart from that it should also be ```
HIDD_ENABLED=1
``` and in addition 
```
HIDD_OPTIONS="-i hci0 --connect 00:07:61:24:0E:B9 --connect 00:07:61:23:eb:58 --master --server
``` where 00:07:61:24:0E:B9 and 00:07:61:23:eb:58 are the bluetooth addresses of my keyboard and mouse. You should add yours.


I hope this works:)

---

### Post by teaker1s on 2008-11-01
for dinovo mini I found that the suggested howto works with 

# HID daemon
HIDD_ENABLED=1
sudo hciconfig hci0 down
sudo hciconfig hci0 up
HIDD_OPTIONS="-i hci0 --connect 046d:c71f --connect 046d:c71e --connect  046d:0b07

if you tried  
> options usbhid quirks=0x046d:0xc71f:0x00080000
 remove from /etc/modprobe.d/options,

created a wiki page here
[https://wiki.ubuntu.com/logitech%20dinovo%20mini]("https://wiki.ubuntu.com/logitech%20dinovo%20mini")

---

