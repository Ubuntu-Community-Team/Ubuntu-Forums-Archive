---
title: "Laserprinter ML 1610"
date: 2005-10-21
forum: Hardware &amp; Laptops
---

### Post by Skerit on 2005-10-21
I recently bought a laserprinter, a few weeks ago, and I installed ubuntu 1 week later. I'm quite happy with it and all but that's another story.

Anyway, when I have to install the driver for the printer I have to install the drivers for the 1510 printer. Everything works fine, it can print documents with ease, but when I tried to print a document that contains an image it just .. does not work.

What can be the problem here?

Oh, and a little question on the side; I couldn't wait for ubuntu breezy badger final so I installed the latest RC, did it already update itself to the correct release or do I have to do a distro upgrade or do I have to download the dvd again?

---

### Post by aysiu on 2005-10-22
ML... is this a Samsung printer? I went to the Samsung website, and they don't have a 1610. They have 1710. Well, if it's Samsung, their website has a whole bunch of Linux printer drivers. If it's not Samsung, what is it?

As for the updated version. If you have the RC and you ```
sudo apt-get update
sudo apt-get upgrade
``` you have the same as the official release of Breezy.

---

### Post by Skerit on 2005-10-22
Oh, well then I have the latest version, have done anough updates now

Anyway, it is a samsung printer and ubuntu has it's own drivers for it (the exact same printer, the exact number) but when I use them and I try to print anything, the "on-line" led jus starts flashing like it's gonna print and then .. it stops, does nothing
Anyway, I'll try some more using other drivers

---

### Post by Tore Van Grembergen on 2006-01-04
yesterday I bought the same samsung printer. (ML 1610)
As mentioned above it does not work correctly with the delivered drivers (e.g. 1410 or 1510)  within UBUNTU. (works for text, but not for graphics)

I found the driver for the ML 1610 on the [www.samsung.be]("http://www.samsung.be") website.
I suppose one can also find it on the [www.samsung.com]("http://www.samsung.com") website.

I just ran the installation program, as described in the documentation that goes with it, and everything worked fine. 

It adds the printer to your cups printers.

After installation I was able to print text and graphics with this printer.


Kind regards

Tore

---

### Post by cvmostert on 2006-01-18
[QUOTE=Tore Van Grembergen]yesterday I bought the same samsung printer. (ML 1610)
As mentioned above it does not work correctly with the delivered drivers (e.g. 1410 or 1510)  within UBUNTU. (works for text, but not for graphics)

I found the driver for the ML 1610 on the [www.samsung.be]("http://www.samsung.be") website.
I suppose one can also find it on the [www.samsung.com]("http://www.samsung.com") website.

I just ran the installation program, as described in the documentation that goes with it, and everything worked fine. 

It adds the printer to your cups printers.

After installation I was able to print text and graphics with this printer.


Kind regards

Tore[/QUOTE]


