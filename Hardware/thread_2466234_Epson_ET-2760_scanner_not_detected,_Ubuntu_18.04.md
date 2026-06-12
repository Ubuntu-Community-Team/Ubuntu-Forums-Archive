---
title: "Epson ET-2760 scanner not detected, Ubuntu 18.04"
date: 2021-08-23
forum: Hardware
---

### Post by Minilek on 2021-08-23
Hi all.

I just bought an ET-2760 scanner and tried to connect to it via wifi from my laptop (running Ubuntu 18.04) to scan a document. I followed these steps:

1. I went to [http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule) and searched for ET-2760 as the product, and Linux as the OS.
2. I downloaded the "All in one" package at the bottom of the resulting page.
3. $ tar xzvf imagescan-bundle-ubuntu-18.04-3.65.0.x64.deb.tar.gz
4. $ cd imagescan-bundle-ubuntu-18.04-3.65.0.x64.deb, then $ sudo ./install.sh
5. I also looked in core/ and plugins/ and dpkg --install'd every deb file in those two folders. There were 4 total, and these were the filenames:
imagescan_3.65.0-1epson4ubuntu18.04_amd64.deb
imagescan-plugin-gt-s650_1.0.3-1epson4ubuntu18.04_amd64.deb
imagescan-plugin-networkscan_1.1.4-1epson4ubuntu18.04_amd64.deb
imagescan-plugin-ocr-engine_1.0.3-1epson4ubuntu18.04_amd64.deb

Now, scanimage -L says "No scanners were identified." Similarly, imagescan says "No devices found". Note: I lost the ->usb cable that came with the printer, and I'm trying to connect with it for the scan over the network. The printer and my laptop are both on the same WiFi network. I can successfully print over the network, but I'm just running into problems detecting the printer for scanning. Any thoughts on what I should be trying here?

---

