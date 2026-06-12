---
title: "Canon LBP3010 not working from... ever"
date: 2011-11-05
forum: Hardware
---

### Post by AdrianPtchv on 2011-11-05
Hi,

I was ruining long time Kubuntu and wasn't able to make my Canon LBP3010 printer work.

With Ubuntu 11.10 I switched to Gnome 3 desktop but sill have no luck with the printer.
I followed this [**instructions**]("https://help.ubuntu.com/community/CanonCaptDrv190?action=show&redirect=HardwareSupportComponentsPrinters%2FCanonPrinters%2FLBP3010#Troubleshooting") but I am still not able to print.

sudo /etc/init.d/ccpd status
 gives the following status:

```
Canon Printer Daemon for CUPS: ccpd: 1071
```

The above mentioned instructions say that the status should give **two** numbers and if not I still have a problem with the way the ccpd daemon is starting.

Anyway, after several hours I am still unable to print.
So please, if someone could help, it will be HUGELY appreciated.

It is disappointing to have drivers for the printer and not be able to make it run...

---

### Post by AdrianPtchv on 2011-11-06
No one had such problem? Strange...

---

### Post by PascalNobus on 2011-11-14
I had the same thing, and as far as I know, there is still no solution
The last available CAPT-driver (2.30) is for ubuntu 11.04.
11.10 is still not supported (as the same for Debain Squeeze)


Workaround I used:
Install VirtualBox (from Oracle not the ubuntu/debian-version)
Install a windows-os onto it.
Add the Extension Pack, and you have USB-2 support.

---

### Post by Pankraker666 on 2011-11-15
I have the same problem on ubuntu 11.10, I've read an installed everything correctly according to the manual of the driver and when I try to print something, the file is processing to eternity.. Is there any way to get it work on ubuntu 11.10? I've installed linux for school and still have a partitioned windows version where it works fine, but it would be great if I wouldn't have to switch from OS whenever I want to print a file..

Matthias.

---

### Post by urke on 2011-11-19
New CUPS that come in 11.10 (Oneirc Ocelot) dropped support for lpusb (replaced with libusb), which is used by CAPT Canon printer driver (as I know for 2.30).

> Problem now is that the Canon driver package does not only ship a filter to generate CAPT output from the print job data but also a CUPS backend to communicate with Canon's printer. This backend uses the usblp kernel module and not libusb.

Check out [this bug report]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/842823").

This drive me crazy an I can't use my LBP3010 since I upgradet from 11.04 (worked perfect) to 11.10 (not working at all). :cry:

---

### Post by tonidito on 2012-11-12
Hi, some days ago I decided to upgrade my Ubuntu 10.04 to the newer  Ubuntu 12.04. Everything went very well, and after some configuration I  felt satisfied. Only a thing created some head scratching: my Canon  printer LBP3010 could not print!
After some unsuccessfully attempts to make the driver functioning I  decided to make some researches in Google. I tried all possible drivers,  deb packages and following strictly all posts that I fount in the  Internet, but... nothing, my printer seems to be dead!
My last chance was to recompile from source. First with unsuccessful  results, due to many error that occurred during the compilation  procedure. Again, after some head scratching and a few sleepless nights  analyzing the source code, I get the right solution and now I have my  LBP3010 fully functioning.

Note that the following procedure is valid for a 64 bit machine.

uname -a gives
Linux toni-laptop 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

In the following I will show the procedure that I followed in order to get the printer working.
First I downloaded the last driver package I found at the Canon web page:

Linux_CAPT_PrinterDriver_V240_uk_EN.tar.gz.

Now the procedure to compile.

First step
1) extract the tar.gz package to a folder of Your choice;
2) cd Linux_CAPT_PrinterDriver_V240_uk_EN/Src/
3) untar cndrvcups-capt-2.40-1.tar.gz  and cndrvcups-common-2.40-1.tar.gz
4) cd cndrvcups-common-2.40/
5) gedit debian/control and change "i386" with "amd64" al line 9, save and close file
6) dpkg-buildpackage.

At the end of operation 6) You will find cndrvcups-common_2.40-1_amd64.deb package in Src directory.

7) install it (required for the next compilation steps) with the common 
    sudo dpkg -i cndrvcups-common_2.40-1_amd64.deb

Second step
1) cd cndrvcups-capt-2.40/
2) gedit debian/control and change "i386" with "amd64" al line 9, save and close file
3) gedit debian/rules and uncomment line 172 which will results, then, in 
    #    dh_shlibdeps
    Save and close
4) gedit statusui/src/ppapdata.c and add the header (this is to define variable ppd_size_t)
    #include <cups/ppd.h>
save and close file.
5) gedit cngplp/configure.in and add "AC_CONFIG_MACRO_DIR([m4])" at line 9, save and close
6) gedit cngplp/Makefile.am and add "ACLOCAL_AMFLAGS=-I m4" at line 5, save and close
7) run the following commands in the cngplp directory:
    libtoolize
    aclocal
    automake
cd .. 
9) dpkg-buildpackage

At the end of operation 9) You will find cndrvcups-capt_2.40-1_amd64.deb package in Src directory.

10) install it with 
    sudo dpkg -i cndrvcups-capt_2.40-1_amd64.deb

End of procedure.
From this point You should follow the printer configuration steps as stated in many other posts.

I hope this will help the Ubuntu Community.
Kind regards

---

