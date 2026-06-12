---
title: "Scanner not Detected"
date: 2024-06-04
forum: Hardware
---

### Post by daniell59 on 2024-06-04
Brother was considerate and sent me up to date instructions. They were clear and easy to follow.
All was going well until I got the following on the terminal.
Setting up brscan-skey (0.3.2-0) ...
apt-get install libusb-0.1-4
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 brscan-skey : Depends: libsane (>= 1.0.11-3) but it is not installable
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
root@daniel-N68SA-M2S:/home/daniel/Downloads# 

I can now print but the scanner is not detected. It once worked, so it should work again.
As usual thanks in advance

---

### Post by currentshaft on 2024-06-04
Did you try running the command suggested in the output "apt --fix-broken install"?

Did you try installing "libsane" with apt? If so, please share the errors.

---

### Post by daniell59 on 2024-06-04
> **currentshaft said:**
> Did you try running the command suggested in the output "apt --fix-broken install"?

Did you try installing "libsane" with apt? If so, please share the errors.

I did apt --fix-broken install

I was impressed with the help that Brother gave me. Hopefully they will follow up with more.

---

### Post by him610 on 2024-06-04
You did not state the model of your Brother printer/scanner. 
Is it a multi-function device?
Did you install it using the newer *driverless* method?

I have used the Brother installation scripts to install all of the drivers for my MFC-7360N including print, copy, scan, fax, and one other function that escapes my memory.

---

### Post by daniell59 on 2024-06-05
> **him610 said:**
> You did not state the model of your Brother printer/scanner. 
Is it a multi-function device?
Did you install it using the newer *driverless* method?

I have used the Brother installation scripts to install all of the drivers for my MFC-7360N including print, copy, scan, fax, and one other function that escapes my memory.

MFC-7340

Getting it to print is easy. The difficulty is getting it to detect the scanner.

---

### Post by him610 on 2024-06-05
This should not be too difficult (hopefully) to figure out since both of machines are about the same vintage - 2008.

Did you happen to use utility this to install your drivers?
***Driver Install Tool***	The tool will install LPR, CUPSwrapper driver and scanner driver (for scanner models).  05/20/2024  (2.2.4-1)	0.02  MB
[https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc7340_us_as&os=128]("https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc7340_us_as&os=128")

How is your MFC-7340 connected to your computer? With a Cat5 cable or a USB cable?

Which version of Ubuntu are you using?

***!! I just noticed this...!!***
I believe the libsane version [COLOR="#FF0000"]1.0.11-3[/COLOR] is incorrect
> brscan-skey : Depends: libsane (>= 1.0.11-3) but it is not installable

This is what my installed version is...
```
 $ apt list libsane
Listing... Done
libsane/jammy,now 1.1.1-5 amd64 [installed]
libsane/jammy 1.1.1-5 i386

```
Yours should probably read, [COLOR="#0000FF"]1.1.1-3[/COLOR] instead of [COLOR="#FF0000"]1.1.11-3[/COLOR]
If you can edit the script and make the correction, it will probably install.

Since you have already been in contact with Brother, you should let them know about the coding mistype.

---

### Post by daniell59 on 2024-06-06
> **him610 said:**
> This should not be too difficult (hopefully) to figure out since both of machines are about the same vintage - 2008.

Did you happen to use utility this to install your drivers?
***Driver Install Tool***	The tool will install LPR, CUPSwrapper driver and scanner driver (for scanner models).  05/20/2024  (2.2.4-1)	0.02  MB
[https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc7340_us_as&os=128]("https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc7340_us_as&os=128")

How is your MFC-7340 connected to your computer? With a Cat5 cable or a USB cable?

Which version of Ubuntu are you using?

***!! I just noticed this...!!***
I believe the libsane version [COLOR="#FF0000"]1.0.11-3[/COLOR] is incorrect


This is what my installed version is...
```
 $ apt list libsane
Listing... Done
libsane/jammy,now 1.1.1-5 amd64 [installed]
libsane/jammy 1.1.1-5 i386

```
Yours should probably read, [COLOR="#0000FF"]1.1.1-3[/COLOR] instead of [COLOR="#FF0000"]1.1.11-3[/COLOR]
If you can edit the script and make the correction, it will probably install.