### Post by him610 on 2021-08-23
Is your ET-2760 connected to your router? If it does not have an IP address there is no way your computer will see it. The Epson ET-2760 User Guide gives some good instructions about connecting your printer to the router. Beginning on page 30 of the User Guide is a whole section on wifi setup for your printer. User Guide can be viewed at [https://files.support.epson.com/docid/cpd5/cpd57083.pdf]("https://files.support.epson.com/docid/cpd5/cpd57083.pdf")

---

### Post by brian_p on 2021-08-24
Please give ```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _uscan._tcp
```

---

### Post by Minilek on 2021-09-07
```
avahi-browse -rt _ipp._tcp
```
This gives
```

+ wlp2s0 IPv6 EPSON ET-2760 Series                          Internet Printer     local
+ wlp2s0 IPv4 EPSON ET-2760 Series                          Internet Printer     local
= wlp2s0 IPv6 EPSON ET-2760 Series                          Internet Printer     local
   hostname = [EPSON4A3AAB.local]
   address = [192.168.86.141]
   port = [631]
   txt = ["TLS=1.2" "UUID=cfe92100-67c4-11d4-a45f-dccd2f4a3aab" "note=" "adminurl=http://EPSON4A3AAB.local.:80/PRESENTATION/BONJOUR" "priority=30" "mopria-certified=1.3" "URF=CP1,PQ4-5,OB9,OFU0,RS360,SRGB24,W8,DM3,IS1,V1.4,MT1-3-6-8-10-11-12" "PaperMax=legal-A4" "kind=document,envelope,photo" "Fax=F" "Scan=T" "Duplex=T" "Color=T" "qtotal=1" "rp=ipp/print" "pdl=application/octet-stream,image/pwg-raster,image/urf,image/jpeg" "product=(EPSON ET-2760 Series)" "usb_MDL=ET-2760 Series" "usb_MFG=EPSON" "ty=EPSON ET-2760 Series" "txtvers=1"]
= wlp2s0 IPv4 EPSON ET-2760 Series                          Internet Printer     local
   hostname = [EPSON4A3AAB.local]
   address = [192.168.86.141]
   port = [631]
   txt = ["TLS=1.2" "UUID=cfe92100-67c4-11d4-a45f-dccd2f4a3aab" "note=" "adminurl=http://EPSON4A3AAB.local.:80/PRESENTATION/BONJOUR" "priority=30" "mopria-certified=1.3" "URF=CP1,PQ4-5,OB9,OFU0,RS360,SRGB24,W8,DM3,IS1,V1.4,MT1-3-6-8-10-11-12" "PaperMax=legal-A4" "kind=document,envelope,photo" "Fax=F" "Scan=T" "Duplex=T" "Color=T" "qtotal=1" "rp=ipp/print" "pdl=application/octet-stream,image/pwg-raster,image/urf,image/jpeg" "product=(EPSON ET-2760 Series)" "usb_MDL=ET-2760 Series" "usb_MFG=EPSON" "ty=EPSON ET-2760 Series" "txtvers=1"]

```


```
avahi-browse -rt _uscan._tcp
```
This gives
```

+ wlp2s0 IPv4 EPSON ET-2760 Series                          _uscan._tcp          local
= wlp2s0 IPv4 EPSON ET-2760 Series                          _uscan._tcp          local
   hostname = [EPSON4A3AAB.local]
   address = [192.168.86.141]
   port = [443]
   txt = ["representation=https://EPSON4A3AAB.local.:443/PRESENTATION/AIRPRINT/PRINTER_128.PNG" "note=" "UUID=cfe92100-67c4-11d4-a45f-dccd2f4a3aab" "adminurl=http://EPSON4A3AAB.local.:80/PRESENTATION/BONJOUR" "duplex=F" "is=platen" "cs=color,grayscale,binary" "pdl=application/pdf,image/jpeg" "ty=EPSON ET-2760 Series" "rs=eSCL" "vers=2.63" "txtvers=1"]

```

To him610: yes, the printer is connected to the router (accomplished via the printer's setup menu on the device itself). Note: I can print over the network. I just can't scan over the network.

---

### Post by brian_p on 2021-09-07
On Ubuntu 21.04 a user would be given **sane-airscan** by default. You will have to download and install it from

[https://download.opensuse.org/repositories/home:/pzz/xUbuntu_18.04/amd64/](https://download.opensuse.org/repositories/home:/pzz/xUbuntu_18.04/amd64/)

The main page is

[https://github.com/alexpevzner/sane-airscan](https://github.com/alexpevzner/sane-airscan)

Please give ```
scanimage -L
``` ```
airscan-discover
```

---

### Post by Minilek on 2021-09-24
Thanks, that seemed to do something!

> minilek@minilek-laptop:~$ scanimage -L
device `airscan:e0:EPSON ET-2760 Series' is a eSCL EPSON ET-2760 Series ip=192.168.86.207
minilek@minilek-laptop:~$ airscan-discover 
[devices]
  EPSON ET-2760 Series = [http://192.168.86.207:443/eSCL/](http://192.168.86.207:443/eSCL/), eSCL
  EPSON ET-2760 Series = [https://192.168.86.207:443/eSCL/](https://192.168.86.207:443/eSCL/), eSCL
  EPSON ET-2760 Series = [http://192.168.86.207:80/WDP/SCAN](http://192.168.86.207:80/WDP/SCAN), WSD
  EPSON ET-2760 Series = [http://[fe80::decd:2fff:fe4a:3aab%253]:80/WDP/SCAN](http://[fe80::decd:2fff:fe4a:3aab%253]:80/WDP/SCAN), WSD
minilek@minilek-laptop:~$ 

How do I actually scan documents though? imagescan still doesn't see the scanner.

---

### Post by brian_p on 2021-09-24
Can you scan with ```
simple-scan "airscan:e0:EPSON ET-2760 Series"
```

---

### Post by Minilek on 2021-09-25
That worked, thanks a lot!

---

