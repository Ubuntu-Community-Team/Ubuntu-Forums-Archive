---
title: "Epson V300 scanner with Ubunutu 9.04"
date: 2009-08-20
forum: Hardware
---

### Post by ravn-hawk on 2009-08-20
Hi all,

I have a problem with the Epson V300 scanner (This has been discussed alto before, but I have not been able to find a solution to my particular problem in previous threads). I managed to install the iscan package from AVASYS on Ubuntu 9.04 w.o. a problem.

According to the manual on the AVASYS website everything is now suppose to work just by running iscan. I however get an error (both from GNOME menu, and from command line. Also when run as root on command line) saying:

Could not send command to scanner.
Check the scanner's status.

Anyone have got any idea about how to solve this?

Further I find the scanner with sane-find-scanner, it outputs:

found USB scanner (vendor=0x04b8 [EPSON], product=0x0131 [EPSON Scanner]) at libusb:001:006

but scanimage -L does not work, saying:

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

---

### Post by fixerdave on 2009-08-21
Me too, same results exactly, but in 8.10  (okay, different usb port)

Still working on it...

I tried editing /etc/sane.d/epkowa.conf to put in  04b8:0131 for my scanner - now it just hangs at:

fixerdave:~$ SANE_DEBUG_SNAPSCAN=128 scanimage -L
[sanei_debug] Setting debug level of snapscan to 128.
[snapscan] sane_snapscan_init
[snapscan] sane_snapscan_init: Snapscan backend version 1.4.53
[snapscan] sane_snapscan_get_devices (0xbf856458, 0)

Still working...  it eventually times out as:

~$ sudo SANE_DEBUG_SNAPSCAN=128 scanimage -L
[sanei_debug] Setting debug level of snapscan to 128.
[snapscan] sane_snapscan_init
[snapscan] sane_snapscan_init: Snapscan backend version 1.4.53
[snapscan] sane_snapscan_get_devices (0xbf90a878, 0)
device `epkowa:usb:002:008' is a Epson (unknown model) flatbed scanner
[snapscan] sane_snapscan_exit
~$ 

So, it's just not being recognised, even though it's on the "supported" list.  Maybe it's the required "esci-interpreter-gt-f720" thing.  How to I tell if that's installed and working properly?

    David...

---

### Post by IcarusR on 2009-08-21
V300 is not listed as a supported device in either stable or development versions of sane. 
[http://www.sane-project.org/sane-mfgs.html#Z-EPSON]("http://www.sane-project.org/sane-mfgs.html#Z-EPSON")
I doubt you will get it to work without being supported.

---

### Post by fixerdave on 2009-08-21
> **IcarusR said:**
> V300 is not listed as a supported device in either stable or development versions of sane. 
[http://www.sane-project.org/sane-mfgs.html#Z-EPSON]("http://www.sane-project.org/sane-mfgs.html#Z-EPSON")
I doubt you will get it to work without being supported.

I mean "supported" in the epkowa list.  People have got this scanner working; I'm just doing something wrong, I think.  

I've gotten so used to Ubuntu "just working" with all the hardware that I've bothered to throw at it that I didn't even consider it not working.  I mean, it even automatically picked up the old HP all-in-one that had refused to function correctly in XP no matter what I tried...

I guess the V300 is still a little too new.  Sigh...

    David...

---

### Post by adibadi on 2009-09-14
In case anyone is wondering how to get this working:

Download and install libltdl3 from the ubuntu 8.10 repository
[URL="http://packages.ubuntu.com/hardy/libltdl3"]http://packages.ubuntu.com/hardy/libltdl3
[/URL]

Download and install avasys iscan and esci interpreter for the V300
[URL="http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do"]http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do
[/URL]

scanimage -L will show it as Unknown model.  Unplug usb cable and plug it back in, run scanimage -L again and it will show as:

device `epkowa:interpreter:002:019' is a Epson Perfection V300 flatbed scanner

For scanning, I used gscan2pdf - excellent program for making images, PDFs and DjVu files.  To install gscan2pdf, you will need libltdl3.

Hope this helps!

---

### Post by fixerdave on 2009-11-02
Well, Ubuntu v9.10 fixes this.  All I had to do was download and install the deb packages from [http://avasys.jp/eng](http://avasys.jp/eng), log out and back in, and it worked just fine.

Honestly, the v9.10 upgrade is pretty awesome; fixes all kinds of annoying problems.

---

### Post by pacut on 2009-12-09
Getleman,

I am looking for a new working scanner to buy.
Do you confimr this scanner can work under Ubuntu 9.10 ?
Thanks
Paolo

---

### Post by adibadi on 2009-12-09
Yes it does.

> **pacut said:**
> Getleman,

I am looking for a new working scanner to buy.
Do you confimr this scanner can work under Ubuntu 9.10 ?
Thanks
Paolo

---

