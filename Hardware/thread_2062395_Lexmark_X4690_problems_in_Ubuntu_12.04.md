---
title: "Lexmark X4690 problems in Ubuntu 12.04"
date: 2012-09-24
forum: Hardware
---

### Post by BobSongs on 2012-09-24
My customer has a Lexmark X4690 printer attached to his Dell PC running Ubuntu Linux 12.04.1 LTS.

We followed the instructions in ***[this thread]("http://ubuntuforums.org/showthread.php?t=1444847&highlight=lexmark+4690&page=1")*** following the link to Lexmark's webpage. Regardless what release of Ubuntu a user selects, the same file is offered (though, for the sake of discussion, we selected the latest version offered: 10.10). The downloadable file, Lexmark claims, was updated as recently as April 13, 2012.

He downloaded **lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz**, double-clicked it and extracted **lexmark-08z-series-driver-1.0-1.i386.deb.sh** to his desktop. Logged in as root in the terminal, he ran the shell file in the proper way (sh ./[filename].sh) and walked through the various instructions in the setup GUI.

The printer, as per the GUI's instructions, was disconnected during the setup process.

The setup process threw this error message:

```
Extracting file: printdriver.te
Extracting file: lexmark-08z-series-driver-1.0-1.i386.deb
Extracting file: launcher.c
Extracting file: launcher
Extracting file: lsbrowser
Extracting file: lsusbdevice
Using dpkg installation
=============================
Execute: dpkg -i --force-architecture lexmark-08z-series-driver-1.0-1.i386.deb > /tmp/selfgz4240/pkg/files/dpkg_msgs

dpkg: error processing lexmark-08z-series-driver-1.0-1.i386.deb (--install):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 9 package 'lexmark-08z-series-driver':
 blank line in value of field 'Description'
Errors were encountered while processing:
 lexmark-08z-series-driver-1.0-1.i386.deb
=============================

=============================
Execute: rm lexmark-08z-series-driver-1.0-1.i386.deb

=============================
***** ERROR REPORT *****
```The GUI also says:

```
6. Manually adding the Printer in CUPS:
---------------------------------------
 1. Attach the printer via USB to the Linux machine.
 2. Run a browser and open "http://localhost:631"
 3. Click "Add Printer" and fill out the details, such as name and description.
    In the Device dropdown list, select "Lexmark <printer model> USB #1"
    Make sure you select the correct device. The printer is not detected by the
    machine if you cannot see its model in the list. On some distro, you may have
    to reboot the machine so it can be detected.

    You can also Browse for the PPD file if the device is not on the list.
    The ppd files are located in folder /usr/lexinkjet/08zero/etc/. The following
    are the different models supported by this driver and with their matching
    ppd file:

    Printer                            PPD
    ------------------------------------------------------
    Lexmark Z2400 Series         ..... lxZ2400.ppd
    Lexmark 3600-4600 Series     ..... lx36-46.ppd
    Lexmark 4900 Series          ..... lx4900.ppd
    Lexmark 5600-6600 Series     ..... lx56-66.ppd
    Lexmark 7600 Series          ..... lx7600.ppd
```However, due to the failed install script, no **/lexinkjet** subdirectory appears under **/usr**

I'm at a loss as to how to continue short of writing Lexmark to request they update their drivers to accommodate Ubuntu 12.04.

=)

---

### Post by alastair_hm on 2013-01-28
I am having the same issues, no solutions as of yet, but I think it is because I am running 64bit and the driver is only 32bit?

---

### Post by CunningAllusionment on 2013-02-01
Yup, Linux noob here.  I just installed Ubuntu 12.10 and came here hoping to find a solution to this problem.  This is dispiriting.

I have heard about people installing an XP emulator or somesuch for this purpose.

---

