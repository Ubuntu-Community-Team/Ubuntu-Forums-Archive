---
title: "Printing only works with OpenOffice"
date: 2020-05-18
forum: Hardware
---

### Post by olaf1234 on 2020-05-18
Hi!

I can only print with OpenOffice, but not with the other software
- Abiword
- Gnumeric
- Chromium browser
- Pluma
- ...
I installed the printer (Epson ET-4750) first "driverless", then again with the correct driver from Epson.


Test page in cups works.


If I use Abiword or similar and start a print command, the printer display briefly says that it is printing and then immediately that the print is finished.

CUPS error log:
> E [18/May/2020:11:28:25 +0200] [cups-deviced] PID 2221 (gutenprint52+usb) stopped with status 1!
...
E [18/May/2020:12:12:03 +0200] [Job 19] Druckauftrag wurde am Drucker abgebrochen.

(E [18/May/2020:12:12:03 +0200] [Job 19] Print job was canceled on the printer.)

What can that be?

Olaf

---

### Post by brian_p on 2020-05-18
You are using Ubuntu 18.04? The printer is connected to the network (wireless)? Give the outputs of ```
lpinfo -v
``` ```
lpstat -t
```

---

### Post by olaf1234 on 2020-05-18
Lubuntu (lxle) 18.04

lpinfo -v:
> 
network beh
file cups-brf:/
direct ecblp:/var/run/ecblp0
network lpd
serial serial:/dev/ttyS0?baud=115200
serial serial:/dev/ttyS1?baud=115200
network ipp
network socket
network https
network ipps
network http
direct hp
direct hpfax
network dnssd://EPSON%20ET-4750%20Series._ipp._tcp.local/?uuid=cfe92100-67c4-11d4-a45f-381a52492d61
network dnssd://EPSON%20ET-4750%20Series._pdl-datastream._tcp.local/
network ipp://EPSON-4750.local:631/ipp/print


lpstat -t:
> 
Zeitplandienst läuft
systemvoreingestelltes Ziel: ET-4750
Gerät für ET-4750: dnssd://EPSON%20ET-4750%20Series._ipp._tcp.local/?uuid=cfe92100-67c4-11d4-a45f-381a52492d61
ET-4750 akzeptiert anfragen seit Mo 18 Mai 2020 12:12:03 CEST
Drucker ET-4750 ist im Leerlauf.  Aktiviert seit Mo 18 Mai 2020 12:12:03 CEST
	Druckauftrag wurde am Drucker abgebrochen.


---

