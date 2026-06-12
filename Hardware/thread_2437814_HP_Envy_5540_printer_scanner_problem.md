---
title: "HP Envy 5540 printer scanner problem"
date: 2020-03-01
forum: Hardware
---

### Post by Philip_Edwards on 2020-03-01
Hi group,

Two weeks after installing Ubuntu 18.04 onto my Acer Aspire V laptop, everything works with the exception of Simplescan.
It fails to detect my HP Envy 5540 printer/scanner.

Strangely the printer works just fine.
Any suggestions?

Phil

---

### Post by brian_p on 2020-03-01
Please post what you get for ```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _uscan._tcp
``` with the printer on the network.

---

### Post by Autodave on 2020-03-01
Did you install hp-lip?

---

### Post by ajgreeny on 2020-03-01
Does the printer connect over network or USB?

I have an Envy 4270 printer scanner which is network connected only and is found by all three machines in our house, printing and scanning faultlessly.
The printer uses a static IP address set using the router setup's "Reserved Devices" dialogue, and all our *ubuntu machines find it with no action on our part.

I do have hplip installed along with hplip-gui, but I'm not sure if that is really needed; it just makes activities easier, such as cleaning the inkjet cartridges.

---

### Post by Philip_Edwards on 2020-03-02
First snippet of code gave this.

+ wlp4s0 IPv6 ENVY 5540 series                              Internet Printer     local
+ wlp4s0 IPv4 ENVY 5540 series                              Internet Printer     local
= wlp4s0 IPv4 ENVY 5540 series                              Internet Printer     local
   hostname = [HPFC3FDBC69071.local]
   address = [192.168.0.16]
   port = [631]
   txt = ["Scan=T" "Duplex=T" "Color=T" "UUID=1c852a4d-b800-1f08-abcd-fc3fdbc69071" "Fax=F" "TLS=1.2" "note=" "adminurl=http://HPFC3FDBC69071.local./#hId-pgAirPrint" "mac=fc:3f:db:c6:90:71" "priority=20" "usb_MDL=ENVY 5540 series" "usb_MFG=HP" "product=(HP ENVY 5540 series)" "ty=ENVY 5540 series" "URF=CP1,MT1-2-8-9-10-11,PQ3-4-5,RS300-600,SRGB24,OB9,OFU0,W8-16,DEVW8-16,DEVRGB24-48,ADOBERGB24-48,DM3,IS1-7,V1.4" "kind=document,envelope,photo,postcard" "PaperMax=legal-A4" "rp=ipp/print" "pdl=application/vnd.hp-PCL,image/jpeg,application/PCLm,image/urf,image/pwg-raster" "qtotal=1" "txtvers=1"]
= wlp4s0 IPv6 ENVY 5540 series                              Internet Printer     local
   hostname = [HPFC3FDBC69071.local]
   address = [192.168.0.16]
   port = [631]
   txt = ["Scan=T" "Duplex=T" "Color=T" "UUID=1c852a4d-b800-1f08-abcd-fc3fdbc69071" "Fax=F" "TLS=1.2" "note=" "adminurl=http://HPFC3FDBC69071.local./#hId-pgAirPrint" "mac=fc:3f:db:c6:90:71" "priority=20" "usb_MDL=ENVY 5540 series" "usb_MFG=HP" "product=(HP ENVY 5540 series)" "ty=ENVY 5540 series" "URF=CP1,MT1-2-8-9-10-11,PQ3-4-5,RS300-600,SRGB24,OB9,OFU0,W8-16,DEVW8-16,DEVRGB24-48,ADOBERGB24-48,DM3,IS1-7,V1.4" "kind=document,envelope,photo,postcard" "PaperMax=legal-A4" "rp=ipp/print" "pdl=application/vnd.hp-PCL,image/jpeg,application/PCLm,image/urf,image/pwg-raster" "qtotal=1" "txtvers=1"]


Second snippet gave this  