i bought the same printer yesterday but can not add printer with the samsung software... using 1510 drivers from ubuntu now... :-(

when i want to add printer, im asked the administrator password... then i geve root and the password... 

authentication failed!

what could be wrong?

---

### Post by cvmostert on 2006-01-20
HI, it took me a while to get to the right place but this link helped me install the application on gnome... now i have trouble with kde...

[http://www.ubuntuforums.org/showthread.php?t=31796]("http://www.ubuntuforums.org/showthread.php?t=31796")

---

### Post by Frenchy on 2006-02-27
Cvmostert, I went there and followed the instructions and it still didn't work.  I ended up just using the 1510 driver from the foomatic-filters-ppds package.  Works great.  I uninstalled the Samsung Printer software and it's still going strong.

---

### Post by zolly on 2006-04-27
yes, this printer works with ML-1510 driver from Ubuntu Dapper, with text and
graphics.

---

### Post by cvmostert on 2006-04-29
i upgraded to dapper and now have trouble again using 1610 drivers, but you are right.. 1510 works in dapper. thanx

---

### Post by lepre on 2006-06-12
i bought this printer too 2 days ago, i'm trying to install it on xubuntu 6.06 ...i'm using the cd-rom and after the installation i can't get the "linux-config" program to work. without any error message.

---

### Post by luisg on 2006-08-03
Just to confirm, Samsung ML-1610 works very well in Ubuntu 5.10 with ML-1510 driver.

Samsung CD or external driver not needed at all.

---

### Post by recupero on 2006-08-30
although this is ubuntu 5.10, I'm talking about dapper here.
Yes, the printer is printing, but only html or pdf.
lpr  reports :
lpr: Could not initialize LPP printing system

---

### Post by thymian on 2006-09-05
I had to do it twice once with Breezy Badger and right now again with Dapper Drake.

The procedure is straight forward:

$ sudo passwd root
Password: notasecret
$ cd Desktop/Samsung\ ML-1610/image/
$ su -c './setup.sh'

You can also add the supplied ppd via the add printer dialog later, either of which is at your preference:

$ sudo cp ppd/C/ML-1610spl2.ppd /usr/share/cups/model/custom/

Now add a new printer under System/Administration/Printers and select the printer driver which gets sorted way down as 'Samsung ML-1610 Series (SPL II)' after installation.

Remove the password which is notasecret and lock the root account again.

$ sudo -l root

Enjoy printing.

---

### Post by timosa on 2006-09-13
I tried both gdi and the official Samsung driver in Ubuntu 6.06. The first one didn't print images and the second one didn't work at all. Then I compiled splix driver (0.0.1) and it printed everything. However there was some problems with margins and installation. When installing the /usr/share/ppd/.../samsung directory must exist.

I don't recommendate anyone to buy Samsung ML-1610 before splix driver is mature enough.

---

### Post by pingvin on 2006-09-27
Hi,

I bought the same printer a couple of months ago, and was able to print text fine with Fedora Core 5, SuSE 10.1 and Ubuntu Dapper. However, graphics made all distros come unstuck. So far, the best way round seems to be this fairly convoluted idea:
I installed the Samsung ML-1610 on the USB port with the ML-1710 driver (works for text, as this driver already converts all text to PostScript). Then I installed another printer on the same machine - this time on the network port IPP (or HTTP port 631) - and installed PostScript driver for it. This is my default printer, so basically it converts everything I print to PostScript Level 1, then passes it to 127.0.0.1 (like I said, it's convoluted, but it works!), which puts it through to the USB port using the ML-1710 ubuntu driver. Now - text, graphics, even full page photos - no probs.

Hope this helps - if nothing else, it means you don't have to install any additional software.

Mike

---

### Post by chris rowan on 2006-10-03
my 1610 is a network printer on a windows machine. I am using a 1510 driver and i can print text ok. If I try and print graphics, windows pc throws up an 'insufficient memory' message. theres enough memory if i print from the pc. anyone solved this yet?

---

### Post by chris rowan on 2006-10-04
succeeded! For anyone else who wants to know -

I downloaded the driver from the samsung site. Couldnt figure out how to rum the installation prog but noticed this line in the autorun file: 

exec sh $BASE/Linux/install.sh

typed it into a root terminal and hey presto!

tried to install the printer locally but always got a 'printer job stopped' message when trying to print. However at this stage the driver was installed and it was straightforward to install as a network printer through system-admin-printers and simply select the appropriate driver.

Hope this helps someone .....

---

### Post by Peter Sommer-Larsen on 2006-11-07
Hi..

I cant get my "Samsung ML-1610" too work on Ubuntu Edgy.
I have downloaded a driver from samsungs homepage, but
when im trying to install it, I get this error

./Linux/install.sh: 1230: source: not found
ERROR: HARDWARE_PLATFORM undefined, execution aborted

Im running XUbuntu (xfce4)

Please help..

Peter

---

### Post by lepre on 2006-11-07
you must install it in CUPS.
run your browser @ [http://localhost:631/](http://localhost:631/)
select add printer and follow instruction.
remeber to say to cups that the printer is a ML1510, otherwise ti won't work.

---

