---
title: "Umax Astra Slim"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by subs on 2007-11-28
I have a umax astraslim scanner.... exact specs ...

> 
Vendor:  05d8 Ultima Electronics Corp.
Device: 4009 Umax Astraslim 


sane supports this particulat scanner model....

however whenever i try to scan nything thru sane.... i get an error saying....

> 
Failed to open device 'artec_eplus48u:libusb:002:002': Invalid argument


i would really appreciate any help u may be able to provide

---

### Post by subs on 2007-11-30
bump!!!:(

---

### Post by subs on 2007-12-06
bump!!!!!!

---

### Post by subs on 2007-12-10
bump!!:(

---

### Post by Marizu on 2007-12-27
I've just managed to get this scanner working.

Firstly, you need to get a copy of the scanner's firmware.
It will be in the Windows install (assuming you have it). The filename is Artec48u.usb
I googled on the filename, downloaded the Windows driver and extracted it on a Windows box to get the file.

Copy the Artec48.usb file to /usr/share/sane/artec_eplus48u/.
I made the file Artec48.usb readable by everyone, using chmod a+r Artec48.usb.
You should ensure that your user is in the scanner group (Administration->Users and Groups)

In the file /etc/sane.d/artec_eplus48u.conf you should find the following section:

[INDENT]# Since the UMAX AstraSlim SE uses a different product id, we add
# another usb section here.
usb 0x05d8 0x4009
option artecFirmwareFile /usr/share/sane/artec_eplus48u/Artec48.usb
option vendorString "UMAX"
option modelString "AstraSlim SE"
option ePlusPro         0[/INDENT]

(I needed to add the line, option ePlusPro 0, or my scans had weird color banding problems).

That got mine working!
Marizu

---

### Post by nebu on 2007-12-27
i dont have a directory /etc/sane.d or /usr/share/sane/artec_eplus48u


do i have to install some other libraries etc...

---

