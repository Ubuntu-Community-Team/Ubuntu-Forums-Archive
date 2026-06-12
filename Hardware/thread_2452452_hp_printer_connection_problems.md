---
title: "hp printer connection problems"
date: 2020-10-22
forum: Hardware
---

### Post by dome78 on 2020-10-22
Hi, I upgraded to ubuntu 20.04.
My printer hp envy photo 6230 no longer works well: I install it and it works, but sometimes after I turn it on it is not detected. 
In that case I have to disconnect and reconnect the cable and then it is recognized.
With ubuntu 18.04 this didn't happen to me. I have already uninstalled ippusbxd, 
which was preventing the printer from being recognized, but the connection problem keeps occurring (I have tried several usb ports of my PC).
Thanks!

---

### Post by Autodave on 2020-10-22
Problems like this can happen when upgrading.  I know that doesn't help you and I am sorry.  But, a looong time ago I learned NOT to do upgrades.  I backup everything and always do clean installs to prevent weird issues like this.

---

### Post by CelticWarrior on 2020-10-22
Although the above is anecdotally true, the problem you describe may not be related with the release upgrade.
As such, I suggest testing a live session before anything else.

---

### Post by dome78 on 2020-10-23
> **Autodave said:**
> Problems like this can happen when upgrading.  I  know that doesn't help you and I am sorry.  But, a looong time ago I  learned NOT to do upgrades.  I backup everything and always do clean  installs to prevent weird issues like this.

Hi, I did a clean install of ubuntu 20.04. I wrote "upgraded" because I had ubuntu 18.04 before

---

### Post by Autodave on 2020-10-23
Did you install hplip-gui?

---

### Post by dome78 on 2020-10-23
> **Autodave said:**
> Did you install hplip-gui?

Hi, i tried with the hplip version included in the distro and manually installing hplip (downloaded from hp site, with the gui): same problem

---

### Post by brian_p on 2020-10-23
> **dome78 said:**
> Hi, i tried with the hplip version included in the distro and manually installing hplip (downloaded from hp site, with the gui): same problem

I am always intrigued by someone with a **modern printer** using HPLIP. Is this habit? Printing has moved on to better things.

---

### Post by dome78 on 2020-10-23
> **brian_p said:**
> I am always intrigued by someone with a **modern printer** using HPLIP. Is this habit? Printing has moved on to better things.

There is an alternative?

---

### Post by brian_p on 2020-10-23
> **dome78 said:**
> There is an alternative?[https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting)

---

### Post by dome78 on 2020-10-24
> **brian_p said:**
> [https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting)

It works for the scanner too?

---

### Post by brian_p on 2020-10-24
> **dome78 said:**
> It works for the scanner too?

Yes, but a targeted response from me would be conditional on what your connection method is (I prefer to do wireless) and whether printing now works. Meanwhile, give the output of ```
scanimage -L
```

---

### Post by dome78 on 2020-10-24
> **brian_p said:**
> Yes, but a targeted response from me would be conditional on what your connection method is (I prefer to do wireless) and whether printing now works. Meanwhile, give the output of ```
scanimage -L
```

Maybe I found the solution: I reinstalled ubuntu, uninstalled hplip and kept ippusbxd. Now everything seems to work. Let's see if the random problems happen again.

---

### Post by dome78 on 2020-10-25
> **brian_p said:**
> Yes, but a targeted response from me would be conditional on what your connection method is (I prefer to do wireless) and whether printing now works. Meanwhile, give the output of ```
scanimage -L
```

The solution i found did not work. Can you explain me how to set up my system for "driveless printing"? I've seen a guide, but it seems complicated to me.

this is the result of scanimage:

