---
title: "Pixma mp800 driver"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by freebooter on 2007-03-09
anyone had any luck installing this printer / scanner ?


Canon Pixma MP800

---

### Post by ramjet_1953 on 2007-03-09
I had a look around and couldn't find an open source Linux driver for this printer.

However, Turbo Print claim to support it under Linux.

Unfortunately, their drivers aren't free, but still far less than buying a new MFP.

[http://www.turboprint.info/printers.html](http://www.turboprint.info/printers.html)

Regards,
Roger :cool:

---

### Post by freebooter on 2007-03-10
hmm seems to be free for low to med resolutions then adds a watermark to anything greater unless you purchase a key.  Oh well I just want to be able to print out openoffice docs anyways :)


Thankyou

---

### Post by RaZoR1394 on 2007-07-01
Maybe you'll have some luck over here, [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu/) .

On Gentoo this printer works great with the Canon's open sourced cnijfilter package but I can't find it for Ubuntu. Another problem is that the server I would like to connect the printer to runs on Feisty amd64 (only i386 packages available).

[http://forums.gentoo.org/viewtopic-t-448354-postdays-0-postorder-asc-start-250.html](http://forums.gentoo.org/viewtopic-t-448354-postdays-0-postorder-asc-start-250.html)

So if you use cnijfilter with mp600 mode there is no need for turboprint. I guess I have to compile it from source.

---

### Post by RaZoR1394 on 2007-11-25
Has anyone made any progress with the Canon provided drivers? I want to move from Sabayon to Ubuntu because of some problems with this distro but I can't find any 64bit .deb's for Ubuntu.

---

### Post by Returner on 2008-04-19
At the moment I'm trying to get(/force;) my MP 800 to print using the mp600 driver package from the japanese site source...cannot get it to work.

Here's about what i've tried one afternoon...it's a modified script by someone using the Canon i850 printer...

[FONT="Courier New"]
# Download and install CUPS

apt-get install cupsys
apt-get install cupsys-client

# Download and install Canon's MP600 drivers

apt-get install wget 
apt-get install alien 
wget [ftp://download.canon.jp/pub/driver/bj/linux/cnijfilter-mp600-2.70-1.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/cnijfilter-mp600-2.70-1.i386.rpm)
wget [ftp://download.canon.jp/pub/driver/bj/linux/cnijfilter-common-2.70-1.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/cnijfilter-common-2.70-1.i386.rpm)
#wget [ftp://download.canon.jp/pub/driver/bj/linux/bjfiltercups-2.2-1.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfiltercups-2.2-1.i386.rpm)
alien cnijfilter-common-2.70-1.i386.rpm
# This one requires -c because it has an important postinstall script
alien -c cnijfilter-mp600-2.70-1.i386.rpm
dpkg -i cnijfilter-mp600_2.70-2_i386.deb
dpkg -i cnijfilter-common_2.70-2_i386.deb

# Create a CUPS print queue named "MP600". This queue uses the Canon
# drivers and is for high-quality output.

lpadmin					\
  -p mp600				\
  -E					\
  -v cnij-usb:/dev/usb/lp0			\
  -m canonmp600.ppd			\
  -D "Canon MP600"

[/FONT]

It all seems to work out but I just can't make a printout. 
Any Idea how to test where it's stuck?

---

### Post by Returner on 2008-04-30
Printing using the MP800 on Kubuntu:

I got good results printing at 600 dpi using the Canon S600 driver like described here:

I'm using Kubuntu, anyway this may apply to your environment:

Choose System Settings, where you can choose printer setup using CUPS,
use it in the Administrator Mode, this may be helpful.

- Connect and turn on the MP800

Add a Printer/Class, then local printer,
- then choose the "mp800"-device attached to the USB-Port <Apply>
- choose a "Canon" - "S600" and then choose the Foomatic using also Canon driver
- Choose your paper format
- Don't deny any users unless necessary
- Print the test page when you have finished configuring all the settings

_________________________________________________________________________

REM: It should also work using the IP4200 driver, which has lots of options like higher resolution, or probably the MP600 driver if listed, but anyway  I could not get any other driver to work better than the one listed above.
_________________________________________________________________________

- Returner

---

