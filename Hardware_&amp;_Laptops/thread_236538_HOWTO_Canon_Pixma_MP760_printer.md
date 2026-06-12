---
title: "HOWTO: Canon Pixma MP760 printer"
date: 2006-08-14
forum: Hardware &amp; Laptops
---

### Post by jdpipe on 2006-08-14
Here are the steps I used to get the Canon Pixma MP760 printer working with Ubuntu 6.06. I was able to get single-sided printing support, but not duplex at this stage.

First, install some libraries that the Canon drivers need, and set up some naughty symbolic links:

```
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
apt-get install libpng3 libxml1
sudo ln -s /usr/lib/libpng.so.3 /usr/lib/libpng.so.2
```

(note that these commands are naughty and could quite easily cause problems with printing in some cases. It would be better to go and get the correct versions of libtiff and libpng, I presume. Not sure if the version numbers .3 and .2 are particular to RPM-based linuces, or apply to all linux including Debian/Ubuntu).

Next, download the RPM packages and convert them to DEB packages, then install the packages.

```

sudo apt-get install alien
wget ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-common-2.50-2.i386.rpm
sudo alien bjfilter-common-2.50-2.i386.rpm
wget ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-pixusip4100-2.50-2.i386.rpm
sudo alien --scripts bjfilter-pixusip4100-2.50-2.i386.rpm

sudo dpkg -i bjfilter-common_2.50-3_i386.deb
sudo dpkg -i bjfilter-pixusip4100_2.50-3_i386.deb
sudo /etc/init.d/cupsys restart
```

Next, add the printer using the GNOME interface:
[LIST]
[*]System menu -> Administration -> Printing
[*]Add Printer
[*]Select "PiXUS IP 4100 Ver 2.50"
[*](new printer appears in the Printers folder)
[*]Right-click, select Properties
[*]Print a Test Page
[/LIST]

I was also able to print a multi-page PDF document from Evince with no problems.

Note the closely related thread at
[http://www.ubuntuforums.org/showthread.php?t=204853](http://www.ubuntuforums.org/showthread.php?t=204853)

Also note that according to the Gentoo Wiki, this printer driver also supports the following other Canon printers:
[LIST]
[*]i860
[*]i865 
[*]ip4000
[*]ip4100
[*]ip5000
[*]mp750
[*]mp760
[*]mp770
[*]mp780
[*]mp790
[/LIST]

[http://gentoo-wiki.com/Canon_pixma_series](http://gentoo-wiki.com/Canon_pixma_series)

---

### Post by pdunn on 2006-09-14
sudo apt-get install alien
wget [ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-common-2.50-2.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-common-2.50-2.i386.rpm)
sudo alien bjfilter-common-2.50-2.i386.rpm
wget [ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-pixusip4100-2.50-2.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-pixusip4100-2.50-2.i386.rpm)
sudo alien --scripts bjfilter-pixusip4100-2.50-2.i386.rpm

sudo dpkg -i bjfilter-common_2.50-3_i386.deb

#This line needs to be added.
sudo dpkg -i bjfilter-pixusip4100_2.50-3_i386.deb

sudo /etc/init.d/cupsys restart

---

### Post by jdpipe on 2008-02-02
In Ubuntu 7.10, there is now a package bjfilter-2.5 that appears to offer the necessary drivers, so I believe that the above approach is no longer required.

---

