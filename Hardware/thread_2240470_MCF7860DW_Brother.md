---
title: "MCF7860DW Brother"
date: 2014-08-20
forum: Hardware
---

### Post by rickm1945 on 2014-08-20
I have instaled the drives from Brother. I have a wireless connection. The printer works fine, but can't get scanner to work. The drivers are installed.
Do I need to Install the PC FAX Drivers as a separate install?
Output:
```
 richard@richard-Studio-XPS-8100:~$  dpkg -l | grep Brother
ii  brscan-skey                                           0.2.4-1                                             amd64        Brother Linux scanner S-KEY tool
ii  brscan4                                               0.4.2-1                                             amd64        Brother Scanner Driver
ii  cupswrappermfc7860dw                                  2.0.4-2                                             i386         Brother MFC7860DW CUPS wrapper driver
ii  mfc7860dwlpr                                          2.1.0-1                                             i386         Brother MFC-7860DW LPR driver
ii  printer-driver-ptouch                                 1.3-8                                               amd64        printer driver Brother P-touch label printers
richard@richard-Studio-XPS-8100:~$ 

```

---

### Post by deb2014 on 2014-08-20
Hello,

I have this very same printer and its scanner works fine with linux, well that is to say I managed to get it friendly with my linux laptop at least.
I mean that I did not make any installation process on my laptop side, I just configured the printer to send automaticaly the (manually) scanned pages
to my laptop through its FTP server.

If you are intestested in that, read the printer manual, it is rather well explained.
I also heard about the way you see it, but di not go far int that direction.


Best regards

---

### Post by rickm1945 on 2014-08-20
I had the printer and then when I tried to print it gave error,"Printer Not Found"

---

### Post by rickm1945 on 2014-08-20
I have Printer back after resetting my network, but scanner is still not working and neither is PCFAX.
```
 http://localhost:631/printers/ Gave this return.

[TABLE="class: list"]
[TR]
[TD][Brother-MFC-7860DW]("http://localhost:631/printers/Brother-MFC-7860DW")[/TD]
[TD]Brother MFC-7860DW[/TD]
[TD][/TD]
[TD]Brother MFC-7840W BR-Script3[/TD]
[TD]Idle - "Waiting for printer to finish."[/TD]
[/TR]
[/TABLE]

```
```
richard@richard-Studio-XPS-8100:~$ dpkg -l | grep Brother
ii  brscan-skey                                           0.2.4-1                                             amd64        Brother Linux scanner S-KEY tool
ii  brscan4                                               0.4.2-1                                             amd64        Brother Scanner Driver
ii  cupswrappermfc7860dw                                  2.0.4-2                                             i386         Brother MFC7860DW CUPS wrapper driver
ii  mfc7860dwlpr                                          2.1.0-1                                             i386         Brother MFC-7860DW LPR driver
ii  printer-driver-ptouch                                 1.3-8                                               amd64        printer driver Brother P-touch label printers
richard@richard-Studio-XPS-8100:~$

```

```
richard@richard-Studio-XPS-8100:~$ brsaneconfig4 -a name=MFC-7860DW model=MFC-7860DW ip=192.168.1.7
"MFC-7860DW" is already registered.
richard@richard-Studio-XPS-8100:~$ 

```

Can anybody find what I'm doing wrong?

---

