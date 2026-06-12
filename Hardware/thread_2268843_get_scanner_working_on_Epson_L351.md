---
title: "get scanner working on Epson L351"
date: 2015-03-11
forum: Hardware
---

### Post by Pedroski55 on 2015-03-11
Hi, I have a new laptop. My printer/scanner is an Epson L351. It prints ok. On my old laptop it can scan ok using Image Scan! Linux, which is an Epson frontend I believe. I did the same there, downloaded the tarball.

I downloaded the tatball from [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=35136&DSCCHK=de9429162c4ec47336d66db3c2c0433f55f79a46](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=35136&DSCCHK=de9429162c4ec47336d66db3c2c0433f55f79a46)

and followed the instructions in the readme 

dpkg-buildpackage -rfakeroot


There were many unmet dependencies. I installed them one at a time

sudo apt-get install .....

In the end, dpkg went through the motions, but there was an error.

make[4]: Entering directory `/home/pedro/Downloads/temp/iscan-2.30.1/lib/tests'
./even-width.pgm - differ: byte 16, line 4
FAIL: compare ./even-width.pgm ./pcx.XUVgYYWU
./odd-width.pgm - differ: byte 16, line 4
FAIL: compare ./odd-width.pgm ./pcx.SmsmgSwg
FAIL: run-test-pcx.sh
=======================================
1 of 1 tests failed
Please report to [email]linux-scanner@epson.jp[/email]
=======================================
make[4]: *** [check-TESTS] Error 1
make[4]: Leaving directory `/home/pedro/Downloads/temp/iscan-2.30.1/lib/tests'
make[3]: *** [check-am] Error 2
make[3]: Leaving directory `/home/pedro/Downloads/temp/iscan-2.30.1/lib/tests'
make[2]: *** [check-recursive] Error 1
make[2]: Leaving directory `/home/pedro/Downloads/temp/iscan-2.30.1/lib'
make[1]: *** [check-recursive] Error 1
make[1]: Leaving directory `/home/pedro/Downloads/temp/iscan-2.30.1'
make: *** [debian/stamp-makefile-check] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
pedro@pedro-schule:~/Downloads/temp/iscan-2.30.1$ ^C


Any tips on how to get around this?? xsane does not find my scanner. I am not exactly a geek, is there any package that will just work??

---

### Post by Pedroski55 on 2015-03-12
I also tried 

./configure
make
sudo make install

on the downloaded tarball, with no error messages, but also no result. I do not have Image Scan! for Linux installed, which was the point of the exercise.

sane-find-scanner finds nothing with the printer scanner switched on and inserted in the usb port This is the case on my old laptop, and on my new one.

scanimage -L finds nothing on the new laptop

plugged into the old laptop, scanimage -L gives

device `epkowa:usb:002:002' is a Epson L210/L350/L351 Series flatbed scanner (note the different apostrophes before epkowa and after 002)

So I did
pedro@pedro-schule:~$ scanimage --device-name `epkowa:usb:002:002' >myscan1.pnm

I get no error messages, but nothing happens, the scanner does nothing.

As root, sane-find-scanner finds no scanner.

So any tips out there please?

---

### Post by Pedroski55 on 2015-03-12
Hi, problem solved:

On my old laptop, which is able to use the scanner, I have in /etc/sane.d/epkowa.conf

epkowa has the following entries which are not masked with #

usb
scsi

and further down

usb 0x04b8 0x8A1

My new laptop does not have epkowa.conf, but it does have /etc/sane.d/epson.conf and epson2.conf

I put 
usb 0x04b8 0x8A1 

in both of them. Now xsane and simple scan both work fine!!

I have no idea what I have done, but it works!

---

