---
title: "Can't print to Canon ip2702"
date: 2010-08-20
forum: Hardware
---

### Post by tjktyler on 2010-08-20
I got a free Canon printer when I bought my new monitor. Unfortunately, I have not been able to print to it. The driver (PostScript Printer Definition, PPD, driver) installs and indicates no errors. The printing function indicates no errors; it actually shows that the print job is in progress and completes. The printer shows no errors (no blinking lights, etc. The power LED just stays solid green). But nothing gets printed. I've tried two different USB cables on two different Ubuntu 10.04 machines. I would really like to be able to print from Ubuntu, because I would hate to have to reboot to Windows just to print a file (I am able to print from Windows using Canon's supplied drivers). Any advice/help/direction?

Additional details:
Ubuntu 10.04 32-bit, 2.6.32-24-generic-pae kernel
CUPS 1.4.3-1ubuntu1.2

---

### Post by iheartubuntu on 2010-08-20
I too am having the same problem. There are DEB files on Canons website (inside of a rar) you can download. It only works for 32 bit, though. ive got a 64 bit system :(

---

### Post by tjktyler on 2010-08-20
> **shirteesdotnet said:**
> I too am having the same problem. There are DEB files on Canons website (inside of a rar) you can download. It only works for 32 bit, though. ive got a 64 bit system :(

Can you provide a link for that? I'm not able to find it.

---

### Post by scarvel8 on 2010-09-07
This is how I got it working on Ubuntu 10.04 LTS (64-bit):

1.) Download the linux printer drivers for the ip2700 series of Canon printers (I found them on the European site at this page: [http://software.canon-europe.com/software/0038679.asp](http://software.canon-europe.com/software/0038679.asp))
2.) Extract the .tar file to get two more compressed files, extract the one with .deb in the name.
3.) To get the driver working in a 64-bit system, edit the file install.sh at around line 1429 from C_FUNC_show_and_exec "sudo dpkg -iG $c_fpath_pkg_name" to C_FUNC_show_and_exec "sudo dpkg -iG --force-architecture $c_fpath_pkg_name"
4.) Run install.sh to install the driver

It should install a new printer named ip2700, try printing a test page!

---

### Post by BroMezzano on 2010-10-09
Thank you so much Scarvel! This was the last thing I needed to finish my fresh Mint 9 install!

---

### Post by llawwehttam on 2010-10-21
> **scarvel8 said:**
> This is how I got it working on Ubuntu 10.04 LTS (64-bit):

1.) Download the linux printer drivers for the ip2700 series of Canon printers (I found them on the European site at this page: [http://software.canon-europe.com/software/0038679.asp](http://software.canon-europe.com/software/0038679.asp))
2.) Extract the .tar file to get two more compressed files, extract the one with .deb in the name.
3.) To get the driver working in a 64-bit system, edit the file install.sh at around line 1429 from C_FUNC_show_and_exec "sudo dpkg -iG $c_fpath_pkg_name" to C_FUNC_show_and_exec "sudo dpkg -iG --force-architecture $c_fpath_pkg_name"
4.) Run install.sh to install the driver

It should install a new printer named ip2700, try printing a test page!

Can't think you enough mate. That worked very well.

---

### Post by Aswdriver on 2010-11-07
I tried this fix but when I ran the install shell I got the following message:
==================================================

Canon Inkjet Printer Driver Ver.3.30-1 for Linux
Copyright CANON INC. 2001-2010
All Rights Reserved.

==================================================
An error occurred. The package management system cannot be identified.

A week later I figured out that I could run the install manually and that worked. After down loading, and extracting the the zip and tar you wind up with a directory called cnijfilter-ip2700series-3.30-1-i386-deb, 
within that directory there is a packages, directory goto the packages directory and run the following two commands:
sudo dpkg -i --force-architecture cnijfilter-common_3.30-1_i386.deb
sudo dpkg -i --force-architecture cnijfilter-ip2700series_3.30-1_i386.deb
When they are installed goto system>administration>printing     turn on and connect the printer and you will find it listed under available printers

---

### Post by gsullice on 2011-02-04
Great fix! Thanks!

---

### Post by jreyst on 2011-03-08
This worked for me as well. Thanks for the help!

---

### Post by heavy metal on 2011-03-08
For Linux RPM or DEB. canon printers drivers go to [http://www.canon.com.my/](http://www.canon.com.my/) and click on "support & download".

---

### Post by a_posse_ad_esse on 2011-04-21
It seems that there is a bit of a hitch regarding this with Natty.  I had installed the drivers using this method before, but I now get:

```

dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 153847 files and directories currently installed.)
Preparing to replace cnijfilter-common:i386 3.30-1 (using cnijfilter-common_3.30-1_i386.deb) ...
Unpacking replacement cnijfilter-common:i386 ...
dpkg: dependency problems prevent configuration of cnijfilter-common:i386:
 cnijfilter-common:i386 depends on libc6 (>= 2.3.4-1).
 cnijfilter-common:i386 depends on libcupsys2 (>= 1.2.1) | libcups2.
 cnijfilter-common:i386 depends on libpopt0 (>= 1.7).
dpkg: error processing cnijfilter-common:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cnijfilter-common:i386

```

All of the dependencies are listed as having the latest version.  I e-mailed Canon technical support and was informed that Linux drivers are "as-is" and no assistance could be given.  (I'm not complaining though, at least they put them out there!)  Any idea about how to work around this?

Thanks

---

### Post by a_posse_ad_esse on 2011-04-22
I have started a new thread [here]("http://ubuntuforums.org/showthread.php?p=10705636") as the problem described above is a distinct issue.

---

