---
title: "Epson 2630-WF problems on Lubuntu 18.04.3"
date: 2019-10-15
forum: Hardware
---

### Post by stilnovo1 on 2019-10-15
Hi to Everybody,

I've just bought an Epson printer (Workforce WF-2630) which I have connected to my new laptop running Lubuntu 18.04.3 via wifi (Google Cloud print).

In Cups the print options are very limited. I've installed the suggested drivers in openprinting.org, that are the ones downloadable in Epson web site.

Now, after a "non-linear" installation, all things seem to work (scanning, printing).

The problems are about the options (that are present in windows driver):

- draft and high quality: there is only one possible options, the normal quality, no other settings available.

- double-sided printing: no possible to set (in Windows this possibility is manually managed via software).

- other minor options (borderless printing, better quality in case of photo colour printing etc.).

Moreover, it seems that I can change the settings only with CUPS (system-config-printer), also when the printer is connected with an USB cable...

Anyone can help me?

Thanks in advance!

Andrea

---

### Post by brian_p on 2019-10-15
> **stilnovo1 said:**
> Hi to Everybody,

I've just bought an Epson printer (Workforce WF-2630) which I have connected to my new laptop running Lubuntu 18.04.3 via wifi (Google Cloud print).

In Cups the print options are very limited. I've installed the suggested drivers in openprinting.org, that are the ones downloadable in Epson web site.

The limitations are probably due to the PPD provided by Epson. Your print queue will have a name. Please post the output of ```
lpoptions -p <print_queue_name> -l
``` With the printer on the network, also give what you get for ```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _uscan._tcp
```

---

### Post by stilnovo1 on 2019-10-15
Hi!

```

lpoptions -p <print_queue_name> -l
bash: print_queue_name: File o directory non esistente
[I](translation: File or directory does not exist)
[/I]
```


```

avahi-browse -rt _ipp._tcp+   eno1 IPv6 EPSON WF-2630 Series                          Internet Printer     local
+   eno1 IPv6 Epson WF-2630locale @ zambo-HP-new            Internet Printer     local
+   eno1 IPv6 EPSON WF-2630 Series @ zambo-HP-new           Internet Printer     local
+   eno1 IPv4 EPSON WF-2630 Series                          Internet Printer     local
+   eno1 IPv4 Epson WF-2630locale @ zambo-HP-new            Internet Printer     local
+   eno1 IPv4 EPSON WF-2630 Series @ zambo-HP-new           Internet Printer     local
+     lo IPv4 Epson WF-2630locale @ zambo-HP-new            Internet Printer     local
+     lo IPv4 EPSON WF-2630 Series @ zambo-HP-new           Internet Printer     local
=   eno1 IPv6 EPSON WF-2630 Series                          Internet Printer     local
   hostname = [EPSON18823B.local]
   address = [192.168.1.159]
   port = [631]
   txt = ["TLS=1.2" "UUID=cfe92100-67c4-11d4-a45f-389d9218823b" "note=" "adminurl=http://EPSON18823B.local.:80/PRESENTATION/BONJOUR" "priority=30" "print_wfds=T" "URF=CP1,MT1-3-8-10-11-12,PQ4,OB9,OFU0,RS360,SRGB24,W8,IS1,V1.4" "PaperMax=legal-A4" "kind=document,envelope,photo" "rfo=ipp/faxout" "Fax=T" "Scan=T" "Duplex=F" "Color=T" "qtotal=1" "rp=ipp/print" "pdl=application/octet-stream,image/pwg-raster,image/urf,image/jpeg" "product=(EPSON WF-2630 Series)" "usb_MDL=WF-2630 Series" "usb_MFG=EPSON" "ty=EPSON WF-2630 Series" "txtvers=1"]
=   eno1 IPv6 Epson WF-2630locale @ zambo-HP-new            Internet Printer     local
   hostname = [zambo-HP-new.local]
   address = [fd3c:fd60:6829:0:c61:3d96:a22d:642b]
   port = [631]
   txt = ["printer-type=0x100E" "printer-state=3" "Color=T" "TLS=1.2" "UUID=25771f1b-97aa-3c88-57b0-48e44456a8b8" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(EPSON WF-2630 Series)" "priority=0" "note=ufficio" "adminurl=https://zambo-HP-new.local.:631/printers/Epson-locale" "ty=Epson WF-2630 Series - epson-inkjet-printer-escpr 1.7.3-1lsb3.2 (Seiko Epson Corporation LSB 3.2)" "rp=printers/Epson-locale" "qtotal=1" "txtvers=1"]
=   eno1 IPv6 EPSON WF-2630 Series @ zambo-HP-new           Internet Printer     local
   hostname = [zambo-HP-new.local]
   address = [fd3c:fd60:6829:0:c61:3d96:a22d:642b]
   port = [631]
   txt = ["printer-type=0x904E" "printer-state=3" "Copies=T" "Color=T" "TLS=1.2" "UUID=fd8ec273-1a99-3c89-6ca2-4cf6a2c35c82" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(EPSON WF-2630 Series)" "priority=0" "note=ufficio" "adminurl=https://zambo-HP-new.local.:631/printers/EPSON-WF-2630-Series" "ty=EPSON WF-2630 Series, driverless, cups-filters 1.20.2" "rp=printers/EPSON-WF-2630-Series" "qtotal=1" "txtvers=1"]
=   eno1 IPv4 Epson WF-2630locale @ zambo-HP-new            Internet Printer     local
   hostname = [zambo-HP-new.local]
   address = [192.168.1.113]
   port = [631]
   txt = ["printer-type=0x100E" "printer-state=3" "Color=T" "TLS=1.2" "UUID=25771f1b-97aa-3c88-57b0-48e44456a8b8" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(EPSON WF-2630 Series)" "priority=0" "note=ufficio" "adminurl=https://zambo-HP-new.local.:631/printers/Epson-locale" "ty=Epson WF-2630 Series - epson-inkjet-printer-escpr 1.7.3-1lsb3.2 (Seiko Epson Corporation LSB 3.2)" "rp=printers/Epson-locale" "qtotal=1" "txtvers=1"]
=   eno1 IPv4 EPSON WF-2630 Series @ zambo-HP-new           Internet Printer     local
   hostname = [zambo-HP-new.local]
   address = [192.168.1.113]
   port = [631]
   txt = ["printer-type=0x904E" "printer-state=3" "Copies=T" "Color=T" "TLS=1.2" "UUID=fd8ec273-1a99-3c89-6ca2-4cf6a2c35c82" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(EPSON WF-2630 Series)" "priority=0" "note=ufficio" "adminurl=https://zambo-HP-new.local.:631/printers/EPSON-WF-2630-Series" "ty=EPSON WF-2630 Series, driverless, cups-filters 1.20.2" "rp=printers/EPSON-WF-2630-Series" "qtotal=1" "txtvers=1"]
=     lo IPv4 Epson WF-2630locale @ zambo-HP-new            Internet Printer     local
   hostname = [localhost]
   address = [127.0.0.1]
   port = [631]
   txt = ["printer-type=0x100E" "printer-state=3" "Color=T" "TLS=1.2" "UUID=25771f1b-97aa-3c88-57b0-48e44456a8b8" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(EPSON WF-2630 Series)" "priority=0" "note=ufficio" "adminurl=https://zambo-HP-new.local.:631/printers/Epson-locale" "ty=Epson WF-2630 Series - epson-inkjet-printer-escpr 1.7.3-1lsb3.2 (Seiko Epson Corporation LSB 3.2)" "rp=printers/Epson-locale" "qtotal=1" "txtvers=1"]
=     lo IPv4 EPSON WF-2630 Series @ zambo-HP-new           Internet Printer     local
   hostname = [localhost]
   address = [127.0.0.1]
   port = [631]
   txt = ["printer-type=0x904E" "printer-state=3" "Copies=T" "Color=T" "TLS=1.2" "UUID=fd8ec273-1a99-3c89-6ca2-4cf6a2c35c82" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(EPSON WF-2630 Series)" "priority=0" "note=ufficio" "adminurl=https://zambo-HP-new.local.:631/printers/EPSON-WF-2630-Series" "ty=EPSON WF-2630 Series, driverless, cups-filters 1.20.2" "rp=printers/EPSON-WF-2630-Series" "qtotal=1" "txtvers=1"]
=   eno1 IPv4 EPSON WF-2630 Series                          Internet Printer     local
   hostname = [EPSON18823B.local]
   address = [192.168.1.159]
   port = [631]
   txt = ["TLS=1.2" "UUID=cfe92100-67c4-11d4-a45f-389d9218823b" "note=" "adminurl=http://EPSON18823B.local.:80/PRESENTATION/BONJOUR" "priority=30" "print_wfds=T" "URF=CP1,MT1-3-8-10-11-12,PQ4,OB9,OFU0,RS360,SRGB24,W8,IS1,V1.4" "PaperMax=legal-A4" "kind=document,envelope,photo" "rfo=ipp/faxout" "Fax=T" "Scan=T" "Duplex=F" "Color=T" "qtotal=1" "rp=ipp/print" "pdl=application/octet-stream,image/pwg-raster,image/urf,image/jpeg" "product=(EPSON WF-2630 Series)" "usb_MDL=WF-2630 Series" "usb_MFG=EPSON" "ty=EPSON WF-2630 Series" "txtvers=1"]

```


