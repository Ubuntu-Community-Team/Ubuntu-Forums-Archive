---
title: "Espon XP-4100 can't print, Ubuntu 20.04"
date: 2020-11-14
forum: Hardware
---

### Post by usndmac on 2020-11-14
Epson xp-4100 printer.

things I've noted so far.

after boot, when first plugged into the usb port, the printer shows in the lsusb list

after some period of time it it no longer appear in the lsusb list

while it is in the list, the print subsystem recognizes it, but does set it up on usb, but as URI with localhost 

I've loaded the escpr drivers and confirmed the lsb version is newer than the minimum specified at the download site for escpr.

it also appears a a driverless printer.

In any case, it doesn't print. anything sent to the print cue just sits in the cue.

i'm out of things to check...looking for ideas.

(If I could I'd get rid of the epson...but, I don't own the system, I'm just trying to help them out.)

---

### Post by brian_p on 2020-11-14
> **usndmac said:**
> Epson xp-4100 printer.

it also appears a a driverless printer.


If this device was connected by wireless, it would be simplicity itself to set up printing. Should you did take this route, the outputs from ```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _uscan._tcp
``` ```
driverless
``` would be useful to have.

---

### Post by usndmac on 2020-11-15
> **brian_p said:**
> If this device was connected by wireless, it would be simplicity itself to set up printing. 

Connecting it wifi *would* be nice...but, they don't have wifi.  It is a single desktop connected to a cable modem. With the printer  plugged into USB on the desktop.


> 
```
avahi-browse -rt _ipp._tcp
```


returns nothing

> 
 ```
avahi-browse -rt _uscan._tcp
```


returns nothing

> 
```
driverless
```


returns nothing

---

### Post by brian_p on 2020-11-15
> **usndmac said:**
> Connecting it wifi *would* be nice...but, they don't have wifi.  It is a single desktop connected to a cable modem. With the printer  plugged into USB on the desktop.

Ok. Let's see if the device is capable of IPP-over-USB. Give what you get for

```
lsusb -v | grep -A 3 bInterfaceClass.*7
```

I had better warn you that I do not intend dealing with Epson drivers :).

---

### Post by usndmac on 2020-11-15
> **brian_p said:**
> Ok. Let's see if the device is capable of IPP-over-USB. Give what you get for

```
lsusb -v | grep -A 3 bInterfaceClass.*7
```

I had better warn you that I do not intend dealing with Epson drivers :).

I have no problem not dealing with epson drivers... In fact if it will work without them I'm all the more happy.

That said, lsusb doesn't show the epson device after some period of time after it is plugged in (I noted this in the OP).

So, the lsusb command you describe produces no output.

