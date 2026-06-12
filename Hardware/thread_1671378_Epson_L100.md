---
title: "Epson L100"
date: 2011-01-19
forum: Hardware
---

### Post by akuhon on 2011-01-19
> **UPDATE [JAN 20, 2014]**, contributed by **rudregues** 

Epson released a full feature driver for L100/L200!!!

Avasys dropped the download service for Epson printer drivers, now you must use this Epson's website [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

Just search for L100 or L200 and there will be two results. The first is for the printer and the second for the scanner.
Now, no need to add your printer as Stylus N10 N11 you add your printer as L100 or L200

1) For the printer (L100 and L200)
Download and install epson-inkjet-printer-l100l200_1.0.0-1lsb3.2_amd64.deb from the first link

2) For the scanner (L200 only)
Download and install iscan-data_1.26.0-1_all.deb then donwload and install iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb


Obs.: If you use Ubuntu 32 bits remember downloading i386 instead of amd64 packages

> UPDATED [JUNE 15th, 2013] : New web site to download

For L100 (no scan function) and L200 (with scan function)

The new web site for this driver is here : [http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)
But you still need :
1. Printer Driver (for L100 and L200), type in search box : Stylus N10 N11
2. Scan driver (only for L200), type in search box : L200

There are some updated model of this kind of printer i.e. : L110, L210 and so on.
To get the driver for printer (L110) or printer with scanner (L210), just type the print model in search box i.e. L210, L110 etc.

Remember that this new models' drivers (L110, L210) for printing or scanning **[COLOR="#0000FF"]_are not compatible_[/COLOR]** with L100 or L200 above.
So if you need printer or scan driver for L100 or L200, please do the above mentioned.

Thanks


Hai

I've just installed a new printer : Epson L100, but I can't find any linux driver suitable for this printing machine. I've tried to see openprinting, but no luck so far..

My question :
1. Is this printer already supported in Linux (especially Ubuntu) ?
2. Anyone know some alternatives for printing driver ?