```

avahi-browse -rt _uscan._tcp
+   eno1 IPv6 EPSON WF-2630 Series                          _uscan._tcp          local
+   eno1 IPv4 EPSON WF-2630 Series                          _uscan._tcp          local
=   eno1 IPv4 EPSON WF-2630 Series                          _uscan._tcp          local
   hostname = [EPSON18823B.local]
   address = [192.168.1.159]
   port = [443]
   txt = ["note=" "UUID=cfe92100-67c4-11d4-a45f-389d9218823b" "adminurl=http://EPSON18823B.local.:80/PRESENTATION/BONJOUR" "duplex=F" "is=platen,adf" "cs=color,grayscale,binary" "pdl=application/pdf,image/jpeg" "ty=EPSON WF-2630 Series" "rs=eSCL" "representation=/PRESENTATION/AIRPRINT/PRINTER_128.PNG" "vers=2.5" "txtvers=1"]
=   eno1 IPv6 EPSON WF-2630 Series                          _uscan._tcp          local
   hostname = [EPSON18823B.local]
   address = [192.168.1.159]
   port = [443]
   txt = ["note=" "UUID=cfe92100-67c4-11d4-a45f-389d9218823b" "adminurl=http://EPSON18823B.local.:80/PRESENTATION/BONJOUR" "duplex=F" "is=platen,adf" "cs=color,grayscale,binary" "pdl=application/pdf,image/jpeg" "ty=EPSON WF-2630 Series" "rs=eSCL" "representation=/PRESENTATION/AIRPRINT/PRINTER_128.PNG" "vers=2.5" "txtvers=1"]

```

---

### Post by brian_p on 2019-10-15
Hello Andrea,

<print_queue_name> is whatever the name is. The angle brackets indicate that that option to the command **must** be given, but they are not typed. In other words, if the name was *epson*, the command would be ```
lpoptions -p epson -l
```

---

### Post by brian_p on 2019-10-15
> **stilnovo1 said:**
> Hi!

```

lpoptions -p <print_queue_name> -l
bash: print_queue_name: File o directory non esistente
[I](translation: File or directory does not exist)
[/I]
```

Please post the output of the corrected command.

> 
```

=   eno1 IPv4 EPSON WF-2630 Series                          Internet Printer     local
   hostname = [EPSON18823B.local]
   address = [192.168.1.159]
   port = [631]
   txt = ["TLS=1.2" "UUID=cfe92100-67c4-11d4-a45f-389d9218823b" "note=" "adminurl=http://EPSON18823B.local.:80/PRESENTATION/BONJOUR" "priority=30" "print_wfds=T" "URF=CP1,MT1-3-8-10-11-12,PQ4,OB9,OFU0,RS360,SRGB24,W8,IS1,V1.4" "PaperMax=legal-A4" "kind=document,envelope,photo" "rfo=ipp/faxout" "Fax=T" "Scan=T" "Duplex=F" "Color=T" "qtotal=1" "rp=ipp/print" "pdl=application/octet-stream,image/pwg-raster,image/urf,image/jpeg" "product=(EPSON WF-2630 Series)" "usb_MDL=WF-2630 Series" "usb_MFG=EPSON" "ty=EPSON WF-2630 Series" "txtvers=1"]

```


Thanks. The *URF=* in this output indictates that your printer is AirPrint-enabled. Execute this command to get a URI for the printer:

```
driverless
```

Now set up these two print queues

```
lpadmin -p wf1 -v <URI> -E -m everywhere
```

```
lpadmin -p wf2 -v <URI> -E -m driverless:<URI>
```

Both commands query the printer directly to get its attributes. What each queue offers can be seen with

```
lpoptions -p wf1 -l
``` and ```
lpoptions -p wf2 -l
```

Post what you get from lpoptions in each case.

---

### Post by stilnovo1 on 2019-10-15
Hi Brian,

excuse me! I'm not so practiced, unfortunately... 

```

 lpoptions -p EPSON-WF-2630-Series -l
PageSize/Media Size: 3.5x5 3.5x5.Borderless 4x6 4x6.Borderless 5x7 5x7.Borderless 5x8 8x10 8x10.Borderless *A4 A4.Borderless A5 A6 B5 Env10 EnvC6 EnvDL Legal Letter Letter.Borderless Postcard Postcard.Borderless Custom.WIDTHxHEIGHT
MediaType/Media Type: *Stationery PhotographicHighGloss Photographic PhotographicSemiGloss PhotographicGlossy PhotographicMatte Envelope
ColorModel/Print Color Mode: RGB *Gray
cupsPrintQuality/Print Quality: *4
print-scaling/Print Scaling: *auto auto-fit fill fit none

```

Ok, now:
```

driverless
ipp://EPSON18823B.local:631/ipp/print

```


For sure, now I have done something wrong:

```

lpadmin -p wf1 -v <ipp://EPSON18823B.local:631/ipp/print> -E -m everywhere
bash: ipp://EPSON18823B.local:631/ipp/print: File o directory non esistente

```

but I don't know what is the wrong part.... 

```

lpoptions -p wf1 -l
lpoptions: non è possibile ottenere il file PPD per wf1: Non esiste la stampante o la classe.

```

[I](the PPD file cannot be obtained for wf1: There is no printer or class)

[/I]same result for the next command:

```
lpoptions -p wf2 -l
lpoptions: non è possibile ottenere il file PPD per wf2: Non esiste la stampante o la classe.

```

---

### Post by brian_p on 2019-10-15
> **stilnovo1 said:**
> Hi Brian,

excuse me! I'm not so practiced, unfortunately...

I will try to be more helpful. :)


> 
Ok, now:
```

driverless
ipp://EPSON18823B.local:631/ipp/print

```

That's ok.
> 


For sure, now I have done something wrong:


```

lpadmin -p wf1 -v <ipp://EPSON18823B.local:631/ipp/print> -E -m everywhere
bash: ipp://EPSON18823B.local:631/ipp/print: File o directory non esistente

```

but I don't know what is the wrong part.... 


Do not type < and >. I tried to indicate this in an earlier post. Not to worry. The command you want is

```
lpadmin -p wf1 -v ipp://EPSON18823B.local:631/ipp/print -E -m everywhere
```

And do the same for the other lpadmin command.

---

### Post by brian_p on 2019-10-16
From the lpoptions output, note the borderless options:

> PageSize/Media Size: 3.5x5 3.5x5.Borderless 4x6 4x6.Borderless 5x7 5x7.Borderless 5x8 8x10 8x10.Borderless *A4 A4.Borderless A5 A6 B5 Env10 EnvC6 EnvDL Legal Letter Letter.Borderless Postcard Postcard.Borderless Custom.WIDTHxHEIGHT

