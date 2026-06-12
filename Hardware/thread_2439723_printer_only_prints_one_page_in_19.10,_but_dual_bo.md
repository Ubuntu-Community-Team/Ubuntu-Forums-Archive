---
title: "printer only prints one page in 19.10, but dual booting 18 prints more than one ok."
date: 2020-03-31
forum: Hardware
---

### Post by seekertom on 2020-03-31
Im dual booting 18 lts and 19.10. printer is et-3750. when i boot to 18 (default) I can print several copies of a libre document ok, but when I boot into 19.10, only 1 of the several copies I try to print actually prints. Even if I try to print 2 or more copies and only 1 prints, I can still repeat the process, that is, the queue doesnt fill up with unprinted copies.

I reinstalled the et printer, no help. It is a network printer in both 18 and 19. 

Im not even sure where to begin, except to check the printer settings, all the same, and the doc settings, tho it's the same doc both cases.

so. Why ok to print multiple copies in 18 but only one at a time in 19?

thanks for your help, and hope y'all stay well!
st.

---

### Post by slickymaster on 2020-03-31
*Thread moved to **Hardware**.*

---

### Post by brian_p on 2020-03-31
This is an Epson ET-3750, we presume. Let us try something  different and modern. Give the outputs of ```
avahi-browse -rt _ipp._tcp
```  ```
avahi-browse -rt _uscan._tcp
``` ```
driverless
``` with the device on the network,

---

### Post by him610 on 2020-03-31
I am not familiar with Epson printers, but I did find this website that may offer some help.
[https://tutorialforlinux.com/2018/04/06/driver-epson-et-3750-ubuntu-16-04-how-to-download-install/]("https://tutorialforlinux.com/2018/04/06/driver-epson-et-3750-ubuntu-16-04-how-to-download-install/")
It seems like most folks need help with the scan function instead of the print function.

---

### Post by seekertom on 2020-03-31
```
kathy@kathy-HP-ProDesk-405-G2-MT:~$ avahi-browse -rt _ipp._tcp
+ enp2s0 IPv6 EPSON ET-3750 Series                          Internet Printer     local
+ enp2s0 IPv4 EPSON ET-3750 Series                          Internet Printer     local
+     lo IPv4 ET-3750 Series [583445513134353750]           Internet Printer     local
= enp2s0 IPv6 EPSON ET-3750 Series                          Internet Printer     local
   hostname = [EPSON3B9197.local]
   address = [10.187.152.144]
   port = [631]
   txt = ["TLS=1.2" "UUID=cfe92100-67c4-11d4-a45f-f8d0273b9197" "note=" "adminurl=http://EPSON3B9197.local.:80/PRESENTATION/BONJOUR" "priority=30" "mopria-certified=1.3" "URF=CP1,PQ4-5,OB9,OFU0,RS300,SRGB24,W8,DM3,IS1,V1.4,MT1-3-8-10-11-12" "PaperMax=legal-A4" "kind=document,envelope,photo" "Fax=F" "Scan=T" "Duplex=T" "Color=T" "qtotal=1" "rp=ipp/print" "pdl=application/octet-stream,image/pwg-raster,image/urf,image/jpeg" "product=(EPSON ET-3750 Series)" "usb_MDL=ET-3750 Series" "usb_MFG=EPSON" "ty=EPSON ET-3750 Series" "txtvers=1"]
= enp2s0 IPv4 EPSON ET-3750 Series                          Internet Printer     local
   hostname = [EPSON3B9197.local]
   address = [10.187.152.144]
   port = [631]
   txt = ["TLS=1.2" "UUID=cfe92100-67c4-11d4-a45f-f8d0273b9197" "note=" "adminurl=http://EPSON3B9197.local.:80/PRESENTATION/BONJOUR" "priority=30" "mopria-certified=1.3" "URF=CP1,PQ4-5,OB9,OFU0,RS300,SRGB24,W8,DM3,IS1,V1.4,MT1-3-8-10-11-12" "PaperMax=legal-A4" "kind=document,envelope,photo" "Fax=F" "Scan=T" "Duplex=T" "Color=T" "qtotal=1" "rp=ipp/print" "pdl=application/octet-stream,image/pwg-raster,image/urf,image/jpeg" "product=(EPSON ET-3750 Series)" "usb_MDL=ET-3750 Series" "usb_MFG=EPSON" "ty=EPSON ET-3750 Series" "txtvers=1"]
=     lo IPv4 ET-3750 Series [583445513134353750]           Internet Printer     local
   hostname = [localhost]
   address = [127.0.0.1]
   port = [60000]
   txt = ["qtotal=1" "txtvers=1" "priority=60" "usb_MDL=ET-3750 Series" "usb_MFG=EPSON" "Copies=U" "Duplex=U" "Color=U" "pdl=" "product=(ET-3750 Series)" "adminurl=http://localhost:60000/" "ty=EPSON ET-3750 Series" "rp=ipp/print"]
kathy@kathy-HP-ProDesk-405-G2-MT:~$
```

---

### Post by seekertom on 2020-03-31
```
kathy@kathy-HP-ProDesk-405-G2-MT:~$ avahi-browse -rt _uscan._tcp
kathy@kathy-HP-ProDesk-405-G2-MT:~$ avahi-browse -rt _uscan._tcp
kathy@kathy-HP-ProDesk-405-G2-MT:~$ driverless
ipp://EPSON3B9197.local:631/ipp/print
kathy@kathy-HP-ProDesk-405-G2-MT:~$
```

---

### Post by brian_p on 2020-03-31
> **seekertom said:**
> 

ipp://EPSON3B9197.local:631/ipp/print


This is the URI for the printer. Print jobs go there. Substitute in ```
lpadmin -p et3750 -v URI -E -m everywhere
``` and try printing. For example, ```
lp -d et3750 /etc/nsswitch.conf
```

---

### Post by brian_p on 2020-03-31
A query for you, if I may, seekertom.

I was bothered by your not having an output for *avahi-browse -rt _uscan._tcp*. However, when I look more closely at your *avahi-browse -rt _ipp._tcp* I see this:

> = lo IPv4 ET-3750 Series [583445513134353750] Internet Printer local
hostname = [localhost]
address = [127.0.0.1]
port = [60000]
txt = ["qtotal=1" "txtvers=1" "priority=60" "usb_MDL=ET-3750 Series" "usb_MFG=EPSON" "Copies=U" "Duplex=U" "Color=U" "pdl=" "product=(ET-3750 Series)" "adminurl=http://localhost:60000/" "ty=EPSON ET-3750 Series" "rp=ipp/print"]

In other words, you have an IPP service on the lo interface at port 60000. The only thing I can think that would cause this is by running *ippusbxd*. Are you running this program? The reason I ask is because it is possible it is stopping you from getting an *avahi-browse -rt _uscan._tcp* output. *ippusbxd* is not needed when the device is actually network-connected.

---

### Post by slickymaster on 2020-04-01
@seekertom:

Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting output because when posted as plain text it loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

---

