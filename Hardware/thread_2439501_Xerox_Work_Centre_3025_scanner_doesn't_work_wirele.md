---
title: "Xerox Work Centre 3025 scanner doesn't work wirelessly"
date: 2020-03-28
forum: Hardware
---

### Post by easytiger87 on 2020-03-28
Hello, 

this is my first post on forum. For some time I've switched to Debian, but recently returned and found a certain problem.

I've Xerox WorkCentre 3025 printer & scanner. It is connected to my router wirelessly. I'm able to print wirelessly, but scanning fails. I'm using Simple Scan and it fails to detect scanner. 

I've already tried solution from this page: 

[https://askubuntu.com/questions/927265/xerox-workcentre-3025-scanner-is-not-working-ubuntu-17-04](https://askubuntu.com/questions/927265/xerox-workcentre-3025-scanner-is-not-working-ubuntu-17-04)


Solution works perfectly on my second machine with Debian Buster on it, but not on Xubuntu 19.10. _So it can be done_

Beside of moves from the thread I've been trying:

- reinstalling printer
- reinstalling printer driver
- purging and installing again libsane and simplescan packages
- adding myself not only to lp group but also to scanner group
- putting in /etc/sane.d/xerox_mfp.conf under the lines:
#Xerox WorkCentre 3025
usb 0x0924 0x42da

also:
tcp 192.168.8.100

The last attempt caused SimpleScan to detect machine, scanner to react, but then Simple Scan hangs.


Lastly I want to mention that I've installed Xubuntu Core, so maybe I lack some important package?


Thanks in advance!

---

### Post by brian_p on 2020-03-28
Please provide what you get with ```
avahi-browse -rt _ipp._tcp
``` and ```
avahi-browse -rt _uscan._tcp
```

---

### Post by easytiger87 on 2020-03-28
Hi!

```
avahi-browse -rt _ipp._tcp
+ wlp18s0b1 IPv4 Xerox WorkCentre 3025 (XRX9C934E418D37)       Internet Printer     local
= wlp18s0b1 IPv4 Xerox WorkCentre 3025 (XRX9C934E418D37)       Internet Printer     local
   hostname = [XRX9C934E418D37.local]
   address = [192.168.8.100]
   port = [631]
   txt = ["Staple=F" "Sort=F" "Fax=F" "Scan=T" "Punch=0" "PaperMax=legal-A4" "PaperCustom=T" "Duplex=F" "Copies=T" "Color=F" "Collate=F" "Bind=F" "URF=W8,RS600,IS1,CP1,IFU0,PQ4,OB10,V1.3" "kind=document,envelope,label" "UUID=16a65700-007c-1000-bb49-9c934e418d37" "MDL=WorkCentre 3025" "MFG=Xerox" "usb_CMD=MFG:Xerox;CMD:SPL,URF,FWV,EXT;MDL:WorkCentre 3025;CLS:PRINTER;CID:XR_GDI3_Class01_Mono;MODE:SCN,SPL3,R000105;" "usb_MDL=WorkCentre 3025" "usb_MFG=Xerox" "adminurl=http://XRX9C934E418D37.local./sws/index.html?link=/sws/app/settings/network/AirPrint/AirPrint.html" "pdl=application/octet-stream,application/x-QPDL,image/urf" "product=(Xerox WorkCentre 3025)" "ty=Xerox WorkCentre 3025" "priority=51" "qtotal=1" "note=" "rp=ipp/print" "txtvers=1"]



```

Second command doesn't provide any output.

Thanks!

---

### Post by brian_p on 2020-03-28
> Second command doesn't provide any output.

Many modern MFDs offer the escl protocol for scanning. The empty output indicates your device does not. I cannot take this any further. Sorry about that.

---

### Post by easytiger87 on 2020-03-29
Hi,

sorry, but it can't be the case.

I've issued both commands on my other PC, ran as I've said on Debian- the result is the same: only first gives any output. Believe me that this PC has even lower specs.

And yet on Debian wireless scanning runs flawlessly. 

I wonder what are the differences?

I forgot to mention in my earlier posts that I quickly compared few files at /etc/sane.d: saned.conf, smfp-xerox.conf, xerox_mfp.conf- at first sight they seem the same.

Cheers!


**EDIT:** To my surprise I've found than scanner doesn't work even connected through USB

---

