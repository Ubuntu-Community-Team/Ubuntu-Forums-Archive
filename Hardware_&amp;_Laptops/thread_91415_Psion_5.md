---
title: "Psion 5"
date: 2005-11-17
forum: Hardware &amp; Laptops
---

### Post by xmastree on 2005-11-17
Somebody gave me a couple of Psion 5 PDAs. But no manuals... :confused: 

Anyway, searching the forums I figured I need p3nfs which I installed. 
I have an InfraRed port, but I've never used it with linux. It shows up if I do lsusb:```
Bus 002 Device 004: ID 066f:4200 SigmaTel, Inc. STIr4200 IrDA Bridge
```

How do I instruct p3nfs to use the IR device? Man page says  /dev/ircomm0  but that device doesn't exist. Do I need to install something

I installed irdautils but running irpsion5 gives:```
No IRDA device found
```

---

### Post by johannes on 2005-11-19
I have never used the Irda port on my laptop with a PDA device since I don't have one, but these are the steps I use to get irda working with to transfer files to/from my cell phone, a Panasonic x200.

```
sudo apt-get install ircp irda-utils openobex-apps
```

```
sudo modprobe irda irtty_sir sir_dev
```

```
sudo gedit /etc/modules
```
and write in the modules you modprobed at the end of the file.

After a system reboot you can check if it's working by activating irda on your mobile device, placing it in front fo your the irda port on your computer and running:
```
sudo irdadump
```

You should then see something like this:
```
14:17:29.114250 xid:cmd 752931d2 > ffffffff S=6 s=0 (14)
14:17:29.204234 xid:cmd 752931d2 > ffffffff S=6 s=1 (14)
14:17:29.294217 xid:cmd 752931d2 > ffffffff S=6 s=2 (14)
14:17:29.384205 xid:cmd 752931d2 > ffffffff S=6 s=3 (14)
14:17:29.471884 xid:rsp 752931d2 < 67bf8d0e S=6 s=3 Panasonic X200 hint=8020 [ IrOBEX ] (31)
14:17:29.474191 xid:cmd 752931d2 > ffffffff S=6 s=4 (14)
14:17:29.564175 xid:cmd 752931d2 > ffffffff S=6 s=5 (14)
14:17:29.654162 xid:cmd 752931d2 > ffffffff S=6 s=* dreamscape hint=0400 [ Computer ] (26)
```
(dreamscape is the host name on my computer :) )

Additionally, you may need to add:
```
sudo mknod /dev/ircomm0 c 161 0
sudo mknod /dev/ircomm1 c 161 1
```
That's not needed for me, but I read it somewhere on the forum.

It seems you have found a program interface to use with your PDA that I guess should work with this method, but in case someone else finds this tread and wants to use it with a cell phone, here is what I use to transfer files:

Sending from computer:
```
irobex_palm3 /path/to/file.xxx
```

Recieving to computer:
```
irobex_palm3
```

Hope it helps. :)

---

