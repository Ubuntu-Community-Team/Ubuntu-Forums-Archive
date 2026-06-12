---
title: "Problem with HP Envy 5640 printer."
date: 2020-04-30
forum: Hardware
---

### Post by Davethehedgehog on 2020-04-30
There is a similar problem to this already posted, but the solution did not work for me.

Since I upgraded to Ubuntu 20.04, I have had a problem with my HP Envy 5640 printer. When I try to print, I get a notification saying:

Printer Error
Printer "ENVY-5640": "Connecting to Device".

The printer is connected to my desktop via USB.
HPLIP is installed.

Any help would be appreciated.

---

### Post by brian_p on 2020-04-30
See [https://ubuntuforums.org/showthread.php?t=2442068](https://ubuntuforums.org/showthread.php?t=2442068)

---

### Post by Davethehedgehog on 2020-04-30
david@David-Desktop:~$ avahi-browse -rt _ipp._tcp
+ enp2s0 IPv6 HP ENVY 5640 series [C8C2D7]                  Internet Printer     local
+ enp2s0 IPv4 HP ENVY 5640 series [C8C2D7]                  Internet Printer     local
+     lo IPv4 ENVY 5640 series [TH6AV9Q02X05ZC]             Internet Printer     local
=     lo IPv4 ENVY 5640 series [TH6AV9Q02X05ZC]             Internet Printer     local
   hostname = [David-Desktop.local]
   address = [127.0.0.1]
   port = [60000]
   txt = ["rfo=ipp/faxout" "Fax=T" "note=" "adminurl=" "qtotal=1" "txtvers=1" "priority=60" "usb_MDL=ENVY 5640 series" "usb_MFG=HP" "rp=ipp/print"]
= enp2s0 IPv4 HP ENVY 5640 series [C8C2D7]                  Internet Printer     local
   hostname = [HPC8D3FFC8C2D7.local]
   address = [192.168.0.33]
   port = [631]
   txt = ["Scan=T" "Duplex=T" "Color=T" "UUID=1c852a4d-b800-1f08-abcd-c8d3ffc8c2d7" "Fax=F" "TLS=1.2" "note=" "adminurl=http://HPC8D3FFC8C2D7.local./#hId-pgAirPrint" "mac=c8:d3:ff:c8:c2:d7" "priority=20" "usb_MDL=ENVY 5640 series" "usb_MFG=HP" "product=(HP ENVY 5640 series)" "ty=HP ENVY 5640 series" "URF=CP1,MT1-2-8-9-10-11,PQ3-4-5,RS300-600,SRGB24,OB9,OFU0,W8-16,DEVW8-16,DEVRGB24-48,ADOBERGB24-48,DM3,IS1-7,V1.4" "kind=document,envelope,photo,postcard" "PaperMax=<legal-A4" "rp=ipp/print" "pdl=application/vnd.hp-PCL,image/jpeg,application/PCLm,image/urf" "qtotal=1" "txtvers=1"]
= enp2s0 IPv6 HP ENVY 5640 series [C8C2D7]                  Internet Printer     local
   hostname = [HPC8D3FFC8C2D7.local]
   address = [192.168.0.33]
   port = [631]
   txt = ["Scan=T" "Duplex=T" "Color=T" "UUID=1c852a4d-b800-1f08-abcd-c8d3ffc8c2d7" "Fax=F" "TLS=1.2" "note=" "adminurl=http://HPC8D3FFC8C2D7.local./#hId-pgAirPrint" "mac=c8:d3:ff:c8:c2:d7" "priority=20" "usb_MDL=ENVY 5640 series" "usb_MFG=HP" "product=(HP ENVY 5640 series)" "ty=HP ENVY 5640 series" "URF=CP1,MT1-2-8-9-10-11,PQ3-4-5,RS300-600,SRGB24,OB9,OFU0,W8-16,DEVW8-16,DEVRGB24-48,ADOBERGB24-48,DM3,IS1-7,V1.4" "kind=document,envelope,photo,postcard" "PaperMax=<legal-A4" "rp=ipp/print" "pdl=application/vnd.hp-PCL,image/jpeg,application/PCLm,image/urf" "qtotal=1" "txtvers=1"]

david@David-Desktop:~$ avahi-browse -rt _uscan._tcp
+ enp2s0 IPv6 HP ENVY 5640 series [C8C2D7]                  _uscan._tcp          local
+ enp2s0 IPv4 HP ENVY 5640 series [C8C2D7]                  _uscan._tcp          local
= enp2s0 IPv4 HP ENVY 5640 series [C8C2D7]                  _uscan._tcp          local
   hostname = [HPC8D3FFC8C2D7.local]
   address = [192.168.0.33]
   port = [8080]
   txt = ["duplex=F" "is=platen" "cs=binary,color,grayscale" "rs=eSCL" "representation=images/printer.png" "UUID=1c852a4d-b800-1f08-abcd-c8d3ffc8c2d7" "note=" "adminurl=http://HPC8D3FFC8C2D7.local." "mfg=HP" "ty=HP ENVY 5640 series" "pdl=application/octet-stream,application/pdf,image/jpeg" "vers=2.5" "txtvers=1"]
= enp2s0 IPv6 HP ENVY 5640 series [C8C2D7]                  _uscan._tcp          local
   hostname = [HPC8D3FFC8C2D7.local]
   address = [192.168.0.33]
   port = [8080]
   txt = ["duplex=F" "is=platen" "cs=binary,color,grayscale" "rs=eSCL" "representation=images/printer.png" "UUID=1c852a4d-b800-1f08-abcd-c8d3ffc8c2d7" "note=" "adminurl=http://HPC8D3FFC8C2D7.local." "mfg=HP" "ty=HP ENVY 5640 series" "pdl=application/octet-stream,application/pdf,image/jpeg" "vers=2.5" "txtvers=1"]

david@David-Desktop:~$ driverless
ipp://HP%20ENVY%205640%20series%20%5BC8C2D7%5D._ipp._tcp.local/

---

### Post by brian_p on 2020-04-30
Thanks for the info.

> ipp://HP%20ENVY%205640%20series%20%5BC8C2D7%5D._ipp._tcp .local/ 

This is the URI for your networked device. Substitute it for URI in this command:

```
lpadmin -p PRINTER_NAME -v URI -E -m everywhere
```

PRINTER_NAME may be anything you choose. Test the print queue with

```
lp -d PRINTER_NAME /etc/nsswitch.conf
```

I would also be interested in what you get for ```
scanimage -L
```

---

### Post by Davethehedgehog on 2020-05-01
Good morning, Brian - thanks for your help!

Here is the info you requested, although there looks to be a problem in the arguments for the lpadmin command. I look forward to hearing from you.

David


david@David-Desktop:~$ lpadmin -p HP-ENVY-5640-series -v ipp://HP%20ENVY%205640%20series%20%5BC8C2D7%5D._ipp._tcp .local/ -E -m everywhere
lpadmin: Unknown argument ".local/".
Usage: lpadmin [options] -d destination
       lpadmin [options] -p destination
       lpadmin [options] -p destination -c class
       lpadmin [options] -p destination -r class
       lpadmin [options] -x destination
Options:
-c class                Add the named destination to a class
-d destination          Set the named destination as the server default
-D description          Specify the textual description of the printer
-E                      Encrypt the connection to the server
-E                      Enable and accept jobs on the printer (after -p)
-h server[:port]        Connect to the named server and port
-i ppd-file             Specify a PPD file for the printer
-L location             Specify the textual location of the printer
-m model                Specify a standard model/PPD file for the printer
-m everywhere           Specify the printer is compatible with IPP Everywhere
-o name-default=value   Specify the default value for the named option
-o Name=Value           Specify the default value for the named PPD option 
-o cupsIPPSupplies=false
                        Disable supply level reporting via IPP
-o cupsSNMPSupplies=false
                        Disable supply level reporting via SNMP
-o job-k-limit=N        Specify the kilobyte limit for per-user quotas
-o job-page-limit=N     Specify the page limit for per-user quotas
-o job-quota-period=N   Specify the per-user quota period in seconds
-o printer-error-policy=name
                        Specify the printer error policy
-o printer-is-shared=true
                        Share the printer
-o printer-op-policy=name
                        Specify the printer operation policy
-p destination          Specify/add the named destination
-r class                Remove the named destination from a class
-R name-default         Remove the default value for the named option
-u allow:all            Allow all users to print
-u allow:list           Allow the list of users or groups (@name) to print
-u deny:list            Prevent the list of users or groups (@name) to print
-U username             Specify the username to use for authentication
-v device-uri           Specify the device URI for the printer
-x destination          Remove the named destination

david@David-Desktop:~$ lp -d HP-ENVY-5640-series /etc/nsswitch.conf
request id is HP-ENVY-5640-series-47 (1 file(s)

david@David-Desktop:~$ scanimage -L
device `escl:[http://fe80::cad3:ffff:fec8:c2d7:8080](http://fe80::cad3:ffff:fec8:c2d7:8080)' is a ESCL HP ENVY 5640 series [C8C2D7] flatbed scanner
device `escl:[http://127.0.0.1:60000](http://127.0.0.1:60000)' is a ESCL ENVY 5640 series [TH6AV9Q02X05ZC] flatbed scanner
device `hpaio:/usb/ENVY_5640_series?serial=TH6AV9Q02X05ZC' is a Hewlett-Packard ENVY_5640_series all-in-one

---

### Post by brian_p on 2020-05-01
> -v ipp://HP%20ENVY%205640%20series%20%5BC8C2D7%5D._ipp._tcp .local/

Hello David,

Note the space after *_tcp*. This is in your original info and should not be there. The corrected URI is

```
ipp://HP%20ENVY%205640%20series%20%5BC8C2D7%5D._ipp._tcp.local/
```

You should also get printing with a URI of

```
ipp://HPC8D3FFC8C2D7.local
``` or ```
ipp://192.168.0.33:631/
``` The latter relies on the IP address being unchanging.

> david@David-Desktop:~$ scanimage -L
device `escl:[http://fe80::cad3:ffff:fec8:c2d7:8080](http://fe80::cad3:ffff:fec8:c2d7:8080)' is a ESCL HP ENVY 5640 series [C8C2D7] flatbed scanner
device `escl:[http://127.0.0.1:60000](http://127.0.0.1:60000)' is a ESCL ENVY 5640 series [TH6AV9Q02X05ZC] flatbed scanner
device `hpaio:/usb/ENVY_5640_series?serial=TH6AV9Q02X05ZC' is a Hewlett-Packard ENVY_5640_series all-in-one

The first and third URIs should be equally as good for scanning with simple-scan or xsane. The second URI appears to have something to do with the 5640's fax facility. You haven't got a USB cable connected?

---

### Post by Davethehedgehog on 2020-05-01
Hi Brian

Below is the output from the lpadmin command after I removed the space from the URI. It doesn't look too encouraging to me.

david@David-Desktop:~$ lpadmin -p HP-Envy-5640-series -v ipp://HP%20ENVY%205640%20series%20%5BC8C2D7%5D._ipp._tcp.local/ -E -m everywhere
lpadmin: Unable to connect to "HPC8D3FFC8C2D7.local:631": Name or service not known

The printer is connected to my PC via USB. This connection was the default for printing from my machine and always worked OK. I assume that ipp://HPC8D3FFC8C2D7.local refers to a wireless connection, but I can't print from my machine on this either.

I tried printing wirelessly from another computer on the home network and this worked fine.

The scanner seems to work on the wireless connection, but not on the USB.

I've never used the FAX and would never need to.

All a bit puzzling.

If you have any further thoughts, I'd be pleased to hear from you.

Thanks fo your help so far - I feel I'm learning things, at least.

Regards

David

---

### Post by brian_p on 2020-05-01
Hello David,

Both of us have messed up. Originally you gave

> david@David-Desktop:~$ driverless
ipp://HP%20ENVY%205640%20series%20%5BC8C2D7%5D._ipp._tcp .local/

This is incorrect and I did not notice. Sorry. The URI is incomplete; it should be
```
ipp://HP%20ENVY%205640%20series%20%5BC8C2D7%5D._ipp._tcp.local/ipp/print
```

An alternative URI (provided the IP has not changed) is ```
ipp://192.168.0.33:631/ipp/print
```

---

### Post by brian_p on 2020-05-01
I made another mistake. ```
ipp://HP%20ENVY%205640%20series%20%5BC8C2D7%5D._ipp._tcp.local/ipp/print
``` is incorrect. Use the other URI.

---

### Post by gja on 2020-05-02
Hello,

Similar issue here:
Printer worked fine via usb before upgrading.
After upgrading to Ubuntu 20.04 the HP Envy 5640, used via usb,  seems to appear as a new different printer regularly.
It does seem to work when selecting the last added one.

From the settings=> printers => printer details
name: ENVY-5640  - (no location filled in) - address: localhost
name: ENVY_5640_series_TH66P9W21D05ZC_ - (no location filled in) - address: [http://ENVY](http://ENVY) 5640 series [TH66P9W21D05ZC]._ipp._tcp.local:631
```

avahi-browse -rt _ipp._tcp
+     lo IPv4 ENVY 5640 series [TH66P9W21D05ZC]             Internet Printer     local
=     lo IPv4 ENVY 5640 series [TH66P9W21D05ZC]             Internet Printer     local
   hostname = [gja-desktop.local]
   address = [127.0.0.1]
   port = [60000]
   txt = ["rfo=ipp/faxout" "Fax=T" "Duplex=T" "PaperMax=legal-A4" "URF=CP1,MT1-2-8-9-10-11,PQ3-4-5,RS300-600,SRGB24,OB9,OFU0,W8-16,DEVW8-16,DEVRGB24-48,ADOBERGB24-48,DM3,IS1-7,V1.4" "pdl=application/vnd.hp-PCL,image/jpeg,application/PCLm,image/urf,application/octet-stream" "product=(HP ENVY 5640 series)" "ty=HP ENVY 5640 series" "note=" "Color=T" "kind=document,envelope,photo,postcard" "UUID=1c852a4d-b800-1f08-abcd-ec8eb5aa1c18" "adminurl=http://127.0.0.1:60000/#hId-pgAirPrint" "qtotal=1" "txtvers=1" "priority=60" "usb_MDL=ENVY 5640 series" "usb_MFG=HP" "rp=ipp/print"]

avahi-browse -rt _uscan._tcp
+     lo IPv4 ENVY 5640 series [TH66P9W21D05ZC]             _uscan._tcp          local
=     lo IPv4 ENVY 5640 series [TH66P9W21D05ZC]             _uscan._tcp          local
   hostname = [gja-desktop.local]
   address = [127.0.0.1]
   port = [60000]
   txt = ["txtvers=1" "vers=2.5" "rs=eSCL" "ty=psc1600" "pdl=application/octet-stream,image/jpeg,application/pdf" "cs=grayscale,color" "duplex=F" "adminurl=http://127.0.0.1:60000/#hId-pgAirPrint" "UUID=1c852a4d-b800-1f08-abcd-ec8eb5aa1c18" "note=" "representation=http://127.0.0.1:60000/webApps/images/printer-small.png,http://127.0.0.1:60000/webApps/images/printer.png,http://127.0.0.1:60000/webApps/images/printer-large.png"]

driverless
ipp://ENVY%205640%20series%20%5BTH66P9W21D05ZC%5D._ipp._tcp.local/

scanimage -L
device `escl:http://127.0.0.1:60000' is a ESCL ENVY 5640 series [TH66P9W21D05ZC] flatbed scanner
device `hpaio:/usb/ENVY_5640_series?serial=TH66P9W21D05ZC' is a Hewlett-Packard ENVY_5640_series all-in-one



```

---

### Post by Davethehedgehog on 2020-05-02
I have attempted to attach a couple of screenshots, one relating to printing, one relating to scanning.

Like gja, my usb printer seemed to appear as a "discovered" printer - the first one on the screenshot (TH6AV9Q02X05ZC). This seems to be operating now, although rather slowly.

I did also install the usb printer myself which appeared separately but didn't work, so I deleted it.

The other printer (C8C2D7) would appear to be the wifi printer. This is now working as well.

The other screen shot relates to scanning and the options offered by XSANE for selecting a scanner.  All of these seem to work except the third one.

---

### Post by brian_p on 2020-05-02
@gja

Unless you have an overwhelming reason to use USB, I would go for a network connection. Use ```
lpadmin -p PRINTER_NAME -v URI -E -m everywhere
``` to set up a queue. The URI is ```
ipp://ENVY%205640%20series%20%5BTH66P9W21D05ZC%5D._ipp._tcp.local/
```

*scanimage -L* will give a different output but scanning will work.

---

### Post by brian_p on 2020-05-02
@ Davethehedgehog

Although you appear to be able to print now, I cannot think of a good reason for having USB and wireless connections at the same time. I would use WiFi; printing and scanning should just work with that.

---

### Post by gja on 2020-05-03
> **brian_p said:**
> @gja

Unless you have an overwhelming reason to use USB, I would go for a network connection. 

I don't like connecting each and every appliance to the network, since mostly that's not the secure thing to do.
On top of that, with printers the risk of automatic firmware updates that may affect functionality negatively also seems not so appealing.

USB printing seems like a basic functionality. I hope there will be a fix for the multiple appearances in the near future.
Willing to help and provide additional info if useful.

---

### Post by gja on 2020-05-03
This thread seems related:
[Pesty automatic printer installation]("https://ubuntuforums.org/showthread.php?t=2441849")

---

### Post by gja on 2020-05-04
I noticed I had a problem with permission on a file.

Found a solution on German forum:
[https://forum.ubuntuusers.de/topic/hp-photosmart-5525-konfigurationsproblem-unter/4/](https://forum.ubuntuusers.de/topic/hp-photosmart-5525-konfigurationsproblem-unter/4/)

Apparently ippusbxd causes problems and can simply be removed.

Try this instruction:
sudo apt purge ippusbxd

---

