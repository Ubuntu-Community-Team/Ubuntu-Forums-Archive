---
title: "What would corrupt data?"
date: 2009-06-08
forum: Hardware
---

### Post by Jesdisciple on 2009-06-08
I had [several problems]("http://jesdisciple.blogspot.com/2009/05/my-ubuntu-adventure.html") with my previous installation.  Now PHP seems to be falling apart pretty fast, and I wonder what would do this?  It seems that data access may be the trigger, as even things that I don't change (like the behavior of PHP's DOMDocument) get messed up.  However, maybe I'm changing a dependency with apt-get.  *shrug*

So what hardware might corrupt data if the device and/or driver is poor?  And how can I test the main suspects?

Thanks.

---

### Post by cariboo on 2009-06-09
The first thing I would check is the health of the hard drive. Go to the hard drives manufacturers web site and download their diagnostic tools and run them on your hard drive.

---

### Post by Jesdisciple on 2009-06-09
I don't see anything for that yet, but I'm certain it will be Windows-only.  Would Wine run it correctly?

Also, the first link below shows this under "BIOS": *Flashing the wrong BIOS can cause harm to the system. Acer recommends that you should only upgrade your firmware/drivers if you have been instructed to do so by an Acer Customer Care representative. By using these firmware/drivers you agree to accept the possibility of product failure.*  Could GRUB have caused problems?

[http://us.acer.com/acer-v2/service.do?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3750&sp=page15e&ctx2.c2att1=25&miu10ekcond13.attN2B2F2EEF=3750&CountryISOCtxParam=US&ctx1g.c2att92=453&ctx1.att21k=1&CRC=2054404012](http://us.acer.com/acer-v2/service.do?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3750&sp=page15e&ctx2.c2att1=25&miu10ekcond13.attN2B2F2EEF=3750&CountryISOCtxParam=US&ctx1g.c2att92=453&ctx1.att21k=1&CRC=2054404012)

"the old page":
[http://www.acerpanam.com/synapse/forms/portal20.cfm?website=AcerPanAm.com&siteid=7117&areaid=2&formid=3394#results](http://www.acerpanam.com/synapse/forms/portal20.cfm?website=AcerPanAm.com&siteid=7117&areaid=2&formid=3394#results)

EDIT: And the model is TravelMate 3260 in case the URL doesn't tell them that.

Thanks.

---

### Post by Jesdisciple on 2009-06-10
I wonder if I should try using fsck after unmounting?  I don't think I know enough to just go ahead with that on my own.

---

### Post by cariboo on 2009-06-10
Get the diagnostic utilities from the hard drive manufacturer, They are usually available as a bootble iso that will run the checks without needing an os. If you aren't sure who the manufacturer is, Open System-->Administration-->Synaptic Package Manager and search for smartmontools and install the package. Once installed open an Applications-->Accessories-->Terminal and type:

```
sudo smartctl -i /dev/sda
```

You should get something that looks like this:

```
sudo smartctl -i /dev/sdb
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.10 family
Device Model:     ST3250620A
Serial Number:    6QE10TQ9
Firmware Version: 3.AAE
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Jun  9 23:56:33 2009 PDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
```

This will show you all the info you need.

---

### Post by Jesdisciple on 2009-06-10
The manufacturer (or at least the vendor) is Acer.  They have several downloads available, but I haven't seen any HDD verification yet.

As for smartctl, should the partition be unmounted first?

Thanks.

---

### Post by TheAftermath on 2009-06-10
Yeah id lean towards the drive itself.
 
but first before i tore my machien aprat. Id make SURE all WIN updates are done. casue.. stoopid vista needs those updates or junk just doesnt work.
 
Be sure the software is runing in admin mode.
 Now if thats your standard practice. yes rip apart the HD.
 
Cause I dont think its gonna be a "driver" per say. 
Try Chkdsk then maybe just try reconstructing the sectors on drive.
 ( altho I know Defrag isnt a real option ) but tools for disk drives can be gotten to let you do that.
 I found the OLD ways over new ways work best.

---

### Post by IcarusR on 2009-06-10
Boot Ubuntu as normal then from a terminal run the smartctl command that cariboo907 gave in his last post. 
This will give you the hard drive manufacturer & model. 
Then go to manufacturer website & search for hard drive diagnostic utility to download. 
Most are in the form of an iso image, burn this to cd. 
Then boot pc from this cd & run the hard drive diagnostics utility. This will tell you what state your drive is in.

---

### Post by Jesdisciple on 2009-06-10
Sorry, I was rushed when I typed my previous post.  The HDD is a [Hitachi]("http://www.google.com/search?hl=en&q=hitachi") [Travelstar 5K160]("http://www.hitachigst.com/portal/site/en/products/travelstar/5K160/"), but I'm having trouble [looking for related downloads]("http://search.hitachi.co.jp/sitesearch/GLOBAL?SITE=GLOBAL&LANG=EN&PL=EN&SET=1&Q=download+travelstar+5k160&x=0&y=0").```
$ sudo smartctl -i /dev/sda2
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Travelstar 5K160 series
Device Model:     Hitachi HTS541680J9SA00
Serial Number:    SB2204SGER83EE
Firmware Version: SB2OC70P
User Capacity:    80,026,361,856 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 1
Local Time is:    Wed Jun 10 12:03:11 2009 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
```

---

### Post by IcarusR on 2009-06-12
You need the 'drive fitness tool' from here  [http://www.hitachigst.com/hdd/support/download.htm#DFT]("http://www.hitachigst.com/hdd/support/download.htm#DFT")

Suggest you use the iso image to create a bootable CD

---

### Post by Jesdisciple on 2009-06-12
Oh, thanks.  I didn't think I was ever going to see it.

Now I have one more question...  I got Ubuntu burned to a DVD-RW before but my machine wouldn't boot off it, so I had to order a Live CD from Canonical.  Should a CD-RW work alright, or does it need to be a CD/DVD-R?

Thanks.

---

