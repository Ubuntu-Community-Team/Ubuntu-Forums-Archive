---
title: "Multi function laser printer recomendations?"
date: 2020-05-16
forum: Hardware
---

### Post by jamiebourque1975 on 2020-05-16
Hello all,

  I am running 18.04LTS.  I need to buy a multi-function laser printer (scan, copy, print) because my wife will be working from home.  I have had very bad luck with printers  since starting with Ubuntu more then twelve years ago.  I have had a Samsung Laser printer that became useless after an OS upgrade and a Brother printer that never worked properly.  I did have an HP inkjet that worked as soon as I plugged it in but that was circa 2005...  Can anyone recommend a laser printer (scanner, copier) that is easily available new today, Best Buy, Staples, Costco, that will work, with 18.04LTS, out of the box in the $150-$300 range?  It has to be able to print and scan reliably from the GUI for my wife to work.  Thanks for your help.

---

### Post by mIk3_08 on 2020-05-17
My Brother printer/scanner works properly in 18.04.4 LTS I haven't encounter any problem since I configured it successfully. All this works via wifi network communication. The scanner works in simple scan and Xsane with free from hassle (Wifi comm). Actually almost all even if the other was not that friendly will works on Linux. It has to be configured/installed successfully.

---

### Post by Autodave on 2020-05-17
HP.  Install hplip and all is well.

---

### Post by jamiebourque1975 on 2020-05-17
[h=1][SIZE=2]**HP LaserJet Pro M130fn**
[/SIZE][/h][SIZE=2]HP LaserJet Pro M130fw

These are the two printers I have been seriously considering.  I think they are the same printer except the M130FW is WIFI capable and has a touch screen.  I have read that if I were to have issues via the USB connection,  the WIFI connection is more flexible.  Is it worth the extra few dollars?  I see that both are supported on HPLIP.  Any extra input would be greatly appreciated, I need to get this done soon.

Thanks
[/SIZE]

---

### Post by oldfred on 2020-05-17
My HP color printer died, so just  got new Brother laser printer as did not need color.
Only used for a couple of weeks, not a lot of use, but very happy so far.

fred@Z170N-focal:~$ lsusb
Bus 001 Device 004: ID 04f9:0428 Brother Industries, Ltd HL-L2390DW

I already configured WiFi, and both scanning & USB printing work, but not sure if scan is USB or WiFi as this user with Network version of printer seemed to have issue.

