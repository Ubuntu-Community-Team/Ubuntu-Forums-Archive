---
title: "Epson ET-3850 EcoTanker"
date: 2022-04-03
forum: Hardware
---

### Post by richramik on 2022-04-03
Just re-installed 18.04 because of the problems I was having with 20.04.  At any rate I have the Epson ET-3850 EcoTanker.  

I was provided the following terminal command line:  **lsusb -v | grep -A 3 bInterfaceClass.*7**

I ran it and got the following results.

rich@rich-500-164:~$ lsusb -v | grep -A 3 bInterfaceClass.*7
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
Couldn't open device, some information will be missing
      iInterface              6 
--
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              9 
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




HELP!!!!!  Don't know what to do.

Thanks,
Rich Ramik

---

### Post by brian_p on 2022-04-04
> **richramik said:**
> Just re-installed 18.04 because of the problems I was having with 20.04.  At any rate I have the Epson ET-3850 EcoTanker.  

--
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      4 
      iInterface              0 

HELP!!!!!  Don't know what to do.


This tells us the device understands the IPP-over-USB protocol.

Go to [https://download.opensuse.org/repositories/home:/pzz/xUbuntu_18.04/amd64/](https://download.opensuse.org/repositories/home:/pzz/xUbuntu_18.04/amd64/). Down;oad and install **ipp-usb** and **sane-airscan**. Disconnect from USB. Reconnect. Give the outputs of ```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _uscan._tcp

``` ```
scanimage -L
``` ```
airscan-discover
```

(I assumed you wanted a USB connection).

---

### Post by mIk3_08 on 2022-04-04
> **richramik said:**
> Just re-installed 18.04 because of the problems I was having with 20.04.  At any rate I have the Epson ET-3850 EcoTanker.  

I was provided the following terminal command line:  **lsusb -v | grep -A 3 bInterfaceClass.*7**

I ran it and got the following results.

rich@rich-500-164:~$ lsusb -v | grep -A 3 bInterfaceClass.*7
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
Couldn't open device, some information will be missing
      iInterface              6 
--
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              9 
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




HELP!!!!!  Don't know what to do.

Thanks,
Rich Ramik
Have you successfully installed the printer drivers coming from Epson website?  You should have too. This will hep you a lot. Good Luck and Regards.

---

### Post by richramik on 2022-04-04
Following are the results of the terminal command line inputs.  Note that I ran it twice in the event I screwed up.

Well some days I wake up and forget who I am!!!!!!   The printer is actually an EPSON ET-4850.


<pre><font color="#8AE234"><b>rich@rich-500-164</b></font>:<font color="#729FCF"><b>~/Downloads</b></font>$ avahi-browse -rt _ipp._tcp
<font color="#8AE234"><b>rich@rich-500-164</b></font>:<font color="#729FCF"><b>~/Downloads</b></font>$ avahi-browse -rt _uscan._tcp
<font color="#8AE234"><b>rich@rich-500-164</b></font>:<font color="#729FCF"><b>~/Downloads</b></font>$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
<font color="#8AE234"><b>rich@rich-500-164</b></font>:<font color="#729FCF"><b>~/Downloads</b></font>$ airscan-discover
[devices]
<font color="#8AE234"><b>rich@rich-500-164</b></font>:<font color="#729FCF"><b>~/Downloads</b></font>$ 
<font color="#8AE234"><b>rich@rich-500-164</b></font>:<font color="#729FCF"><b>~/Downloads</b></font>$ 
<font color="#8AE234"><b>rich@rich-500-164</b></font>:<font color="#729FCF"><b>~/Downloads</b></font>$ 
<font color="#8AE234"><b>rich@rich-500-164</b></font>:<font color="#729FCF"><b>~/Downloads</b></font>$ avahi-browse -rt _ipp._tcp
<font color="#8AE234"><b>rich@rich-500-164</b></font>:<font color="#729FCF"><b>~/Downloads</b></font>$ avahi-browse -rt _uscan._tcp
<font color="#8AE234"><b>rich@rich-500-164</b></font>:<font color="#729FCF"><b>~/Downloads</b></font>$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
<font color="#8AE234"><b>rich@rich-500-164</b></font>:<font color="#729FCF"><b>~/Downloads</b></font>$ airscan-discover
[devices]
<font color="#8AE234"><b>rich@rich-500-164</b></font>:<font color="#729FCF"><b>~/Downloads</b></font>$ </pre>


Thanks,
Rich Ramik

---

### Post by richramik on 2022-04-04
I went out to the Epson website and didn't find anything related to Linux or Ubuntu.  Where may I ask did you find the drivers????

Some days I wake up and forget who I am!!!!!!   The printer is actually an EPSON ET-4850.

Thanks, 
Rich Ramik

---

### Post by him610 on 2022-04-04
After entering your model in search box, look for epson drivers for et-4850 at bottom of page that opens, [http://download.ebz.epson.net/dsc/search/01/search/searchModule]("http://download.ebz.epson.net/dsc/search/01/search/searchModule")

---

### Post by richramik on 2022-04-05
Today I know who I am.  My name is in my under ware: CHAMPION.  lololol  Have to giggle at least once to start the day.

At any rate, should I re-run the following commands after visiting the **download.ebz.epson.net......** website????  The assumption is that I would use the **All-in-one** package?????

avahi-browse -rt _ipp._tcp
avahi-browse -rt _uscan._tcp
scanimage -L
airscan-discover

Thanks,
Rich Ramik

---

### Post by brian_p on 2022-04-05
> **richramik said:**
> Today I know who I am.  My name is in my under ware: CHAMPION.  lololol  Have to giggle at least once to start the day.

At any rate, should I re-run the following commands after visiting the **download.ebz.epson.net......** website????  The assumption is that I would use the **All-in-one** package?????

avahi-browse -rt _ipp._tcp
avahi-browse -rt _uscan._tcp
scanimage -L
airscan-discover

Thanks,
Rich Ramik

Rich, you only gave the output of scanimage -L last time and that wasn't very useful. There are **four** commands and **ipp-usb and sane-airscan have to be installed**. My advice above has nothing to do with Epson drivers.

---

### Post by richramik on 2022-04-05
Brian:

Understand.  Not sure how I missed them.  Will take care of this when I get home this evening.

Thanks,
Rich Ramik

---

### Post by richramik on 2022-04-05
I re-ran the commands, all four this time.  Following are the entries and results.  Both have been highlighted as BOLD.

rich@rich-500-164:~$ **avahi-browse -rt _ipp._tcp**
rich@rich-500-164:~$ 

rich@rich-500-164:~$ **avahi-browse -rt _uscan._tcp**
rich@rich-500-164:~$ 

rich@rich-500-164:~$ [B]scanimage -L
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).[/B]
rich@rich-500-164:~$ 

rich@rich-500-164:~$ [B]airscan-discover
[devices][/B]

rich@rich-500-164:~$ 

Thanks,
Rich Ramik

---

### Post by brian_p on 2022-04-06
> **richramik said:**
> I re-ran the commands, all four this time.  Following are the entries and results.  Both have been highlighted as BOLD.

rich@rich-500-164:~$ **avahi-browse -rt _ipp._tcp**
rich@rich-500-164:~$ 

rich@rich-500-164:~$ **avahi-browse -rt _uscan._tcp**
rich@rich-500-164:~$ 

rich@rich-500-164:~$ [B]scanimage -L
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).[/B]
rich@rich-500-164:~$ 

rich@rich-500-164:~$ [B]airscan-discover
[devices][/B]

rich@rich-500-164:~$ 

Thanks,
Rich Ramik

Thanks for the info. Now give

```
dpkg -l ipp-usb
```
```
systemctl status ipp-usb
```

after disconnecting from USB and reconnecting.

---

### Post by richramik on 2022-04-06
Well now, I have a completely revised output.  Rather than just disconnecting the printer, I disconnected the printer and restarted my system.  

I then went to settings and found and "ET" that was labeled as a dot matrix printer.  I deleted that one and then ran the four commands.  Following is the output.

rich@rich-500-164:~$ **avahi-browse -rt _ipp._tcp**
+     lo IPv4 EPSON ET-4850 Series (USB)            Internet Printer     local
=     lo IPv4 EPSON ET-4850 Series (USB)            Internet Printer     local
   hostname = [localhost]
   address = [127.0.0.1]
   port = [60000]
   txt = ["air=none" "mopria-certified=2.0" "rp=ipp/print" "priority=50" "kind=document,envelope,photo" "PaperMax=isoC-A2" "URF=CP1,PQ4-5,OB9,OFU0,RS300,SRGB24,W8,DM3,IS1,V1.4,MT1-3-6-8-10-11-12" "UUID=cfe92100-67c4-11d4-a45f-dccd2f38bb0a" "Color=T" "Duplex=T" "note=" "qtotal=1" "usb_MDL=ET-4850 Series" "usb_MFG=EPSON" "usb_CMD=ESCPL2,BDC,D4,D4PX,ESCPR7,END4,GENEP,PWGRaster,URF" "ty=EPSON ET-4850 Series" "product=(EPSON ET-4850 Series)" "pdl=application/octet-stream,image/pwg-raster,image/urf,image/jpeg,application/vnd.epson.escpr" "txtvers=1" "adminurl=http://localhost:60000/PRESENTATION/BONJOUR" "Fax=T" "rfo=ipp/faxout" "Scan=T"]
rich@rich-500-164:~$ **avahi-browse -rt _uscan._tcp**
+     lo IPv4 EPSON ET-4850 Series (USB)                _uscan._tcp          local
=     lo IPv4 EPSON ET-4850 Series (USB)                _uscan._tcp          local
   hostname = [localhost]
   address = [127.0.0.1]
   port = [60000]
   txt = ["duplex=F" "is=platen,adf" "cs=binary,color,grayscale" "UUID=cfe92100-67c4-11d4-a45f-dccd2f38bb0a" "adminurl=http://localhost:60000/PRESENTATION/BONJOUR" "representation=http://localhost:60000/icon.png" "pdl=application/pdf,image/jpeg" "ty=ET-4850 Series" "rs=eSCL" "vers=2.63" "txtvers=1"]
rich@rich-500-164:~$ **scanimage -L**
device `airscan:e0:EPSON ET-4850 Series (USB)' is a eSCL EPSON ET-4850 Series (USB) ip=127.0.0.1
rich@rich-500-164:~$ **airscan-discover**
[devices]
  EPSON ET-4850 Series (USB) = [http://127.0.0.1:60000/eSCL/](http://127.0.0.1:60000/eSCL/), eSCL
rich@rich-500-164:~$ 


Thanks,
Rich Ramik

---

### Post by brian_p on 2022-04-06
Your output for the commands is now exactly what we expect from a USB connected modern printer.

Printing shouls be automatically set up. If it is not, do ```
lpadmin -p PRINTER_NAME -v ipp://localhost:60000/ipp/print -E -m everywhere
``` and test with ```
lp -d PRINTER_NAME /etc/nsswitch.conf
```

PRINTER_NAME can be anything you want, such as et4850.

Does ```
simple-scan "airscan:e0:EPSON ET-4850 Series (USB)"
``` give you scanning?

---

### Post by richramik on 2022-04-06
I was just checking email and other information sources.  I will check this over the next several days to possibly the weekend.

Had a tragedy today.  Our beloved pet Roxie (Australian Shepard dog) crossed over the Rainbow Bridge.

I came upstairs to the area where I have my computer.  Wanted to do something to get my mind off of today's happening.  The saving grace is that it happened quick and she didn't suffer.

Any way, thanks for the information.  Like I said, I will look into it over the next several days.

Thanks,
Rich Ramik

---

### Post by richramik on 2022-04-07
I have used the commands provided in #13.

Well I have found that the printer works.  I printed several documents: simplex and duplex.

I am using Simple Scan and seems to work just fine.  Is there a duplex option/feature?

Am I missing anything else????

Thanks,
Rich Ramik

---

### Post by brian_p on 2022-04-08
> **richramik said:**
> I have used the commands provided in #13.

Well I have found that the printer works.  I printed several documents: simplex and duplex.

Good!
> 
I am using Simple Scan and seems to work just fine.  Is there a duplex option/feature?

Even better!

The document scanner is the same as simple-scan . Look in its interface or that of xsane (installed?) for 
duplex options.

---

### Post by richramik on 2022-04-08
The week is finally over.  YEAH!!!!!!!!!  Now I can do what us old guys do and that is hang out at the local hobby shop and buy more trains.  LOLOLOLOL  On to business.

I really checked the options (meaning I did some in depth reading) for the ET-4850.  It does not have duplex scan capabilities.  This is not a game changer.  For my needs, I have a work around.

At this point I have to say that I am please with the ET-4850,  now that I have read.  It works as advertised.

I couldn't have reached this point without your assistance.

Thank you very much for everything.

Sincerely,
Rich Ramik

---

### Post by brian_p on 2022-04-08
> **richramik said:**
> The week is finally over.  YEAH!!!!!!!!!  Now I can do what us old guys do and that is hang out at the local hobby shop and buy more trains.  LOLOLOLOL  On to business.

I really checked the options (meaning I did some in depth reading) for the ET-4850.  It does not have duplex scan capabilities.  This is not a game changer.  For my needs, I have a work around.

Yes, you are out of luck. Your **avahi-browse -rt _uscan._tcp** output has

> 
txt = ["duplex=F" "is=platen,adf" 

> 
At this point I have to say that I am please with the ET-4850,  now that I have read.  It works as advertised.

I couldn't have reached this point without your assistance.

Thank you very much for everything.

Sincerely,
Rich Ramik

And thank you too, Rich, for engaging. Enjoy your weekend. Try to cheer yourself up, but not by buying the shop :).

---

### Post by richramik on 2022-04-08
All right.  I give up.  What does **txt = ["duplex=F" "is=platen,adf"** mean?

Thanks,
Rich Ramik

---

### Post by brian_p on 2022-04-09
> **richramik said:**
> All right.  I give up.  What does **txt = ["duplex=F" "is=platen,adf"** mean?


**adf** is **automatic document feeder**.
**platen** is the flat glass plate to place a document on.
Your scanner provides both input methods.
I think **is** is **input scan**.

**duplex=F**. F is **false** It tells you that duplex scanning is absent.

These are part of the text record (**txt=**).

---

### Post by richramik on 2022-04-09
Brian:

That answers that question.

At some point I will probably upgrade to 22.04.  I tend not to load a new release unless there is a "dot" version.  

With that in mind, should I archive the information you provided when the day of the upgrade occurs?

And no, I didn't buy out the hobby shop.  There still some trains left LOLOLOL.

Thanks,
Rich Ramik

---

### Post by brian_p on 2022-04-10
> **richramik said:**
> Brian:

That answers that question.

At some point I will probably upgrade to 22.04.  I tend not to load a new release unless there is a "dot" version.  

With that in mind, should I archive the information you provided when the day of the upgrade occurs?


22.04 comes with ipp-usb and sane-airscan. You will get updated packages. What we have done here puts you ahead of the game :D. By all means keep notes if you wish.

---

### Post by richramik on 2022-04-10
Brian:

It's nice to be ahead of the curve for a change.

Thanks again for the assistance / education.

Rich Ramik

---

