---
title: "Epson L3110 Scanner not working"
date: 2019-02-25
forum: Hardware
---

### Post by jurgen32 on 2019-02-25
I've bought a Epson L3110 all in one printer. Before i did this I checked whether there were drivers available on epson.com (and there are).
Why this printer you ask? Well, we live in the middel of nowhere on Madagascar, not much choice.

Anyway, after installing and (in konsole) *sane-find-scanner* I get this:
***found USB scanner (vendor=0x04b8 [EPSON], product=0x1142 [L3110 Series]) at libusb:003:008***
Then *scanimage -L*
***device `imagescan:esci:usb:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.0' is a EPSON L3110_Series*** 
However, when I open the Epson programme *imagescan* I get this:
[B][I]Cannot access EPSON L3110_Series
(esci:usb:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.0)
device busy[/I]
[/B]
I run Kubuntu 16:04, kde Plasma 5.14, kernel 4.4.0-142 with libsane 1.0.27. 

According to [http://download.ebz.epson.net/faq/linux/faq_ls_00017.html](http://download.ebz.epson.net/faq/linux/faq_ls_00017.html) This can be a solution (but it did not work):
[B][I] After Image Scan v3 or Image Scan for Linux installlation is completed,
The scanner driver may fails to start or scan. 
[/I][/B]
[B][I] When using our scanner driver, we recommend that you do the following
(Disable other SANE backends).
[/I][/B]

[LIST]
[*][B][I]Edit /etc/sane.d/dll.conf with administrator authority. 
[/I][/B] 
[*][B][I]Add '#' to the following line in the setting file.
epson2
epsonds[/I][/B] 
[/LIST]

I tried adding 
[B][I]scsi "EPSON L3118"
usb 0x04b8 0x1142[/I][/B]
in /etc/sane.d/epson2.conf
This makes xsane a little happy as it sees the scanner. But when I scan I get this message:
***failed to start scanner: error during device i/o***

I'm a bit out of ideas. Tried sudo aswell but no luck.

Hopefully someone has some bright ideas for me? 
P.s.: It might take a while for me to respond due to bad internet.

---

### Post by Volker Vohdin on 2019-03-24
I live in the Philippines and have been to Madagascar also. I bought this L3110 printer/scanner by mistake. I use Xubuntu, and there was no problem with the printer, because the standard epson L310 driver of Xubuntu handls it nicely. The scanner did not work for a long time, until I found a way:

Google "epson l3110 scanner linux"

log on to epson.com/Support/wa00821 or epson.net/linux/imagescanv3.....

Download scanner driver for Ubuntu. Untar with tar -xvaf filename. Read Read.me file in resulting folder. Start install script:

./install.sh --without-network --without-ocr-engine

Then put
 scsi "EPSON L3118"
 usb 0x04b8 0x1142
into /etc/sane.d/epson2.conf

Do not change dll.conf. Leave it intact. There has to be an "epson2" in it.

Afterwards "simple scan" and all the other scan utilities do not work. But "sudo scanimage" works.

List available options:
sudo scanimage -A > file

scan to a file:
sudo scanimage > junk

Make script:
#!/bin/bash
sudo scanimage -v --format=jpeg --mode color --resolution 300 -p > ../../Downloads/$1.jpg

That delivers the scanned images to the Downloads folder and can also be invoked from a launcher.

The scanned images have high quality, but somehow the scanner is rather slow. It takes about 5 sec before it reacts.

---

### Post by Volker Vohdin on 2019-04-03
Hi, in the meantime I have been using a different computer with this L3110 scanner. I found, that it is unnecessary to download the driver from Epson.com,
although at first sight that makes sense. But scanimage has a fitting driver built in already. So presumably the Epson driver got loaded to somewhere,
but was never activated. Also, if the -d option is used for scanimage, then scanimage is much faster.

So what has to be done is

1. put  "usb 0x04b8 0x1142"  into /etc/sane.d/epson2.conf

2. run script

#!/bin/bash
#set -o verbose
ss=$1
if [ .$ss == . ]; then
   ss=scanned
fi
echo scanning to: $ss
sudo scanimage -d epson2 -v -B --format=jpeg --mode color --resolution 300 -p > ../../Downloads/$ss.jpg

And that scans like a charm.

---

### Post by pdk-knight on 2019-05-08
Maybe this will help
went from 12.04 to 16.04 , scanner stopped working.
sane-find-scanner picked up the scanner on usb
scanimage -L could not find scanner.
My scanner details were in 
/etc/sane.d/snapscan.conf file  So you either have to find a file with those details or create one
snapscan has the line
# Benq/Acer/Vuego 3300 / 4300 *********************
usb 0x04a5 0x20b0

added snapscan as a single line to /etc/sane.d/dll.d/libsane-extras
I had the driver file from 12.04.
changed snapscan.conf  to setup the firmware.
firmware /usr/share/sane/snapscan/u176v042.bin
(this has been over a period of 2 years)

---

