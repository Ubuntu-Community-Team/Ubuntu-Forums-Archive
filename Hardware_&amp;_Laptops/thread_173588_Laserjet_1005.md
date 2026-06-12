---
title: "Laserjet 1005"
date: 2006-05-10
forum: Hardware &amp; Laptops
---

### Post by catflea on 2006-05-10
Ok,

I followed the instructions for installing a HP printer at 
[https://wiki.ubuntu.com/HpPrinterInstallationAndMaintenanceDapper](https://wiki.ubuntu.com/HpPrinterInstallationAndMaintenanceDapper)

my laserjet 1005 now appears in the printer list,  but HPLIP doesn't support it.  When ever I try to print it says that its been sent to the printer but nothing happens - the printer doesn't spool up or anything.

Followed the same instructions to get my deskjet 3650 going and that works fine - but I need to get new cartridges in it!

any ideas what I can do to get my laserjet working?

---

### Post by cilynx on 2006-05-10
See here:
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1005](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1005)

Don't worry about the foo2zjs stuff as you're correct in using HPLIP.

Basically what it comes down to is that your printer is dumb (I can say that, I have a Laserjet 1000).  You have to upload the firmware to it every time you reboot or it gets unplugged else it won't print.  If you send a job to it before uploading the firmware, it'll lock up and you have to un/re-plug the power to the thing to get it back.  Follow the instructions on the link above.  You should be able to find the firmware image on the Windows driver disk that came with the printer.  Good luck.

---

### Post by catflea on 2006-05-10
Thanks for that.  Bit late to try it now.  Will try and sort it out in the morning.  Will update on progress

---

### Post by catflea on 2006-05-11
Ok,   I'm still stuck!

Does anyone have any kind of walkthrough?    This is a bit irritating.  I need to print off a job application

---

### Post by David Haas on 2006-05-12
Catflea--I see that Breezy has two PPD files for the HP Laserjet 1005 at /usr/share/cups/model/foomatic-ppds/HP:
HP-LaserJet_1005-foo2zjs.ppd.gz
HP-LaserJet_1005-pbmtozjs.ppd.gz

Have you tried installing each of them (first one and then the other) with the Gnome printing manager? with Breezy, a default file seems to be selected when one selects the printer fron the list, but you can click on select driver and click through the directories (above) to select the PPD file (driver) of your choice. You can check which has been installed by looking in the directory /etc/cups/ppd. Here you should see the unzipped file listed.

David

---

### Post by eamon on 2006-06-04
I just managed to install this printer under dapper / 6.06 LTS.

First of all, install lprng using apt-get or adept. This will also remove cups, for added value.

also, remove foo2zjs using your package manager, and build foo2zjs from [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) following the instructions on that page. After doing that, powercycle your printer [so that the new firmware gets uploaded]

The tarball from there has a .ppd file in the PPD subdir. Get a simple .ps file, and try

```
sudo foomatic-rip --ppd /path/to/ppd/of/printer.ppd test.ps > /dev/usb/lp0

```
The device might be /dev/usblp0. Or it might be /dev/lp0 if you are using the parallel port.

If that doesn't print test.ps on the printer, I fear you are hosed. If it does, you now know at least how to print that job application :-) (hint: print to ps first)

The next step is to edit /etc/printcap and install a print queue.

for this, take a look at

[http://www.linuxprinting.org/lpd-doc.html](http://www.linuxprinting.org/lpd-doc.html)

and follow the instructions there.

hope this helps.

---