device `hpaio:/usb/ENVY_Photo_6200_series?serial=************* is a Hewlett-Packard ENVY_Photo_6200_series all-in-one

---

### Post by brian_p on 2020-10-25
> The solution i found did not work. Can you explain me how to set up my system for "driveless printing"? I've seen a guide, but it seems complicated to me.


Any chance you can set the 6200 up with a wireless connection and give the output of ```
driverless
``` (I could do USB but it is a little more involved because Ubuntu 20.04 needs tweaking).

---

### Post by dome78 on 2020-10-25
> **brian_p said:**
> Any chance you can set the 6200 up with a wireless connection and give the output of ```
driverless
``` (I could do USB but it is a little more involved because Ubuntu 20.04 needs tweaking).

My PC is a desktop without wireless. I need that the printer works with usb

---

### Post by brian_p on 2020-10-25
> My PC is a desktop without wireless. I need that the printer works with usb

Ok, fair enough.

[list]Purge ippusbxd: ```
apt purge ippusbxd
```[/list]
[list]Switch the printer off and disconnect it from USB.[/list]
[list]Install ipp-usb from

[https://github.com/alexpevzner/sane-airscan](https://github.com/alexpevzner/sane-airscan)
[https://download.opensuse.org/repositories/home:/pzz/xUbuntu_20.04/amd64/](https://download.opensuse.org/repositories/home:/pzz/xUbuntu_20.04/amd64/)

It is much better than ippusbxd[/list]
[list]While you are there get sane-airscan and install it.[/list]
[list]Switch the printer on and connect it to USB.[/list]
[list]Get the output of ```
driverless
``` The output is a URI. **Substitute** the output in ```
lpadmin -p 6500 -v URI -E -m everywhere
```[/list]
[list]Test printing with ```
lp -d 6500 /etc/nsswitch.conf
```[/list]
[LIST]
[/LIST]
[list]Provide us with the outputs of ```
scanimage -L
``` ```
airscan-discover
```[/list]

---

### Post by dome78 on 2020-10-25
> **brian_p said:**
> Ok, fair enough.

[LIST]
[*]Purge ippusbxd: ```
apt purge ippusbxd
``` 
[/LIST]

[LIST]
[*]Switch the printer off and disconnect it from USB. 
[/LIST]

[LIST]
[*]Install ipp-usb from

[https://github.com/alexpevzner/sane-airscan](https://github.com/alexpevzner/sane-airscan)
[https://download.opensuse.org/repositories/home:/pzz/xUbuntu_20.04/amd64/](https://download.opensuse.org/repositories/home:/pzz/xUbuntu_20.04/amd64/)

It is much better than ippusbxd 
[/LIST]

[LIST]
[*]While you are there get sane-airscan and install it. 
[/LIST]

[LIST]
[*]Switch the printer on and connect it to USB. 
[/LIST]

[LIST]
[*]Get the output of ```
driverless
``` The output is a URI. **Substitute** the output in ```
lpadmin -p 6500 -v URI -E -m everywhere
``` 
[/LIST]

[LIST]
[*]Test printing with ```
lp -d 6500 /etc/nsswitch.conf
``` 
[/LIST]

[LIST]
[*]Provide us with the outputs of ```
scanimage -L
``` ```
airscan-discover
``` 
[/LIST]



URI is
ipp://HP%20ENVY%20Photo%206200%20series%20%5B97311A%5D%20(USB)._ipp._tcp.local/

lpadmin says sintax error because of the brackets

scanimage -L
device `escl:[http://127.0.0.1:60000](http://127.0.0.1:60000)' is a ESCL HP ENVY Photo 6200 series [97311A] (USB) flatbed scanner
device `airscan:e0:HP ENVY Photo 6200 series [97311A] (USB)' is a eSCL HP ENVY Photo 6200 series [97311A] (USB) eSCL network scanner
device `hpaio:/usb/ENVY_Photo_6200_series?serial=TH8BC9W12C' is a Hewlett-Packard ENVY_Photo_6200_series all-in-one


...but all seems working now. In simple scan three printers are detected (the first, hp envy_photo...) dont work, the other 2 (ESCL hp envy photo and eSCL hp envy photo) work.

---

### Post by brian_p on 2020-10-25
> **dome78 said:**
> URI is
ipp://HP%20ENVY%20Photo%206200%20series%20%5B97311A%5D%20(USB)._ipp._tcp.local/

lpadmin says sintax error because of the brackets

I forgot! Put the URI is double quotes. Like so; "URI". You should be ok then for printing. BTW, the -p option is the print queue name; you can have what you like for it.

> 
scanimage -L
device `escl:[http://127.0.0.1:60000](http://127.0.0.1:60000)' is a ESCL HP ENVY Photo 6200 series [97311A] (USB) flatbed scanner
device `airscan:e0:HP ENVY Photo 6200 series [97311A] (USB)' is a eSCL HP ENVY Photo 6200 series [97311A] (USB) eSCL network scanner
device `hpaio:/usb/ENVY_Photo_6200_series?serial=TH8BC9W12C' is a Hewlett-Packard ENVY_Photo_6200_series all-in-one


...but all seems working now. In simple scan three printers are detected (the first, hp envy_photo...) dont work, the other 2 (ESCL hp envy photo and eSCL hp envy photo) work.

Good. The hpaio device will not work because of the way IPP-over-USB operates. This is not a bug.

A favour please, dome78. For my records I would like ```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _uscan._tcp
```

---

### Post by dome78 on 2020-10-25
> **brian_p said:**
> I forgot! Put the URI is double quotes. Like so; "URI". You should be ok then for printing. BTW, the -p option is the print queue name; you can have what you like for it.



Good. The hpaio device will not work because of the way IPP-over-USB operates. This is not a bug.

A favour please, dome78. For my records I would like ```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _uscan._tcp
```

lpadmin installed another printer with the name 6500: it's normal?


Here the avahi-browse results.
avahi-browse -rt _ipp._tcp
+     lo IPv4 HP ENVY Photo 6200 series [97311A] (USB)      Internet Printer     local
=     lo IPv4 HP ENVY Photo 6200 series [97311A] (USB)      Internet Printer     local
   hostname = [nik-desktop.local]
   address = [127.0.0.1]
   port = [60000]
   txt = ["air=none" "mopria-certified=1.3" "rp=ipp/print" "priority=50" "kind=document,envelope,photo,postcard" "PaperMax=legal-A4" "URF=CP1,MT1-2-8-9-10-11,PQ3-4-5,RS300-600,SRGB24,OB9,OFU0,W8-16,DEVW8-16,DEVRGB24-48,ADOBERGB24-48,DM3,FN3,IS1-7,V1.4" "UUID=1baaecfa-cc12-57f6-0eee-b3f606ae3a06" "Color=T" "Duplex=T" "note=" "qtotal=1" "usb_MDL=ENVY Photo 6200 series" "usb_MFG=HP" "usb_CMD=PCL3GUI,PCL3,PJL,Automatic,JPEG,PCLM,AppleRaster,PWGRaster,DW-PCL,802.11,DESKJET,DYN" "ty=HP ENVY Photo 6200 series" "product=(HP ENVY Photo 6200 series)" "pdl=application/vnd.hp-PCL,image/jpeg,application/PCLm,image/urf,image/pwg-raster,application/octet-stream" "txtvers=1" "adminurl=http://localhost:60000/#hId-pgAirPrint" "Fax=F" "Scan=T"]



avahi-browse -rt _uscan._tcp
+     lo IPv4 HP ENVY Photo 6200 series [97311A] (USB)      _uscan._tcp          local
=     lo IPv4 HP ENVY Photo 6200 series [97311A] (USB)      _uscan._tcp          local
   hostname = [nik-desktop.local]
   address = [127.0.0.1]
   port = [60000]
   txt = ["duplex=F" "is=platen" "cs=binary,color,grayscale" "UUID=1baaecfa-cc12-57f6-0eee-b3f606ae3a06" "adminurl=http://localhost:60000" "representation=images/printer.png" "pdl=application/octet-stream,application/pdf,image/jpeg" "ty=ENVY Photo 6200 series" "rs=eSCL" "vers=2.62" "txtvers=1"]

---

### Post by brian_p on 2020-10-25
> lpadmin installed another printer with the name 6500: it's normal?


I meant to use 6200. You could remove both printers and install one with a name of your choice, like envy6200. To remove use ```
lpadmin -x PRINTER_NAME
```

---

### Post by ajgreeny on 2020-10-25
I have not had any problem using an HP printer for a very long time now.

I do still install hplip along with hplip-gui but I sometimes wonder why these days as I never need it any more for the head cleaning jobs etc for which I used it in the past, and my printer, in my case wireless connected, has been found by the system immediately after installing the OS and always worked out of the box.

Just out of interest what do you see if you go to [http://localhost:631/](http://localhost:631/) in your web-browser, and search for the printer with that, using CUPS?
Have you also considered trying another USB cable or a different USB port; maybe one or other is faulty?

---

### Post by dome78 on 2020-10-25
> **ajgreeny said:**
> I have not had any problem using an HP printer for a very long time now.

I do still install hplip along with hplip-gui but I sometimes wonder why these days as I never need it any more for the head cleaning jobs etc for which I used it in the past, and my printer, in my case wireless connected, has been found by the system immediately after installing the OS and always worked out of the box.

Just out of interest what do you see if you go to [http://localhost:631/](http://localhost:631/) in your web-browser, and search for the printer with that, using CUPS?
Have you also considered trying another USB cable or a different USB port; maybe one or other is faulty?

The problem is related to ubuntu 20.04. In ubuntu 18.04 the printer worked well.

[http://localhost:631/](http://localhost:631/) give me the cups screen

---

### Post by dome78 on 2020-10-25
> **brian_p said:**
> I meant to use 6200. You could remove both printers and install one with a name of your choice, like envy6200. To remove use ```
lpadmin -x PRINTER_NAME
```

Thanks!

---

### Post by ajgreeny on 2020-10-25
> **dome78 said:**
> The problem is related to ubuntu 20.04. In ubuntu 18.04 the printer worked well.

[http://localhost:631/](http://localhost:631/) give me the cups screen
Yes, I presumed it would, but can you find the HP printer using it?
That was my main reason for asking you.

---

### Post by dome78 on 2020-10-25
> **ajgreeny said:**
> Yes, I presumed it would, but can you find the HP printer using it?
That was my main reason for asking you.

No, but I uninstalled hplip.

---

### Post by ajgreeny on 2020-10-26
Removing hplip will make no difference to what cups can or can not do.

On the cups webmin page go to Printers in the tabs up top, if you haven't  already done so.

---

### Post by dome78 on 2020-10-26
> **ajgreeny said:**
> Removing hplip will make no difference to what cups can or can not do.

On the cups webmin page go to Printers in the tabs up top, if you haven't  already done so.

Cups screen says:

[TABLE="class: list"]
[TR]
[TD][hp_envy_6230]("http://localhost:631/printers/hp_envy_6230")[/TD]
[TD]HP ENVY Photo 6200 series [97311A][/TD]
[TD][/TD]
[TD]ENVY Photo 6200 series - IPP Everywhere[/TD]
[TD]Idle[/TD]
[/TR]
[/TABLE]

---

### Post by ajgreeny on 2020-10-26
OK, so cups did find the printer.

What happens if you try to print a test page from cups or carry out any other activity?

---

### Post by dome78 on 2020-10-27
> **ajgreeny said:**
> OK, so cups did find the printer.

What happens if you try to print a test page from cups or carry out any other activity?

...I have found that maybe was a usb cable problem. For now everything seems to be working fine

---

### Post by ajgreeny on 2020-10-27
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by dome78 on 2020-10-29
> **ajgreeny said:**
> Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

I want to wait a few days to make sure the cable was the problem.

---

### Post by dome78 on 2020-10-30
Solved!

---

