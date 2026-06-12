---
title: "Lexmark E230 driver install"
date: 2006-05-19
forum: Hardware &amp; Laptops
---

### Post by getglenn on 2006-05-19
g'day all, am trying to install this printer, without success ( and this might be the "straw" that breaks the back of my "love-affair" with Ubuntu!!!)

i'm hoping someone can point me in the right direction...

here is what i have done, so far...

===============
Lexmark E230 Driver Install

In the directory containing the .deb file

	sudo dpkg -i print-drivers-linux-glibc2-x86.deb
	
resulting output

	(Reading database ... 122022 files and directories currently installed.)
	Preparing to replace drivers-lexprtdrv 5.3.2-2 (using print-drivers-linux-glibc2-x86.deb) ...
           -- Removing symbolic links
	Unpacking replacement drivers-lexprtdrv ...
	Setting up drivers-lexprtdrv (5.3.2-2) ...
	   -- Updating symbolic links

	Lexmark Print Drivers is installed.

	You must run the following scripts to complete the installation.

	   # /usr/local/lexmark/setup.lexprint

so...

	 sudo /usr/local/lexmark/setup.lexprint
	 
result...

	---------------------------------------------------
	Lexmark Print Drivers Setup Script
	---------------------------------------------------

	This application is a suid root program, which allows the
	root user or members of the administrative group to have
	administrative privileges. These privileges include adding,
	removing, and modifying printer queues.

	To set the administrative group, select any valid group that
	is listed in /etc/group file.

	Enter an administrative group or press <ENTER>
	to use the default (bin): -->ENTER
	
	---------------------------------------------------

	Checking your spool directories:

	   /var/spool/lexmark  exists... OK
	   /var/spool/lexmark/unix_prt_drivers  exists... OK
	   /var/spool/lexmark/unix_prt_drivers/.lexprint  exists... OK
	   /var/spool/lexmark/unix_prt_drivers/.lexprint/props  exists... OK
	   /var/spool/lexmark/unix_prt_drivers/vir_devices  exists... OK
	   /var/spool/lexmark/unix_prt_drivers/vir_queues  exists... OK

	Setting PDD permissions... Done

	---------------------------------------------------

	Lexmark Print Drivers Help System consists of html files.
	To be able to view these html help files, we need the
	absolute path to a valid "Web Browser".

	1. /usr/bin/mozilla
	2. /usr/bin/firefox
	3. Specify a web browser.
	4. None.

	Enter your choice : [4] -->2
	

	Setting up Lexmark Print Drivers to use /usr/bin/firefox.
	---------------------------------------------------
	Default paper size selection.

	 1.  Letter (default)
	 2.  A4

	Enter your choice : [2] -->2

	---------------------------------------------------
	Asian Driver Support

	Enabling Asian Driver support provides users with additional Asian
	printing options, such as printing with and without the Asian Font
	Dimm.  You can access these features from the driver properties
	font tab.

	In-order to take advantage of these features, you must enable this
	option and create a printer queue with Asian in the model name.

	Do you want to enable Asian driver support?

	 1.  Disable (default)
	 2.  Enable

	Enter your choice : [1] -->1
	
	---------------------------------------------------
	---------------------------------------------------

	Lexmark GNOME Menu Utility

	  1. Install Lexmark applications into the GNOME Menu.
	  2. Remove Lexmark applications from the GNOME Menu.
	  3. Exit.

	Enter your choice : [3] -->1
	
	GNOME's Menu [ System Tools ] has been updated.
	You may need to restart GNOME for changes to take effect.
	---------------------------------------------------


	Configuring this application to use the [ CUPSD ] print subsystem.


	The Common UNIX Print Subsystem (CUPS) uses mime.types to determine
	how to filter print jobs.  One of the mime types is defined as
	[ application/vnd.cups-raw ], which causes PCL print jobs to by-pass
	the print filters.  This define needs to be commented out so that PCL
	print jobs are passed through the print filters.

	We have determined that we have already commented out this define.

	Do you want to restore this define? (y|n) : [n] -->n
	
	
	Debian GNU/Linux Distribution.

	Setup complete!
	
	
	
so now... "Lexmark Print Drivers" has been added to the Applications --> System Tools menu.

so I... Switch ON printer

        CONNECT USB cable to PC

and TRY to print something... but no printer is INSTALLED!! what the...????

so I select "Lexmark Printer Drivers" from the Applications --> System Tools menu

and NOTHING happens!!???

========================

so much for "Linux compatible", i think...

so i then... READ all I can google, on printers, CUPS, foomatic, PCL6, 5 et. al. Postscript etc etc

but what i CAN'T find, is a simple explanation of the steps required to actually make the printer PRINT... and I bought the thing A WEEK AGO!!!

so far, as much as I like Ubuntu, it has only proven how much Microsoft got right!!!

I enjoyed learning to use Ubuntu, but my productivity has dropped to an abysmally LOW level, while i tangle with SIMPLE procedures that are NEEDLESSLY complex...

PLEASE put me out of my misery, one way or the other!!!! PLEASE!!!!

---

### Post by Sef on 2006-05-19
> so much for "Linux compatible", i think...

so i then... READ all I can google, on printers, CUPS, foomatic, PCL6, 5 et. al. Postscript etc etc

but what i CAN'T find, is a simple explanation of the steps required to actually make the printer PRINT... and I bought the thing A WEEK AGO!!!

so far, as much as I like Ubuntu, it has only proven how much Microsoft got right!!!

I enjoyed learning to use Ubuntu, but my productivity has dropped to an abysmally LOW level, while i tangle with SIMPLE procedures that are NEEDLESSLY complex...

PLEASE put me out of my misery, one way or the other!!!! PLEASE!!!!

From linuxprinting.org

> Other Brands
    There are few good free software drivers for Canon and Lexmark inkjets. Do not buy one and expect success. Often you have either a printer not working at all, fight with incompatibilities of the few manufacturer-supplied proprietary drivers, or you have to calculate in extra costs for third-party proprietary drivers like Turboprint. 

[http://poblano.linuxprinting.org/suggested.html]("http://poblano.linuxprinting.org/suggested.html")

---

### Post by getglenn on 2006-09-26
for the benefit of others, i have been able to use this printer, in DAPPER..

NOT by using the Lexmark driver but

the GENERIC PCL6

---

### Post by mondalaci on 2007-11-25
Thanks getglenn!

That did the trick.  Lexmark can kiss my ***.

---