From the TEXT record (txt=) in the avahi-browse output, note:

> "Duplex=F"

This printer does not offer a duplex facility by itself.

Also:

> cupsPrintQuality/Print Quality: *4

The printer itself offers only normal quality. The Epson PPD doesn't even offer that.

---

### Post by stilnovo1 on 2019-10-17
Hi Brian!

Well, the first command:
```
lpadmin -p wf1 -v ipp://EPSON18823B.local:631/ipp/print -E -m everywhere
```

gives me no otuput... no error message, simply nothing.

Also the second one:
```
lpadmin -p wf2 -v ipp://EPSON18823B.local:631/ipp/print -E -m driverless:ipp://EPSON18823B.local:631/ipp/print
```

gives no results...

The quite strange thing (to me!) is that a previous faulty command now gives a result:

```
lpoptions -p wf1 -l
PageSize/Media Size: *A4 4x6 5x7 8x10 A5 A6 Legal Letter B5 3.5x5 Postcard Env10 EnvC6 EnvDL 5x8
MediaType/Media Type: *Stationery PhotographicHighGloss Photographic PhotographicSemiGloss PhotographicGlossy PhotographicMatte Envelope
ColorModel/ModalitÃ  colore: *RGB Gray
cupsPrintQuality/Print Quality: Draft *Normal
```

Now also the other one gives back an answer:

```
lpoptions -p wf2 -l
PageSize/Media Size: 3.5x5 3.5x5.Borderless 4x6 4x6.Borderless 5x7 5x7.Borderless 5x8 8x10 8x10.Borderless *A4 A4.Borderless A5 A6 B5 Env10 EnvC6 EnvDL Legal Letter Letter.Borderless Postcard Postcard.Borderless Custom.WIDTHxHEIGHT
MediaType/Media Type: *Stationery PhotographicHighGloss Photographic PhotographicSemiGloss PhotographicGlossy PhotographicMatte Envelope
ColorModel/Print Color Mode: *RGB Gray
cupsPrintQuality/Print Quality: *4
print-scaling/Print Scaling: *auto auto-fit fill fit none
```

Same commands, same syntax, it's a mystery to me why before I had an error and now not...  but anyway, now there is an output!

Well, in Windows driver there is the 'manual' duplex option: it doesn't do itself, but the printer prints the odd pages first and then the even ones (you have to take the pages and put again in the printer on the other side). About the quality: in Windows you can choose draft, normal and high quality, since this printer can (should) have a max resolution of 5760 x 1440 dpi... in Lubuntu I don't understand the resolution that the printer is actually using.

Thanks in advance for your patience!

---

### Post by stilnovo1 on 2019-10-17
Another strange (to me, of course!) behaviour: now in system-config-printer panel, after that commands, two 'new' printer icons have appeared (WF1 and WF2). It has happened after the two lpadmin commands... I have multiplied my printer :D:D

---

### Post by stilnovo1 on 2019-10-17
Excuse me, I add another question: I've seen now on the Epson website that there is a new driver release from yesterday. How can I update them? I'm finding online only material on how to do a fresh install, but nothing on the ways to update them...

---

### Post by brian_p on 2019-10-17
> **stilnovo1 said:**
> Hi Brian!

Well, the first command:
```
lpadmin -p wf1 -v ipp://EPSON18823B.local:631/ipp/print -E -m everywhere
```

gives me no otuput... no error message, simply nothing.

Also the second one:
```
lpadmin -p wf2 -v ipp://EPSON18823B.local:631/ipp/print -E -m driverless:ipp://EPSON18823B.local:631/ipp/print
```

gives no results...

There is no output unless there is a warning or error to give the user. Nothing to worry about here.

> 
The quite strange thing (to me!) is that a previous faulty command now gives a result:

Please see [https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting).

> 
```
lpoptions -p wf1 -l
PageSize/Media Size: *A4 4x6 5x7 8x10 A5 A6 Legal Letter B5 3.5x5 Postcard Env10 EnvC6 EnvDL 5x8
MediaType/Media Type: *Stationery PhotographicHighGloss Photographic PhotographicSemiGloss PhotographicGlossy PhotographicMatte Envelope
ColorModel/ModalitÃ  colore: *RGB Gray
cupsPrintQuality/Print Quality: Draft *Normal
```

The wf1 queue is set up using the CUPS PPD generator.

> Now also the other one gives back an answer:


```
lpoptions -p wf2 -l
PageSize/Media Size: 3.5x5 3.5x5.Borderless 4x6 4x6.Borderless 5x7 5x7.Borderless 5x8 8x10 8x10.Borderless *A4 A4.Borderless A5 A6 B5 Env10 EnvC6 EnvDL Legal Letter Letter.Borderless Postcard Postcard.Borderless Custom.WIDTHxHEIGHT
MediaType/Media Type: *Stationery PhotographicHighGloss Photographic PhotographicSemiGloss PhotographicGlossy PhotographicMatte Envelope
ColorModel/Print Color Mode: *RGB Gray
cupsPrintQuality/Print Quality: *4
print-scaling/Print Scaling: *auto auto-fit fill fit none
```

Same commands, same syntax, it's a mystery to me why before I had an error and now not...  but anyway, now there is an output!

The wf2 queue is set up using the cups-filters generator.

> 
Well, in Windows driver there is the 'manual' duplex option: it doesn't do itself, but the printer prints the odd pages first and then the even ones (you have to take the pages and put again in the printer on the other side). About the quality: in Windows you can choose draft, normal and high quality, since this printer can (should) have a max resolution of 5760 x 1440 dpi... in Lubuntu I don't understand the resolution that the printer is actually using.

Thanks in advance for your patience!

