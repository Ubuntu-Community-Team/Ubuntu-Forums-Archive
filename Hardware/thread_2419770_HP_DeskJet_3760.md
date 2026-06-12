---
title: "HP DeskJet 3760"
date: 2019-05-25
forum: Hardware
---

### Post by kernowroger on 2019-05-25
Hi

Having problems printing from Ubuntu with my new HP Deskjet 3760. It&#8217;s connected to the Internet and works fine printing from my iPhone, Chromebook and via Google&#8217;s Cloud print.

I&#8217;ve added the 3760 as a new printer, installed the recommended drivers and it&#8217;s shown in my  settings window. The Device URL socket://192.1.12 is correct and I&#8217;ve tried using Connections as IPP network printer via DNS-SD and AppSocket/HP JetDirect. I've also connected via a USB cable

My PC seems to be connected to the printer - it appears as one of the options when I try to print a document - but when I press &#8216;Print&#8217; nothing happens apart from the on/off light on the printer flashing. This is the case for both the wireless and the USB cable connection. My old printer, an HP Deskjet 1050A works fine with a USB cable connection.

When I try to print a document, the on/off light on the printer flashes - as though it 'thinks' it's printing - but nothing gets printed. The only thing I can think of is that there's something wrong with the drivers, but HP support for Linux has been pretty good in the past, and the 3700 series is a very common printer; so that seems unlikely. I've also tried setting up the printer as a new device using HPLIP, but when a search for USB connections,  I get no device found

All suggestions will be much appreciated.

RogerD

---

### Post by CatKiller on 2019-05-25
> **kernowroger said:**
> My PC seems to be connected to the printer - it appears as one of the options when I try to print a document - but when I press ‘Print’ nothing happens apart from the on/off light on the printer flashing. This is the case for both the wireless and the USB cable connection.

Check the printer queue in either the HPLIP interface or the CUPS interface. It sounds like it might be accepting jobs, but "paused."

Using lots of colours and fonts in your posts isn't helpful.

---

### Post by kernowroger on 2019-05-25
Apologies for the fonts and colour - not sure how that happened.

I've tried the HPLIP interface, but it doesn't show my new 3760 printer - just my old 1050 printer - even when I've disconnected the 1050 and connected the 3760 via a USB cable.

---

### Post by brian_p on 2019-05-25
> **kernowroger said:**
> Hi

Having problems printing from Ubuntu with my new HP Deskjet 3760. It’s connected to the Internet and works fine printing from my iPhone, Chromebook and via Google’s Cloud print.

Your are using driverless printing here, so...........

> I’ve added the 3760 as a new printer, installed the recommended drivers and it’s shown in my  settings window. The Device URL socket://192.1.12 is correct and I’ve tried using Connections as IPP network printer via DNS-SD and AppSocket/HP JetDirect. I've also connected via a USB cable

............why bother with drivers here.

