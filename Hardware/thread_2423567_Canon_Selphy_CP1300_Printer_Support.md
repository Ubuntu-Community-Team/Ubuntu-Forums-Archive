---
title: "Canon Selphy CP1300 Printer Support"
date: 2019-07-25
forum: Hardware
---

### Post by Geek4096 on 2019-07-25
Has anyone successfully added a Canon Selphy CP1300 to an Ubuntu 18+ system?  The CP910 worked great but the CP1300 doesn't appear to be supported.  Any help is much appreciated. Thanks.

---

### Post by him610 on 2019-07-25
Don't think it's Linux time for this printer yet - may never be. At the Amazon webpage for this printer, there  are 438 reviews with no mention of Linux or Ubuntu. From the Amazon description....
 > Requires an Internet connection and the Canon PRINT Inkjet/SELPHY app, available for free on the App Store and at Google Play. Compatible with iPad, iPhone 3GS or later, and iPod touch 3rd generation or later devices running iOS 7.0 or later, and AndroidTM mobile devices running Android 2.3.3 or later. Your device must be connected to the same working network with wireless 802.11 b/g/n/ac/ad capability as your printer. Requires an compatible social media account and is subject to that social media account’s Terms of Service. Certain exceptions may apply.
Looks like it's made to be used with smart phones.

---

### Post by brian_p on 2019-07-26
> **him610 said:**
> Don't think it's Linux time for this printer yet - may never be.

Let's see. Geek4096 should put the device on the network and give us the outputs of these two commands:

```
driverless
```
```
avahi-browse -rt _ipp._tcp
```

Hopefully, the Ubuntu being used is at least 18.04.

---

### Post by dimtass on 2019-08-06
> **brian_p said:**
> Let's see. Geek4096 should put the device on the network and give us the outputs of these two commands:

```
driverless
```
```
avahi-browse -rt _ipp._tcp
```

Hopefully, the Ubuntu being used is at least 18.04.

Since there wasn't any reply from the original poster and I'm having the same issue, I'll post my output

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic
```

```