### Post by brian_p on 2020-05-18
Ok, the printer is network connected; that's good. Please give what you get for ```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _uscan._tcp
```

Instead of a "driverless" print queue we will set up an "everywhere" queue and see how we go on: ```
lpadmin -p et4750 -v ipp://EPSON-4750.local:631/ipp/print -E -m everywhere
```

Is printing to et4750 working?

---

### Post by olaf1234 on 2020-05-18
[B]avahi-browse -rt _ipp._tcp
[/B]> 
+ wlx0013ef1007d3 IPv6 EPSON ET-4750 Series                          Internet Printer     local
+ wlx0013ef1007d3 IPv4 EPSON ET-4750 Series                          Internet Printer     local
= wlx0013ef1007d3 IPv6 EPSON ET-4750 Series                          Internet Printer     local
   hostname = [EPSON-4750.local]
   address = [192.168.178.213]
   port = [631]
   txt = ["TLS=1.2" "UUID=cfe92100-67c4-11d4-a45f-381a52492d61" "note=" "adminurl=http://EPSON-4750.local.:80/PRESENTATION/BONJOUR" "priority=30" "mopria-certified=1.3" "PaperMax=legal-A4" "kind=document,envelope,photo" "rfo=ipp/faxout" "Fax=T" "Scan=T" "Duplex=T" "Color=T" "qtotal=1" "rp=ipp/print" "pdl=application/octet-stream,image/pwg-raster,image/urf,image/jpeg" "product=(EPSON ET-4750 Series)" "usb_MDL=ET-4750 Series" "usb_MFG=EPSON" "ty=EPSON ET-4750 Series" "txtvers=1"]
= wlx0013ef1007d3 IPv4 EPSON ET-4750 Series                          Internet Printer     local
   hostname = [EPSON-4750.local]
   address = [192.168.178.213]
   port = [631]
   txt = ["TLS=1.2" "UUID=cfe92100-67c4-11d4-a45f-381a52492d61" "note=" "adminurl=http://EPSON-4750.local.:80/PRESENTATION/BONJOUR" "priority=30" "mopria-certified=1.3" "PaperMax=legal-A4" "kind=document,envelope,photo" "rfo=ipp/faxout" "Fax=T" "Scan=T" "Duplex=T" "Color=T" "qtotal=1" "rp=ipp/print" "pdl=application/octet-stream,image/pwg-raster,image/urf,image/jpeg" "product=(EPSON ET-4750 Series)" "usb_MDL=ET-4750 Series" "usb_MFG=EPSON" "ty=EPSON ET-4750 Series" "txtvers=1"]



[B]avahi-browse -rt _uscan._tcp
[/B]-> nothing, empty

[B]lpadmin -p et4750 -v ipp://EPSON-4750.local:631/ipp/print -E -m everywhere
[/B]-> nothing


> **brian_p said:**
> 
[COLOR=#000000]Is printing to et4750 working?[/COLOR]

Unfortunately, no

Just overlooked:
> **brian_p said:**
> network (wireless)?
Yes, wireless

---

### Post by brian_p on 2020-05-18
[QUOTE=olaf1234;13958339]

[B]avahi-browse -rt _uscan._tcp
[/B]-> nothing, empty

That's ok. The device does not offer a uscan service.

[B]lpadmin -p et4750 -v ipp://EPSON-4750.local:631/ipp/print -E -m everywhere
[/B]-> nothing

No response means the command completed successfully. Nothing to worry about. I have checked the **lpadmin** command and it is ok.

Can you print ```
lp -d et4750 /etc/nsswitch.conf
```

---

### Post by olaf1234 on 2020-05-18
[B]lp -d et4750 /etc/nsswitch.conf
[/B]> 
Anfrage-ID ist et4750-20 (1 Datei(en))

and the 4750 printed a page  (see attached pdf)

---

### Post by brian_p on 2020-05-18
> **olaf1234 said:**
> [B]lp -d et4750 /etc/nsswitch.conf
[/B]
and the 4750 printed a page  (see attached pdf)

The 4750 queue works! As far as I am concerned it should therefore work from any application. Which application did you print from last time?

---

### Post by olaf1234 on 2020-05-18
I'm not sure if I understand the question correctly (my English is not so good -> google translate).


I tried printing from the above applications, it only worked from OpenOffice and testpage from cups [http://localhost:631](http://localhost:631).
The last attempt (before our tests here) was successful with OpenOffice Calc.

EDIT
I just found a new line in the CUPS error log:
E [18/May/2020:16:04:37 +0200] [cups-deviced] PID 5464 (gutenprint52+usb) stopped with status 1!

That was 5 3/4 hours ago. But I don't know which attempt.

---

### Post by brian_p on 2020-05-18
I had an idea of what your issue is. Maybe it is wrong,

[https://forums.linuxmint.com/viewtopic.php?f=51&t=319420](https://forums.linuxmint.com/viewtopic.php?f=51&t=319420)

---

### Post by olaf1234 on 2020-05-18
> **brian_p said:**
> I had an idea of what your issue is. Maybe it is wrong,

[https://forums.linuxmint.com/viewtopic.php?f=51&t=319420](https://forums.linuxmint.com/viewtopic.php?f=51&t=319420)



I read through this and found that I did not understand you correctly at some point (English ...):


The user dhfx on linuxmint wrote
> I executed" lpadmin -p 4720 -v ipp: //EPSONC72B8C.local: 631 / ipp / print -E -m everywhere "and tried printing from Firefox using the" 4720 "queue, and it worked. Same in Document Viewer with a PDF. 


I did not understand this line here in our thread at all, that this creates a second printer and therefore did not even test to print with it. I thought this line would also start printing.


I've only just seen and tested that, and lo and behold, I can use it to print from Chromium, Gnumeric and Abiword (and probably all others).


Unfortunately I don't understand the rest of the post on Linuxmint.
Is this a usable permanent solution now?


EDIT
Why does Cups always tell me
> Not authorized
Enter your username and password or the root username and password to access this page. If you use Kerberos authentication, make sure you have a valid Kerberos ticket. 
I gave my account all rights, I think.
There is also no password query from CUPS.
EDIT3
Solution found for CUPS problem: [https://ubuntuforums.org/showthread.php?t=2388741](https://ubuntuforums.org/showthread.php?t=2388741)

EDIT2
It works, I seem to be able to print everything (and still work a lot this evening), thank you very much, Brian!

---

### Post by brian_p on 2020-05-18
Hello Olaf,

Sorry if I have not been clear but I am pleased you are now able to print.

Your Epson printer has a bug in its firmware. I have met this on two other printers. Keep using the everywhere queue. The bug is fixed in later editions of Ubuntu.

---

