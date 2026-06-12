---
title: "ma620 usb irda"
date: 2006-06-30
forum: Hardware &amp; Laptops
---

### Post by c4pp4 on 2006-06-30
connect usb/irda (ID 0df7:0620) adapter
command:```
dmesg | grep tty
```
dump:```
[4294704.782000] usb 1-1: PL-2303 converter now attached to [COLOR="Red"]ttyUSB0[/COLOR]
```
command:```
sudo apt-get install irda-utils
```
command:```
sudo gedit /etc/default/irda-utils
```
```
ENABLE="true"
AUTOMATIC="true"
DISCOVERY="true"
DEVICE="/dev/[COLOR="Red"]ttyUSB0[/COLOR]"
DONGLE="ma600"
SETSERIAL=""
```

[COLOR="blue"]* for Dapper and Edgy (not necessary for Breezy) *
command:```
sudo modprobe irda
```
command:```
sudo gedit /etc/modules
```
add new line:
```
irda
```
**********************************
[/COLOR]
command:```
sudo /etc/init.d/irda-utils start
```
command:```
sudo irdadump
```
dump:
```
16:00:42.064181 xid:cmd c3d543e3 > ffffffff S=6 s=0 (14)
16:00:42.154104 xid:cmd c3d543e3 > ffffffff S=6 s=1 (14)
16:00:42.244091 xid:cmd c3d543e3 > ffffffff S=6 s=2 (14)
16:00:42.334077 xid:cmd c3d543e3 > ffffffff S=6 s=3 (14)
16:00:42.424063 xid:cmd c3d543e3 > ffffffff S=6 s=4 (14)
16:00:42.514049 xid:cmd c3d543e3 > ffffffff S=6 s=5 (14)
16:00:42.604039 xid:cmd c3d543e3 > ffffffff S=6 s=* ubuntu hint=0400 [ Computer ] (22)
```

when i used sony ericsson K300i:
```
16:01:15.059106 xid:cmd c3d543e3 > ffffffff S=6 s=0 (14)
16:01:15.149089 xid:cmd c3d543e3 > ffffffff S=6 s=1 (14)
16:01:15.239074 xid:cmd c3d543e3 > ffffffff S=6 s=2 (14)
16:01:15.325057 xid:rsp c3d543e3 < 00007c49 S=6 s=2 K300 series hint=9124 [ PnP Modem IrCOMM IrOBEX ] (28)
16:01:15.329063 xid:cmd c3d543e3 > ffffffff S=6 s=3 (14)
16:01:15.419053 xid:cmd c3d543e3 > ffffffff S=6 s=4 (14)
16:01:15.509041 xid:cmd c3d543e3 > ffffffff S=6 s=5 (14)
16:01:15.599022 xid:cmd c3d543e3 > ffffffff S=6 s=* ubuntu hint=0400 [ Computer ] (22)
```
so it works... :)

browser:
command:```
sudo apt-get install kdebluetooth
```
launch Konqueror and insert target:
```
obex://irda/
```

---

### Post by Cyr4x on 2007-01-21
I've got a MI-620 model (looks almost the same as on attached image) and this howto doesn't work. Dmesg doesn't see anything at ttyUSB0 and irda-utils too. I've tried with USB 2.0 and 1.1 - nothing happens.

---

### Post by c4pp4 on 2007-05-05
> **Cyr4x said:**
> I've got a MI-620 model (looks almost the same as on attached image) and this howto doesn't work. Dmesg doesn't see anything at ttyUSB0 and irda-utils too. I've tried with USB 2.0 and 1.1 - nothing happens.

Maybe you can try ttyUSB1 ttyUSB2 ...

---

### Post by chicoicho on 2007-06-22
Greath man you are the best this help my greath many thanks :popcorn:

---

### Post by esmerine on 2008-01-17
I've got ma660 and this helped me connect it. When I put my se in front of adapter irdadump sees it. Hooray. Thank you.

---

