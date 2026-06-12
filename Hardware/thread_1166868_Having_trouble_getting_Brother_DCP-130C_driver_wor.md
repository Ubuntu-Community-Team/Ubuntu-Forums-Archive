---
title: "Having trouble getting Brother DCP-130C driver working"
date: 2009-05-22
forum: Hardware
---

### Post by chrisbay90 on 2009-05-22
Hi,

I have a Brother DCP-130C printer and am trying to get it installed and running on Ubuntu.

The printer isn't listed under the default database that pops up when Ubuntu detects a new printer.

I found some linux drivers on the brother website. [http://solutions.brother.com/linux/en_us/download_prn.html#DCP-130C](http://solutions.brother.com/linux/en_us/download_prn.html#DCP-130C)

I downloaded the deb files (as opposed to rpm) which i believe is right, yes/no?

Had no luck installing them myself.

I then followed this tutorial howto [http://ubuntuforums.org/showthread.php?t=71104](http://ubuntuforums.org/showthread.php?t=71104)

with a little more luck, but still got some errors.

```
sudo dpkg -i DCP130lrp.deb
```produced this error
```
mkdir: cannot create directory `/var/spool/lpd/dcp130c': No such file or directory
chown: cannot access `/var/spool/lpd/dcp130c': No such file or directory
chgrp: cannot access `/var/spool/lpd/dcp130c': No such file or directory
chmod: cannot access `/var/spool/lpd/dcp130c': No such file or directory

```and
```
sudo dpkg -i DCP130lrp.deb
```this error
```
/usr/local/Brother/Printer/dcp130c/cupswrapper/cupswrapperdcp130c: 70: cannot create /usr/share/cups/model/brdcp130c.ppd: Directory nonexistent
/usr/local/Brother/Printer/dcp130c/cupswrapper/cupswrapperdcp130c: 274: cannot create /usr/share/cups/model/brdcp130c.ppd: Directory nonexistent
chmod: cannot access `/usr/share/cups/model/brdcp130c.ppd': No such file or directory
cp: cannot stat `/usr/share/cups/model/brdcp130c.ppd': No such file or directory
chmod: cannot access `/usr/share/ppd/brdcp130c.ppd': No such file or directory
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
lpadmin: Unable to copy PPD file!

```Any help or insight you can give would be greatly appreciated.

---

### Post by TopEnder on 2009-05-23
> **chrisbay90 said:**
> Hi,

I have a Brother DCP-130C printer and am trying to get it installed and running on Ubuntu.

The printer isn't listed under the default database that pops up when Ubuntu detects a new printer.

I found some linux drivers on the brother website. [http://solutions.brother.com/linux/en_us/download_prn.html#DCP-130C](http://solutions.brother.com/linux/en_us/download_prn.html#DCP-130C)

I downloaded the deb files (as opposed to rpm) which i believe is right, yes/no?

Had no luck installing them myself.

I then followed this tutorial howto [http://ubuntuforums.org/showthread.php?t=71104](http://ubuntuforums.org/showthread.php?t=71104)

with a little more luck, but still got some errors.

```
sudo dpkg -i DCP130lrp.deb
```produced this error
```
mkdir: cannot create directory `/var/spool/lpd/dcp130c': No such file or directory
chown: cannot access `/var/spool/lpd/dcp130c': No such file or directory
chgrp: cannot access `/var/spool/lpd/dcp130c': No such file or directory
chmod: cannot access `/var/spool/lpd/dcp130c': No such file or directory

```and
```
sudo dpkg -i DCP130lrp.deb
```this error
```
/usr/local/Brother/Printer/dcp130c/cupswrapper/cupswrapperdcp130c: 70: cannot create /usr/share/cups/model/brdcp130c.ppd: Directory nonexistent
/usr/local/Brother/Printer/dcp130c/cupswrapper/cupswrapperdcp130c: 274: cannot create /usr/share/cups/model/brdcp130c.ppd: Directory nonexistent
chmod: cannot access `/usr/share/cups/model/brdcp130c.ppd': No such file or directory
cp: cannot stat `/usr/share/cups/model/brdcp130c.ppd': No such file or directory
chmod: cannot access `/usr/share/ppd/brdcp130c.ppd': No such file or directory
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
lpadmin: Unable to copy PPD file!

```Any help or insight you can give would be greatly appreciated.
chrisbay90, you did not menion what version of Ubuntu you are using, you shoukld be able to down load the drivers/packages from Synaptic Package Manager located in System/Administration/Synaptic Package Manager, just to a search for DCP_130C, packages you are lookin for are: [COLOR="Blue"]brother-cups-wrapper-bh7[/COLOR] and [COLOR="Blue"]brothe-lpr-drivers-bh7[/COLOR]  install these packages and hopefully your DCP-130C printer will work to install the Scanner corectly it will depend on what version of Ubuntu you are using.  The turtorial yuo use is getting a little long in the tooth for recent versions of Ubuntu.  May I suggest you read the Post by [COLOR="Blue"]BroadDWorld Poll:  HOWTO: Ubuntu All Brother Printer & Scanner Driver Installation for Newbies![/COLOR] there are many threads but it's worth the read to help you understand about Brother multi-functions printers.  TopEnder

---

### Post by Frantic_Earthling on 2009-05-23
I think that TopEnder's advice probably gives the safest way to install your printer but if you still want to go with Brother's Linux drivers (which I do myself), please note that you must install first the LPR driver, then the CUPS WRAPPER driver, in that order. Failure to do this generates errors.

Then, from your favorite web navigator, type "localhost:631". This gives you access to the Common UNIX Printing System. Click "Add Printer" and follow the install procedure.

---

### Post by chrisbay90 on 2009-05-23
> **TopEnder said:**
> you shoukld be able to down load the drivers/packages from Synaptic Package Manager located in System/Administration/Synaptic Package Manager, just to a search for DCP_130C, packages you are lookin for are: [COLOR=Blue]brother-cups-wrapper-bh7[/COLOR] and [COLOR=Blue]brothe-lpr-drivers-bh7[/COLOR]  install these packages and hopefully your DCP-130C printer will work
Thank you. That worked perfectly.

> **TopEnder said:**
> you did not menion what version of Ubuntu you are using
Ubuntu 9.04
Everything works fine now but I thought i would add it incase someone else comes along with the same problem.



That other HOWTO seems very promising in getting the scanner working.

Again thank you very much.

---

### Post by chrisbay90 on 2009-05-26
> **Frantic_Earthling said:**
> I think that TopEnder's advice probably gives the safest way to install your printer but if you still want to go with Brother's Linux drivers (which I do myself), please note that you must install first the LPR driver, then the CUPS WRAPPER driver, in that order. Failure to do this generates errors.

Then, from your favorite web navigator, type "localhost:631". This gives you access to the Common UNIX Printing System. Click "Add Printer" and follow the install procedure.

Thanx for the advice Frantic_Earthling. I'v tried that, but it just doesnt seem to work for me. I do have it working now though, using TopEnder's advice. Thanx for the tip about the ocalhost:631 CUPS web interface, its been EXTREMLY usefull and have been using it since.

---

### Post by babyfoxx on 2009-12-11
Thank you! Thank you! Thank you! Worked for me also!
:popcorn:

---

