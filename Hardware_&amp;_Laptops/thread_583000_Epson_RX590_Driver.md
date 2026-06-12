---
title: "Epson RX590 Driver"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by derekco on 2007-10-20
I purchased an Epson Stylus Photo RX595 printer and I am trying to get it to work with my Ubuntu Dapper installation.  I visited [linuxprinting.org]("http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_RX585") and [avasys.jp]("http://www.avasys.jp/english/linux_e/dl_spc.html").  I found that Epson offers an RX590 driver through their Avasys.jp website and that other users of this same printer have had luck using that driver.

The bad part is that Avasys is saying that are [down for maintenance]("http://avasys.jp/hp/page000001100/hpg000001022.htm") and they have been under maintenance since October 4.  (16 days!).  All I need is the RX590 driver (eksprx590.ppd); does anyone else know an alternate site I can get it?

I searched all over for the driver and can't find it anywhere else.   Also, l cannot find any alternative solultions that work for me.   

Any ideas or suggestions would be greatly appreciated.

Thanks!
-Derek

---

### Post by derekco on 2007-10-21
I got it to work!!!

I found that the Epson Stylus Photo RX590 driver is part of Gutenprint 5.0.1.  I manually downloaded, compiled and installed it. There may be an easier way, but for reference, this is how I did it.

Downloaded the Source Code for GutenPrint 5.0.1 from [Source Forge]("http://linux.softpedia.com/get/Printing/Gutenprint-112.shtml")

Install all the development libraries: System->Administration->Synaptic Package Manger ==> Choose the following:
[LIST]
[*]libcupsys2-dev
[*]libgutenprintui1-dev
[*]libjpeg62-dev
[*]libpng3-dev
[*]libtiff4-dev
[/LIST]

After unpacking the source code, compiled the driver from the command line with: 
[LIST]
[*]./configure
[*]make clean
[*]make
[*]sudo make install
[/LIST]

Restarted Cups: 
[LIST]
[*]sudo /etc/init.d/cupsys restart
[/LIST]

The RX590RX driver should now appear under SYSTEM->ADMINISTRATION->PRINTING->ADD A PRINTER===>PRINTER DRIVER

Some of these steps may be extra, but I just wanted to document what worked for me in case anyone else had the same problem.

Again, I am using Ubuntu Dapper.  Gutsy may have this version of Gutenprint already, in which case this whole process is not needed.

Hope this helps anyone struggling with the same problem.

---

### Post by Lulu58e2 on 2007-10-24
Thanks for your post: I tried the RX590 driver (for my RX595) that came with Gutsy and it worked great! 

(Ubuntu just won BIG points with the wife! We're not out of the woods yet, though. :() 

C>

---

### Post by Kwisniew on 2007-11-02
Kudo's this worked for me as well, thanks a bunch, saved me a lot of time!!:

---

### Post by mike.grabowski on 2008-02-09
I am considering buying the RX595. I am using Gusty. Can anyone confirm if all features are usable on linux? I'm referring to the scanning and cd printing etc.

BTW, if anyone else is interested, Epson.com has it on sale for $99. I'm going to order it as soon as I get a reply. Or I might just go ahead and get it anyhow. Looks like a steal of a deal.

Thanks for any info!
Mike

---

### Post by mike366 on 2008-02-10
I have tried everything as mentioned in these threads to install the Epson RX595, to no avail.  The driver for the 590 never shows up in the printer list.

Any other ideas?

---

### Post by gengle77 on 2008-02-10
Yes this printer,and scanning feature works fine with Gutsy. As far as the cd printing I have not tried that yet.

---

### Post by mike366 on 2008-02-10
How were you able to get the RX590 driver to show up when you Add a Printer?  I followed these instructions, but only see the 500, 510, 600, etc, under epson, none of which work.

I am using Gutsy.

---

### Post by gengle77 on 2008-02-10
As far as that coming up under my drivers it was there from the beginning. I just started using Gutsy so Im no expert when it comes to finding ways to get it.

---

### Post by gengle77 on 2008-02-10
I went under main menu-system-administration- click on printing click on change next to your make and model it should search it will find epson click on forward and it should be there. It is there for me.

---

### Post by mike366 on 2008-02-10
Pardon my ignorance, where might I find the equivalent of "main menu-system-administration- click on printing" in Kubuntu?

---

### Post by gengle77 on 2008-02-10
Kubuntu I have no idea Im only familar with ubuntu.

---

### Post by mike.grabowski on 2008-02-11
Thanks for the reply! I'm going to order one up!

---

### Post by mike366 on 2008-02-12
I dumped Kubuntu and installed Ubuntu, not only do I like it better, Ubuntu immediately recognized the RX595, and all is well.

I am soooooo anoyed with Kubuntu / KDE.

---

### Post by wcGary83 on 2008-02-19
I can't believe my RX595 worked instantly!!!

It took an hour to download and get the stupid **** drivers working off the website in XP!

(I lost the CD)  

KUDOS to Ubuntu!!!

---