WiFi Brother Print
[https://help.brother-usa.com/app/answers/detail/a_id/166020/~/connect-to-a-wireless-network---linux](https://help.brother-usa.com/app/answers/detail/a_id/166020/~/connect-to-a-wireless-network---linux)
scan issues 2395
[https://ubuntuforums.org/showthread.php?t=2443188](https://ubuntuforums.org/showthread.php?t=2443188)

Was actually cheaper at Staples than on Amazon. And  a Staples was just down the street.

---

### Post by jamiebourque1975 on 2020-05-17
> **oldfred said:**
> My HP color printer died, so just  got new Brother laser printer as did not need color.
Only used for a couple of weeks, not a lot of use, but very happy so far.

fred@Z170N-focal:~$ lsusb
Bus 001 Device 004: ID 04f9:0428 Brother Industries, Ltd HL-L2390DW

I already configured WiFi, and both scanning & USB printing work, but not sure if scan is USB or WiFi as this user with Network version of printer seemed to have issue.

WiFi Brother Print
[https://help.brother-usa.com/app/answers/detail/a_id/166020/~/connect-to-a-wireless-network---linux](https://help.brother-usa.com/app/answers/detail/a_id/166020/~/connect-to-a-wireless-network---linux)
scan issues 2395
[https://ubuntuforums.org/showthread.php?t=2443188](https://ubuntuforums.org/showthread.php?t=2443188)

Was actually cheaper at Staples than on Amazon. And  a Staples was just down the street.

Thanks for the advice.  My brother DCP-1512, which is next to me right now, never worked right and I spent so much time and effort on it. I can't see myself investing in another Brother printer for a while.  I know the HP printers are generally more expensive both in initial investment and toner but I need it to work (this is for my wife, working from home.  if it were for me cheap and a bit of command line magic are not an issue.)

Thanks

---

### Post by oldfred on 2020-05-17
Some have issues with HP also. I never did with two different color inkjet HP printers.But with 20.04 had some minor issues as multiple printers kept getting added automatically.
But they changed from hplip by default.

18.04 Bionic Beaver
Driverless printing support is now available. 
PostScript Printer Description (PPD) files are created by vendors to describe the entire set of features and capabilities available for their PostScript printers.
[https://askubuntu.com/questions/1030926/ubuntu-18-04-doesnt-see-the-hp-scanner](https://askubuntu.com/questions/1030926/ubuntu-18-04-doesnt-see-the-hp-scanner)

Scanner HP Deskjet no longer works with Ubuntu 18.04 
[https://ubuntuforums.org/showthread.php?t=2411629&page=3](https://ubuntuforums.org/showthread.php?t=2411629&page=3)
[https://wiki.debian.org/QuickPrintQueuesCUPS](https://wiki.debian.org/QuickPrintQueuesCUPS)

Printers now use ipp.
[https://www.pwg.org/ipp/everywhere.html](https://www.pwg.org/ipp/everywhere.html)
I believe it is now the same as all other systems, Windows & Mac use, so all printers should work.
But not same with scanners as drivers still seem to be needed.

---

### Post by brian_p on 2020-05-17
> **jamiebourque1975 said:**
> [h=1][SIZE=2]**HP LaserJet Pro M130fn**
[/SIZE][/h][SIZE=2]HP LaserJet Pro M130fw

These are the two printers I have been seriously considering.  I think they are the same printer except the M130FW is WIFI capable and has a touch screen.  I have read that if I were to have issues via the USB connection,  the WIFI connection is more flexible.  Is it worth the extra few dollars?  I see that both are supported on HPLIP.  Any extra input would be greatly appreciated, I need to get this done soon.

Thanks
[/SIZE]

For the reason of flexibility you mention, a network connection is far preferable. HPLIP is not required for printing on 18.04. And neither are Brother, Samsung, Canon etc proprietary drivers needed. After two years, driverless printing (this is the future) appears to have passed many Ubuntu users by and they still reach for vendor drivers as a comfort blanket.

[https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting)

---

### Post by brian_p on 2020-05-17
> **oldfred said:**
> 

Printers now use ipp.
[https://www.pwg.org/ipp/everywhere.html](https://www.pwg.org/ipp/everywhere.html)
I believe it is now the same as all other systems, Windows & Mac use, so all printers should work.
But not same with scanners as drivers still seem to be needed.

**All** modern printers aimed at the desktop user use IPP and are AirPrint devices. That means they fit the driverless printing system provided by Ubuntu. They will immediately work with a default Ubuntu installation when connected to a network (wireless or ethernet).

Ubuntu 20.04 introduces driverless scanning. Forget about installing any vendor drivers (HP, Brother, Canon etc).

---

### Post by kurt18947 on 2020-05-17
> **brian_p said:**
> **All** modern printers aimed at the desktop user use IPP and are AirPrint devices. That means they fit the driverless printing system provided by Ubuntu. They will immediately work with a default Ubuntu installation when connected to a network (wireless or ethernet).

Ubuntu 20.04 introduces driverless scanning. Forget about installing any vendor drivers (HP, Brother, Canon etc).

Perhaps. I have a Samsung printer connected via ethernet over MoCA. I just started gscan2pdf and checked for scanners. It found only the Brother which has Brother drivers installed. I also have a Samsung laser Multi-function. The printing does appear to work correctly in 20.04, it didn't on 18.04.4. 18.04.4 would printer a one or a few lines of gibberish per page and would keep going until it ran out of paper. The Samsung Linux driver downloaded from HP's support site (HP bought the Samsung printer business) worked properly. I think the newer Brother printers work well with the driverless printer model, not sure about the scan functions. My most used Brother is a 10+ year old inkjet. We also have a Brother HL-3170 color laser which has been very reliable. Based on what i read here and elsewhere, HP and Brother seem to provide the easiest and best Linux experience.

---

### Post by brian_p on 2020-05-17
> **kurt18947 said:**
> Perhaps. I have a Samsung printer connected via ethernet over MoCA. I just started gscan2pdf and checked for scanners. It found only the Brother which has Brother drivers installed. I also have a Samsung laser Multi-function. The printing does appear to work correctly in 20.04, it didn't on 18.04.4. 18.04.4 would printer a one or a few lines of gibberish per page and would keep going until it ran out of paper. The Samsung Linux driver downloaded from HP's support site (HP bought the Samsung printer business) worked properly. I think the newer Brother printers work well with the driverless printer model, not sure about the scan functions. My most used Brother is a 10+ year old inkjet. We also have a Brother HL-3170 color laser which has been very reliable. Based on what i read here and elsewhere, HP and Brother seem to provide the easiest and best Linux experience.

Considering that you do not give the models of Samsung devices you have, it is difficult to work out what impotance or significance to attach to *perhaps*.

---

### Post by jamiebourque1975 on 2020-05-17
Well, I decided to pull the trigger on the HP LaserJet Pro M130fn as it is available for quick delivery.  Everything here is still locked down for the most part.  I will update this thread with my results.  Thanks for all the information.

---

### Post by kurt18947 on 2020-05-17
> **brian_p said:**
> Considering that you do not give the models of Samsung devices you have, it is difficult to work out what impotance or significance to attach to *perhaps*.

Xpress M2870FW. I don't know what HP's plans are for Samsung branded printers but I imagine the Samsung name will disappear on desktop/SOHO devices. I read that HP bought Samsung's printer division for their IP and expertise in the enterprise document space.

---

### Post by brian_p on 2020-05-17
The Xpress M2870FW has an AirPrint facility. Howver, this is not the only criterion for driverless scanning to work on Ubuntu 20.04. We would need the outputs of ```
avahi-browse -rt _ipp._tcp
``` and ```
avahi-browse -rt _uscan._tcp
``` when the device is on the network to ascertain that,

---

### Post by kurt18947 on 2020-05-18
Hi Brian
Ask and ye shall receive :)

```
$ avahi-browse -rt _ipp._tcp
+ enp31s0 IPv4 Samsung M267x 287x Series (SEC001599E531A7)   Internet Printer     local
= enp31s0 IPv4 Samsung M267x 287x Series (SEC001599E531A7)   Internet Printer     local
   hostname = [SEC001599E531A7.local]
   address = [xxx.xxx.xxx.xxx]
   port = [631]
   txt = ["Staple=F" "Sort=F" "Fax=T" "Scan=T" "Punch=0" "PaperCustom=T" "Duplex=T" "Copies=T" "Color=F" "Collate=F" "Bind=F" "URF=W8,RS600,IS1,CP1,IFU0,PQ4,OB10,DM1,V1.2" "UUID=16a65700-007c-1000-bb49-001599e531a7" "MDL=M267x 287x Series" "MFG=Samsung" "usb_CMD=MFG:Samsung;CMD:PCL6,URF,FAX,FWV,PIC,DCU,EXT;MDL:M267x 287x Series;CLS:PRINTER;CID:SA_PCL6_BW;MODE:FAX3,SCN,SPL3,R000105;" "usb_MDL=M267x 287x Series" "usb_MFG=Samsung" "adminurl=http://SEC001599E531A7.local./sws/index.html?link=/sws/app/settings/network/AirPrint/AirPrint.html" "pdl=application/octet-stream,application/PCL,application/vnd.hp-PCL,application/vnd.hp-PCLXL,application/x-QPDL,text/plain,image/urf" "product=(Samsung M267x 287x Series)" "ty=Samsung M267x 287x Series" "priority=51" "qtotal=1" "note=" "rp=ipp/print" "txtvers=1"]
```

No response to the second command
```
$ avahi-browse -rt _uscan._tcp


```
And thank you.

I used the print function today on several pages and it performed as expected. I'm not put out by the scan function not working as this device is a flight of stairs plus from my work area.

---

### Post by brian_p on 2020-05-19
Hello Kurt,

> URF=W8,RS600,IS1,CP1,IFU0,PQ4,OB10,DM1,V1.2

The *URF=* key tells us that the Xpress M2870FW has an AirPrint facility (version 1.2).

> No response to the second command

There isn't a _uscan._tcp service offered. The device cannot do driverless scanning. A user wanting to scan would possibly have to use the driver Samsung offers.

---

### Post by jamiebourque1975 on 2020-05-26
Long story short; the tech from my wife's company put all of two minutes into setting her up remotely on Linux.  Told me to put Windows on it.  I kept cool and kept my opinions to myself.  Got her an Acer pre-fab machine from Staples that was on sale.  Set her up and all is good.  The printer, not what I would have chosen if I had known I was going to use Windows, works flawlessly, in Windows.  On my Ubuntu 18.04 not so much.  Via USB it detects it perfectly.  Printing starts and stops immediately.  The scanner goes undetected.  I don't have time to play around with it, so I'm almost glad I have a Windows machine to fall back on.  I plan to put 20.04 on my machine soon, maybe it will work then.  Thanks for the help anyway.

---

### Post by Autodave on 2020-05-26
Did you install *hplip?  *I have yet to see an HP that wouldn't work via USB cable.

---

### Post by jamiebourque1975 on 2020-05-26
Just threw on 20.04, the printer works perfectly!  The scanner however does not.  Document scanner detects it but fails.  I'm happy it prints.  Eventually I will put it on the network and see how that goes.

---

### Post by jamiebourque1975 on 2020-05-26
I guess I am really bored tonight.  Installed HPLIP, had to install a driver for the scanner.  Everything works fine now.  Thanks for all the help.

---

### Post by maccamenzies on 2020-05-26
Using Brother Laser Printers - black and white scanner printer and another Brother Color Scanner printer. All recognised straight away in latest Ubuntu

---

### Post by kurt18947 on 2020-05-27
> **jamiebourque1975 said:**
> Long story short; the tech from my wife's company put all of two minutes into setting her up remotely on Linux.  Told me to put Windows on it. 
 
In a situation like that you don't really have a lot of choice. The tech probably didn't have a script for Linux, he/she DID have a script for Windows. It's possible that techs are tired or overwhelmed with setting people up to work remotely. They don't want to deal with 'outliers'. Stinks but I could understand it.

---