If you need more info regarding this printer, I'm happy to help.
You can see this printer here :
[http://www.epson.co.id/epson_indonesia/printers_and_all_in_ones/inkjet/product.page?product_name=Epson_L100](http://www.epson.co.id/epson_indonesia/printers_and_all_in_ones/inkjet/product.page?product_name=Epson_L100)

In the meantime, I've done the 'lsusb -v' command and the result:

[COLOR="Blue"]```
Bus 003 Device 002: ID 04b8:001b Seiko Epson Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x04b8 Seiko Epson Corp.
  idProduct          0x001b 
  bcdDevice            1.00
  iManufacturer           1 EPSON
  iProduct                2 EPSON L100 Series
  iSerial                 3 NLUK013539        
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0001
  Self Powered
```[/COLOR]

**_[SIZE="3"]SOLUTION[/SIZE]_**

**For Epson L100**

Please download the following driver :
```
[http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-i386/epson-inkjet-printer-n10-nx127_1.0.0-1lsb3.2_i386.deb]("http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-i386/epson-inkjet-printer-n10-nx127_1.0.0-1lsb3.2_i386.deb")
If the link doesn't work go to :
[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/)
then, scroll down until you find Stylus N10 or Stylus N11.
Download the driver according your system (32 bit or 64bit)
```

Disconnect the Epson L100 / L200 USB printer cable, install the driver, then connect the cable -> push start button 

It will try to search the driver but no luck, just "cancel" it.

Then in "Choose Driver", make sure you tick the "Select printer form database"

choose [Epson] -> [Stylus N10 N11] -> [Forward] -> [Apply] -> give any names if necessary. Done.

**For Epson 200**

Same as the above for L100, with additional files for scanning to download i.e. :

the data 

```
[http://linux.avasys.jp/drivers/iscan-data/1.8.0/iscan-data_1.8.0-0_all.deb]("http://linux.avasys.jp/drivers/iscan-data/1.8.0/iscan-data_1.8.0-0_all.deb")
```

and the core 

```
[http://linux.avasys.jp/drivers/iscan/2.26.2/iscan_2.26.2-1.ltdl7_i386.deb]("http://linux.avasys.jp/drivers/iscan/2.26.2/iscan_2.26.2-1.ltdl7_i386.deb")
```

Install it and restart Ubuntu

You can print and scan now ... For scanning, just use xsane or any other scan s/w.

note:for the core files, you have to make sure, what types of processor (CPU) you're running and Ubuntu version.
Please go to this site : [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do) to change (just scroll down the page until you see "L200", tick it and choose whatever Linux and its version). My system now running Ubuntu 9.04 with 32bit Intel-based CPU

That's all, hope it help.

---

### Post by cchhrriiss121212 on 2011-01-20
Epson printers are supported on Linux by a company called Avasys. They do not have your printer listed yet, but you could try using the generic driver as they all use the same standard:
[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/]("http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/")
After installing the deb file from here, run the printing app from the system menu.

---

### Post by akuhon on 2011-01-20
hai,

Thanks...

I'll try ... and will report here.
Also there's an app called mtink (ttink).
Does it neccessary to be installed ?

Rgds,
Arthur

---

### Post by akuhon on 2011-01-21
Tried, the avasys driver, no luck so far ....

---

### Post by cchhrriiss121212 on 2011-01-21
Try contacting Epson or Avasys, they might tell you what the status is.

---

### Post by akuhon on 2011-02-10
I have contacted avasys but no definitive answer.

I did the idiot way .... trying all the new drivers here :
[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/)
Then I found 1 driver that work with Epson L100 on Ubuntu 10.4 

If you use Intel-based std machine (like me), not the high-end one, please download this driver to use Epson L100 printer :

```
[http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-i386/epson-inkjet-printer-px-503a-203-series_1.0.0-1lsb3.2_i386.deb]("http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-i386/epson-inkjet-printer-px-503a-203-series_1.0.0-1lsb3.2_i386.deb")

install it (dpkg or from GUI ... )

Then choose "Stylus N10 N11" from the selectable drivers option
```

Please choose other files, according to your processors (CPU).

As of this writing, this printer (Epson L100) it's not officially support yet (no official announcement at Avasys) but it works for me. Hope it helps.


Thanks

---

### Post by psadikin on 2011-03-04
Hi,

I tried the advice, and it works!!  But there is no printer driver for Epson N10 11, so I use driver for Epson NX100 and it works wonderfully.

Thank you for sharing the tip.

Priadi

---

### Post by akuhon on 2011-03-23
> **psadikin said:**
> Hi,

I tried the advice, and it works!!  But there is no printer driver for Epson N10 11, so I use driver for Epson NX100 and it works wonderfully.

Thank you for sharing the tip.

Priadi

I think they seperated the files.
By the time I downloaded, the driver is packed together within the file link above, now they separate it in :

```
[http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-i386/epson-inkjet-printer-n10-nx127_1.0.0-1lsb3.2_i386.deb]("http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-i386/epson-inkjet-printer-n10-nx127_1.0.0-1lsb3.2_i386.deb")
```

NX100 worked but not perfectly aligned at that time. Maybe it's better now.

---

### Post by akuhon on 2011-03-28
Just add aditional info for Epson L200 under Ubuntu..

Please see my 1st post ..

Thanks

---

### Post by akuhon on 2011-03-28
Link correction on 1st post ...

---

### Post by arvin555 on 2011-10-10
Just wanted to share this info I just read:

[http://www.omgubuntu.co.uk/2011/04/ubuntu-11-04-gets-automatic-epson-driver-download/]("http://www.omgubuntu.co.uk/2011/04/ubuntu-11-04-gets-automatic-epson-driver-download/")

Apparently Epson woke up and will now hopefully have one of the most convenient driver support for Linux amongst Printer makers.  We just have to first update to Ubuntu 11.04. 

Wonder why we can't just add a Distro for our older Ubuntu versions?

TTFN
Arvin

---

### Post by anezch on 2011-10-20
Hi, anyone tried to refill the ink without Epson monitoring app in MS Windows?

---

### Post by galerie on 2012-01-04
> **akuhon said:**
> Hai

I've just installed a new printer : Epson L100, but I can't find any linux driver suitable for this printing machine. I've tried to see openprinting, but no luck so far..

My question :
1. Is this printer already supported in Linux (especially Ubuntu) ?
2. Anyone know some alternatives for printing driver ?

If you need more info regarding this printer, I'm happy to help.
You can see this printer here :
[http://www.epson.co.id/epson_indonesia/printers_and_all_in_ones/inkjet/product.page?product_name=Epson_L100](http://www.epson.co.id/epson_indonesia/printers_and_all_in_ones/inkjet/product.page?product_name=Epson_L100)

In the meantime, I've done the 'lsusb -v' command and the result:

[COLOR=Blue]```
Bus 003 Device 002: ID 04b8:001b Seiko Epson Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x04b8 Seiko Epson Corp.
  idProduct          0x001b 
  bcdDevice            1.00
  iManufacturer           1 EPSON
  iProduct                2 EPSON L100 Series
  iSerial                 3 NLUK013539        
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0001
  Self Powered
```[/COLOR]

**_[SIZE=3]SOLUTION[/SIZE]_**

**For Epson L100**

Please download the following driver :
```
[http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-i386/epson-inkjet-printer-n10-nx127_1.0.0-1lsb3.2_i386.deb](http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-i386/epson-inkjet-printer-n10-nx127_1.0.0-1lsb3.2_i386.deb)
```Disconnect the Epson L100 / L200 USB printer cable, install the driver, then connect the cable -> push start button 

It will try to search the driver but no luck, just "cancel" it.

Then in "Choose Driver", make sure you tick the "Select printer form database"

choose [Epson] -> [Stylus N10 N11] -> [Forward] -> [Apply] -> give any names if necessary. Done.

**For Epson 200**

Same as the above for L100, with additional files for scanning to download i.e. :

the data 

```
[http://linux.avasys.jp/drivers/iscan-data/1.8.0/iscan-data_1.8.0-0_all.deb](http://linux.avasys.jp/drivers/iscan-data/1.8.0/iscan-data_1.8.0-0_all.deb)
```and the core 

```
[http://linux.avasys.jp/drivers/iscan/2.26.2/iscan_2.26.2-1.ltdl7_i386.deb](http://linux.avasys.jp/drivers/iscan/2.26.2/iscan_2.26.2-1.ltdl7_i386.deb)
```Install it and restart Ubuntu

You can print and scan now ... For scanning, just use xsane or any other scan s/w.

note:for the core files, you have to make sure, what types of processor (CPU) you're running and Ubuntu version.
Please go to this site : [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do) to change (just scroll down the page until you see "L200", tick it and choose whatever Linux and its version). My system now running Ubuntu 9.04 with 32bit Intel-based CPU

That's all, hope it help.
what if it is a network printer is this work too? Sorry or my bad english, since u told that u use epson l-200 I assumed that u came from indonesia.than I should try asking question in indonesian:D
Q: kalau mw connect ke printer l200 yang ada di jaringan gimana caranya gan?
baru 2 hari make ubuntu masih bingung :D

---

### Post by AlexanderDGreat on 2012-01-11
Guys, why does it always have to be damn tiring and plain old difficult for Ubuntu?

Our life is short.

Just use VirtualBox, install Windows, and install the printer there!

---

### Post by galerie on 2012-01-24
> **AlexanderDGreat said:**
> Guys, why does it always have to be damn tiring and plain old difficult for Ubuntu?

Our life is short.

Just use VirtualBox, install Windows, and install the printer there!

yep.. for me as a truly noob to linux, it may help. but what if I install ubuntu on my old computer?
I am talking bout resources. does virtual need a lot of resources? if it does than I should find another option T_T. cause I have an old rig in my room and I want to install ubuntu on it.

---

### Post by mehersanjeev on 2012-03-15
[B]thanks
[/B]

---

### Post by mehersanjeev on 2012-03-15
> **galerie said:**
> what if it is a network printer is this work too? Sorry or my bad english, since u told that u use epson l-200 I assumed that u came from indonesia.than I should try asking question in indonesian:D
Q: kalau mw connect ke printer l200 yang ada di jaringan gimana caranya gan?
baru 2 hari make ubuntu masih bingung :D
Originally Posted by **akuhon** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10377802#post10377802") 				
 				Hai

I've just installed a new printer : Epson L100, but I can't find any  linux driver suitable for this printing machine. I've tried to see  openprinting, but no luck so far..

My question :
1. Is this printer already supported in Linux (especially Ubuntu) ?
2. Anyone know some alternatives for printing driver ?

If you need more info regarding this printer, I'm happy to help.
You can see this printer here :
[http://www.epson.co.id/epson_indones...ame=Epson_L100]("http://www.epson.co.id/epson_indonesia/printers_and_all_in_ones/inkjet/product.page?product_name=Epson_L100")

In the meantime, I've done the 'lsusb -v' command and the result:


Its working now properly

thanks

---

### Post by akuhon on 2012-05-11
> **galerie said:**
> what if it is a network printer is this work too? Sorry or my bad english, since u told that u use epson l-200 I assumed that u came from indonesia.than I should try asking question in indonesian:D
Q: kalau mw connect ke printer l200 yang ada di jaringan gimana caranya gan?
baru 2 hari make ubuntu masih bingung :D

You need time to learn ...
Just go to System -> Admin -> Printing. Add Printer -> Networked Printer .... Fill out the ip address of the computer, where the printer attached.

OK...

---

### Post by Jetset Funky on 2012-06-14
> **akuhon said:**
> Hai

I've just installed a new printer : Epson L100, but I can't find any linux driver suitable for this printing machine. I've tried to see openprinting, but no luck so far..

My question :
1. Is this printer already supported in Linux (especially Ubuntu) ?
2. Anyone know some alternatives for printing driver ?

If you need more info regarding this printer, I'm happy to help.
You can see this printer here :
[http://www.epson.co.id/epson_indonesia/printers_and_all_in_ones/inkjet/product.page?product_name=Epson_L100](http://www.epson.co.id/epson_indonesia/printers_and_all_in_ones/inkjet/product.page?product_name=Epson_L100)

In the meantime, I've done the 'lsusb -v' command and the result:

[COLOR=Blue]```
Bus 003 Device 002: ID 04b8:001b Seiko Epson Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x04b8 Seiko Epson Corp.
  idProduct          0x001b 
  bcdDevice            1.00
  iManufacturer           1 EPSON
  iProduct                2 EPSON L100 Series
  iSerial                 3 NLUK013539        
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0001
  Self Powered
```[/COLOR]

**_[SIZE=3]SOLUTION[/SIZE]_**

**For Epson L100**

Please download the following driver :
```
[http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-i386/epson-inkjet-printer-n10-nx127_1.0.0-1lsb3.2_i386.deb](http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-i386/epson-inkjet-printer-n10-nx127_1.0.0-1lsb3.2_i386.deb)
If the link doesn't work go to :
[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/)
then, scroll down until you find Stylus N10 or Stylus N11.
Download the driver according your system (32 bit or 64bit)
```Disconnect the Epson L100 / L200 USB printer cable, install the driver, then connect the cable -> push start button 

It will try to search the driver but no luck, just "cancel" it.

Then in "Choose Driver", make sure you tick the "Select printer form database"

choose [Epson] -> [Stylus N10 N11] -> [Forward] -> [Apply] -> give any names if necessary. Done.

**For Epson 200**

Same as the above for L100, with additional files for scanning to download i.e. :

the data 

```
[http://linux.avasys.jp/drivers/iscan-data/1.8.0/iscan-data_1.8.0-0_all.deb](http://linux.avasys.jp/drivers/iscan-data/1.8.0/iscan-data_1.8.0-0_all.deb)
```and the core 

```
[http://linux.avasys.jp/drivers/iscan/2.26.2/iscan_2.26.2-1.ltdl7_i386.deb](http://linux.avasys.jp/drivers/iscan/2.26.2/iscan_2.26.2-1.ltdl7_i386.deb)
```Install it and restart Ubuntu

You can print and scan now ... For scanning, just use xsane or any other scan s/w.

note:for the core files, you have to make sure, what types of processor (CPU) you're running and Ubuntu version.
Please go to this site : [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do) to change (just scroll down the page until you see "L200", tick it and choose whatever Linux and its version). My system now running Ubuntu 9.04 with 32bit Intel-based CPU

That's all, hope it help.

Thanks, work nicely for me on BT5R2 :guitar:

---

### Post by rudregues on 2012-06-16
Hey guys, I'm installing those drivers on my new L200, but I've found this notice:

"[COLOR=red]**Notice on transferring the responsibility of Linux Driver Download Website**
Regarding our Linux driver download service, we will transfer the  service from AVASYS CORPORATION to SEIKO EPSON CORPORATION on Thursday,  December 22nd, 2011 (0:00 JST).
After the transfer, the download service is available in the following website[COLOR=Black]." 
source: [http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/)


There is more updated drivers in [this website]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX")[]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX")

Searching by L200, will give you  [this]("http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=PT&CN2=&DSCMI=17168&DSCCHK=c995530f7b1509a5811e418c8e2b5763042a4998") as result.[/COLOR][/COLOR][URL="http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=PT&CN2=&DSCMI=17168&DSCCHK=c995530f7b1509a5811e418c8e2b5763042a4998"]

[/URL]I'll now restart my system with the new drivers installed then test my printer.
[URL="http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=PT&CN2=&DSCMI=17168&DSCCHK=c995530f7b1509a5811e418c8e2b5763042a4998"]
[/URL][  ]'s

---

### Post by ezugaru on 2012-07-10
> **rudregues said:**
> Hey guys, I'm installing those drivers on my new L200, but I've found this notice:

"[COLOR=red]**Notice on transferring the responsibility of Linux Driver Download Website**
Regarding our Linux driver download service, we will transfer the  service from AVASYS CORPORATION to SEIKO EPSON CORPORATION on Thursday,  December 22nd, 2011 (0:00 JST).
After the transfer, the download service is available in the following website[COLOR=Black]." 
source: [http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/)


There is more updated drivers in [this website]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX")[]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX")

Searching by L200, will give you  [this]("http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=PT&CN2=&DSCMI=17168&DSCCHK=c995530f7b1509a5811e418c8e2b5763042a4998") as result.[/COLOR][/COLOR][URL="http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=PT&CN2=&DSCMI=17168&DSCCHK=c995530f7b1509a5811e418c8e2b5763042a4998"]

[/URL]I'll now restart my system with the new drivers installed then test my printer.
[URL="http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=PT&CN2=&DSCMI=17168&DSCCHK=c995530f7b1509a5811e418c8e2b5763042a4998"]
[/URL][  ]'s

Hi, how does the installation went for you? doesnt the driver just work for the scanner? or it does contain the printer driver too? I does include the app that verify the code of the ink bottles? Thanks in advance ;)

---

### Post by rudregues on 2012-07-11
Apparently, the driver works out of the box, both scanner and printer. I don't know about print high resolution images, never tried, but common text and low resolution images it's excelent.

I followed all steps described in the first post, only changing the core package described by the more updated I had found. 

> It does include the app that verify the code of the ink bottles? 
No, unfortunately  :frown:
For this, you must go Windows. Mac OS and Linux users cannot until now.

 [ ]'s

---

### Post by stJac on 2013-05-16
> **AlexanderDGreat said:**
> Guys, why does it always have to be damn tiring and plain old difficult for Ubuntu?

Our life is short.

Just use VirtualBox, install Windows, and install the printer there!

Just do that and be calm. I hope, this suggestion prevent your suicide. My was prevented :)

---

### Post by akuhon on 2013-06-14
Please see the update on 1st page

Thx all

---

### Post by rudregues on 2014-01-20
[SIZE=5][COLOR=#ff0000]Major update!!!![/COLOR]

[COLOR=#ff0000][SIZE=3]Epson released a full feature driver for L100/L200!!![/SIZE][/COLOR]
[/SIZE]
Avasys dropped the download service for Epson printer drivers, now you must use this Epson's website [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)


Just search for L100 or L200 and there will be two results. The first is for the printer and the second for the scanner.

1) For the printer
Download and install epson-inkjet-printer-l100l200_1.0.0-1lsb3.2_amd64.deb from the first link

2) For the scanner
Download and install iscan-data_1.26.0-1_all.deb then donwload and install iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb

3) Now, instead of add your printer as [COLOR=#ff0000]Stylus N10 N11 [/COLOR]you add your printer as [COLOR=#ff0000]L100[/COLOR] or [COLOR=#ff0000]L200[/COLOR]


Obs.: If you use Ubuntu 32 bits remember downloading i386 instead of amd64 packages

---

### Post by akuhon on 2014-01-20
Thanks... I update the front page

Cheers.

---

### Post by rudregues on 2014-05-03
I've downloaded 14.04 LiveDVD and for my surprise, when I tried to add  the printer, there was no L-100/L-200/L-800 drivers in the list yet. From L  family there was just L-1000 driver. I've reported a bug in launchpad [https://bugs.launchpad.net/ubuntu/+bug/1315096](https://bugs.launchpad.net/ubuntu/+bug/1315096) if someone want to help Canonical put some effort within these driver and support it by default, just login launchpad and mark "This bug affects you" option.

---

