---
title: "Ubuntu 9.04 - HP 2180"
date: 2009-10-23
forum: Hardware
---

### Post by quimkaos on 2009-10-23
i'm having trouble getting my scanner of my multifuntional HP F2180 to work. I installed the drivers, the printer is working since first install, but no scanner... xsane is giving me an I/O error.

 please help me with this!

**in console when i do:**
dpkg -l hplip 

**I get**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Nome           Versão        Descrição
+++-==============-==============-============================================
ii  hplip          3.9.2-3ubuntu4 HP Linux Printing and Imaging System (HPLIP)

---

### Post by quimkaos on 2009-10-23
bump... 
please help!
any ideas?

---

### Post by silvagroup on 2009-10-23
Did you download and install HPLIP form HP's site. It is the most current and contains more printers than t what may be in the repo.
[http://hplipopensource.com/hplip-web/index.html]("http://hplipopensource.com/hplip-web/index.html")

---

### Post by quimkaos on 2009-10-23
**and console runing:** sh hplip-3.9.8

**gives-me this:**

Creating directory hplip-3.9.8
Verifying archive integrity... All good.
Uncompressing HPLIP 3.9.8 Self Extracting Archive..........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

HP Linux Imaging and Printing System (ver. 3.9.8)
HPLIP Installer ver. 5.1

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Sat-24-Oct-2009_01:34:44.log

/
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.


INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to choose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, q=quit) : a

Initializing. Please wait...
 

INTRODUCTION
------------
This installer will install HPLIP version 3.9.8 on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).


DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 9.04.

Is "Ubuntu 9.04" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y


ENTER ROOT/SUPERUSER PASSWORD
-----------------------------
Please enter the root/superuser password: 
Password accepted


INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for more information.  Disable the CD-ROM/DVD source if you do not have the Ubuntu installation media inserted in the drive.

Please read the installation notes. Press <enter> to continue or 'q' to quit: 


RUNNING PRE-INSTALL COMMANDS
----------------------------
OK


CHECKING FOR NETWORK CONNECTION
-------------------------------
Network connection present.


RUNNING PRE-PACKAGE COMMANDS
----------------------------
sudo dpkg --configure -a (Pre-depend step 1)
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
sudo aptitude update (Pre-depend step 3)
OK


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
warning: A previous install of HPLIP is installed and/or running.
sudo apt-get remove --assume-yes hplip hpijs foomatic-db-hpijs (Removing old HPLIP version)
warning: HPLIP removal failed. The previous install may have been installed using a tarball or this installer.
warning: Continuing to run installer - this installation should overwrite the previous one.


RUNNING POST-PACKAGE COMMANDS
-----------------------------
OK


RE-CHECKING DEPENDENCIES
------------------------
OK


PRE-BUILD COMMANDS
------------------
OK


BUILD AND INSTALL
-----------------
Running './configure --with-hpppddir=/usr/share/ppd/HP --libdir=/usr/lib64 --prefix=/usr --enable-qt4 --enable-doc-build --disable-cups-ppd-install --disable-foomatic-drv-install --disable-foomatic-ppd-install --disable-hpijs-install --enable-policykit --enable-cups-drv-install --enable-hpcups-install --enable-network-build --enable-dbus-build --enable-scan-build --enable-fax-build'
Please wait, this may take several minutes...
Command completed successfully.

Running 'make clean'
Please wait, this may take several minutes...
Command completed successfully.

Running 'make'
Please wait, this may take several minutes...
error: 'make' command failed with status code 2

---

### Post by silvagroup on 2009-10-24
Try purging hplip from the system, that can be easily done from synaptic.
Then as root try installing the downloaded hplip.

---

### Post by quimkaos on 2009-10-27
did a fresh intall with 9.10 and nothing...

---

### Post by silvagroup on 2009-10-27
Ubuntu 9.10 supplies HPLIP 3.9.2 and it does support your printer. This from the HPLIP page.

So go to [http://hplipopensource.com/hplip-web/index.html]("http://hplipopensource.com/hplip-web/index.html") and you'll have much better luck.

---

### Post by quimkaos on 2009-10-28
i've already been there... and

---

### Post by quimkaos on 2009-10-28
> **silvagroup said:**
> Ubuntu 9.10 supplies HPLIP 3.9.2 and it does support your printer. This from the HPLIP page.

So go to [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) and you'll have much better luck.

...and it worked... finaly... and i have been there doing just that "script".
This should be on the hardware faqs if there were any.

i love you!! can i give you a kiss!!

tho this is one of the perks of Ubuntu! especially with this type of printers/scanner. This is a mainstream printer/scanner, and it's used by a lot of people just because it's price is between 40 and 60 €. It should be out of the box!
Sometimes I'm a little scared advising costumers and friends to move to linux/ubuntu because of this fails. Tho i think people should have to face problems, so they gain knowledge and start getting the notion that not everything is just click and go. But, in some case things should be easy, especially when people migrate from another OS were this is realy easy. People will give up, by giving up installing it or by giving up on Ubuntu. By the way this is not only a Ubuntu problem... i tried with Debian and Caixa Mágica (fedora based) and it the same thing.
This multifunction printer also has smaller problems in windows. Everything works but in systems with lower hardware specs it crumbles up the OS making it crawl like a zombie snail, just because the installer bloated with BS software. the solution is just installing the driver by downloading it from the site.

and Thank You again

---

### Post by silvagroup on 2009-10-28
Yay !!! Glad it worked out.

Yes these things can be rather annoying, especially for the newbie.

That's why if I recommend *nix for a newbie I bring home all their hardware and do the set up for them. 

That way when they get the system back it is fully functional, especially if they are migrating from Apple or Microsoft.

That however does not guarantee satisfaction. After all every *nix version does things their own way and not the Microsoft or Apple way and that becomes a problem for those who don't like to think and would prefer some one else do the thinking for them. 

So if I do the set up for them they have all the things they are used to already working for them, takes out the thought process, and they are generally more satisfied with the results.

Don't forget to mark the thread solved.

---

