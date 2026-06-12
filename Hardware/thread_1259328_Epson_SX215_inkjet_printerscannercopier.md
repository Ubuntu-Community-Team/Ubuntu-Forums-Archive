---
title: "Epson SX215 inkjet printer/scanner/copier"
date: 2009-09-06
forum: Hardware
---

### Post by Wobblybob on 2009-09-06
Hi,

Just thinking of upgrading my Epson stylus photo r200 to the above, has anyone got this printer, printing and scanning and if so how?

Martin

---

### Post by hansdown on 2009-09-06
Hi Wobblybob.

It seems to be supported.

[http://avasys.jp/hp/page000001300/news00005_e.htm](http://avasys.jp/hp/page000001300/news00005_e.htm)

---

### Post by Wobblybob on 2009-09-06
> **hansdown said:**
> Hi Wobblybob.

It seems to be supported.

[http://avasys.jp/hp/page000001300/news00005_e.htm](http://avasys.jp/hp/page000001300/news00005_e.htm)

thanks mate, I've never seen this site before, would be nice to find someone using it though before I buy.

---

### Post by johnleonard on 2009-11-28
Well, I have the SX215 and have downloaded the drivers for 9.04 but I can't get it to work. The printer just shoots the paper out then demands more. Has anyone managed to get this to work? If so, how?

---

### Post by johnleonard on 2009-11-28
Answered my own question. When adding a new local printer in CUPS the device Epson Stylus SX210 and the driver Epson Stylus SX100 - CUPS+Gutenprint v5.2.3  work for me

---

### Post by spnoe on 2009-12-16
> **johnleonard said:**
> Answered my own question. When adding a new local printer in CUPS the device Epson Stylus SX210 and the driver Epson Stylus SX100 - CUPS+Gutenprint v5.2.3  work for me

Thanks for the tip John. I was having problems finding a driver for my new SX210 and as you say the SX100 seems to work fine.

Best wishes,
Steve

---

### Post by OliW on 2010-01-27
I bought one of these and yes the SX100 Gutenprint driver does work, albeit a little slowly

Seeing Avasys is supposed to be the "proper" driver (and there now is a SX215 PPD) I compiled (I'm 64bit - there are only 32bit debs) and installed pipslite 1.4.0 and tried adding the PPD. Total failure.

Have any of you had any luck with the Avasys driver and if you did, were you using 32bit or 64bit?

---

### Post by spnoe on 2010-01-27
> **OliW said:**
> I bought one of these and yes the SX100 Gutenprint driver does work, albeit a little slowly

Seeing Avasys is supposed to be the "proper" driver (and there now is a SX215 PPD) I compiled (I'm 64bit - there are only 32bit debs) and installed pipslite 1.4.0 and tried adding the PPD. Total failure.

Have any of you had any luck with the Avasys driver and if you did, were you using 32bit or 64bit?

Hi OliW, No once I found that the SX100 driver worked I settled
for that. Yes it is a little slow but works at present.

Steve

---

### Post by Goldenlight on 2010-01-27
I own an Epson ARtesian 810 The wireless printing worked out of the box.  Ubuntu automatically detected it.  Havn't messed with Scanning, but Im sure I can get it to work if I do some reading on it.

---

### Post by mick222 on 2010-04-19
New drivers out for epson printers seem to work better than the gutenprint drivers [http://avasys.jp/eng/linux_driver/news/id000804.php](http://avasys.jp/eng/linux_driver/news/id000804.php)

---

### Post by OliW on 2010-04-19
> **mick222 said:**
> New drivers out for epson printers seem to work better than the gutenprint drivers [http://avasys.jp/eng/linux_driver/news/id000804.php](http://avasys.jp/eng/linux_driver/news/id000804.php)

Thing I've noticed in the 10 minutes using these drivers:

[LIST]
[*]No faster than Gutenprint
[*]Fewer quality/paper/scaling options
[*]Still no ink level feedback (I know it would just lie all the time but still - it would be nice to have an idea)
[/LIST]

---

### Post by babru2222 on 2010-06-15
Bought my sx215 a few weeks back, after checking it would work in ubuntu.It didn't.I've been searching for a suitable driver since. Found your info this morning. Printer up and running, 
Mick222 thanks

---

### Post by OliW on 2010-06-15
Since my last post, I've started trialling [TurboPrint 2]("http://www.turboprint.info/"). It's not free (&#8364;30 - which is about as much as I paid for the printer >_<) and it's not open source but it does work quite well.

---

### Post by gaz90 on 2010-06-18
Just got my SX215 running on 10.4 after the previous mentioned problems!

It's all GOOD!

---

### Post by GaryLittlemore on 2010-06-24
I've been unable to get my Epson SX215 printer working, and I'm a noob with Linux. Would someone be able to give me step by step instructions on how to get the drivers installed please.

---

### Post by Leperous on 2010-09-28
Perhaps too late for the last chap, but this should work if you're finding it spitting out paper:

Delete the printer if you've already installed it.

Download the .DEB file from the avasys website that corresponds to your architecture (i.e. 32 bit, Intel 64 bit, AMD 64 bit):
[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/)

Install it, restart Ubuntu.

Add a new printer, it should be listed there and work properly.

---

### Post by Unterseeboot_234 on 2011-05-26
Not sure what's going on, but originally I had the first suggestion installed on ubuntu 9.04 and 10.04. I switched over to the 2nd suggested driver. Worked very well, as good as Windows7 autodownload for the sx215.

Then while installing 11.04, I went straight for the 2nd suggested driver. I got endless paper spitting out. Deleted the printer icon, reboot. Plugged in the USB printer cord so the printer gets discoverd, re-added a printer in Printer Administration. It works, but very, very slow, like the first suggestion for using sx210 driver with gutenprint. I mean 2 minutes to print 1 line from TextEditor.

So, it works. But it is spooky and unknown how to work it back up to speed.

edit::::::::::::
My experience was the newer driver was just as slow as the first driver while upgrading to Natty. I finished up my add-ons for my computer upgrade by installing Padre, an IDE for perl. That requires a rebuild of wxWidgets. It was the rebuilding of wxWidgets that got me the warning I was using restricted MSFonts. I think that is what fixed the avasys driver. Now my Epson prints and responds to my expectations. I was missing the fonts the printer wants so it doesn't have to contrive soft fonts.

---

