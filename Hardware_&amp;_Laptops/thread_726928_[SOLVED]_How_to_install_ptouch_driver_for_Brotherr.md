---
title: "[SOLVED] How to install ptouch driver for Brotherr QL-500"
date: 2008-03-17
forum: Hardware &amp; Laptops
---

### Post by debian-potato on 2008-03-17
I just bought a QL-500 thermal label printer from Brother. It is supported by the ptouch driver according to linuxprinting.org (I have no wish to use binary-only drivers).

I downloaded the driver as well as the two debs needed (libcupsys2-dev and libcupsimage2-dev) and built the driver.

After the configure;make;;make install; dance I tried making the ppd file using:
foomatic-ppdfile -p Brother-QL-500 > ql-500.ppd

but I get the error
ERROR: foomatic-ppdfile: Printer 'Brother-QL-500' and driver 'ptouch' are not compatible
ERROR: foomatic-ppdfile: Driver 'ptouch' not in database!

---

### Post by debian-potato on 2008-03-18
Solved by removing all existing setup on Ubunty Gutsy 7.10

dpkg -r --force-depends cupsys foomatic-db

and deleting printer entries in /etc/cups/*.conf

then apt-get -f install foomatic-db cupsys
then sudo aa-complain cupsd
/etc/init.d/cupsys restart

then as root unpacking ptouch*.tar.gz and doing 
./configure --prefix=/usr/share
make clean; make && make install

Then I used the KDE interface to setup the printer.
However, it also automatically set itself up too!
The automatic process even chose the right paper size.

W00t!

---

### Post by squeakyfrommage on 2008-04-29
I had the same problem and in my case all I needed to do was copy (I imagine symlink would work as well) the actual driver (ptouch.xml) to /usr/share/foomatic/db/source/driver.

---

### Post by Andre-D on 2008-05-13
ubuntu 8.04 here.
Please help, I have same printer, another problem:

got my drivers from: [http://welcome.solutions.brother.com/bsc/public_s/es/os/linux/index.html](http://welcome.solutions.brother.com/bsc/public_s/es/os/linux/index.html)

I do 
sudo dpkg -i --force-all ql500lpr-1.0.0-1.i386.deb

This goes as brother says it should, now:

dpkg -i --force-all ql500cupswrapper-1.0.0-1.debian.i386.deb

some errors..

```
(Reading database ... 156073 files and directories currently installed.)
Preparing to replace ql500lpr 1.0.0-1 (using ql500lpr-1.0.0-1.i386.deb) ...
Unpacking replacement ql500lpr ...
Setting up ql500lpr (1.0.0-1) ...

andre@Ubuntu:~/Documents/QL-500$ dpkg -i --force-all ql500cupswrapper-1.0.0-1.debian.i386.deb
dpkg: operation requires read/write access to dpkg status area
andre@Ubuntu:~/Documents/QL-500$ sudo dpkg -i --force-all ql500cupswrapper-1.0.0-1.debian.i386.deb
Selecting previously deselected package ql500cupswrapper.
dpkg: regarding ql500cupswrapper-1.0.0-1.debian.i386.deb containing ql500cupswrapper:
 ql500cupswrapper conflicts with ql500cupswrapperinch
  ql500cupswrapperinch (version 1.0.0-1) is present and installed.
dpkg: warning - ignoring conflict, may proceed anyway !
dpkg: regarding ql500cupswrapper-1.0.0-1.debian.i386.deb containing ql500cupswrapper:
 ql500cupswrapperinch conflicts with ql500cupswrapper
  ql500cupswrapper (version 1.0.0-1) is to be installed.
dpkg: warning - ignoring conflict, may proceed anyway !
(Reading database ... 156073 files and directories currently installed.)
Unpacking ql500cupswrapper (from ql500cupswrapper-1.0.0-1.debian.i386.deb) ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/local/Brother/PTouch/ql500/cupswrapper/brcupsconfpt1', which is also in package ql500cupswrapperinch
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/local/Brother/PTouch/ql500/cupswrapper/cupswrapperql500pt1', which is also in package ql500cupswrapperinch
(Noting disappearance of ql500cupswrapperinch, which has been completely replaced.)
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
Setting up ql500cupswrapper (1.0.0-1) ...
/var/lib/dpkg/info/ql500cupswrapper.postinst: 3: /usr/local/Brother/PTouch/ql500/cupswrapper/cupswrapperql500pt1: not found
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 

```

This results in an "almost" success, results in printer instaled, but not being able to print , because CUPS only thinks it can print the "legal" page format.

---

