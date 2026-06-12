---
title: "3Com PCMCIA Bluetooth (3CRWB6096)"
date: 2006-02-19
forum: Hardware &amp; Laptops
---

### Post by nolifer on 2006-02-19
I can't get my bluetooth card working in ubuntu 5.10. I have 2.6.12-10 kernel and I've tried to follow this [guide.]("http://www.teaparty.net/technotes/blue-gprs.html")

I've succesfully installed all packages and modified that modules.conf. 
/etc/init.d/bluez-utils starts without errors, but hciconfig/lspci does not recognize that card.

[Image]("http://pc.watch.impress.co.jp/docs/2002/0110/synnex2.jpg")

---

### Post by nolifer on 2006-02-20
dmesg says
"bt3c_open: Firmware request failed"

What is that file that it requests, and where should it be?

---

### Post by nolifer on 2006-02-23
[QUOTE=nolifer]dmesg says
"bt3c_open: Firmware request failed"

What is that file that it requests, and where should it be?[/QUOTE]

Anyone? :)

---

### Post by macko on 2007-10-03
Read here
[http://www.dotmana.com/index.php/?m=200703](http://www.dotmana.com/index.php/?m=200703)
under Bluetooth Wireless PC card 3COM 3CRWB6096

Basically, you have to download and unpack windows drivers. (and it seems that 3com is blocking download of their drivers from Linux systems - I was able to download only from my WinXP machine - bastards! :mad:)

---