[https://wiki.debian.org/QuickPrintQueuesCUPS](https://wiki.debian.org/QuickPrintQueuesCUPS)

---

### Post by kernowroger on 2019-05-25
Many thanks for taking an interest in my problem. I've had a look at the link you supplied, but, having a fairly rudimentary  knowledge of Linux, I'm far from clear as to how it helps.

Could you supply a few more details please?

RogerD

---

### Post by brian_p on 2019-05-25
As detailed at

[https://wiki.debian.org/QuickPrintQueuesCUPS#IPP_Printers](https://wiki.debian.org/QuickPrintQueuesCUPS#IPP_Printers)

there are only two  things for you to do. Please say which of them you do not understand.

---

### Post by kernowroger on 2019-05-26
Sorry, but you'll have to spell out what these two things are.

I've had a go with a couple of entries into a terminal, but, so far, no progress:

roger@desktop:~$ lpstat -a
Deskjet-1050-J410-series accepting requests since Sat 25 May 2019 14:35:59 BST
HP-DeskJet-3700-series accepting requests since Sat 25 May 2019 16:19:06 BST
roger@desktop:~$ CreateIPPPrinterQueues
CreateIPPPrinterQueues: command not found
roger@desktop:~$ systemctl restart cups-browsed
roger@desktop:~$ 

Roger







It will be great to get this printer working.


Deskjet-1050-J410-series accepting requests since Sat 25 May 2019 14:35:59 BST
HP-DeskJet-3700-series accepting requests since Sat 25 May 2019 16:19:06 BST
roger@desktop:~$ CreateIPPPrinterQueues
CreateIPPPrinterQueues: command not found
roger@desktop:~$ systemctl restart cups-browsed
roger@desktop:~$

---

### Post by kernowroger on 2019-05-26
I've had another thought - I'm currently using Ubuntu 16.04 LTS, would it possibly help to upgrade to 18.04 LTS? Form what I can see, support for driverless printing was added to Ubuntu from 17.04.

---

### Post by brian_p on 2019-05-26
> **kernowroger said:**
> 

It will be great to get this printer working.

HP-DeskJet-3700-series accepting requests since Sat 25 May 2019 16:19:06 BST


HP-DeskJet-3700-series is seen by the printing system, so you should be able to print to it with
the comand

```
lp -d /etc/nsswitch.conf
```

in a terminal. Check if you are able to.

If not, give the terminal outputs of

```
lpstat -t
lpoptions -p HP-DeskJet-3700-series
```

---

### Post by kernowroger on 2019-05-26
Hmm... still not pot printing:

roger@desktop:~$ lp -d /etc/nsswitch.conf
lp: The printer or class does not exist.
roger@desktop:~$ lpstat -t
scheduler is running
system default destination: Deskjet-1050-J410-series
device for Deskjet-1050-J410-series: hp:/usb/Deskjet_1050_J410_series?serial=CN27Q1GG7V05QT
device for HP-DeskJet-3700-series: dnssd://HP%20DeskJet%203700%20series%20%5BC66E83%5D._ipp._tcp.local/?uuid=365f778a-0f6e-717f-f235-19a57c66c6fc
Deskjet-1050-J410-series accepting requests since Sat 25 May 2019 14:35:59 BST
HP-DeskJet-3700-series accepting requests since Sun 26 May 2019 07:51:29 BST
printer Deskjet-1050-J410-series is idle.  enabled since Sat 25 May 2019 14:35:59 BST
printer HP-DeskJet-3700-series is idle.  enabled since Sun 26 May 2019 07:51:29 BST
roger@desktop:~$ lpoptions -p HP-DeskJet-3700-series

---

### Post by kernowroger on 2019-05-26
With additional terminal output:

roger@desktop:~$ lp -d /etc/nsswitch.conf
lp: The printer or class does not exist.
roger@desktop:~$ lpstat -t
scheduler is running
system default destination: Deskjet-1050-J410-series
device for Deskjet-1050-J410-series: hp:/usb/Deskjet_1050_J410_series?serial=CN27Q1GG7V05QT
device for HP-DeskJet-3700-series: dnssd://HP%20DeskJet%203700%20series%20%5BC66E83%5D._ipp._tcp.local/?uuid=365f778a-0f6e-717f-f235-19a57c66c6fc
Deskjet-1050-J410-series accepting requests since Sat 25 May 2019 14:35:59 BST
HP-DeskJet-3700-series accepting requests since Sun 26 May 2019 07:51:29 BST
printer Deskjet-1050-J410-series is idle.  enabled since Sat 25 May 2019 14:35:59 BST
printer HP-DeskJet-3700-series is idle.  enabled since Sun 26 May 2019 07:51:29 BST
roger@desktop:~$ lpoptions -p HP-DeskJet-3700-series
copies=1 device-uri=dnssd://HP%20DeskJet%203700%20series%20%5BC66E83%5D._ipp._tcp.local/?uuid=365f778a-0f6e-717f-f235-19a57c66c6fc finishings=3 job-cancel-after=10800 job-hold-until=no-hold job-priority=50 job-sheets=none,none marker-change-time=1558874150 marker-colors=#00FFFF#FF00FF#FFFF00,#000000 marker-high-levels=100,100 marker-levels=-1,-1 marker-low-levels=1,1 marker-names='tri-color\ ink,black\ ink' marker-types=ink-cartridge,ink-cartridge number-up=1 printer-commands=none printer-info='HP DeskJet 3700 series' printer-is-accepting-jobs=true printer-is-shared=true printer-location printer-make-and-model='HP Deskjet 3740, hpcups 3.16.3' printer-state=3 printer-state-change-time=1558874150 printer-state-reasons=none printer-type=36892 printer-uri-supported=ipp://localhost/printers/HP-DeskJet-3700-series
roger@desktop:~$

---

### Post by kernowroger on 2019-05-26
Solved!

My suspicions about support for driverless printing in Ubuntu 16.04 seems to have be justified. I've upgraded to 18.04 and all my printers are now working. In Settings>Printers I now have a choice of two printers: my old printer, HP Desktop 1050j410 Series (connected by USB) and my new printer, HP DeskJet 3700 series, driveless (connected by Wifi). I don't understand how this driverless printing works, but it certainly seems pretty brilliant.

Brian, may thanks for your help with my problem

Roger

---

### Post by brian_p on 2019-05-26
> My suspicions about support for driverless printing in Ubuntu 16.04 seems to have be justified. 

I owe you two apologies, kernowroger.

Firstly, I should have asked you what OS you were using. Because you said you are a new user I assumed it was 18.04. You are correct: 16.04 is basically not a driverless printing OS.

Secondly, my lp command was incorrect. A tip: Ubuntu has manual pages. In this case you would do

```
man lp
```

Reading the manual would reveal my error. I'll let you find it. :P

Glad you sorted your issue.

---

### Post by brian_p on 2019-05-26
I forgot to ask a favour.

Would you post what you get for

```
avahi-browse -rt _ipp._tcp
```

and

```
avahi-browse -rt _uscan._tcp
```

avahi-browse is in the avahi-utils package. It should be on your system.

Thanks.

---

### Post by kernowroger on 2019-05-28
Hi Brian

Hope this all means something:

roger@desktop:~$ avahi-browse -rt _ipp._tcp
+  wlan0 IPv6 HP DeskJet 3700 series [C66E83]               Internet Printer     local
+  wlan0 IPv6 HP DeskJet 3700 series [C66E83] @ desktop     Internet Printer     local
+  wlan0 IPv6 HP Deskjet 1050 J410 series @ desktop         Internet Printer     local
+  wlan0 IPv4 HP DeskJet 3700 series [C66E83]               Internet Printer     local
+  wlan0 IPv4 HP DeskJet 3700 series [C66E83] @ desktop     Internet Printer     local
+  wlan0 IPv4 HP Deskjet 1050 J410 series @ desktop         Internet Printer     local
+     lo IPv4 HP Deskjet 1050 J410 series @ desktop         Internet Printer     local
+     lo IPv4 HP DeskJet 3700 series [C66E83] @ desktop     Internet Printer     local
=  wlan0 IPv4 HP DeskJet 3700 series [C66E83]               Internet Printer     local
   hostname = [HPE4E749C66E83.local]
   address = [192.168.1.12]
   port = [631]
   txt = ["Scan=T" "Duplex=F" "Color=T" "UUID=365f778a-0f6e-717f-f235-19a57c66c6fc" "Fax=F" "TLS=1.2" "note=" "adminurl=http://HPE4E749C66E83.local./#hId-pgAirPrint" "mac=e4:e7:49:c6:6e:83" "priority=20" "usb_MDL=DeskJet 3700 series" "usb_MFG=HP" "product=(HP DeskJet 3700 series)" "ty=HP DeskJet 3700 series" "URF=CP1,MT1-2-8-9-10-11,PQ3-4-5,RS300,SRGB24,OB9,OFU0,W8-16,DEVW8-16,DEVRGB24-48,ADOBERGB24-48,FN3,IS1,V1.4" "kind=document,envelope,photo,postcard" "PaperMax=legal-A4" "rp=ipp/print" "pdl=application/vnd.hp-PCL,image/jpeg,application/PCLm,image/urf,image/pwg-raster" "qtotal=1" "txtvers=1"]
=  wlan0 IPv4 HP DeskJet 3700 series [C66E83] @ desktop     Internet Printer     local
   hostname = [desktop.local]
   address = [192.168.1.3]
   port = [631]
   txt = ["printer-type=0x904E" "printer-state=3" "Copies=T" "Color=T" "TLS=1.2" "UUID=27fd9bc7-c74d-31f3-7143-43768247ee5a" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(HP DeskJet 3700 series)" "priority=0" "adminurl=https://desktop.local.:631/printers/DeskJet-3700" "ty=HP DeskJet 3700 series, driverless, cups-filters 1.20.2" "rp=printers/DeskJet-3700" "qtotal=1" "txtvers=1"]
=  wlan0 IPv4 HP Deskjet 1050 J410 series @ desktop         Internet Printer     local
   hostname = [desktop.local]
   address = [192.168.1.3]
   port = [631]
   txt = ["printer-type=0x900E" "printer-state=3" "Color=T" "TLS=1.2" "UUID=e1712237-0b2a-389e-7081-e68a0f210a31" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(HP Deskjet 1056 All-in-one Printer -j410a)" "priority=0" "note=desktop" "adminurl=https://desktop.local.:631/printers/Deskjet-1050-J410-series" "ty=HP Deskjet 1050 j410 Series, hpcups 3.17.10" "rp=printers/Deskjet-1050-J410-series" "qtotal=1" "txtvers=1"]
=     lo IPv4 HP DeskJet 3700 series [C66E83] @ desktop     Internet Printer     local
   hostname = [localhost]
   address = [127.0.0.1]
   port = [631]
   txt = ["printer-type=0x904E" "printer-state=3" "Copies=T" "Color=T" "TLS=1.2" "UUID=27fd9bc7-c74d-31f3-7143-43768247ee5a" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(HP DeskJet 3700 series)" "priority=0" "adminurl=https://desktop.local.:631/printers/DeskJet-3700" "ty=HP DeskJet 3700 series, driverless, cups-filters 1.20.2" "rp=printers/DeskJet-3700" "qtotal=1" "txtvers=1"]
=     lo IPv4 HP Deskjet 1050 J410 series @ desktop         Internet Printer     local
   hostname = [localhost]
   address = [127.0.0.1]
   port = [631]
   txt = ["printer-type=0x900E" "printer-state=3" "Color=T" "TLS=1.2" "UUID=e1712237-0b2a-389e-7081-e68a0f210a31" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(HP Deskjet 1056 All-in-one Printer -j410a)" "priority=0" "note=desktop" "adminurl=https://desktop.local.:631/printers/Deskjet-1050-J410-series" "ty=HP Deskjet 1050 j410 Series, hpcups 3.17.10" "rp=printers/Deskjet-1050-J410-series" "qtotal=1" "txtvers=1"]
=  wlan0 IPv6 HP DeskJet 3700 series [C66E83] @ desktop     Internet Printer     local
   hostname = [desktop.local]
   address = [fe80::221:2fff:fe3b:4cc1]
   port = [631]
   txt = ["printer-type=0x904E" "printer-state=3" "Copies=T" "Color=T" "TLS=1.2" "UUID=27fd9bc7-c74d-31f3-7143-43768247ee5a" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(HP DeskJet 3700 series)" "priority=0" "adminurl=https://desktop.local.:631/printers/DeskJet-3700" "ty=HP DeskJet 3700 series, driverless, cups-filters 1.20.2" "rp=printers/DeskJet-3700" "qtotal=1" "txtvers=1"]
=  wlan0 IPv6 HP Deskjet 1050 J410 series @ desktop         Internet Printer     local
   hostname = [desktop.local]
   address = [fe80::221:2fff:fe3b:4cc1]
   port = [631]
   txt = ["printer-type=0x900E" "printer-state=3" "Color=T" "TLS=1.2" "UUID=e1712237-0b2a-389e-7081-e68a0f210a31" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(HP Deskjet 1056 All-in-one Printer -j410a)" "priority=0" "note=desktop" "adminurl=https://desktop.local.:631/printers/Deskjet-1050-J410-series" "ty=HP Deskjet 1050 j410 Series, hpcups 3.17.10" "rp=printers/Deskjet-1050-J410-series" "qtotal=1" "txtvers=1"]
=  wlan0 IPv6 HP DeskJet 3700 series [C66E83]               Internet Printer     local
   hostname = [HPE4E749C66E83.local]
   address = [192.168.1.12]
   port = [631]
   txt = ["Scan=T" "Duplex=F" "Color=T" "UUID=365f778a-0f6e-717f-f235-19a57c66c6fc" "Fax=F" "TLS=1.2" "note=" "adminurl=http://HPE4E749C66E83.local./#hId-pgAirPrint" "mac=e4:e7:49:c6:6e:83" "priority=20" "usb_MDL=DeskJet 3700 series" "usb_MFG=HP" "product=(HP DeskJet 3700 series)" "ty=HP DeskJet 3700 series" "URF=CP1,MT1-2-8-9-10-11,PQ3-4-5,RS300,SRGB24,OB9,OFU0,W8-16,DEVW8-16,DEVRGB24-48,ADOBERGB24-48,FN3,IS1,V1.4" "kind=document,envelope,photo,postcard" "PaperMax=legal-A4" "rp=ipp/print" "pdl=application/vnd.hp-PCL,image/jpeg,application/PCLm,image/urf,image/pwg-raster" "qtotal=1" "txtvers=1"]
roger@desktop:~$ 
roger@desktop:~$ avahi-browse -rt _uscan._tcp
+  wlan0 IPv6 HP DeskJet 3700 series [C66E83]               _uscan._tcp          local
+  wlan0 IPv4 HP DeskJet 3700 series [C66E83]               _uscan._tcp          local
=  wlan0 IPv4 HP DeskJet 3700 series [C66E83]               _uscan._tcp          local
   hostname = [HPE4E749C66E83.local]
   address = [192.168.1.12]
   port = [8080]
   txt = ["duplex=F" "is=adf" "cs=binary,color,grayscale" "rs=eSCL" "representation=images/printer.png" "UUID=365f778a-0f6e-717f-f235-19a57c66c6fc" "note=" "adminurl=http://HPE4E749C66E83.local." "ty=HP DeskJet 3700 series" "pdl=application/octet-stream,application/pdf,image/jpeg" "vers=2.5" "txtvers=1"]
=  wlan0 IPv6 HP DeskJet 3700 series [C66E83]               _uscan._tcp          local
   hostname = [HPE4E749C66E83.local]
   address = [192.168.1.12]
   port = [8080]
   txt = ["duplex=F" "is=adf" "cs=binary,color,grayscale" "rs=eSCL" "representation=images/printer.png" "UUID=365f778a-0f6e-717f-f235-19a57c66c6fc" "note=" "adminurl=http://HPE4E749C66E83.local." "ty=HP DeskJet 3700 series" "pdl=application/octet-stream,application/pdf,image/jpeg" "vers=2.5" "txtvers=1"]
roger@desktop:~$

---

