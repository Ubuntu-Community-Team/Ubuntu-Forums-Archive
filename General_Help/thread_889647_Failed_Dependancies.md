---
title: "Failed Dependancies"
date: 2008-08-14
forum: General Help
---

### Post by mike_g on 2008-08-14
I'm trying to install the drivers for a Star TSP100 receipt printer. I followed the instructions in the manual:
> Note: Most modern installations allow for the graphical installation of RPM files. Generally when
double clicking the file, a full installation will begin, allowing you to skip the following steps.
1. Use the "su" command to enable root account privileges.
2. Navigate to the directory where the "starcupsdrv-2.3.0-1.i586.rpm" file is located.
3. Run the rpm command using the 'i' and 'v' switches and the name of the RPM file. The full
command should read: rpm -iv starcupsdrv-2.3.0-1.i586.rpm

When I run the last command I get the following errors:
> error: Failed dependencies:
        /bin/sh is needed by starcupsdrv-2.3.0-1.i586
        ld-linux.so.2 is needed by starcupsdrv-2.3.0-1.i586
        libc.so.6 is needed by starcupsdrv-2.3.0-1.i586
        libdl.so.2 is needed by starcupsdrv-2.3.0-1.i586
        libc.so.6(GLIBC_2.0) is needed by starcupsdrv-2.3.0-1.i586
        libdl.so.2(GLIBC_2.0) is needed by starcupsdrv-2.3.0-1.i586
        libdl.so.2(GLIBC_2.1) is needed by starcupsdrv-2.3.0-1.i586

Anyone know how I can fix this? I don't get why /bin/sh is coming up as a failed dependancy as I have obviously got it.

Its quite important that I get this running so help would be much appreciated :)

---

### Post by scragar on 2008-08-14
by the looks of it your running RPM on a debian system :P

first use alien to convert the rpm to a .deb, then use the debian package manager dpkg to install that:
```
apt-get install alien
alien  ./starcupsdrv-2.3.0-1.i586.rpm
```
then run ```
ls
``` looking for the new .deb package.
install that with```
dpkg -i **NewPackage**
```

---

### Post by renzokuken on 2008-08-14
are you trying to installan RPM in Ubuntu?

maybe use alien to convert the rpm into a deb and try again using

```
sudo dpkg -i nameoffile.deb
```

EDIT: darn, beaten to it

---

### Post by sayakb on 2008-08-14
Using alien converted deb packages sometimes breaks the system. Try finding a deb alternative for the same application instead.

---

### Post by mike_g on 2008-08-14
Thanks guys. It looks like I'm making progress, but I'm still getting a failed dependancy when I try and install the .deb:
> required library libcups.so not available
dpkg: error processing starcupsdrv_2.3.0-2_i386.deb (--install):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 starcupsdrv_2.3.0-2_i386.deb
I searched apt for libcups and attempted to install libcupsys2, but apparently it was already installed. Any ideas how I can get this last part working?

Cheers.


> Using alien converted deb packages sometimes breaks the system. Try finding a deb alternative for the same application instead.
Ok, I'll try doing this for the moment ;)

---

### Post by renzokuken on 2008-08-14
that probably means it is looking for libcupsys.so in the wrong place, if you can view the source code maybe try and find where it expects to find it and create a soft link to it

---

### Post by mike_g on 2008-08-14
Well I'm trying to compile the drivers from source now. I installed the required development headers and the makefile output seems to be good until it gets to the end where it says:
> #get ppd options via lphelp
lphelp ppd/sp512.ppd >> docs/sp512-options.txt
/bin/sh: lphelp: not found
make: *** [sp512-options.txt] Error 127

Whats lphelp? I cant seem to find it in the repositories or the manpages.

Cheers.

---

### Post by renzokuken on 2008-08-14
lphelp is something to do with CUPS (common unix printing system) regarding information gathering about installed printers

install cups from the repos and see if that helps

---

### Post by mike_g on 2008-08-14
Yeah, I installed cups so thats not the problem. According to this thread:
[http://ubuntuforums.org/showthread.php?t=644026](http://ubuntuforums.org/showthread.php?t=644026)
The drivers I have are probably for red hat (or at least the setup scripts are). I have been searching, but am so far unable to find a debian version.

Maybe I'll have to dig around in the scripts. I don't know a lot about bash, so this could get messy, lol

---

### Post by fanum on 2012-08-01
I know this is an old thread, but I figured out what the issue is. The two lines that need to be changed in the make file are:

@if ! (ls /usr/lib/ | grep libcups.* > /dev/null); then echo "libcups not available - exiting"; exit 1; fi

Needs to be changed to:

@if ! (ls /usr/lib/i386-linux-gnu/ | grep libcups.* > /dev/null); then echo "libcups not available - exiting"; exit 1; fi

And:

@if ! (ls /usr/lib/ | grep libcupsimage.* > /dev/null); then echo "libcupsimage not available - exiting"; exit 1; fi

Needs to be changed to:

@if ! (ls /usr/lib/i386-linux-gnu/ | grep libcupsimage.* > /dev/null); then echo "libcupsimage not available - exiting"; exit 1; fi

I am running Lubuntu 12.04 x86

---

### Post by wildmanne39 on 2012-08-02
Hi, this is an old thread so it has been closed, thanks for sharing.

---

