---
title: "Scanner install questions"
date: 2020-01-06
forum: Hardware
---

### Post by lwalper on 2020-01-06
Trying to get my Epson Perfection 3170 connected via USB. I have XSane, Lios, SimpleScan installed. Have looked for Epson drivers at

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

but don't have any idea how to install the drivers.

I also found this on the Epson site 

[http://download.ebz.epson.net/man/linux/iscan_e.html#sec4](http://download.ebz.epson.net/man/linux/iscan_e.html#sec4)

and have downloaded the .tar file

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=15831&DSCCHK=dc314c7561f36b1e0796b28c20038ddc9fc14ff3](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=15831&DSCCHK=dc314c7561f36b1e0796b28c20038ddc9fc14ff3)

Now, what to do with it--and do I need the "plugin package" to go with it?

I've extracted the downloaded file and have this list

```
leslie@leslie-HP-Notebook:~/Downloads/iscan-2.10.0$ ls
ABOUT-NLS
config.h.in
debian
intl
Makefile.am
po
aclocal.m4
config.rpath
depcomp
iscan.spec
Makefile.in
README
AUTHORS
config.sub
doc
iscan.spec.in
missing
README.ja
backend
configure
frontend
lib
mkinstalldirs
sanei
ChangeLog
configure.ac
include
libltdl
NEWS
utils
compile
COPYING
INSTALL
ltmain.sh
NEWS.ja
config.guess
COPYING.LIB
install-sh
m4
non-free
```

**What's next?**

I've installed [VueScan]("https://www.hamrick.com/"). Haven't had a chance to see if it will work yet. May still need to install drivers. If there's a problem they suggest "try running as root" -- whatever that means?? Well, I'll give it a try.

So I now have my scanner plugged in, turned on, and VueScan does not see it. The suggestion in the help file is "try running as "root." How do I do that?

I opened a terminal,

navigated to /usr/bin,

typed sudo vuescan

which opened the program, but still no scanner detection via USB.

---

### Post by lwalper on 2020-01-07
So I get this pop-up window with advice on how to troubleshoot the scanner installation.

[ATTACH=CONFIG]284760[/ATTACH]

How do I check for a libusb protection problem?

---

### Post by chris6672 on 2020-01-09
Hi

Open a terminal, and type in:

sudo scanimage -L

Tell us what you get.

---

### Post by SeijiSensei on 2020-01-09
VueScan works without any additional drivers. I installed it when I inherited an HP scanner that isn't supported by SANE.

---

### Post by howefield on 2020-01-10
I have an old Perfection Photo 1260, fired it up with both Vuescan and Xsane, both see the scanner without additional drivers. Xsane took a while to initialise the scanner but worked well enough when it did.

In any event, I wouldn't give much for your chances of installing the above 9 year old driver, you are likely to run into a shed load of dependency issues which you may or may not be able to overcome.

Try a different USB port, especially if you are using USB3 with the scanner.

---

### Post by lwalper on 2020-01-10
This is what I get with sudo scanimage -L. The scanner is plugged in, turned on, and connected via USB to my computer. 

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

---

### Post by howefield on 2020-01-10
Does the system recognise the scanner..

```
sudo lsusb
```

---

### Post by lwalper on 2020-01-10
Xsane returns the error "no devices available."  VueScan gives similar message and redirects to a web page with the following advice:

    1. Make sure your scanner is plugged in and turned on before you start VueScan
    2. If you're using a USB Scanner, try using a different USB cable or port. Old USB cables can often go bad
    3. If you're using Linux, try running VueScan as root (sudo)
    4. If you're unable to connect to your scanner, send us a message below and we'll see if we can help fix the problem.

I have three USB ports available on my laptop - have tried each one with same results. VueScan did have an update which I did install - with same results.

> **howefield said:**
> I have an old Perfection Photo 1260, fired it up with both Vuescan and Xsane, both see the scanner without additional drivers. Xsane took a while to initialise the scanner but worked well enough when it did.

In any event, I wouldn't give much for your chances of installing the above 9 year old driver, you are likely to run into a shed load of dependency issues which you may or may not be able to overcome.

Try a different USB port, especially if you are using USB3 with the scanner.

---

### Post by lwalper on 2020-01-10
Looks like it does:

leslie@leslie-HP-Notebook:~$ sudo lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0c45:651b Microdia 
Bus 001 Device 006: ID 04b8:0116 Seiko Epson Corp. GT-9400UF [Perfection 3170]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


> **howefield said:**
> Does the system recognise the scanner..

```
sudo lsusb
```

---

### Post by lwalper on 2020-01-10
Might this be part of my problem? It appears that there are three instances of Vuescan installed, none of which have I been able to remove. When I click remove, nothing happens. I looked in the bin folder to see if I could just delete anything related to Vuescan and there were a couple of files there that seemed related to the program, but could not delete anything there.

[ATTACH=CONFIG]284782[/ATTACH]

---

### Post by lwalper on 2020-01-12
The only way I could figure out how to get rid of that multiple entries issue was to delete this install. So, have now gone back to zero, cleaned the partition and installed 16.04.3. Didn't lose anything other than a few hours, but it's a learning thing I suppose. Education usually takes a little time.

---

### Post by lwalper on 2020-01-13
I was reading in "man sane-dll" that the backend may not be loaded by SANE, and that one could add "an entry to the dll.conf configuration file.  In other words, no applications  need  to  be  modified  or recompiled to add support for new devices."

Maybe that dll.conf file could be edited to add my scanner to the list? Just shootin' in the dark here??

---

### Post by SeijiSensei on 2020-01-13
All three of those VueScan packages were creating by converting from a tar archive.  You'd have to remove them using apt with sudo I suspect.

I just downloaded the VueScan binary (currently [https://www.hamrick.com/files/vuex6497.tgz](https://www.hamrick.com/files/vuex6497.tgz)) and expanded it into my home directory. The archive includes the executable, vuescan, and three supporting files.

If you can't remove the versions you have, try using "locate -i vuescan" and removing the directories manually.

---

### Post by lwalper on 2020-01-14
OK Thanks! That worked great. Had a little trouble navigating to the folder (it must have been hidden and didn't show in the "ls" command).

Thanks again!!


$ locate -i vuescan
/home/leslie/.vuescan
/home/leslie/.vuescan/vuescan.ini
/home/leslie/.vuescan/vuescan.log

---