I'll get the user to unplug/plug and see if I can catch it when it's there (I'm about 100 miles away doing this via ssh... :( so, it might not be until later today.)  


Thanks for the help!

---

### Post by brian_p on 2020-11-15
> **usndmac said:**
> 

That said, lsusb doesn't show the epson device after some period of time after it is plugged in (I noted this in the OP).

The device should show straightaway in lsusb and journalctl. I don't have any definitive advice apart from changing USB ports and cable.

---

### Post by usndmac on 2020-11-15
Ok, so duh...the user had the PC on, but had powered off the printer. #-o

So here is all the previously requested info:

```
avahi-browse -rt _ipp._tcp
+     lo IPv4 XP-4100 Series [583642513235393524]           Internet Printer     local
=     lo IPv4 XP-4100 Series [583642513235393524]           Internet Printer     local
   hostname = [BnL.local]
   address = [127.0.0.1]
   port = [60000]
   txt = ["rfo=ipp/faxout" "Fax=T" "Duplex=T" "PaperMax=legal-A4" "URF=CP1,PQ4-5,OB9,OFU0,RS360,SRGB24,W8,DM3,IS1,V1.4,MT1-3-6-8-10-11-12" "pdl=application/octet-stream,image/pwg-raster,image/urf,image/jpeg,application/vnd.epson.escpr" "product=(EPSON XP-4100 Series)" "ty=EPSON XP-4100 Series" "note=" "Color=T" "kind=document,envelope,photo" "mopria-certified=mopria-certified 1.3" "UUID=cfe92100-67c4-11d4-a45f-381a522c42a4" "adminurl=http://127.0.0.1:60000/PRESENTATION/BONJOUR" "qtotal=1" "txtvers=1" "priority=60" "usb_MDL=XP-4100 Series" "usb_MFG=EPSON" "rp=ipp/print"]



avahi-browse -rt _uscan._tcp
+     lo IPv4 XP-4100 Series [583642513235393524]           _uscan._tcp          local
=     lo IPv4 XP-4100 Series [583642513235393524]           _uscan._tcp          local
   hostname = [BnL.local]
   address = [127.0.0.1]
   port = [60000]
   txt = ["txtvers=1" "vers=2.63" "rs=eSCL" "ty=EPSON XP-4100 Series" "pdl=application/pdf,image/jpeg" "cs=binary,grayscale,color" "duplex=F" "adminurl=http://127.0.0.1:60000/PRESENTATION/BONJOUR" "UUID=cfe92100-67c4-11d4-a45f-381a522c42a4" "note=" "representation=http://127.0.0.1:60000/icon.png"]

driverless
ipp://XP-4100%20Series%20%5B583642513235393524%5D._ipp._tcp.local/


lsusb -v | grep -A 3 bInterfaceClass.*7
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              6 
--
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      4 
      iInterface              0 
--
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      4 
      iInterface              0 
--
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      4 
      iInterface              0 
Couldn't open device, some information will be missing
--
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      4 
      iInterface              0 
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing


lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04b8:1137 Seiko Epson Corp. XP-4100 Series
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

---

### Post by brian_p on 2020-11-15
> **usndmac said:**
> Ok, so duh...the user had the PC on, but had powered off the printer. #-o

It went through my mind to edit my post and suggest that be checked. But then I thought - surely a user would not neglect such an elementary step! Glad it's sorted. The information is very useful. The presence of the **bInterfaceProtocol      4** lines in the output of ```
lsusb -v | grep -A 3 bInterfaceClass.*7
``` clearly shows that IPP-over-USB is supported. This is confirmed from the other two commands by **port = [60000]**.

We have lift-off and should get into orbit. However, we are carrying some outdated and failure-prone equipment, so whether we will stay there is problematic. Later, (if you wish), I will help to conduct running repairs. Meanwhile, we will continue on our journey with fingers crossed.

> 
driverless
ipp://XP-4100%20Series%20%5B583642513235393524%5D._ipp._tcp.local/

Set up this print queue:

```
lpadmin -p xp4100 -v "ipp://XP-4100%20Series%20%5B583642513235393524%5D._ipp._tcp.local/" -E -m everywhere
```

Test printing with ```
lp -d xp4100 /etc/nsswitch.conf
```

---

### Post by usndmac on 2020-11-15
Ok, so that seems to work. :D

- so what's the deal with ipp? (I get that the lpadmin command created a printer)

- is it possible to delete the other printer that are there so the user isn't confused (from my ssh login)

```
lpc status
xp4100:
    printer is on device 'ipp' speed -1
    queuing is enabled
    printing is enabled
    no entries
    daemon present
XP_4100_Series_583642513235393524_:
    printer is on device 'implicitclass' speed -1
    queuing is enabled
    printing is enabled
    no entries
    daemon present

```

- is it possible to set the default printer for apps (from my ssh login)

- tel me more about: "...outdated and failure-prone equipment, so whether we will stay there is  problematic...conduct running  repairs"

---

### Post by brian_p on 2020-11-15
> **usndmac said:**
> Ok, so that seems to work. :D

Excellent. The device has now essentially become a network device. Do you want to do scanning?

> 
- so what's the deal with ipp? (I get that the lpadmin command created a printer)

I am not too sure what you are after here, but see [https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting).
> 
- is it possible to delete the other printer that are there so the user isn't confused (from my ssh login)

See the -x option at ```
man lpadmin
```

> 
- is it possible to set the default printer for apps (from my ssh login)

See the -d option at ```
man lpoptions
```
> 
- tel me more about: "...outdated and failure-prone equipment, so whether we will stay there is  problematic...conduct running  repairs"

The OS is running ippusbxd, ```
systemctl status ippusbxd
```

which is acknowleged as being sub-optimal. The strong advice is to replace it with ipp-usb.

[https://github.com/alexpevzner/sane-airscan](https://github.com/alexpevzner/sane-airscan)
[https://download.opensuse.org/repositories/home:/pzz/xUbuntu_20.04/amd64/](https://download.opensuse.org/repositories/home:/pzz/xUbuntu_20.04/amd64/)

---

### Post by usndmac on 2020-11-16
Ok, I knew about the lpadmin commands. Just wan't sure ihow they effected what the user will see in the normal desktop ui.

So:

```
systemctl status ippusbxd
Unit ippusbxd.service could not be found.

```

So if I install the deb for ipp usb does it autonmagically replace the bxd?
Anything I should do first?

General questions:

If I do a normal apt update/upgrade is that likely to break what I've done?
Should I remove the escpr stuff?

There is also a firmware update waiting for the Logictech mouse. What are my chances of breaking anything?
(I realize it's probably a crap shoot, so just curious as to your thoughts...)

---

### Post by brian_p on 2020-11-16
> **usndmac said:**
> 

```
systemctl status ippusbxd
Unit ippusbxd.service could not be found.

```

Very strange. Ubuntu 20.04 installs and runs this service.
> 
So if I install the deb for ipp usb does it autonmagically replace the bxd?
Anything I should do first?

It's probably best to remove ippusbxd first: ```
apt purge ippusbxd
```

> 
General questions:

If I do a normal apt update/upgrade is that likely to break what I've done?

No.

> 
Should I remove the escpr stuff?

I would; it isn't required for printing. It isn't even needed for scanning, should that be a requirement.

> 
There is also a firmware update waiting for the Logictech mouse. What are my chances of breaking anything?
(I realize it's probably a crap shoot, so just curious as to your thoughts...)

Such a firmware update is of zero consquence for printing.

---

