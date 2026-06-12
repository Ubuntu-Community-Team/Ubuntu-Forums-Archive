---
title: "Trying to get P-Touch label printer working"
date: 2011-09-03
forum: Hardware
---

### Post by PM47 on 2011-09-03
I'm running Ubuntu 10.10 (Maverick Meercat).

I have a Brother P-Touch 2420PC label printer which is not directly supported. I've installed the supported Brother PT1500 drivers through Synaptic, the driver works, the printer is online, I can print from various apps and the print que briefly shows the output is working, but the printer itself refuses to print, the front LED flashes indicating the wrong tape is inserted.

I've contacted Brother and they inform me this is due to differences between the 1500 and 2420 printers, they can't (won't) help as the 2420 is obsolete 

I've tried installing the Brother Windoze apps in Wine, the label editor can't see the driver, the driver can't see the printer

I've found a third party P-Touch printer driver that has been tested with the 2420 here :

[http://etc.nkadesign.com/Printers/QL550LabelPrinterCUPS?setskin=glossyhue](http://etc.nkadesign.com/Printers/QL550LabelPrinterCUPS?setskin=glossyhue)

I'm reasonably familiar with programming microprocessors but not PCs. I've downloaded the Vn1.2 source tarball, which is for Fedora Core 6, hoping I may be able to get it to work with Ubuntu. Following the instructions, I can extract the files Ok, the ./configure command is Ok but the Make command throws up an error as follows :

paul@Doris:~/Downloads/ptouch-driver-1.2$ make
make all-am
make[1]: Entering directory `/home/paul/Downloads/ptouch-driver-1.2'
if gcc -DHAVE_CONFIG_H -I. -I. -I. -D_GNU_SOURCE -g -O2 -MT rastertoptch-rastertoptch.o -MD -MP -MF ".deps/rastertoptch-rastertoptch.Tpo" -c -o rastertoptch-rastertoptch.o `test -f 'rastertoptch.c' || echo './'`rastertoptch.c; \
then mv -f ".deps/rastertoptch-rastertoptch.Tpo" ".deps/rastertoptch-rastertoptch.Po"; else rm -f ".deps/rastertoptch-rastertoptch.Tpo"; exit 1; fi
rastertoptch.c:312: fatal error: cups/raster.h: No such file or directory
compilation terminated.
make[1]: *** [rastertoptch-rastertoptch.o] Error 1
make[1]: Leaving directory `/home/paul/Downloads/ptouch-driver-1.2'
make: *** [all] Error 2

As far as I can see the cups/raster.h file is missing, or located elsewhere. 

Any chance some-one may be able to give me some guidance on possibly getting this driver installed please ??

Thanks
Paul

---

### Post by royleith on 2012-06-08
Just an unhelpful reply! I have a P-Touch 1500 and it fails with the flashing power light in the same way that yours does. 

The self test also fails.

I changed the 'Page Size' setting to 9mm and used 9mm tape. I might try restoring the setting to 22mm and using 22mm tape. I'll be back if I have any success.

Regards
Roy Leith

---

### Post by royleith on 2012-06-08
As threatened, I tried it with 24 mm tape and with Scribus and Kate, with the printer settings set to 24 mm, selecting portrait and landscape and making sure the contents fitted well within the tape.

In all cases, the printer power light flashed a few seconds after the 'System Tray' printer icon closed.

'Print Test Page' failed in the same way. That is not surprising as it is about A4 in size!

'Print Self Test' failed, but I do not remember anything of the sort in Windows.

I think the driver has a problem. I suspect that, if it can be corrected, then most USB connected P-Touch printers would work.

I hope it gets sorted. You don't know how silly it feels to boot up my slow old Windows installation to print out a few centimetres of label.

Regards
Roy Leith

Kubuntu 12.04 with recently updated P-Touch driver

---

### Post by PM47 on 2012-06-08
I never did get the 2420 working in Ubuntu. I have two or three Windoze apps that I've not found a decent equivalent for in Ubuntu so I've installed VirtualBox and loaded a minimal WinXP install for these and the Brother label printer software. Not ideal, but at least I don't have to boot up anything else just to print a label :-)

Paul

---