Since you have already been in contact with Brother, you should let them know about the coding mistype.
Presently I am overwhelmed by the process. This was my last attempt.
Selecting previously unselected package brscan-skey.
(Reading database ... 186879 files and directories currently installed.)
Preparing to unpack brscan-skey-0.3.2-0.amd64.deb ...
Unpacking brscan-skey (0.3.2-0) ...
dpkg: brscan-skey: dependency problems, but configuring anyway as you requested:
 brscan-skey depends on libsane (>= 1.0.11-3); however:
  Package libsane is not installed.

Setting up brscan-skey (0.3.2-0) ...
apt-get install libusb-0.1-4
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 brscan-skey : Depends: libsane (>= 1.0.11-3) but it is not installable
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

---

### Post by daniell59 on 2024-06-06
Brother just sent me additional instructions. Though I appreciate their help, it getting too much for me.

[https://help.brother-usa.com/app/answers/detail/a_id/166572/track/AvPfPAoeDv8S~aYGGj0e~yL3Xz0qlC75Mv_S~zj~PP9b](https://help.brother-usa.com/app/answers/detail/a_id/166572/track/AvPfPAoeDv8S~aYGGj0e~yL3Xz0qlC75Mv_S~zj~PP9b)

---

### Post by daniell59 on 2024-06-07
I officially give up. There is no more that I can do.
Now my options.

I would like to find a reasonably priced driverless scanner
If I run the machine on Windows, Brother no longer Supports OCR software for it.

---

### Post by yancek on 2024-06-07
> brscan-skey : Depends: libsane (>= 1.0.11-3) but it is not installable 

You never responded to the question in post 6 about the incorrect version.  Did you make that change in your Brother Scripts?  If you run the command suggested in post 6 ( apt list libsane), what output do you get?  I would expect it to be the same as that shown in post 6.

---

### Post by daniell59 on 2024-06-07
> **yancek said:**
> You never responded to the question in post 6 about the incorrect version.  Did you make that change in your Brother Scripts?  If you run the command suggested in post 6 ( apt list libsane), what output do you get?  I would expect it to be the same as that shown in post 6.



aniel@daniel-N68SA-M2S:~$ apt list libsane
Listing... Done

---

### Post by daniell59 on 2024-06-08
Just some reflecting.
I will try again once I finally build my new computer.
Some thoughts
I had no trouble with the scanner on my previous, now dead and gone computer. I had taken the SD out and put it in my present one. That is the only time that the scanner was detected with this computer. When I reinstalled the OS, I was never able to get it to work again.
Thanks to all for your patience

---

### Post by Dennis N on 2024-06-08
If you want to check the version of libsane, you can use dpkg:

```
dmn@Kayleigh:~$ dpkg --list libsane*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                Version                Architecture Description
+++-===================-======================-============-===========================================================
ii  libsane-common      1.2.1-7build4          all          API library for scanners -- documentation and support files
ii  libsane-hpaio:amd64 3.23.12+dfsg0-0ubuntu5 amd64        HP SANE backend for multi-function peripherals
ii  libsane1:amd64      1.2.1-7build4          amd64        API library for scanners

```

The ii at the beginning of line indicates the package is installed. libsane must be installed in Ubuntu by default, since I have no scanner on this machine.

Sorry I cannot help further. No experience with that Brand. I do have an old Acer scanner on my other Linux computer, and it was not easy to get working. You have my sympathy.

---

### Post by Yellow Pasque on 2024-06-08
The problem is that libsane has just been a transitional package that points to libsane1 for several releases of Debian/Ubuntu now. It was removed in Ubuntu 23.10

The easiest way around this is installing the last libsane package to make brscan-skey stop complaining: [http://launchpadlibrarian.net/651734016/libsane_1.2.1-1_amd64.deb](http://launchpadlibrarian.net/651734016/libsane_1.2.1-1_amd64.deb)

---

