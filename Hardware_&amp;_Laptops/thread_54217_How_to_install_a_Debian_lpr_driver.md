---
title: "How to install a Debian lpr driver"
date: 2005-08-03
forum: Hardware &amp; Laptops
---

### Post by MoreBikesFewerCars on 2005-08-03
Okay... I'm I newbie, so step-by-step helps. I found a Debian driver for my Brother HL-2040 USB laser printer. I ran the dpkg command and got this:

$: sudo dpkg -i brhl2040lpr_1.1.2-3_i386.deb
Password:
Selecting previously deselected package brhl2040lpr.
(Reading database ... 63417 files and directories currently installed.)
Unpacking brhl2040lpr (from brhl2040lpr_1.1.2-3_i386.deb) ...
Setting up brhl2040lpr (1.1.2-3) ...

$: 

So now what do I do?

---

### Post by MrCheese on 2005-08-04
[QUOTE=MoreBikesFewerCars]Okay... I'm I newbie, so step-by-step helps. I found a Debian driver for my Brother HL-2040 USB laser printer. I ran the dpkg command and got this:

$: sudo dpkg -i brhl2040lpr_1.1.2-3_i386.deb
Password:
Selecting previously deselected package brhl2040lpr.
(Reading database ... 63417 files and directories currently installed.)
Unpacking brhl2040lpr (from brhl2040lpr_1.1.2-3_i386.deb) ...
Setting up brhl2040lpr (1.1.2-3) ...

$: 

So now what do I do?[/QUOTE]

I can't give you a specific answer, but here's a pointer to see what the package actually supplies :

Install mc (if you don't already have it) and open the .deb and look at any documentation inside the package. There should be some indication what to do with the resulting print driver.

Looking at [HTML]http://usalug.org/phpBB2/viewtopic.php?p=61196&[/HTML] this driver may not actualy be needed to use the printer anyhow.

---

### Post by MoreBikesFewerCars on 2005-08-04
Thanks for the tip, but the only readme-type file just had the number "2" in it. What the heck?

After that, I did more digging around on Brother's Web site, which is quite confusing. I eventually found instructions which apply to users of the HL-2040 laser printer and these other models:

HL-2030, HL-2070N, FAX-2820, FAX-2920, MFC-7220, MFC-7225N, MFC-7420, MFC7820N, DCP-7010, DCP-7020, DCP-7025

Instructions are here:

[http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install3.html](http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install3.html)

There's a good explanation of how to install the LPR driver and a cupswrapper driver. I followed the Debian-specific steps, of course. After that, the printer just showed up in my printer settings. I had to restart OpenOffice to get it to print correctly, though.

Hope this helps someone else.

---

### Post by umuro on 2006-07-02
See also [http://www.ubuntuforums.org/showthread.php?p=1206934#post1206934]("http://www.ubuntuforums.org/showthread.php?p=1206934#post1206934")

---

### Post by alexlloyd on 2006-08-02
I am trying to install the Brother HL1030. I am running into problems and have tried 

sudo dpkg -i --force-all /home/alex/Desktop/hl1030lpr_1.1.2-1_i386.deb

I get the error 

dpkg: error processing home/alex/Desktop/hl1030lpr_1.1.2-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 home/alex/Desktop/hl1030lpr_1.1.2-1_i386.deb

What now...

---

