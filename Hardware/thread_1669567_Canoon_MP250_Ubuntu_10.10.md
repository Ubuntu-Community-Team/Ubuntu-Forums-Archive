---
title: "Canoon MP250 Ubuntu 10.10"
date: 2011-01-17
forum: Hardware
---

### Post by Urorboros on 2011-01-17
Folks I need help, below is pasted the list of instructions what baffles me is the weird "pathway" that wouldn't  exist on my computer in a million years.
I need you help writing the proper command line so I  can get the Terminal  to recognise where I've downloaded the files


this is the line that doesn't make any sense:


/home/user/Maintenance/MP250Install/printer folder


the line I wrote was

/home/user/Downloads/MP250Install/printer folder



but still it was unable to connect to the downloaded  Deb file



First command line was fine



cd /home/user/Maintenance/MP250Install/printer




Second command line


cnijfilter-common_3.20-1_i386.deb



Error message:



dpkg: error processing cnijfilter-common_3.20-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 cnijfilter-common_3.20-1_i386.deb
john@john-System-Product-Name:~$ 


so the line



 cd /home/user/Maintenance/MP250Install/printer

 is wrong...any suggestions???

Below is a copy of these instructions which I believe to be true gold,  except for this weird glitch.

Much  thanks

JR




Step 2 - unpack the files

double left click on the package and then extract to a suitable folder. In this readme the files were extracted to /home/user/Maintenance/MP250Install/printer folder

The files you need are: 
cnijfilter-common_3.20-1_i386.deb
cnijfilter-mp250series_3.20-1_i386.deb

The software version was correct at 8th August 2010.
---------------

Step 3 - install the printer driver with the printer off.

Open a terminal Applications>Accessories>Terminal

Run these commands in the order listed to install the printer driver for Canon MP250

cd /home/user/Maintenance/MP250Install/printer
sudo dpkg --force-architecture -i cnijfilter-common_3.20-1_i386.deb
sudo dpkg --force-architecture -i cnijfilter-mp250series_3.20-1_i386.deb

Turn on the printer, reboot and the printer should be shown in System>Administration>Printing

---

