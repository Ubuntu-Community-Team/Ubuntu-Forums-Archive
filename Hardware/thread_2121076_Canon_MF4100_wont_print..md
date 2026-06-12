---
title: "Canon MF4100 wont print."
date: 2013-02-28
forum: Hardware
---

### Post by vasilenko93 on 2013-02-28
I installed the driver from the official website (64-bit version) and Ubuntu detected and added the printer right away. Also I am able to use SimpleScan with the printer, so it is connected and works. But when I try to print something the print queue says "Stopped - Printer configuration error" and the printer state becomes "Idle - File "/usr/lib/cups/filter/pstoufr2cpca" not available: No such file or directory"

Driver link [http://support-au.canon.com.au/contents/AU/EN/0100270808.html](http://support-au.canon.com.au/contents/AU/EN/0100270808.html)

Any thoughts, ideas?

---

### Post by pdc on 2013-03-01
this post offers an answer.......

[https://phpraxis.wordpress.com/2012/07/08/install-canon-mf4350-cups-printer-drivers-in-64-bit-ubuntu-linux/](https://phpraxis.wordpress.com/2012/07/08/install-canon-mf4350-cups-printer-drivers-in-64-bit-ubuntu-linux/)

........ you need a symbolic link to tell your system where to the find the missing file

> [COLOR="#FF0000"]sudo ln -s /usr/lib64/cups/filter/pstoufr2cpca /usr/lib/cups/filter/pstoufr2cpca[/COLOR]

---

### Post by vasilenko93 on 2013-03-01
The error is gone, however printing is not back. Now the printer state always says "Idle - Sending data to printer."

---

### Post by pdc on 2013-03-01
there are recurrent issues with 64bit systems; and printers;

some options:
1) install a 32bit system; see no difference in speed etc and have the printer working well
2) stick with 64bit and attempt to resolve: this wiki [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) is something to work through; there seem no easy options; we would all love to give the immediate answer; apart from a 32bit system......... there doesn't seem to be one.....I guess one could run a 32bit system as a virtual install inside a 64bit..........

---

### Post by speedygarth on 2013-03-04
Try [h=3]A native 64-bit driver package is now available![/h]
[LIST]
[*]The only real solution is to install the native 64-bit drivers, but unfortunately Canon only provides 32-bit DEB packages.

[*]After a lot of experimentation and a borrowed Canon MF4350dn all-in-one, I've managed to build the drivers *and* get them to work. They are available [in a PPA]("https://launchpad.net/~auanswers/+archive/canon64/").
[/LIST]
[h=3]How to install:[/h]
[LIST]
[*]**Important:** you must first install the libxml2:i386 package (which pulls in the 32-bit libc6 and zlib packages which are also needed). This manual step is necessary because the alternative is to force people to install the 250 MB+ ia32-libs package.

[*]Start by opening a terminal and typing:

sudo apt-get install libxml2:i386
[*]Add the PPA with:

sudo apt-add-repository ppa:auanswers/canon64
[*]Update with sudo apt-get update

[*]Install the North American version:

sudo apt-get install cndrvcups-ufr2-usor the European version

sudo apt-get install cndrvcups-ufr2-uk
[*]Make sure your printer's device in *Settings...Printing* is the cnusb: device:
[IMG]http://i.stack.imgur.com/0A71M.png[/IMG]
[IMG]http://i.stack.imgur.com/mJs4h.png[/IMG]
[/LIST]
[HR][/HR][COLOR=#333333][FONT=Ubuntu Beta]**Help! I got a warning, installation failed, now what!?**[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta][IMG]http://i.stack.imgur.com/glB86.png[/IMG][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]This just means you forgot to install the i386 dependencies. Type [/FONT][/COLOR]sudo apt-get install libc:i386 zlib1g:i386 libxml2:i386[COLOR=#333333][FONT=Ubuntu Beta], and then try again with [/FONT][/COLOR]sudo apt-get install cndrvcups-ufr2-us[COLOR=#333333][FONT=Ubuntu Beta] (or [/FONT][/COLOR]-uk[COLOR=#333333][FONT=Ubuntu Beta])[/FONT][/COLOR] these steps

---

### Post by Frank_Rotte on 2014-03-03
I'm really having trouble with this. I downloded the drivers from Canon, but I'm just not getting this. If someone could post step by step from Canon download to the end, I would really appreciate it. Total newb, but trying. Thanks.

---

### Post by pdc on 2014-03-03
which version of ubuntu are you using please; 

32 or 64bit?

have you downloaded the UFR 2.8 driver?

eg from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html)

---

### Post by Frank_Rotte on 2014-03-03
12.04 LTS 64bit I'll download that driver now

---

### Post by Frank_Rotte on 2014-03-03
I installed UFR 2.8 driver. But it said I need to uninstall ufr2-uk and ufr2-us first. How do I uninstall?

---

### Post by pdc on 2014-03-03
If you copy and paste this command

> sudo dpkg -l | grep cndrvcups

...........can you copy and paste back here what the result is .....

_______________________________________________________________

to delete the UFR the commands are

> sudo dpkg -P cndrvcups-common

and then


> sudo dpkg -P cndrvcups-ufr2

_____________________________________________________________


Canon have now issued a 2.8 for the UFR: 

if one downloads that to a Downloads directory the command would be

> cd Downloads

> tar -zxvf Linux_UFRII_PrinterDriver_V280_uk_EN.tar.gz

> cd Linux_UFRII_PrinterDriver_V280_uk_EN/64-bit_Driver/Debian

> sudo dpkg -i cndrvcups-common_2.80-1_amd64.deb

> sudo dpkg -i cndrvcups-ufr2-uk_2.80-1_amd64.deb

____________________

I meant to send this earlier: delay in despatching

---

