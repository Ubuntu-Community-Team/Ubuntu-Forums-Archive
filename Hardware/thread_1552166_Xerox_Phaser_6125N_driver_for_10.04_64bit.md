---
title: "Xerox Phaser 6125N driver for 10.04 64bit"
date: 2010-08-13
forum: Hardware
---

### Post by RayVad on 2010-08-13
The following was found on [http://zoffix.com/other/Installing-Dell-1320c-Color-Laser-Printer-on-Ubuntu]("http://zoffix.com/other/Installing-Dell-1320c-Color-Laser-Printer-on-Ubuntu") and share it with you on this forum.
It is working for me on Ubuntu Lucid Lynx 10.04.

I ran into a forum thread that claimed that my precious printer will work with Fuji Xerox Docuprint C525 driver. Fuji's site only offered a 32-bit RPM, which you can download and convert into .deb yourself if you really want to.

Unfortunately, I had an amd64 system and alien command refused to convert it into a DEB package. I asked someone online to do that for me. Result: a 32-bit DEB package for the Fuji driver.

Download the Fuji's 32-bit RPM file and convert it yourself or use my 32-bit DEB that is already converted [http://http://zoffix.com/content-pics/dell_printer/fuji-xerox-docuprint-c525-a-ap_1.0-2_i386.deb]("http://http://zoffix.com/content-pics/dell_printer/fuji-xerox-docuprint-c525-a-ap_1.0-2_i386.deb")

Install it: sudo dpkg -i --force-architecture fuji-xerox-docuprint-c525-a-ap_1.0-2_i386.deb (the --force-architecture bit is not needed if you're running 32-bit system)

Go to System->Administration->Printing (or whatever it is if you're using KDE) and add your 1320c printer. You may have the Fuji driver in the list, but I did not have it. What I did is chose "Provide PPD file" and pointed it to /usr/share/cups/model/FujiXerox/en/FX_DocuPrint_C525_A_AP.ppd.

Now, feel free to tweak the settings to whatever you want (and what works). By default my printer was crying for different paper. This is what I have set (other options were left at default)

[IMG]http://zoffix.com/content-pics/dell_printer/dell_printer_options.jpg[/IMG]

---

### Post by jeremyellman on 2010-09-18
Worked like a charm. Thanks for posting

Jeremy

---

### Post by jan9850 on 2010-11-13
Very helpful, working fine, tks

---

### Post by zig1 on 2011-03-22
Hi,

I was trying to download the package for:  fuji-xerox-docuprint-c525-a-ap_1.0-2_i386.deb on the url: [http://http://zoffix.com/content-pic...1.0-2_i386.deb](http://http://zoffix.com/content-pic...1.0-2_i386.deb)

The file isn't there anymore. Does anyone still have it or can you convert the rpm on a 64-bit system in ubuntu 10.10

Alien doesn't work for me.

Best Regards,

Zig1

---

### Post by markosjal on 2012-04-12
deb package here [http://teknogeekz.com/blog/?p=367](http://teknogeekz.com/blog/?p=367)

---

### Post by zig1 on 2012-04-12
Thank you :-)

---

### Post by markosjal on 2012-04-22
Zig1
surpised you still needed it after a year!

---

### Post by jaxån on 2013-01-27
Ok, here is how to build a 64 bit version of this.  I uses multi-arch to support.

Download the rpm-file from here: 
[http://onlinesupport.fujixerox.com/]("http://onlinesupport.fujixerox.com/tiles/common/hc_drivers_download.jsp?system='Linux'&shortdesc=null&xcrealpath=http://www.fujixeroxprinters.com/downloads/uploaded/dpc525a_linux_.0.0.tar_81c2.zip")

[FONT="Courier New"][SIZE="2"]$ mkdir ~/XP-6125N
$ cd ~/XP-6125N
$ url -# -o dpc525a_linux_.0.0.tar_81c2.zip \
"http://onlinesupport.fujixerox.com/tiles/common/hc_drivers_download.jsp?system='Linux'&shortdesc=null&xcrealpath=http://www.fujixeroxprinters.com/downloads/uploaded/dpc525a_linux_.0.0.tar_81c2.zip"
$ # Install multi-arch support for libcups2:i386
$ sudo apt-get install libcups2:i386
$ # Unpack rpm-package using alien
$ fakeroot alien -g Fuji_Xerox-DocuPrint_C525_A_AP-1.0-1.i386.rpm 
$ cd Fuji_Xerox-DocuPrint_C525_A_AP-1.0
$ # Change #Architecture: i386" to "Architecture: amd64"
$ #  in debian/control
$ sed -i -e s/i386/amd64/ debian/control
$ # Create package and install it
$ fakeroot ./debian/rules binary
$ sudo dpkg -i ../fuji-xerox-docuprint-c525-a-ap_1.0-2_amd64.deb 
[/SIZE][/FONT]
Happy printing.

---

