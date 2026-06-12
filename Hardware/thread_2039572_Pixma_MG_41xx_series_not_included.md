---
title: "Pixma MG 41xx series not included"
date: 2012-08-09
forum: Hardware
---

### Post by Pacedeus on 2012-08-09
When I tried to install my new printer, I got offered Pixma MG31xx series, Pixma MG51xx seires, Pixma MG61xx series, but in the driver catalogue there was nowhere a Pixma41xx series. now I can only print b/w and parts of the page don't get printed at all. Is there somewhere a driver for PIXMA MG4140? I am running Ubuntu 12.04

---

### Post by Vakman on 2012-08-09
I don't think they officially support that one as in I can't seem to find a driver on their website.
You can check out [Gutenprint]("http://gimp-print.sourceforge.net/"). They might have support for your printer.

---

### Post by aikishugyo on 2012-08-09
> **Thisislaw said:**
> I don't think they officially support that one as in I can't seem to find a driver on their website.
You can check out [Gutenprint]("http://gimp-print.sourceforge.net/"). They might have support for your printer.

Yes, gutenprint has support for the MG4100 family. It needs testing, so please feel free to let us know how it works for you.

---

### Post by Vakman on 2012-08-10
> **aikishugyo said:**
> Yes, gutenprint has support for the MG4100 family. It needs testing, so please feel free to let us know how it works for you.

I thought it might, wasn't positive though. Good to know :)

---

### Post by unevenflow on 2012-08-10
Hey first remove your printer and then try installing from this ppa
**sudo add-apt-repository ppa:michael-gruz/canon**
**sudo apt-get update**
**sudo apt-get install cnijfilter-mg4140series**
then from the cog thingie add your printer again and when it'll ask for the driver location navigate to **usr/share/ppd/** and search for ...4140.ppd if its there click it and try printing.

---

### Post by pdc on 2012-08-10
Canon **_DO PROVIDE_** a driver for the 4100 series;

I usually go the "canon asia" website, downloads section and ...........hey presto...................there it all is !!!!!!!!!!!!!!!!

they package the driver for the 4100 series as rpm or .deb or the source file;

so going here

[http://support-sg.canon-asia.com/contents/SG/EN/0100395002.html](http://support-sg.canon-asia.com/contents/SG/EN/0100395002.html)

should give you the link to download the driver;

I recently installed a 3100 series driver (.deb); it all worked well

with a GUI one can download to a Downloads directory; it is likely in .tar.gz form but it should open with a click into two folders: packages and resources;

and an install.sh script; Clicking on the latter should offer a "run" option and clicking should allow it to run and install: the installer should detect that you are using .deb and whether you are using a 32bit or 64bit system

---

### Post by Vakman on 2012-08-11
> **pdc said:**
> Canon **_DO PROVIDE_** a driver for the 4100 series;

I usually go the "canon asia" website, downloads section and ...........hey presto...................there it all is !!!!!!!!!!!!!!!!

they package the driver for the 4100 series as rpm or .deb or the source file;

so going here

[http://support-sg.canon-asia.com/contents/SG/EN/0100395002.html](http://support-sg.canon-asia.com/contents/SG/EN/0100395002.html)

should give you the link to download the driver;

I recently installed a 3100 series driver (.deb); it all worked well

with a GUI one can download to a Downloads directory; it is likely in .tar.gz form but it should open with a click into two folders: packages and resources;

and an install.sh script; Clicking on the latter should offer a "run" option and clicking should allow it to run and install: the installer should detect that you are using .deb and whether you are using a 32bit or 64bit system

Very nice. Do this :).

---

### Post by Pacedeus on 2012-08-19
Hi pdc,
that was so great, what you said. the only negativ part is, that the driver is for Ubuntu 10.10 and I am running Ubuntu 12.04. Is there a way to update that driver? Had a very busy week, that's why I come back so late.
Pacedeus

---

### Post by Pacedeus on 2012-08-19
Hi unevenflow,
I get the error: **cnijfilter-mg4140series **cannot be found.Your tip doesn't work either. even installing the stuff you mentioned comes with Errors for packages not found.

---

### Post by unevenflow on 2012-08-19
Hi, so sorry i made a mistake the correct ppa is
**sudo add-apt-repository ****ppa:michael-gruz/canon-trunk**
**sudo apt-get update**
**sudo apt-get install cnijfilter-mg4140series**
or
[B]sudo apt-get install cnijfilter-mg4140series
[/B]then from the cog thingie add your printer again and when it'll ask for the driver location navigate to **usr/share/ppd/** and search for ...4140.ppd if its there click it and try printing.
Please post back the results.

---

### Post by Pacedeus on 2012-08-20
Hi unevenflow,
the mg4140series did not work either, but the mg4100series worked fine. Printer is now installed and prints fine.

---

### Post by Vakman on 2012-08-20
> **Pacedeus said:**
> Hi unevenflow,
the mg4140series did not work either, but the mg4100series worked fine. Printer is now installed and prints fine.

Good to hear! Please mark the thread as solved if all is well.

---

### Post by pdc on 2012-08-25
good that the printer is working

>  *the driver is for Ubuntu 10.10 and I am running Ubuntu 12.04.*

........that has got to be wrong............ where did you get that from..

---

