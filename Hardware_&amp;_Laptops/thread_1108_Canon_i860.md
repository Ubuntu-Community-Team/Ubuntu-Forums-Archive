---
title: "Canon i860"
date: 2004-10-18
forum: Hardware &amp; Laptops
---

### Post by Bertmartin on 2004-10-18
I am having problem getting my printer to work.  I have a canon i860.  I have tried two methods:

1) I found a linux driver for the Japanese version of the printer that is suppose to work.  But everything is printed in Japanese - just kidding.  Actually when I setup the printer to use the driver nothing happens.

2) I tried turboprinter which is suppose to support the i860 but I get an error with that  lpr: unable to print file: client-error-not-found

I can get it to print if I use a Canon 600 and 800 but it doesn't print the colors correctly (print cartridges are setup differently on this printer).

Thanks,
Bert

---

### Post by lockenkeyster on 2004-10-29
I am having a similar issue with my i850... it is shared on my home network on a windows box but I can't seem to even see, let alone use it. I have heard from a friend that other's have the problem with other linux distros and canons. Have you ever gotten yours to work under Linux (another distro possibly)?

---

### Post by jdodson on 2004-11-02
i got my canon i860 or i850(forgot which) to work in fedora core 2.  canon did release print driver for this model in rpm format.  here is a link to very good setup instructions for :)  [getting things going for debian](http://www.teaser.fr/~amajorel/howto/CANON-I850-CUPS).  i havent tried it yet, but i assume it works fine.  i am going to actually do this in the next few days.

---

### Post by mercurus on 2004-11-03
[QUOTE=lockenkeyster]I am having a similar issue with my i850... it is shared on my home network on a windows box but I can't seem to even see, let alone use it. I have heard from a friend that other's have the problem with other linux distros and canons. Have you ever gotten yours to work under Linux (another distro possibly)?[/QUOTE]
 I've got my Canon i250 running on my Debian Sarge server without significant problems. I share it with CUPS and I print onto it with my Ubuntu desktop.

I wrote a document about the process and posted it to the linuxprinting.org forums a while ago:
[http://www.linuxprinting.org/pipermail/canon-list/2004q2/001468.html](http://www.linuxprinting.org/pipermail/canon-list/2004q2/001468.html)

I would also search the linuxprinting.org database about your printer model, and then try the mailing list \ forums.

Cheers
mercurus

---

### Post by Jasonc221 on 2005-02-20
I tried doing what jdodson recommended [doing](http://www.teaser.fr/~amajorel/howto/CANON-I850-CUPS), but it didn't work.  I also went through and attempted to use ALL the Canon drivers that came with Ubuntu to no avail.

I just installed Ubuntu for my Dad, and I don't want this to leave a sour taste in his mouth about Linux.  Help?

---

### Post by kleeman on 2005-02-20
Try Linux Turboprint and download the free version:

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

It does support your printer (I looked). The free version is not very crippled with the
exception that if you print at highest resolution it puts a logo on the output.

---

### Post by Jasonc221 on 2005-02-21
[QUOTE=kleeman]Try Linux Turboprint and download the free version:

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

It does support your printer (I looked). The free version is not very crippled with the
exception that if you print at highest resolution it puts a logo on the output.[/QUOTE]

Ok I've downloaded Turbolinux and converted the RPM using alien.  I then installed it and followed the instructions for setting up a new printer.  The only problem is, the printer spool it's wanting to point to doesn't exist.  I tried creating it, but I continually get the error: *lpr: unable to print file: client-error-not-found*.

I am not that familiar with Ubuntu yet, but I believe this is because the default installation of Ubuntu uses the CUPS system, while Turboprint is trying to use the BSD printing system?  Any ideas on how to resolve this issue?

Thanks for pointing me in the right direction :)

---

### Post by kleeman on 2005-02-21
I think turboprint can handle CUPS (I have it working fine on Ubuntu with two different printers). One other thing to try after the turboprint installation is kprinter( apt-get install it). It has a nice wizard for installing new printers and should list all your new turboprint drivers........
I just noticed you used alien to convert the rpm. I seem to remember that doing this caused me problems. Try a manual installation instead using the tgz file.....

---

### Post by happyg on 2005-03-21
I played with CUPS config options to correct the common light/pale print on my Canon i850:

 - Use [http://localhost:631/](http://localhost:631/)  to do your tweaking
 - Option button [Configure Printer]
 - Change settings to  
[INDENT]Resolution:   600x600 dpi[/INDENT]
[INDENT]Density:   2.000[/INDENT]
 - Test Print will now show full color and sharp blacks

I tried various settings and these two are the only ones that made a difference.  Got the Density change idea from a Debian i850 'lpoptions' post somewhere.

I am using CUPS:  CANON S800 GimpPrint v4.2.7 driver 
Connected thru a ethernet JetDirect 170x TCP/IP print server on my home network.

Hope someone finds this helpful...   I found little help in my surfing.

happyg

---

### Post by orev on 2005-06-22
Used this "how to" to get Canon 860i up and running well:

[http://www.ubuntuforums.org/showthread.php?t=10540&highlight=canon+i860](http://www.ubuntuforums.org/showthread.php?t=10540&highlight=canon+i860)

Had to restart system and install cups (sudo apt-get install cupsys), then had no problems.

---

### Post by mouser on 2005-08-04
I've tried that, but can't get it to work. 

Please be patient with me I am a n00b. I can't get alien to to work. when I type 

sudo alien X.rpm

It creates a file then tells me it can't find that file and the opp fails. any thoughts?

---

### Post by orev on 2005-08-04
You may have to go through and read the entire thread to get all of the juicy bits needed for everything to work properly.

What type of hardware are you running?

---

### Post by mouser on 2005-08-13
what do you mean? I have a canon i860 as far as the printer goes. I did read the entire thread. My prob is with alien. i've never been able to get it to work properly.

---

### Post by ahildoer on 2005-11-10
I modified a script that was originally written to install an i850. It will download the Japanese rpm drivers, convert them to deb packages, install the deb packages and setup the print queues. If the script asks for any confirmations, just type 'y'.

This script will setup a USB i860 on a debian machine.
[http://www.hildoer.com/linux/scripts/install_canon_i860.sh]("http://www.hildoer.com/linux/scripts/install_canon_i860.sh")

Run it like this:

$ sudo ./install_canon_i860.sh 

If you need to setup for a different type of connection, or if you are installing a second canon brand, usb printer, you will need to figure out the connection by running:

$ lpinfo -v

Then edit the lpadmin -v entry with one of the connections listed by lpinfo.

If you have any questions about the script, e-mail me: [ahildoer@gmail.com]("mailto:ahildoer@gmail.com")

Good luck!

-=Anthony=-

---

### Post by Carolyn62 on 2006-11-21
> This script will setup a USB i860 on a debian machine.
[http://www.hildoer.com/linux/scripts..._canon_i860.sh](http://www.hildoer.com/linux/scripts..._canon_i860.sh)


Boy, do I have 2 dumb questions. I am very new at this so please don't holler.

1. Will this work on dapper 6.06lt?

2. Where do I download it to?

Thank You,
Carolyn

---

