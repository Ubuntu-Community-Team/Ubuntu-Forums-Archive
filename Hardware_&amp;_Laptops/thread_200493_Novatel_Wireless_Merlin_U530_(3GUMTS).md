---
title: "Novatel Wireless Merlin U530 (3G/UMTS)"
date: 2006-06-20
forum: Hardware &amp; Laptops
---

### Post by hfdragon on 2006-06-20
I had the card mentioned aboce working perfectly with breezy, but now I have problems with Dapper.

It seems that there are a lot of errors with RX paquets, and the data transfer rate is  now very very low... :( :( 

Anyone has come up with this problem ?

here is my dmesg when I plug the card in :

[17261823.772000] pccard: PCMCIA card inserted into slot 0
[17261823.772000] pcmcia: registering new device pcmcia0.0
[17261823.772000] pcmcia: registering new device pcmcia0.1
[17261823.908000] 0.0: ttyS0 at I/O 0x3f8 (irq = 3) is a 16550A

Are these 2 devices registered normal ??

---

### Post by hfdragon on 2006-06-25
It seems that window$ is also registering two devices, so i figure this is something normal...

But my modem card is still not working properly, as it was with breezy :-(

---

### Post by Carlos Santiago on 2006-10-24
Hi. I have an merlin 630 and i have solved the slow problem changing the baud rate to 460800 (instead of the 115200). 
However i had a problem, the card sometimes is ttyS0, and ther times is ttyS4, what make me to change the connection script. Do you also have this problem? How can I for the ttyS to be always the same? 
ty

---

### Post by Carlos Santiago on 2006-11-03
I also add the following AT command to the chat script (/etc/chatscript/ppp0) imediatlly after ATZ

  AT$NWRAT=0,2

---

### Post by YaseenKriel on 2006-11-16
i have a merlin U630 card and i have managed to install GPRS easy connect but when u choose a port and try to connect get an error. How are u guys connecting with your cards?

[http://www.gprsec.hu/modules/news/view.php?id=260](http://www.gprsec.hu/modules/news/view.php?id=260)

[17181042.400000] pcmcia: registering new device pcmcia0.0
[17181042.400000] pcmcia: registering new device pcmcia0.1
[17181042.620000] 0.0: ttyS0 at I/O 0x3f8 (irq = 3) is a 16550A
[17181042.660000] 0.1: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A

---

### Post by magicfab on 2007-01-26
Unfortunately lots of manual intervention is required to configure these cards. Your best bet is to formally complain about official support for Linux directly to your provider and to merlin. If enough people do that, they will probably provide official .deb packages for Ubuntu and other packages for other distributions or better yet, have them commercially packaged and offered by Canonical or else.

---

### Post by Carlos Santiago on 2007-07-10
I made this DEB package for my PCMCIA Wireless UMTS / 3G modem (Novatel Merlin U630)
to connect to my ISP ([www.kanguru.pt](www.kanguru.pt))

---