$ [COLOR=#000000][FONT=&amp]driverless[/FONT][/COLOR] [COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]ipp://CP1300b3a49e.local:631/ipp/print
```

```
$ avahi-browse -rt _ipp._tcp
+ enp31s0 IPv4 Canon SELPHY CP1300                           Internet Printer     local
= enp31s0 IPv4 Canon SELPHY CP1300                           Internet Printer     local
   hostname = [CP1300b3a49e.local]
   address = [192.168.0.105]
   port = [631]
   txt = ["note=" "mopria-certified=1.3" "print_wfds=T" "kind=photo" "URF=W8,SRGB24,V1.4,RS300,IS7,MT11,PQ4,OB9,IFU0,OFU0,CP99" "TLS=1.2" "Staple=F" "Sort=F" "Scan=F" "Punch=0" "PaperMax=<legal-A4" "PaperCustom=T" "Fax=F" "Duplex=F" "Copies=T" "Color=T" "Collate=F" "Bind=F" "TBCP=F" "Binary=F" "Transparent=F" "UUID=f84aad2c-f8a5-43ac-9673-9c32ceb3a49e" "usb_CMD=URF" "usb_MDL=SELPHY CP1300" "usb_MFG=Canon" "adminurl=http://CP1300b3a49e.local:8008/index.html" "pdl=image/urf,image/jpeg,image/pwg-raster,application/octet-stream" "product=(Canon SELPHY CP1300 HTTP)" "ty=Canon SELPHY CP1300 HTTP" "priority=50" "qtotal=1" "rp=ipp/print" "txtvers=1"]
```

It would be great having this printer working in Ubuntu. I'm a bit shamed that I have to launch a win10 vbox to print or use darktable to export the pictures, then copy them to my smartphone and print... :/

Thanks!

---

### Post by brian_p on 2019-08-06
> **dimtass said:**
> Since there wasn't any reply from the original poster and I'm having the same issue, I'll post my output

Thank you.

> 
```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic
```



Good.

```

$ [COLOR=#000000][FONT=&amp]driverless[/FONT][/COLOR] [COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]ipp://CP1300b3a49e.local:631/ipp/print
```

This following is a partial quote from the information provided:

> 
   txt = ["URF=W8,SRGB24,V1.4,RS300,IS7,MT11,PQ4,OB9,IFU0,OFU0,CP99"
"pdl=image/urf,image/jpeg,image/pwg-raster,application/octet-stream"]

*URF=* indicates that this is an AirPrint device. *pdl=* indicates the document types the printer will accept. CUPS + cups-filters can provide any of them. image/urf will be the preferred one generated and sent to the printer.

Set up a print queue with

```
lpadmin -p cp1300 -v ipp://CP1300b3a49e.local:631/ipp/print -E -m everywhere
```

I would be surprised if you could not print with

```
lp -d cp1300 /etc/nsswitch
```

or from any application.

---

### Post by aqui_c on 2019-08-15
I've managed to make it work by installing the latest drivers from Gutenprint. The stock version of Gutenprint has support up to CP1200, while the latest version includes the CP1300. 
I will copy the steps I've followed below:

Just head to the [downloads page]("https://sourceforge.net/projects/gimp-print/files/"), and unzip it with the following command:

```
tar xjvf gutenprint-5.0.0.tar.bz2
```

You should also install **libcups2-dev** in case you don't have it already:

```
sudo apt install libcups2-dev
```.

Enter into the gutenprint folder and run the following command:

```
./configure
```

Check that the output contains something like the following, to ensure CUPS drivers will be updated:

```
  Features:
    Build CUPS:                                 yes, installing in /usr
        Build CUPS 1.2 enhancements:            yes
        Build CUPS PPD files:                   no
        Generate PS level 3 CUPS PPD files:     yes

```

Then, it is time to compile and install:

```
make
sudo make install
```

And then, restart cups:

```
sudo systemctl restart cups
```

And head to 

```
http://localhost:631
``` 

in order to see the CUPS admin, and add your printer.

---

### Post by Geek4096 on 2020-01-22
> **aqui_c said:**
> I've managed to make it work by installing the latest drivers from Gutenprint. The stock version of Gutenprint has support up to CP1200, while the latest version includes the CP1300. 
I will copy the steps I've followed below:

Just head to the [downloads page]("https://sourceforge.net/projects/gimp-print/files/"), and unzip it with the following command:

```
tar xjvf gutenprint-5.0.0.tar.bz2
```

You should also install **libcups2-dev** in case you don't have it already:

```
sudo apt install libcups2-dev
```.

Enter into the gutenprint folder and run the following command:

```
./configure
```

Check that the output contains something like the following, to ensure CUPS drivers will be updated:

```
  Features:
    Build CUPS:                                 yes, installing in /usr
        Build CUPS 1.2 enhancements:            yes
        Build CUPS PPD files:                   no
        Generate PS level 3 CUPS PPD files:     yes

```

Then, it is time to compile and install:

```
make
sudo make install
```

And then, restart cups:

```
sudo systemctl restart cups
```

And head to 

```
http://localhost:631
``` 

in order to see the CUPS admin, and add your printer.




So...my humble apologies that I failed to respond following the discussion on my original post. (I'm old and got distracted :o|  ).  I have recompiled CUPS on Ubuntu 19.10 and have the same issues after following the advice above on the CP1300. 

The output from driverless:

ipp://CP1300b126ad.local:631/ipp/print


The output from the avahi-browse command is (relative to the CP1300):

 
avahi-browse -rt _ipp._tcp

   hostname = [CP1300b126ad.local]
   address = [192.168.6.251]
   port = [631]
   txt = ["note=" "mopria-certified=1.3" "print_wfds=T" "kind=photo" "URF=W8,SRGB24,V1.4,RS300,IS7,MT11,PQ4,OB9,IFU0,OFU0,CP99" "TLS=1.2" "Staple=F" "Sort=F" "Scan=F" "Punch=0" "PaperMax=<legal-A4" "PaperCustom=T" "Fax=F" "Duplex=F" "Copies=T" "Color=T" "Collate=F" "Bind=F" "TBCP=F" "Binary=F" "Transparent=F" "UUID=9f10be80-7c62-4229-b8da-9c32ceb126ad" "usb_CMD=URF" "usb_MDL=SELPHY CP1300" "usb_MFG=Canon" "adminurl=http://CP1300b126ad.local:8008/index.html" "pdl=image/urf,image/jpeg,image/pwg-raster,application/octet-stream" "product=(Canon SELPHY CP1300 HTTP)" "ty=Canon SELPHY CP1300 HTTP" "priority=50" "qtotal=1" "rp=ipp/print" "txtvers=1"]


I've tried every combination that cups offers without success...the printer goes busy, then always responds with "Cannot read data!  Cannot print incompatible images or memory card not readable".  I've checked to make sure paper size is correct (and there is no sd memory card installed in the printer)

Thanks (and, again, sorry for spacing it out months back...)

---

### Post by brian_p on 2020-01-22
The print queue to set up is:

```
lpadmin -p cp1300 -v ipp://CP1300b126ad.local:631/ipp/print -E -m everywhere
```

Can you print with

```
lp -d cp1300 /etc/nsswitch.conf
```

---

### Post by brian_p on 2020-01-24
> So...my humble apologies that I failed to respond following the discussion on my original post. (I'm old and got distracted 

Looks as though distraction is the norm  in this thread. Ah well!

---

### Post by Geek4096 on 2020-02-05
brian_p, I do appreciate your technical reply.  Here is the command line response:

  $ lpadmin -p cp1300 -v ipp://CP1300b126ad.local:631/ipp/print -E -m everywherelpadmin: Unable to connect to "CP1300b126ad.local:631": Name or service not known

$ lp -d cp1300 /etc/nsswitch.conf
lp: No such file or directory

---

