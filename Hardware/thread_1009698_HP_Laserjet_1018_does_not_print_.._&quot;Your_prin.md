---
title: "HP Laserjet 1018 does not print .. &quot;Your printer may not be connected&quot;"
date: 2008-12-12
forum: Hardware
---

### Post by fuwkej on 2008-12-12
I have been trying to get this printer (HP Laserjet 1018 ) to work for the past 2 years. It seems that if i connect it to a windows computer it will work on my ubuntu computer.

It seems that my computer does not even see the printer, I've ran through every existing walkthrough out there, and none have got this printer to work on this non-functional operating system.

:confused::confused::confused::confused::confused:

---

### Post by marpola on 2008-12-12
I have the HP Laserjet 1018 working on Opensuse and Ubuntu. It took me 4 hours to find the driver and figure out how to install it. 

I just installed it again from my text file info onto a new Ubuntu Studio 8.10 in 10 minutes.

The driver in linux installations does not work.

If you want I´ll clean up my notes and print a copy here.

---

### Post by Camilia on 2008-12-13
I am having a similar problem with a HP deskjet printer. How do you find the drivers. I think that the proper 1 I need is missing.

---

### Post by marpola on 2008-12-13
Read the website for more explanation.
You&#314;l get an earful about HP.

I abbreviated my notes here.
let me know if it works for you.

#####All the printers and details are at foo2zjs.rkkda.com
#####this is for 1018 only on Ubuntu Studio 8.10 and cups
#####Unpack:
    $ wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
    $ tar zxf foo2zjs.tar.gz
    $ cd foo2zjs

######### first need to download make and gcc 
#####(Optional) Uninstall:
    $ sudo make uninstall

#####Compile:
    $ make

####Get extra files from the web such as .ICM profiles (for color correction)
####and firmware.  ? no color on this printer.
    $ ./getweb 1018	# Get HP LaserJet 1018 firmware file

######Install driver, foomatic XML files, PPD files, and extra files:
    $ sudo make install
    
#####(Optional) Install hotplug (for HP LJ 1000/1005/1018/1020/P1005/P1006/P1505):
#####this makes sure you get installed again on reboots.
    $ sudo make install-hotplug
    
#####OK so far, installed both
      Unplug and re-plug the USB printer

#####If you use CUPS to manage your printers, you must restart cupsd:
    $ sudo make cups

######Create printers (Fedora 6/7/8/9 and Ubuntu 7.10/8.x):
    $ system-config-printer

######### created printer with default settings
######### didn't work until printer restarted. Prints OK.
----------This was the end for me, Ubuntu Studio 8.10-----------

########Create printers (Ubuntu 5.10/6.06/6.10/7.04)
    $ sudo gnome-cups-manager
    $ sudo make cups		# Ubuntu has a bug in gnome-cups-manager

---