+ wlp4s0 IPv4 ENVY 5540 series                              _uscan._tcp          local
= wlp4s0 IPv4 ENVY 5540 series                              _uscan._tcp          local
   hostname = [HPFC3FDBC69071.local]
   address = [192.168.0.16]
   port = [8080]
   txt = ["duplex=F" "is=platen" "cs=binary,color,grayscale" "rs=eSCL" "representation=images/printer.png" "UUID=1c852a4d-b800-1f08-abcd-fc3fdbc69071" "note=" "adminurl=http://HPFC3FDBC69071.local." "ty=ENVY 5540 series" "pdl=application/octet-stream,application/pdf,image/jpeg" "vers=2.5" "txtvers=1"]
+ wlp4s0 IPv6 ENVY 5540 series                              _uscan._tcp          local
= wlp4s0 IPv6 ENVY 5540 series                              _uscan._tcp          local
   hostname = [HPFC3FDBC69071.local]
   address = [192.168.0.16]
   port = [8080]
   txt = ["duplex=F" "is=platen" "cs=binary,color,grayscale" "rs=eSCL" "representation=images/printer.png" "UUID=1c852a4d-b800-1f08-abcd-fc3fdbc69071" "note=" "adminurl=http://HPFC3FDBC69071.local." "ty=ENVY 5540 series" "pdl=application/octet-stream,application/pdf,image/jpeg" "vers=2.5" "txtvers=1"]


Thanks for helping me.

---

### Post by brian_p on 2020-03-02
Getting an output from *avahi-browse -rt _uscan._tcp* indicates your device supports the eSCL protocol. Scanning can take place without having to rely on a vendor driver such as *libsane-hpaio*. Read              
                                                                                                                       
  [https://github.com/alexpevzner/sane-airscan](https://github.com/alexpevzner/sane-airscan)                                                                          
                                                                                                                       
then go to                                                                                                             
                                                                                                                       
  [https://software.opensuse.org//download.html?project=home%3Apzz&package=sane-airscan](https://software.opensuse.org//download.html?project=home%3Apzz&package=sane-airscan)                                 
                                                                                                                       
and download a suitable file, or use the provided repository.                                                          
                                                                                                                       
Assuming it gets downloaded to the Downloads directory, I would do                                                     
                                                                                                                       
  ```
cd Downloads
```                                                                                                         
  ```
sudo apt install ./DOWNLOADED_FILE_NAME
```
                                                                                                                       
Then I would check for the sane-airscan backend being found with                                                       
                                                                                                                       
  scanimage -L                                                                                                         
                                                                                                                       
and, if it is, run                                                                                                     
                                                                                                                       
  ```
simple-scan
```                                                                                                          
                                                                                                                       
or                                                                                                                     
                                                                                                                       
  ```
xsane
```

---

### Post by Philip_Edwards on 2020-03-02
Huge thanks. It works now.
I did get stuck on this bit   [https://software.opensuse.org//downl...e=sane-airscan]("https://software.opensuse.org//download.html?project=home%3Apzz&package=sane-airscan")[COLOR=#000000][/COLOR]

[COLOR=#000000]and download a suitable file, or use the provided repository.

It downloaded a zip file....which contained about a dozen files with no indication as to which chould be installed but it doesn't matter because the last two snippets of code showed that everything works. 

Now everything is working.

Big thanks 
Phil[/COLOR]

---

### Post by brian_p on 2020-03-02
> **Philip_Edwards said:**
> Huge thanks. It works now.

Excellent.

>  did get stuck on this bit   [https://software.opensuse.org//downl...e=sane-airscan]("https://software.opensuse.org//download.html?project=home%3Apzz&package=sane-airscan")[COLOR=#000000][/COLOR]

[COLOR=#000000]and download a suitable file, or use the provided repository.

It downloaded a zip file....which contained about a dozen files with no indication as to which chould be installed but it doesn't matter because the last two snippets of code showed that everything works. 

I thought that would be an easy bit! :) Ubuntu is offered and you wanted to *Grab binary packages directly* and go for xUbuntu 18.04. Never mind.

> Now everything is working.

Big thanks 
Phil[/COLOR]

Note that if you changed your device to a modern Brother, Epson or Canon MFD, sane-airscan should continue to work. No more driver installation for you. You can actually do the same for printing, but that is a different story: [https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting). (Then you could remove HPLIP from the system).

---

