---
title: "Canon printer resolution?"
date: 2008-09-11
forum: Hardware
---

### Post by 2CV67 on 2008-09-11
Hi guys!

I have a Canon printer which I have installed in Hardy, one time using the default Gutenprint drivers & one time using the Canon Australia drivers.

Neither installation allows better than 600dpi - not even visible as an option in the settings box.

For the Canon drivers, I modified the ppd files (see below) to introduce more resolution/quality options, but they don't show up - even in the settings box.

I followed lots of threads on Canon printers which often include these same instructions, but never say that they actually produce better resolution.

My particular printer is an iP4300 & I am running up-to-date Hardy, but I suspect the situation is not specific to that configuration.

ppd file mods:
> Advanced Features
Unfortunately, the installed PPD file doesn't allow you to select the printing quality. To fix this, back up your ppd file, then open it as root:
Code:
gksudo gedit /etc/cups/ppd/iP4300-Ver.2.70.ppd
Insert these lines in the file after the "Resolution" section:
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality
and File/Save.
The following gives a greater choice of print resolution if added to the "Resolution" section, but I am not clear whether the Quality setting impinges upon this. Note that the ip4200 only offers 600dpi in black and white.
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*Resolution 4800/4800 dpi: "<</HWResolution[4800 4800]>>setpagedevice"
(from [http://gentoo-wiki.com/Canon_Pixma_Series](http://gentoo-wiki.com/Canon_Pixma_Series))

Has anybody got these changes to produce results, even to show in the dialog boxes?

Or any other (free) method of getting photo-quality resolution?

Thanks!

---

### Post by DoctorMO on 2008-09-11
Hey there, I have an Canon iP5000 and it's a great printer. But despite the work put in by Sascha on the drivers (gutenprint) It's not tuned right the colours come out wrong.

So, Get involved in the gutten print mailing list, ask your question there. Offer your help to test modifications or to get usb dumps (if asked) of windows performing the desired actions.

Hopefully more involvement can get the problems worked out for everybody.

---

### Post by colintivy on 2008-09-11
Hi!2CV

I have a Canon i905D which was not happy with Guitenprint, actually that source does not list mine, only some near relatives. Salvation came from some bright spark, try [www.zedonet.com/en_p_turboprint_printers.phtml](www.zedonet.com/en_p_turboprint_printers.phtml)

There you will find a vast list of most of the world's printers including lots of Canon (who are very tardy in providing drivers for us). Turboprint2 claims to equal or even better the original Windows performance using the installation disk from Canon. I have no reason to disbelieve them.

I only wish I could find an equivalent source of a driver for my Canon 9900F Scanner which is giving me grief.

Colintivy  :-/

---

### Post by 2CV67 on 2008-09-18
Thanks for the suggestions.

I have tried TurboPrint & it works well, but I am looking for a free driver - partly being mean & partly out of enthusiasm for the open-source ethic.

I signed up for the gutenprint list, so will see what that brings.
I am certainly willing to help, but probably not very useful!

So - it looks like no free driver with better than 600dpi then? :(

Surprising to see all those sites proposing the ppd file mods if they don't do anything...

---

### Post by 2CV67 on 2008-09-27
Nobody getting better than 600dpi out of a Canon?

---

### Post by Special K on 2010-09-23
I have been using my Canon IPX4300 for quite a while now on Ubuntu and even with the upgrade to 10.04, it is still stuck with a max res of 600dpi.

It's a big shame, as the printer does and did everything i needed when using the dreaded Microsoft OS, including full duplex capability when connect both locally and over a network.

However, duplex is just a dream for me on 10.4 when printing from 10.04 to a windows shared ipx 4300.

Its a shame these little niggles stop it being my main use machine

---

### Post by 2CV67 on 2011-07-17
Just upgraded Ubuntu to 11.04 & still only 600dpi max available for my Canon Pixma iP4300, which claims to give up to 9600x2400dpi...

Using the Canon driver I am only offered 600 with no options.
Using CUPS/Gutenprint the offer is 600/300/300Draft/Auto.

Anybody doing any better than this yet?

Thanks!

---

### Post by 2CV67 on 2011-10-25
For various reasons, I just tried re-installing my printer via localhost631 & was surprised to see the prefered driver was the OEM Canon iP4300 Ver.2.70 not CUPS/Gutenprint whatever.

I tried it & it actually offers me 600/1200/2400/4800dpi!

Sounds good.
Only problem is the printer is not actually working with this driver so far.
That will be for another thread...

---

### Post by 2CV67 on 2011-10-29
That other thread is here:
[http://ubuntuforums.org/showthread.php?t=1869131](http://ubuntuforums.org/showthread.php?t=1869131)

Current status is that the Canon driverworks OK with 600dpi & **_1200dpi_**, which is good progress & better than Gutenprint.

Still no printing at the higher dpi's offered though (2400 & 4800).

Problem seems to be at this point in /var/log/cups/error-log:
D [27/Oct/2011:15:08:48 +0200] [Job 50] Read 174 bytes of print data...
D [27/Oct/2011:15:08:48 +0200] [Job 50] Wrote 174 bytes of print data...
D [27/Oct/2011:15:08:48 +0200] [Job 50] **CIF COMMAND ERROR :memory allocate Error!**
D [27/Oct/2011:15:08:48 +0200] [Job 50] Error in ppm_image_raster
D [27/Oct/2011:15:08:48 +0200] [Job 50] err in bjf_image_read_raster

Any clues gratefully received!

---

### Post by Steve R. on 2012-02-21
> **DoctorMO said:**
> Hey there, I have an Canon iP5000 and it's a great printer. But despite the work put in by Sascha on the drivers (gutenprint) It's not tuned right the colours come out wrong.

So, Get involved in the gutten print mailing list, ask your question there. Offer your help to test modifications or to get usb dumps (if asked) of windows performing the desired actions.

Hopefully more involvement can get the problems worked out for everybody.

I have the same issue of improper color registration. Sent a few emails to Canon, but I think they just tossed them into the trash. Just left an email here: [GIMP=Print]("http://gimp-print.sourceforge.net/p_Contact_Us.php"). Wait and see.

---

### Post by Steve R. on 2012-02-21
Below is another email message that I left with Canon, in case anyone else is motivated to leave a similar message.
-------------------------------------------------------------
I have been trying to leave a suggestion for LINUX printer drivers. So far, I have simply received only the noncommittal non-informative "thank-you" response. So I am trying here now. I hope that Canon is listening.

Specifically, I find it incomprehensible that Canon will not provide LINUX print drivers. HP does. So would Canon prefer that I buy an HP printer - or would Canon prefer that I continue to buy Canon ink and should my Canon IP5000 die, that I buy another Canon printer?

Currently you are discouraging me from continuing my 7+years as a Canon customer. I might be one person, but there are many others who have Canon printers that are dissatisfied that Canon does not have LINUX drivers. These are LOST sales. REDUCED profits for Cannon. Sure it may cost Canon $$$ to develop Linux drivers, but would you have me and others buy HP instead?

I hope that you will contact Gutenprint and assist them with providing a world class Canon print driver.

---

### Post by 2CV67 on 2012-02-21
For resolution, I reported here that I am now successfully using the modified Canon drivers from Michael Gruz PPA:
[http://ubuntuforums.org/showpost.php?p=11704448&postcount=5](http://ubuntuforums.org/showpost.php?p=11704448&postcount=5)

This offers me resolutions up to 9600dpi instead of only 600dpi with Gutenprint...
4800dpi prints OK but I did not try to measure the quality of the result.
9600dpi seems to overtax something in my old PC, but who needs 9600dpi anyway?

On the colour side, the Canon drivers seem OK to me.
The Gutenprint drivers give extremely muddy colours when set at RGB colour model.
I use CMYK with Gutenprint & that seems OK to me.

---

### Post by aikishugyo on 2012-02-22
> **DoctorMO said:**
> Hey there, I have an Canon iP5000 and it's a great printer. But despite the work put in by Sascha on the drivers (gutenprint) It's not tuned right the colours come out wrong.

So, Get involved in the gutten print mailing list, ask your question there. Offer your help to test modifications or to get usb dumps (if asked) of windows performing the desired actions.

Hopefully more involvement can get the problems worked out for everybody.


Hi, thanks for the message on the gutenprint mailing list: the crux is that your gutenprint is old (5.2.6). You should use 5.2.7 or better still, 5.3.8pre1, which are available from the gutenprint project website.

Regards,
Gernot Hassenpflug

---

### Post by Steve R. on 2012-02-22
Canon just sent me a terse message that they do not support Linux and referred me to the [Linux Foundation Canon ip5000]("http://www.openprinting.org/printer/Canon/Canon-PIXMA_iP5000") printer.
-----------------------------------------------------------
I left a message on [Linux Foundation]("http://www.linuxfoundation.org/") and received this helpful reply from Gernot Hassenpflug. Evidently, Ubuntu Version 10.10 did **NOT** update to the most current printer drivers. It will be a while before I can test upgrading to a newer version.

> 1) 5.2.6 is pretty old. 5.2.7 is out since May 2011 and I added plenty of corrections to printer in 5.2.7, including likely for the iP5000. 5.2.8pre1 is also out since Dec 2012 so you might try installing that.

2) I see, yes, you will only have perhaps 1 mode there.

3) the gutenprint web page has download page links where you can get the latest version. Ubuntu 10.10 did not upgrade it seems, a bit surprising. You can install another version locally without conflict with the system version already present.

In conclusion, if you install 5.2.7, or better still, 5.2.8pre1, you can at least get (I hope) correctly registered colors. Whether the colors need tuning is something to be determined after that, since without a physical printer available we simply do not know. Thus, if you could test, that would help a lot.

Best regards,
 Gernot Hassenpflug

---

### Post by Steve R. on 2012-02-22
> **2CV67 said:**
> The Gutenprint drivers give extremely muddy colours when set at RGB colour model.
I use CMYK with Gutenprint & that seems OK to me.I was wondering about those settings. Experimenting with those settings will have to wait till I get the print driver updated.

---

### Post by Steve R. on 2012-02-22
I downloaded the updated drivers. The Canon Pixima ip5000 printer is attached to a Ubuntu computer, which is networked.

In testing, I discovered that the color offset was caused by using the wrong driver on my Windows7 computer. Clearly **_not_** the fault of Gutenprint driver. This went unnoticed as virtually everything we print is in B/W which prints correctly. 

I am also beginning to think that the printer may not be working correctly. I will have to run some more tests.

The picture below on the left is printing from the local Ubuntu computer to the attached Canon Pixima ip5000 printer.  The middle picture is printing from a Windows computer over the home network to the Canon Pixima ip5000 printer as a Windows networked printer. The picture on the far right is the "control" picture, what the other two pictures should have looked like.

PS: I printed the Analog cover on another printer and it came out the same as the "control" picture on the far right. The obvious implication, the Canon Pixima ip5000 print head is not working correctly.

---

