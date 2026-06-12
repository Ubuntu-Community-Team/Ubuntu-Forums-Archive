---
title: "Canon PIXMA MP210 and Ubuntu 64-bit"
date: 2008-05-31
forum: Hardware
---

### Post by SnakeArtworX on 2008-05-31
Hello.
Few days ago, I've became a happy owner of Canon PIXMA MP210 multifunctional device. I've found linux drivers on Canon site, but they're only for 32 bit. At the moment I've configured the printer using MP150 driver, but there's no output on paper. The test page prints only in small part, but after a while the printer seems to stop. What to do? Is there a 64 bit version of these Canon drivers?

---

### Post by OKnotOK on 2008-07-31
*Bump*

I've got the same printer on 64-bit system. 

Can anyone answer this?

---

### Post by prshah on 2008-07-31
> **SnakeArtworX said:**
> 
I've found linux drivers on Canon site, but they're only for 32 bit.
Is there a 64 bit version of these Canon drivers?

> **OKnotOK said:**
> 
I've got the same printer on 64-bit system. 


Just a suggestion; if you can get hold of the PPD file from the driver package, you can direct CUPS (Common Unix Printing System) to use that PPD to setup a custom printer with capabilities read from the PPD file. You can access CUPS by launching a browser and browsing to either of the below addresses```
http://localhost:631
http://127.0.0.1:631
```

Load the CUPS page, then click on "Add Printer", fill in suitable values for name, location, etc

==
From this point on, the values are all guesswork; you should find out the correct values for your printer; the steps shown here are just for illustration/guidance 

Choose "Device" as AppSocket/HP JetDirect, Continue
Enter a device URI (example) "usb://EPSON/Stylus%20CX2800", Continue
==

Now you will get the option to select a make/model **OR PROVIDE A PPD FILE**. Point it to the location of the PPD file, and your printers capabilities, etc should all be recognized correctly.

Hope this helps.

---

### Post by pay on 2008-09-09
To get the ppd, Download cnijfilter-mp210series_2.80-1_i386.deb from the canon site then do ```
mkdir tmp
dpkg -x cnijfilter-mp210series_2.80-1_i386.deb tmp/
sudo cp tmp/usr/share/ppd/canonmp210.ppd /usr/share/ppd
```

---

### Post by Sense on 2008-11-01
Canon doesn't only provide pre-compiled and packaged drivers, but you can also download the sourcecode. It contains the PPDs and the printing UI and Canon's filters. I haven't tried to compile it yet, but I hope it will work.

By the way, the only place where you can download the official drivers: [http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp210_support.aspx](http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp210_support.aspx)

---

### Post by jakeofspades on 2009-01-05
Sorry - I know this is an old thread but I'd just like to add a word of advice to people that are possibly in the same situation - they've got 64-bit architecture and can only get 32-bit deb printer drivers.

For me - forcing an install with the 32 bit debian packages on my 64-bit machine is working fine.
I just downloaded this tarball : [http://software.canon-europe.com/software/0030808.asp]("http://software.canon-europe.com/software/0030808.asp") and then used the --force-architecture command.

I extracted the tar, ventured inside the driver folder and issued these commands,
```

sudo dpkg -i --force-architecture ./cnijfilter-common_2.80-1_i386.deb 
sudo dpkg -i --force-architecture ./cnijfilter-mp210series_2.80-1_i386.deb 

```

Then all I had to do was set the printer up on CUPS - choosing the new and shiny driver from the list.

This has worked for me both on Ubuntu Hardy Heron and Intrepid Ibex. I didn't previously know you could force-architecture install things to be frank (although I think this will be the only time I shall resort to it). Hope this helps somebody.

Ps if you really don't want to do that, compiling from source seems to be the only option and it seems really messy.

---