You can have manual duplex on Ubuntu using one of the methods at [https://wiki.debian.org/CUPSTea4CUPS](https://wiki.debian.org/CUPSTea4CUPS)

The way the CUPS and cups-filters PPD generators choose what to offer for print quality is quite complex. Run

```
ipptool -tv ipp://EPSON18823B.local:631/ipp/print get-printer-attributes.test > log
``` and post log as an attachment.

---

### Post by brian_p on 2019-10-17
> **stilnovo1 said:**
> Another strange (to me, of course!) behaviour: now in system-config-printer panel, after that commands, two 'new' printer icons have appeared (WF1 and WF2). It has happened after the two lpadmin commands... I have multiplied my printer :D:D

You can delete any queue you do not want from system-config-printer. But note very carefully: wf1 and wf2 are different queues (different printers). Which one would you use for borderless printing?

---

### Post by brian_p on 2019-10-17
> **stilnovo1 said:**
> Excuse me, I add another question: I've seen now on the Epson website that there is a new driver release from yesterday. How can I update them? I'm finding online only material on how to do a fresh install, but nothing on the ways to update them...

You would have to provide a link to the new driver release for me to offer any advice.

---

### Post by stilnovo1 on 2019-10-17
Ciao Brian!

Well:

```
[COLOR=#000000][FONT=&amp]ipptool -tv ipp://EPSON18823B.local:631/ipp/print get-printer-attributes.test > log[/FONT][/COLOR]
```

Here there is no otuput...

[COLOR=#000000]" brian_p[/COLOR]
[COLOR=#000000][INDENT]**Re: Epson 2630-WF problems on Lubuntu 18.04.3**
[I][IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **stilnovo1** [[IMG]https://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("https://ubuntuforums.org/showthread.php?p=13898042#post13898042")
Another strange (to me, of course!) behaviour: now in system-config-printer panel, after that commands, two 'new' printer icons have appeared (WF1 and WF2). It has happened after the two lpadmin commands... I have multiplied my printer :grin::grin:

[/I]

You can delete any queue you do not want from system-config-printer. But note very carefully: wf1 and wf2 are different queues (different printers). Which one would you use for borderless printing? "


Good question, I don't know: they are appeared after the two lpadmin commands that I've copied from you: apparently, they permit identical options.

Thanks for the two links that you have provided to me, I will read them.

epson link for the new drivers: [http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

Here, in the module I've written WF-2630.


[/INDENT]
[/COLOR]

---

### Post by brian_p on 2019-10-17
> **stilnovo1 said:**
> Ciao Brian!

Well:

```
[COLOR=#000000][FONT=&amp]ipptool -tv ipp://EPSON18823B.local:631/ipp/print get-printer-attributes.test > log[/FONT][/COLOR]
```

Here there is no otuput...

The output is recorded in the file *log*. What does ```
less log
``` give you?

---

### Post by brian_p on 2019-10-17
> **stilnovo1 said:**
> 

Good question, I don't know: they are appeared after the two lpadmin commands that I've copied from you: apparently, they permit identical options.

Nothey do not - wf1 and wf2 offer different options. Look at what you get for ```
lpoptions -p wf1 -l
``` and ```
lpoptions -p wf2 -l
```

---

### Post by brian_p on 2019-10-18
> **stilnovo1 said:**
> 
epson link for the new drivers: [http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

Here, in the module I've written WF-2630.


The new package offers exactly the same PPD capabilities as the old package.

---

### Post by brian_p on 2019-10-19
Hello Stilnovo1,

Is there some problem with getting an output with ```
ipptool -tv ipp://EPSON18823B.local:631/ipp/print get-printer-attributes.test
```

It would be interesting to see what it gives.

---

### Post by stilnovo1 on 2019-11-01
Ciao Brian,

excuse me for my late reply, but I've been out for work in the last days...

Well:

```
ipptool -tv ipp://EPSON18823B.local:631/ipp/print get-printer-attributes.test"/usr/share/cups/ipptool/get-printer-attributes.test":
    Get-Printer-Attributes:
        attributes-charset (charset) = utf-8
        attributes-natural-language (naturalLanguage) = en
        printer-uri (uri) = ipp://EPSON18823B.local:631/ipp/print
    Get printer attributes using Get-Printer-Attributes                  [PASS]
        RECEIVED: 7149 bytes in response
        status-code = successful-ok (successful-ok)
        attributes-charset (charset) = utf-8
        attributes-natural-language (naturalLanguage) = en-us
        copies-default (integer) = 1
        copies-supported (rangeOfInteger) = 1-99
        finishings-default (enum) = none
        finishings-supported (enum) = none
        media-default (keyword) = iso_a4_210x297mm
        media-supported (1setOf keyword) = iso_a4_210x297mm,na_index-4x6_4x6in,na_5x7_5x7in,na_govt-letter_8x10in,iso_a5_148x210mm,iso_a6_105x148mm,na_legal_8.5x14in,na_letter_8.5x11in,jis_b5_182x257mm,oe_photo-l_3.5x5in,jpn_hagaki_100x148mm,na_number-10_4.125x9.5in,iso_c6_114x162mm,iso_dl_110x220mm,na_index-5x8_5x8in,custom_min_89x127mm,custom_max_215.9x1200mm
        orientation-requested-default (enum) = portrait
        orientation-requested-supported (enum) = portrait
        output-bin-default (keyword) = face-up
        output-bin-supported (keyword) = face-up
        print-quality-default (enum) = normal
        print-quality-supported (enum) = normal
        printer-resolution-default (resolution) = 360dpi
        printer-resolution-supported (1setOf resolution) = 360dpi,1440x720dpi
        sides-default (keyword) = one-sided
        sides-supported (keyword) = one-sided
        print-content-optimize-default (keyword) = auto
        print-content-optimize-supported (keyword) = auto
        media-col-supported (1setOf keyword) = media-size,media-top-margin,media-left-margin,media-right-margin,media-bottom-margin,media-type,media-source
        media-col-default (collection) = {media-size={x-dimension=21000 y-dimension=29700} media-top-margin=300 media-left-margin=300 media-right-margin=300 media-bottom-margin=300 media-type=stationery media-source=main}
        print-color-mode-default (keyword) = auto
        print-color-mode-supported (1setOf keyword) = color,monochrome,auto-monochrome,process-monochrome,auto
        print-scaling-default (keyword) = auto
        print-scaling-supported (1setOf keyword) = auto,auto-fit,fill,fit,none
        charset-configured (charset) = utf-8
        charset-supported (charset) = utf-8
        color-supported (boolean) = true
        compression-supported (1setOf keyword) = none,gzip
        document-format-default (mimeMediaType) = application/octet-stream
        document-format-supported (1setOf mimeMediaType) = application/octet-stream,image/pwg-raster,image/urf,image/jpeg
        generated-natural-language-supported (naturalLanguage) = en-us
        ipp-versions-supported (1setOf keyword) = 1.0,1.1,2.0
        natural-language-configured (naturalLanguage) = en-us
        operations-supported (1setOf enum) = Print-Job,Validate-Job,Create-Job,Send-Document,Cancel-Job,Get-Job-Attributes,Get-Jobs,Get-Printer-Attributes,Identify-Printer
        pages-per-minute (integer) = 9
        pages-per-minute-color (integer) = 4
        pdl-override-supported (keyword) = attempted
        printer-alert (octetString) = code=other
        printer-alert-description (textWithoutLanguage) = idle
        printer-device-id (textWithoutLanguage) = MFG:EPSON;CMD:ESCPL2,BDC,D4,D4PX,ESCPR1,END4,URF;MDL:WF-2630 Series;CLS:PRINTER;DES:EPSON WF-2630 Series;CID:EpsonRGB;FID:FXA,DPN,WFA,ETN,AFA,DAN,WRA;RID:40;DDS:022500;ELG:0E90;URF:CP1,MT1-3-8-10-11-12,PQ4,OB9,OFU0,RS360,SRGB24,W8,IS1,V1.4;
        printer-info (textWithoutLanguage) = EPSON WF-2630 Series
        printer-is-accepting-jobs (boolean) = true
        printer-location (textWithoutLanguage) = 
        printer-make-and-model (textWithoutLanguage) = EPSON WF-2630 Series
        printer-more-info (uri) = http://EPSON18823B.local.:80/PRESENTATION/BONJOUR
        printer-name (nameWithoutLanguage) = ipp/print
        printer-state (enum) = idle
        printer-state-reasons (keyword) = none
        printer-up-time (integer) = 184105422
        printer-uri-supported (1setOf uri) = ipps://EPSON18823B.local.:631/ipp/print,ipp://EPSON18823B.local.:631/ipp/print
        queued-job-count (integer) = 0
        uri-security-supported (1setOf keyword) = tls,none
        uri-authentication-supported (1setOf keyword) = none,none
        printer-geo-location (unknown) = unknown
        identify-actions-default (keyword) = flash
        identify-actions-supported (1setOf keyword) = flash,sound
        media-left-margin-supported (1setOf integer) = 0,300
        media-right-margin-supported (1setOf integer) = 0,300
        media-top-margin-supported (1setOf integer) = 0,300
        media-bottom-margin-supported (1setOf integer) = 0,300
        media-type-supported (1setOf keyword) = stationery,photographic-high-gloss,photographic,photographic-semi-gloss,photographic-glossy,photographic-matte,envelope
        media-source-supported (keyword) = main
        jpeg-k-octets-supported (rangeOfInteger) = 0-12300
        jpeg-x-dimension-supported (rangeOfInteger) = 0-10200
        jpeg-y-dimension-supported (rangeOfInteger) = 1-10200
        pdf-versions-supported (keyword) = none
        urf-supported (1setOf keyword) = CP1,MT1-3-8-10-11-12,PQ4,OB9,OFU0,RS360,SRGB24,W8,IS1,V1.4
        job-creation-attributes-supported (1setOf keyword) = copies,finishings,ipp-attribute-fidelity,job-name,media,media-col,orientation-requested,output-bin,print-quality,printer-resolution,sides,print-color-mode,print-content-optimize,print-scaling
        marker-names (1setOf nameWithoutLanguage) = Black ink,Cyan ink,Magenta ink,Yellow ink
        marker-colors (1setOf nameWithoutLanguage) = #000000,#00FFFF,#FF00FF,#FFFF00
        marker-types (1setOf keyword) = ink-cartridge,ink-cartridge,ink-cartridge,ink-cartridge
        marker-low-levels (1setOf integer) = 15,15,15,15
        marker-high-levels (1setOf integer) = 100,100,100,100
        marker-levels (1setOf integer) = 57,94,95,95
        printer-icons (1setOf uri) = https://EPSON18823B.local.:443/PRESENTATION/AIRPRINT/PRINTER_128.PNG,https://EPSON18823B.local.:443/PRESENTATION/AIRPRINT/PRINTER_512.PNG
        landscape-orientation-requested-preferred (enum) = 5
        printer-uuid (uri) = urn:uuid:cfe92100-67c4-11d4-a45f-389d9218823b
        printer-dns-sd-name (nameWithoutLanguage) = EPSON WF-2630 Series
        printer-supply-info-uri (uri) = http://EPSON18823B.local.:80/PRESENTATION/HTML/TOP/PRTINFO.HTML
        media-size-supported (1setOf collection) = {x-dimension=21000 y-dimension=29700},{x-dimension=10160 y-dimension=15240},{x-dimension=12700 y-dimension=17780},{x-dimension=20320 y-dimension=25400},{x-dimension=14800 y-dimension=21000},{x-dimension=10500 y-dimension=14800},{x-dimension=21590 y-dimension=35560},{x-dimension=21590 y-dimension=27940},{x-dimension=18200 y-dimension=25700},{x-dimension=8890 y-dimension=12700},{x-dimension=10000 y-dimension=14800},{x-dimension=10477 y-dimension=24130},{x-dimension=11400 y-dimension=16200},{x-dimension=11000 y-dimension=22000},{x-dimension=12700 y-dimension=20320},{x-dimension=8900-21590 y-dimension=12700-120000}
        multiple-document-jobs-supported (boolean) = false
        multiple-operation-time-out (integer) = 60
        ipp-features-supported (1setOf keyword) = wfds-print-1.0,airprint-1.4
        printer-kind (1setOf keyword) = document,envelope,photo
        media-col-ready (collection) = {media-size={x-dimension=21000 y-dimension=29700} media-top-margin=300 media-left-margin=300 media-right-margin=300 media-bottom-margin=300 media-type=stationery media-source=main}
        media-ready (keyword) = iso_a4_210x297mm
        printer-firmware-name (1setOf nameWithoutLanguage) = Main,Network
        printer-firmware-string-version (1setOf textWithoutLanguage) = LF25I7,16.66
        printer-firmware-version (1setOf octetString) = 000000010000I7250000000000000000,00000001000016660000000000000000\000
        printer-input-tray (octetString) = printer-input-tray[0]\ =type=sheetFeedAutoNonRemovableTray;dimunit=micrometers;mediafeed=297000;mediaxfeed=210000;maxcapacity=-2;level=-2;status=0;name=Rear\ Auto\ Sheet\ Feeder;
        printer-output-tray (octetString) = type=unRemovableBin;maxcapacity=-2;remaining=-2;status=0;name=Output\ Front;stackingorder=lastToFirst;pagedelivery=faceUp;\000
        pwg-raster-document-type-supported (1setOf keyword) = sgray_8,srgb_8
        pwg-raster-document-resolution-supported (resolution) = 360dpi
        pwg-raster-document-sheet-back (keyword) = rotated



```

Then:

```
lpoptions -p wf1 -lPageSize/Media Size: *A4 4x6 5x7 8x10 A5 A6 Legal Letter B5 3.5x5 Postcard Env10 EnvC6 EnvDL 5x8
MediaType/Media Type: *Stationery PhotographicHighGloss Photographic PhotographicSemiGloss PhotographicGlossy PhotographicMatte Envelope
ColorModel/ModalitÃ  colore: *RGB Gray
cupsPrintQuality/Print Quality: Draft *Normal



```


again:

```
lpoptions -p wf2 -lPageSize/Media Size: 3.5x5 3.5x5.Borderless 4x6 4x6.Borderless 5x7 5x7.Borderless 5x8 8x10 8x10.Borderless *A4 A4.Borderless A5 A6 B5 Env10 EnvC6 EnvDL Legal Letter Letter.Borderless Postcard Postcard.Borderless Custom.WIDTHxHEIGHT
MediaType/Media Type: *Stationery PhotographicHighGloss Photographic PhotographicSemiGloss PhotographicGlossy PhotographicMatte Envelope
ColorModel/Print Color Mode: *RGB Gray
cupsPrintQuality/Print Quality: *4
print-scaling/Print Scaling: *auto auto-fit fill fit none



```

Am I forgetting something?

Thanks in advance and excuse me again!

Andrea

---

### Post by brian_p on 2019-11-02
Thanks for the *ipptool* output. It settles one aspect of your observations - this printer does not support duplex:

> sides-supported (keyword) = one-sided

The other differences are down to the differences in PPD generation of the wf1 and wf2 queues. One is done by CUPS, the other by cups-filters. See [https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting). We have

> printer-resolution-supported (1setOf resolution) = 360dpi,1440x720dpi
>  print-quality-supported (enum) = normal

CUPS uses these two attributes differently from cups-filters. There isn't any attrubute for *draft* in quality-supported.

Maybe the disparities would disappear on newer versions of CUPS and cups-filters.

---

### Post by brian_p on 2019-11-05
Hello again  stilnovo1,

I was still puzzled by your outputs for for the two queues, wf1 and wf2, so I sent a query to the upstream cups-filters maintainer. You can see my post at [https://github.com/OpenPrinting/cups-filters/issues/171](https://github.com/OpenPrinting/cups-filters/issues/171).

The maintainer has responded with

> 
Could you have your user attach the PPD files of the two print
queues (`/etc/cups/ppd/wf1.ppd` and `/etc/cups/ppd/wf2.ppd`) 
to the forum thread? This way one could see the PaperDimension
and ImageableArea entries for the paper sizes.

Please would you attach the two PPDs to a post which you send to this forum.

Thanks in advance.

---

### Post by stilnovo1 on 2019-11-07
Ciao Brian,

wf1.ppd:

```
*PPD-Adobe: "4.3"
*FormatVersion: "4.3"
*FileVersion: "2.2"
*LanguageVersion: English
*LanguageEncoding: ISOLatin1
*PSVersion: "(3010.000) 0"
*LanguageLevel: "3"
*FileSystem: False
*PCFileName: "ippeve.ppd"
*Manufacturer: "EPSON"
*ModelName: "WF-2630 Series"
*Product: "(WF-2630 Series)"
*NickName: "WF-2630 Series"
*ShortNickName: "WF-2630 Series"
*ColorDevice: True
*cupsVersion: 2.2
*cupsSNMPSupplies: False
*cupsLanguages: "en"
*cupsFilter2: "image/jpeg image/jpeg 0 -"
*cupsFilter2: "image/urf image/urf 100 -"
*OpenUI *PageSize: PickOne
*OrderDependency: 10 AnySetup *PageSize
*DefaultPageSize: A4
*PageSize A4: "<</PageSize[595.275590551181 841.889763779528]>>setpagedevice"
*PageSize 4x6: "<</PageSize[288 432]>>setpagedevice"
*PageSize 5x7: "<</PageSize[360 504]>>setpagedevice"
*PageSize 8x10: "<</PageSize[576 720]>>setpagedevice"
*PageSize A5: "<</PageSize[419.527559055118 595.275590551181]>>setpagedevice"
*PageSize A6: "<</PageSize[297.637795275591 419.527559055118]>>setpagedevice"
*PageSize Legal: "<</PageSize[612 1008]>>setpagedevice"
*PageSize Letter: "<</PageSize[612 792]>>setpagedevice"
*PageSize B5: "<</PageSize[515.905511811024 728.503937007874]>>setpagedevice"
*PageSize 3.5x5: "<</PageSize[252 360]>>setpagedevice"
*PageSize Postcard: "<</PageSize[283.464566929134 419.527559055118]>>setpagedevice"
*PageSize Env10: "<</PageSize[296.985826771654 684]>>setpagedevice"
*PageSize EnvC6: "<</PageSize[323.149606299213 459.212598425197]>>setpagedevice"
*PageSize EnvDL: "<</PageSize[311.811023622047 623.622047244094]>>setpagedevice"
*PageSize 5x8: "<</PageSize[360 576]>>setpagedevice"
*CloseUI: *PageSize
*OpenUI *PageRegion: PickOne
*OrderDependency: 10 AnySetup *PageRegion
*DefaultPageRegion: A4
*PageRegion A4: "<</PageSize[595.275590551181 841.889763779528]>>setpagedevice"
*PageRegion 4x6: "<</PageSize[288 432]>>setpagedevice"
*PageRegion 5x7: "<</PageSize[360 504]>>setpagedevice"
*PageRegion 8x10: "<</PageSize[576 720]>>setpagedevice"
*PageRegion A5: "<</PageSize[419.527559055118 595.275590551181]>>setpagedevice"
*PageRegion A6: "<</PageSize[297.637795275591 419.527559055118]>>setpagedevice"
*PageRegion Legal: "<</PageSize[612 1008]>>setpagedevice"
*PageRegion Letter: "<</PageSize[612 792]>>setpagedevice"
*PageRegion B5: "<</PageSize[515.905511811024 728.503937007874]>>setpagedevice"
*PageRegion 3.5x5: "<</PageSize[252 360]>>setpagedevice"
*PageRegion Postcard: "<</PageSize[283.464566929134 419.527559055118]>>setpagedevice"
*PageRegion Env10: "<</PageSize[296.985826771654 684]>>setpagedevice"
*PageRegion EnvC6: "<</PageSize[323.149606299213 459.212598425197]>>setpagedevice"
*PageRegion EnvDL: "<</PageSize[311.811023622047 623.622047244094]>>setpagedevice"
*PageRegion 5x8: "<</PageSize[360 576]>>setpagedevice"
*CloseUI: *PageRegion
*DefaultImageableArea: A4
*DefaultPaperDimension: A4
*ImageableArea A4: "8.503937007874 8.503937007874 586.771653543307 833.385826771654"
*PaperDimension A4: "595.275590551181 841.889763779528"
*ImageableArea 4x6: "8.503937007874 8.503937007874 279.496062992126 423.496062992126"
*PaperDimension 4x6: "288 432"
*ImageableArea 5x7: "8.503937007874 8.503937007874 351.496062992126 495.496062992126"
*PaperDimension 5x7: "360 504"
*ImageableArea 8x10: "8.503937007874 8.503937007874 567.496062992126 711.496062992126"
*PaperDimension 8x10: "576 720"
*ImageableArea A5: "8.503937007874 8.503937007874 411.023622047244 586.771653543307"
*PaperDimension A5: "419.527559055118 595.275590551181"
*ImageableArea A6: "8.503937007874 8.503937007874 289.133858267717 411.023622047244"
*PaperDimension A6: "297.637795275591 419.527559055118"
*ImageableArea Legal: "8.503937007874 8.503937007874 603.496062992126 999.496062992126"
*PaperDimension Legal: "612 1008"
*ImageableArea Letter: "8.503937007874 8.503937007874 603.496062992126 783.496062992126"
*PaperDimension Letter: "612 792"
*ImageableArea B5: "8.503937007874 8.503937007874 507.40157480315 720"
*PaperDimension B5: "515.905511811024 728.503937007874"
*ImageableArea 3.5x5: "8.503937007874 8.503937007874 243.496062992126 351.496062992126"
*PaperDimension 3.5x5: "252 360"
*ImageableArea Postcard: "8.503937007874 8.503937007874 274.96062992126 411.023622047244"
*PaperDimension Postcard: "283.464566929134 419.527559055118"
*ImageableArea Env10: "8.503937007874 8.503937007874 288.48188976378 675.496062992126"
*PaperDimension Env10: "296.985826771654 684"
*ImageableArea EnvC6: "8.503937007874 8.503937007874 314.645669291339 450.708661417323"
*PaperDimension EnvC6: "323.149606299213 459.212598425197"
*ImageableArea EnvDL: "8.503937007874 8.503937007874 303.307086614173 615.11811023622"
*PaperDimension EnvDL: "311.811023622047 623.622047244094"
*ImageableArea 5x8: "8.503937007874 8.503937007874 351.496062992126 567.496062992126"
*PaperDimension 5x8: "360 576"
*OpenUI *MediaType: PickOne
*OrderDependency: 10 AnySetup *MediaType
*DefaultMediaType: Stationery
*MediaType Stationery/Carta comune: "<</MediaType(Stationery)>>setpagedevice"
*MediaType PhotographicHighGloss/High Gloss Photo Paper: "<</MediaType(PhotographicHighGloss)>>setpagedevice"
*MediaType Photographic/Photo Paper: "<</MediaType(Photographic)>>setpagedevice"
*MediaType PhotographicSemiGloss/Semi-Gloss Photo Paper: "<</MediaType(PhotographicSemiGloss)>>setpagedevice"
*MediaType PhotographicGlossy/Glossy Photo Paper: "<</MediaType(PhotographicGlossy)>>setpagedevice"
*MediaType PhotographicMatte/Matte Photo Paper: "<</MediaType(PhotographicMatte)>>setpagedevice"
*MediaType Envelope/Envelope: "<</MediaType(Envelope)>>setpagedevice"
*CloseUI: *MediaType
*OpenUI *ColorModel/ModalitÃ  colore: PickOne
*OrderDependency: 10 AnySetup *ColorModel
*ColorModel RGB/Colore: "<</cupsColorSpace 19/cupsBitsPerColor 8/cupsColorOrder 0/cupsCompression 0>>setpagedevice"
*ColorModel Gray/Scala di grigi: "<</cupsColorSpace 18/cupsBitsPerColor 8/cupsColorOrder 0/cupsCompression 0>>setpagedevice"
*DefaultColorModel: RGB
*CloseUI: *ColorModel
*DefaultResolution: 360dpi
*OpenUI *cupsPrintQuality/Print Quality: PickOne
*OrderDependency: 10 AnySetup *cupsPrintQuality
*DefaultcupsPrintQuality: Normal
*cupsPrintQuality Draft/Draft: "<</HWResolution[360 180]>>setpagedevice"
*cupsPrintQuality Normal/Normale: "<</HWResolution[360 360]>>setpagedevice"
*CloseUI: *cupsPrintQuality
```


wf2.ppd:

```
*PPD-Adobe: "4.3"
*FormatVersion: "4.3"
*FileVersion: "1.20.2"
*LanguageVersion: English
*LanguageEncoding: ISOLatin1
*PSVersion: "(3010.000) 0"
*LanguageLevel: "3"
*FileSystem: False
*PCFileName: "drvless.ppd"
*Manufacturer: "EPSON"
*ModelName: "EPSON WF-2630 Series"
*Product: "(EPSON WF-2630 Series)"
*NickName: "EPSON WF-2630 Series, driverless, cups-filters 1.20.2"
*ShortNickName: "EPSON WF-2630 Series"
*ColorDevice: True
*cupsVersion: 2.2
*cupsSNMPSupplies: False
*cupsLanguages: "en"
*APSupplies: "http://EPSON18823B.local.:80/PRESENTATION/BONJOUR"
*cupsFilter2: "image/pwg-raster image/pwg-raster 0 -"
*cupsFilter2: "image/urf image/urf 100 -"
*cupsFilter2: "image/jpeg image/jpeg 0 -"
*OpenUI *PageSize/Media Size: PickOne
*OrderDependency: 10 AnySetup *PageSize
*DefaultPageSize: A4
*PageSize 3.5x5/3.5 x 5": "<</PageSize[252 360]>>setpagedevice"
*PageSize 3.5x5.Borderless/3.5 x 5" (Borderless): "<</PageSize[252 360]>>setpagedevice"
*PageSize 4x6/4 x 6": "<</PageSize[288 432]>>setpagedevice"
*PageSize 4x6.Borderless/4 x 6" (Borderless): "<</PageSize[288 432]>>setpagedevice"
*PageSize 5x7/5 x 7": "<</PageSize[360 504]>>setpagedevice"
*PageSize 5x7.Borderless/5 x 7" (Borderless): "<</PageSize[360 504]>>setpagedevice"
*PageSize 5x8/5 x 8": "<</PageSize[360 576]>>setpagedevice"
*PageSize 8x10/8 x 10": "<</PageSize[576 720]>>setpagedevice"
*PageSize 8x10.Borderless/8 x 10" (Borderless): "<</PageSize[576 720]>>setpagedevice"
*PageSize A4/A4: "<</PageSize[595.275590551181 841.889763779528]>>setpagedevice"
*PageSize A4.Borderless/A4 (Borderless): "<</PageSize[595.275590551181 841.889763779528]>>setpagedevice"
*PageSize A5/A5: "<</PageSize[419.527559055118 595.275590551181]>>setpagedevice"
*PageSize A6/A6: "<</PageSize[297.637795275591 419.527559055118]>>setpagedevice"
*PageSize B5/JIS B5: "<</PageSize[515.905511811024 728.503937007874]>>setpagedevice"
*PageSize Env10/#10 Envelope: "<</PageSize[296.985826771654 684]>>setpagedevice"
*PageSize EnvC6/C6 Envelope: "<</PageSize[323.149606299213 459.212598425197]>>setpagedevice"
*PageSize EnvDL/DL Envelope: "<</PageSize[311.811023622047 623.622047244094]>>setpagedevice"
*PageSize Legal/US Legal: "<</PageSize[612 1008]>>setpagedevice"
*PageSize Letter/US Letter: "<</PageSize[612 792]>>setpagedevice"
*PageSize Letter.Borderless/US Letter (Borderless): "<</PageSize[612 792]>>setpagedevice"
*PageSize Postcard/Hagaki: "<</PageSize[283.464566929134 419.527559055118]>>setpagedevice"
*PageSize Postcard.Borderless/Hagaki (Borderless): "<</PageSize[283.464566929134 419.527559055118]>>setpagedevice"
*CloseUI: *PageSize
*OpenUI *PageRegion/Media Size: PickOne
*OrderDependency: 10 AnySetup *PageRegion
*DefaultPageRegion: A4
*PageRegion 3.5x5/3.5 x 5": "<</PageSize[252 360]>>setpagedevice"
*PageRegion 3.5x5.Borderless/3.5 x 5" (Borderless): "<</PageSize[252 360]>>setpagedevice"
*PageRegion 4x6/4 x 6": "<</PageSize[288 432]>>setpagedevice"
*PageRegion 4x6.Borderless/4 x 6" (Borderless): "<</PageSize[288 432]>>setpagedevice"
*PageRegion 5x7/5 x 7": "<</PageSize[360 504]>>setpagedevice"
*PageRegion 5x7.Borderless/5 x 7" (Borderless): "<</PageSize[360 504]>>setpagedevice"
*PageRegion 5x8/5 x 8": "<</PageSize[360 576]>>setpagedevice"
*PageRegion 8x10/8 x 10": "<</PageSize[576 720]>>setpagedevice"
*PageRegion 8x10.Borderless/8 x 10" (Borderless): "<</PageSize[576 720]>>setpagedevice"
*PageRegion A4/A4: "<</PageSize[595.275590551181 841.889763779528]>>setpagedevice"
*PageRegion A4.Borderless/A4 (Borderless): "<</PageSize[595.275590551181 841.889763779528]>>setpagedevice"
*PageRegion A5/A5: "<</PageSize[419.527559055118 595.275590551181]>>setpagedevice"
*PageRegion A6/A6: "<</PageSize[297.637795275591 419.527559055118]>>setpagedevice"
*PageRegion B5/JIS B5: "<</PageSize[515.905511811024 728.503937007874]>>setpagedevice"
*PageRegion Env10/#10 Envelope: "<</PageSize[296.985826771654 684]>>setpagedevice"
*PageRegion EnvC6/C6 Envelope: "<</PageSize[323.149606299213 459.212598425197]>>setpagedevice"
*PageRegion EnvDL/DL Envelope: "<</PageSize[311.811023622047 623.622047244094]>>setpagedevice"
*PageRegion Legal/US Legal: "<</PageSize[612 1008]>>setpagedevice"
*PageRegion Letter/US Letter: "<</PageSize[612 792]>>setpagedevice"
*PageRegion Letter.Borderless/US Letter (Borderless): "<</PageSize[612 792]>>setpagedevice"
*PageRegion Postcard/Hagaki: "<</PageSize[283.464566929134 419.527559055118]>>setpagedevice"
*PageRegion Postcard.Borderless/Hagaki (Borderless): "<</PageSize[283.464566929134 419.527559055118]>>setpagedevice"
*CloseUI: *PageRegion
*DefaultImageableArea: A4
*DefaultPaperDimension: A4
*ImageableArea 3.5x5: "8.503937007874 8.503937007874 243.496062992126 351.496062992126"
*PaperDimension 3.5x5: "252 360"
*ImageableArea 3.5x5.Borderless: "0 0 252 360"
*PaperDimension 3.5x5.Borderless: "252 360"
*ImageableArea 4x6: "8.503937007874 8.503937007874 279.496062992126 423.496062992126"
*PaperDimension 4x6: "288 432"
*ImageableArea 4x6.Borderless: "0 0 288 432"
*PaperDimension 4x6.Borderless: "288 432"
*ImageableArea 5x7: "8.503937007874 8.503937007874 351.496062992126 495.496062992126"
*PaperDimension 5x7: "360 504"
*ImageableArea 5x7.Borderless: "0 0 360 504"
*PaperDimension 5x7.Borderless: "360 504"
*ImageableArea 5x8: "8.503937007874 8.503937007874 351.496062992126 567.496062992126"
*PaperDimension 5x8: "360 576"
*ImageableArea 8x10: "8.503937007874 8.503937007874 567.496062992126 711.496062992126"
*PaperDimension 8x10: "576 720"
*ImageableArea 8x10.Borderless: "0 0 576 720"
*PaperDimension 8x10.Borderless: "576 720"
*ImageableArea A4: "8.503937007874 8.503937007874 586.771653543307 833.385826771654"
*PaperDimension A4: "595.275590551181 841.889763779528"
*ImageableArea A4.Borderless: "0 0 595.275590551181 841.889763779528"
*PaperDimension A4.Borderless: "595.275590551181 841.889763779528"
*ImageableArea A5: "8.503937007874 8.503937007874 411.023622047244 586.771653543307"
*PaperDimension A5: "419.527559055118 595.275590551181"
*ImageableArea A6: "8.503937007874 8.503937007874 289.133858267717 411.023622047244"
*PaperDimension A6: "297.637795275591 419.527559055118"
*ImageableArea B5: "8.503937007874 8.503937007874 507.40157480315 720"
*PaperDimension B5: "515.905511811024 728.503937007874"
*ImageableArea Env10: "8.503937007874 8.503937007874 288.48188976378 675.496062992126"
*PaperDimension Env10: "296.985826771654 684"
*ImageableArea EnvC6: "8.503937007874 8.503937007874 314.645669291339 450.708661417323"
*PaperDimension EnvC6: "323.149606299213 459.212598425197"
*ImageableArea EnvDL: "8.503937007874 8.503937007874 303.307086614173 615.11811023622"
*PaperDimension EnvDL: "311.811023622047 623.622047244094"
*ImageableArea Legal: "8.503937007874 8.503937007874 603.496062992126 999.496062992126"
*PaperDimension Legal: "612 1008"
*ImageableArea Letter: "8.503937007874 8.503937007874 603.496062992126 783.496062992126"
*PaperDimension Letter: "612 792"
*ImageableArea Letter.Borderless: "0 0 612 792"
*PaperDimension Letter.Borderless: "612 792"
*ImageableArea Postcard: "8.503937007874 8.503937007874 274.96062992126 411.023622047244"
*PaperDimension Postcard: "283.464566929134 419.527559055118"
*ImageableArea Postcard.Borderless: "0 0 283.464566929134 419.527559055118"
*PaperDimension Postcard.Borderless: "283.464566929134 419.527559055118"
*HWMargins: "8.503937007874 8.503937007874 8.503937007874 8.503937007874"
*ParamCustomPageSize Width: 1 points 252.283464566929 612
*ParamCustomPageSize Height: 2 points 360 3401.574803149606
*ParamCustomPageSize WidthOffset: 3 points 0 0
*ParamCustomPageSize HeightOffset: 4 points 0 0
*ParamCustomPageSize Orientation: 5 int 0 3
*CustomPageSize True: "pop pop pop <</PageSize[5 -2 roll]/ImagingBBox null>>setpagedevice"
*OpenUI *MediaType/Media Type: PickOne
*OrderDependency: 10 AnySetup *MediaType
*DefaultMediaType: Stationery
*MediaType Stationery/Stationery: "<</MediaType(Stationery)>>setpagedevice"
*MediaType PhotographicHighGloss/High Gloss Photo Paper: "<</MediaType(PhotographicHighGloss)>>setpagedevice"
*MediaType Photographic/Photo Paper: "<</MediaType(Photographic)>>setpagedevice"
*MediaType PhotographicSemiGloss/Semi-Gloss Photo Paper: "<</MediaType(PhotographicSemiGloss)>>setpagedevice"
*MediaType PhotographicGlossy/Glossy Photo Paper: "<</MediaType(PhotographicGlossy)>>setpagedevice"
*MediaType PhotographicMatte/Matte Photo Paper: "<</MediaType(PhotographicMatte)>>setpagedevice"
*MediaType Envelope/Envelope: "<</MediaType(Envelope)>>setpagedevice"
*CloseUI: *MediaType
*OpenUI *ColorModel/Print Color Mode: PickOne
*OrderDependency: 10 AnySetup *ColorModel
*ColorModel RGB/Color: "<</cupsColorSpace 19/cupsBitsPerColor 8/cupsColorOrder 0/cupsCompression 0>>setpagedevice"
*ColorModel Gray/Monochrome: "<</cupsColorSpace 18/cupsBitsPerColor 8/cupsColorOrder 0/cupsCompression 0>>setpagedevice"
*DefaultColorModel: RGB
*CloseUI: *ColorModel
*DefaultResolution: 360dpi
*OpenUI *cupsPrintQuality/Print Quality: PickOne
*OrderDependency: 10 AnySetup *cupsPrintQuality
*DefaultcupsPrintQuality: 4
*cupsPrintQuality 4/Normal: "<</HWResolution[360 360]>>setpagedevice"
*CloseUI: *cupsPrintQuality
*OpenUI *print-scaling/Print Scaling: PickOne
*OrderDependency: 10 AnySetup *print-scaling
*Defaultprint-scaling: auto
*print-scaling auto/Automatic: ""
*print-scaling auto-fit/Auto Fit: ""
*print-scaling fill/Fill: ""
*print-scaling fit/Fit: ""
*print-scaling none/None: ""
*CloseUI: *print-scaling
```


ciao!

---

### Post by Till Kamppeter on 2019-11-11
The problem why you are not able to print is that some printers report that they accept PWG Raster as input format but are not able to actually print jobs in this format. Most of them also accept Apple Raster and therefore the PPD generator of CUPS prioritizes Apple Raster if both are supported. I will modify the PPD generator of cups-filters to do the same. See [my comment on the issue in cups-filters]("https://github.com/OpenPrinting/cups-filters/issues/171#issuecomment-552549278").

The differences in the option choices I will investigate separately.

   Till

---

### Post by Till Kamppeter on 2019-11-11
@stilnovo1, could you run the following command

```
ipptool -tv ipp://EPSON18823B.local:631/ipp/print get-printer-attributes-2.0.test
```

and post or attach the output here? Thanks.

Important is the "-2.0" here.

   Till

---

### Post by Till Kamppeter on 2019-11-12
I have found solutions for the option choice discrepancies now:

- The listing of the borderless page sizes by cups-filters is correct. Your printer actually supports borderless printing. In CUPS this is fixed from 2.3.x on.
- CUPS lists a draft print quality for your printer because the minimum resolution listed is even, not because a draft print quality choice is reported by the printer. I think that this will not reliably work for every printer and let cups-filters only list a draft print quality if the printer actually reports it.
- I have fixed the "cupsPrintQuality" option in the PPD generator of cups-filters to use "Draft", "Normal", and "High" as choice names and not 3, 4, and 5.

See also my last comments in the [issue report on cups-filters]("https://github.com/OpenPrinting/cups-filters/issues/171").

   Till

---

### Post by stilnovo1 on 2019-11-12
@Till

```
ipptool -tv ipp://EPSON18823B.local:631/ipp/print get-printer-attributes-2.0.test
ipptool: Unable to open test file get-printer-attributes-2.0.test - File o directory non esistente
```

This is the output, but I imagine I'm doing something wrong....

---

### Post by brian_p on 2019-11-12
> **stilnovo1 said:**
> @Till

```
ipptool -tv ipp://EPSON18823B.local:631/ipp/print get-printer-attributes-2.0.test
ipptool: Unable to open test file get-printer-attributes-2.0.test - File o directory non esistente
```

This is the output, but I imagine I'm doing something wrong....

You are doing nothing wrong but Till might not have appreciated you are on Ubuntu 18.04. I have attached get-printer-attributes-2.0.test to this post. Put it in your home directory and do

```
mv get-printer-attributes-2.0.test.txt get-printer-attributes-2.0.test
```

Run the command Till gave you like this:

```
ipptool -tv ipp://EPSON18823B.local:631/ipp/print $HOME/get-printer-attributes-2.0.test
```

Thank you for your time and trouble, stilnovo1. You are doing really well.

---

### Post by stilnovo1 on 2019-11-16
Ciao Brian!

```
zambo@zambo-HP-new:~$ mv get-printer-attributes-2.0.test.txt get-printer-attributes-2.0.testmv: impossibile eseguire stat di 'get-printer-attributes-2.0.test.txt': File o directory non esistente

```

the second one:

```
ipptool -tv ipp://EPSON18823B.local:631/ipp/print $HOME/get-printer-attributes-2.0.test
ipptool: Unable to open test file /home/zambo/get-printer-attributes-2.0.test - File o directory non esistente



```

I've run in the home directory... do you want that I translate in english the italian replies I get from the terminal in the next posts?

---

### Post by brian_p on 2019-11-16
No thanks. I've got the message. Try putting get-printer-attributes-2.0.test in /usr/share/cups/ipptool/ and running ```
ipptool -tv ipp://EPSON18823B.local:631/ipp/print get-printer-attributes-2.0.test
```

---

### Post by stilnovo1 on 2019-12-10
Ciao Brian!

Sometimes it seems that I disappear, but it's only for working reasons.

Well:

```
zambo@zambo-HP-new:/usr/share/cups/ipptool$ ipptool -tv ipp://EPSON18823B.local:631/ipp/print get-printer-attributes-2.0.testipptool: Unable to open test file get-printer-attributes-2.0.test - File o directory non esistente



```

---

### Post by brian_p on 2019-12-10
Hello stilnovo1, Thank you for keeping us in your thoughts,  :p your update is appreciated. However, I do not think we need go any further with this. Your previous co-operation has led to alterations being made in upstream cups-filters. That's a good result.

---

### Post by stilnovo1 on 2019-12-11
Well, I'm happy in having contributed to better...cups-filters! So, have I to mark this thread as solved?

---

### Post by brian_p on 2019-12-11
> **stilnovo1 said:**
> Well, I'm happy in having contributed to better...cups-filters! So, have I to mark this thread as solved?

I think that would be best.

---

