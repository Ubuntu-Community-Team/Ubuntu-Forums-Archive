---
title: "Canon Pixma MP500"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by drobvice on 2006-06-17
I am currently using the free turboprint driver for this printer, but I found a Japanese driver in rpm format here (translated page):

[http://translate.google.com/translate?u=http%3A%2F%2Fcweb.canon.jp%2Fdrv-upd%2Fbj%2Fbjlinux260.html&langpair=ja%7Cen&hl=en&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools]("http://translate.google.com/translate?u=http%3A%2F%2Fcweb.canon.jp%2Fdrv-upd%2Fbj%2Fbjlinux260.html&langpair=ja%7Cen&hl=en&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools")

There is a common package and a printer specific package.  I tried to use alien to install as a deb for both but the test page won't print.  Has anyone tried this or have any insight as to if this will work?


Also, I found a link for this scanner driver with instructions for install under Ubuntu Dapper:

[http://home.arcor.de/wittawat/pixma/]("http://home.arcor.de/wittawat/pixma/")

I haven't tried it yet but it looks pretty straight foreword.

Would like input from anyone that has been attempting or successfully using either of these on Dapper. :hopeful:

---

### Post by that_loony on 2006-06-28
I have the MP500 and have it installed with Dapper. 

I am currently using the Turboprint drivers but have yet to pay (they use a watermark) as I am not totally convinced yet I want to shell out $40 for the privilage. Yet.

I tried the drivers from Canon JP but no joy. I did the alien import of the RPMs and I could not get them to work at all. Kept saying the printer was asleap. 
 
I have successfully added the printer with Turboprint and have printed.

But I have as yet been unable to get the box to be a print server for my home client machines, a WinXP and a MaxOSX. Its a cups/samba issue.

---

### Post by canadianwriterman on 2006-07-01
The new version of TurboPrint supports the MP500. I've installed it and my MP500 now works perfectly.

---

### Post by drobvice on 2006-08-14
How about the scanning function?

---

### Post by jdpipe on 2006-08-15
Re scanning, I found these instructions worked fine for me:
[http://ubuntuforums.org/showthread.php?t=236538](http://ubuntuforums.org/showthread.php?t=236538)

Re printing, you might find these steps useful. I succeeded in printing to an MP760 printer using the Canon (japanese site) drivers. I wasn't able to build the .rpm from the .src.rpm, but I was able to convert their RPM with Alien and then to install and use the driver. No double-side printing at this stage, though, sadly.
[http://ubuntuforums.org/showthread.php?t=236538](http://ubuntuforums.org/showthread.php?t=236538)

Cheers
JP

---

### Post by j2m on 2006-08-25
Concerning scanning the adress you give is not correct (the same as printing).
Is it possible to have the right one ?

Regards
J2M

---

### Post by DoctorMO on 2006-08-25
the sane backend supports the MP500, so if you don't get access to the scanner directly then either you need a later version of sane-backends (1.0.18 is newest, 1.0.17 installed in ubuntu) or sometimes the scanner is hidden because the usb node is root only (for some odd reason) chmodding does help but it's best if I could find a more perminant fix and let you know.

Best Regards, Martin Owens (who is writing the MP360 driver patch)

---

### Post by tanari on 2006-09-08
I also want to buy printer/scaner. Canon PIXMA MP500 is a good choise, but after what I have read :(.

Is it true that Ubuntu has good HP printers, scaners support?

From Breezy release notes:
> All-in-one printer/scanner devices from Hewlett-Packard (HP) are supported out of the box

What can you advice to me?

P.S.
Everybody please sign this petition!
maybe canon will make drivers

[http://www.canon-europe.com/Support/Software/Linux/registration.asp?ComponentID=312222&SourcePageID=312225#1](http://www.canon-europe.com/Support/Software/Linux/registration.asp?ComponentID=312222&SourcePageID=312225#1)

---

### Post by nybjj on 2006-10-14
I got my Pixma MP500 to work pretty well under Ubuntu 6.06 by setting it up as a BJC-8200 and selecting the Gutenprint driver.

---

### Post by finite9 on 2006-11-10
nybjj--how did you manage this?  I use Ubuntu 6.06.1 amd64 and the printer is autodetected and I choose BJC-8200 Gutenprint, but when I print a test page from CUPS or a web page from Firefox, it just feeds the page and prints a few 1cm coloured lines down the page.  I tried the IP4200 driver, normal BJC-8200, Gutenprint and BJC-4400 Photo without any luck whatsoever.

---

### Post by drobvice on 2006-11-18
This has been resolved for me.  See this thread [http://www.ubuntuforums.org/showthread.php?p=1776062#post1776062]("http://www.ubuntuforums.org/showthread.php?p=1776062#post1776062")

**Edit**

Not completely resolved.  I can print a test page but not print from open office :(  Printing from firefox works!!

**Edit-Edit**

Now the printer will not accept jobs.  Me sad.

---

### Post by 42Wired on 2007-02-19
> **drobvice said:**
> Also, I found a link for this scanner driver with instructions for install under Ubuntu Dapper:

[http://home.arcor.de/wittawat/pixma/]("http://home.arcor.de/wittawat/pixma/")


I successfully installed the driver for the scanner, and the test scan went perfectly, but I can't seem to access the scanner from the command prompt.

These are the usage instructions from the readme file:

[I]scan - the stand-alone program

You must have read and write permissions for the USB device node of your scanner. Otherwise, you have to run scan and SANE frontends as root.

```
./scan output.pnm
```

will scan the whole area at 75 DPI in color mode and save the output to output.pnm. Press the "scan" button on the device to begin. Running scan without parameters will show all available options.

```
./scan -LL
```

prints all supported models. Experimental subdrivers are disabled by default. scan will tell you how to enable them.[/I]

This is what I get from running /usr/local/bin/pixmascan in the terminal:

[I]Scanner utility for Canon PIXMA MP series
Version 0.12.2 Copyright (C) 2006 Wittawat Yamwong

Usage: scan [options] <output.tif|pnm>
  -p {help,A4,...}
	 set paper size.
  -m {color,gray}
	 set scan mode, color or grayscale.
  -x <x> -y <y>
  -w <w> -h <h>
	 offset (x,y) dimension (w,h) in millimeters.
  -r {75,150,300,600,1200,...}
	 resolution in DPI.
  -1
	 start immediately and scan only 1 page.
  -f pnm
	 set output file format, default is pnm.
  -L
	 list connected scanners.
  -LL
	 list all supported scanners.
  -g <gamma>
	 set gamma value, default = 2.2
  -W
	 allow overwriting output file
  -a
	 use automatic document feeder
  -B
	 wait until a scanner button is pressed and exit.
  -d debug level [0,100][/I]

I've tried many combinations of options, but the basic line I type is ```
./scan /home/me/Desktop/output.pnm -1
``` which returns ```
-bash: ./scan: No such file or directory
```

I just want it to scan the whole glass area and edit it in GIMP or something.

Please help a noob out.

---

### Post by Rocketmac on 2007-07-03
I was able to get my Pixma MP500 working.

Details are in this thread.

[http://ubuntuforums.org/showthread.php?t=282096&page=4&highlight=MP510](http://ubuntuforums.org/showthread.php?t=282096&page=4&highlight=MP510)

-- Duplex printing **[COLOR="Red"]did[/COLOR]** work for me.

---

