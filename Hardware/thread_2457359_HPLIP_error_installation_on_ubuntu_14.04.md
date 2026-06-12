---
title: "HPLIP error installation on ubuntu 14.04"
date: 2021-01-31
forum: Hardware
---

### Post by wht-crl on 2021-01-31
0
                                         
          
                                        1- I wanted to install HPLIP 3.20.11 on Ubuntu 14.04 from
 [HTML]https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index[/HTML]
 but got some warnings on scanjet dependency which yield to the make failure:
 error: 'make' command failed with status code 2
 How could I fix this?
 Below you will see the complete run result.
 2- Another question is that how could I set up HP deskjet plus 4100 All-in-one series, 4122 model with HPLIP 3.14.3? Does it have or is it better to be with HPLIP 3.20.11?
 The problem is that HPLIP 3.14.3 doesn't detect the printer wifi to get information for set up?

 3- how to show hplip toolbox in the menu bar?
 [HR][/HR] 
```
sh hplip-3.20.11.run
Creating directory hplip-3.20.11
Verifying archive integrity... All good.
Uncompressing HPLIP 3.20.11 Self Extracting Archive...............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

HP Linux Imaging and Printing System (ver. 3.20.11)
HPLIP Installer ver. 5.1

Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Sat-30-Jan-2021_17:36:15.log

\
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.

INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to choose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, q=quit) : a


INTRODUCTION
------------
This installer will install HPLIP version 3.20.11 on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).


DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 14.04.

Is "Ubuntu 14.04" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y

Initializing. Please wait...


ENTER USER PASSWORD
-------------------
Please enter the sudoer (ctril)'s password:

INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for more information. Disable the CD-ROM/DVD source if you do not have the Ubuntu installation media inserted in the drive.

Please read the installation notes. Press <enter> to continue or 'q' to quit:


SECURITY PACKAGES
-----------------
AppArmor is installed.
AppArmor protects the application from external intrusion attempts making the application secure

Would you like to have this installer install the hplip specific policy/profile (y=yes*, n=no, q=quit) ? y


RUNNING PRE-INSTALL COMMANDS
----------------------------
OK


RUNNING HPLIP LIBS REMOVE COMMANDS
----------------------------------
sudo apt-get remove libhpmud0 libsane-hpaio
sudo apt-get remove libhpmud0 libsane-hpaio ( hp_libs_remove step 1)
OK


RUNNING SCANJET DEPENDENCY COMMANDS
-----------------------------------
sudo apt-get install --assume-yes python-pip (Scanjet-depend step 1)
sudo pip2 install --upgrade pip (Scanjet-depend step 2)
warning: Failed to install this Scanjet dependency package. Some Scanjet features will not work.
sudo apt-get install --assume-yes libleptonica-dev (Scanjet-depend step 3)
sudo apt-get install --assume-yes tesseract-ocr (Scanjet-depend step 4)
sudo apt-get install --assume-yes libtesseract-dev (Scanjet-depend step 5)
sudo -H pip2 install tesserocr (Scanjet-depend step 6)
warning: Failed to install this Scanjet dependency package. Some Scanjet features will not work.
sudo apt-get install --assume-yes tesseract-ocr-all (Scanjet-depend step 7)
warning: Failed to install this Scanjet dependency package. Some Scanjet features will not work.
sudo apt-get install --assume-yes libzbar-dev (Scanjet-depend step &#128526;
sudo apt-get install --assume-yes python-zbar (Scanjet-depend step 9)
sudo -H pip2 install opencv-python (Scanjet-depend step 10)
warning: Failed to install this Scanjet dependency package. Some Scanjet features will not work.
sudo -H pip2 install PyPDF2 (Scanjet-depend step 11)
warning: Failed to install this Scanjet dependency package. Some Scanjet features will not work.
sudo -H pip2 install imutils (Scanjet-depend step 12)
warning: Failed to install this Scanjet dependency package. Some Scanjet features will not work.
sudo -H pip2 install pypdfocr (Scanjet-depend step 13)
warning: Failed to install this Scanjet dependency package. Some Scanjet features will not work.
sudo -H pip2 install scikit-image (Scanjet-depend step 14)
warning: Failed to install this Scanjet dependency package. Some Scanjet features will not work.
sudo -H pip2 install scipy (Scanjet-depend step 15)
warning: Failed to install this Scanjet dependency package. Some Scanjet features will not work.
OK


PRE-BUILD COMMANDS
------------------
OK


BUILD AND INSTALL
-----------------
Running './configure --with-hpppddir=/usr/share/ppd/HP --libdir=/usr/lib --prefix=/usr --enable-qt4 --disable-qt5 --enable-doc-build --disable-cups-ppd-install --disable-foomatic-drv-install --disable-libusb01_build --disable-foomatic-ppd-install --disable-hpijs-install --disable-class-driver --disable-udev_sysfs_rules --disable-policykit --enable-cups-drv-install --enable-hpcups-install --enable-network-build --enable-dbus-build --enable-scan-build --enable-fax-build --enable-apparmor_build'
Please wait, this may take several minutes...
Command completed successfully.

Running 'make clean'
Please wait, this may take several minutes...
Command completed successfully.

Running 'make'
Please wait, this may take several minutes...
error: 'make' command failed with status code 2
```

---

### Post by Autodave on 2021-01-31
I would say that the very first thing that you need to do is to get with a supported release....14.04 is woefully out of date and has reached its end of life.  My suggestion would be to copy everything that you need and then do a new install of 20.04.  If you have your printer connected and turned on while doing the install, your printer will probably work just fine w/o doing anything else.

---

### Post by deadflowr on 2021-01-31
The issue is Ubuntu 14.04 has reached end of life.
Now I know the archives still exist and are usable if you have Ubuntu's [Ubuntu ESM.]("https://ubuntu.com/security/esm")
That seems likely to be the cause of this
```
RUNNING SCANJET DEPENDENCY COMMANDS
-----------------------------------
sudo apt-get install --assume-yes python-pip (Scanjet-depend step 1)
sudo pip2 install --upgrade pip (Scanjet-depend step 2)
warning: Failed to install this Scanjet dependency package. Some Scanjet features will not work.
sudo apt-get install --assume-yes libleptonica-dev (Scanjet-depend step 3)
sudo apt-get install --assume-yes tesseract-ocr (Scanjet-depend step 4)
sudo apt-get install --assume-yes libtesseract-dev (Scanjet-depend step 5)
sudo -H pip2 install tesserocr (Scanjet-depend step 6)
warning: Failed to install this Scanjet dependency package. Some Scanjet features will not work.
sudo apt-get install --assume-yes tesseract-ocr-all (Scanjet-depend step 7)
warning: Failed to install this Scanjet dependency package. Some Scanjet features will not work.
sudo apt-get install --assume-yes libzbar-dev (Scanjet-depend step &#55357;&#56846;
sudo apt-get install --assume-yes python-zbar (Scanjet-depend step 9)
sudo -H pip2 install opencv-python (Scanjet-depend step 10)
warning: Failed to install this Scanjet dependency package. Some Scanjet features will not work.
sudo -H pip2 install PyPDF2 (Scanjet-depend step 11)
warning: Failed to install this Scanjet dependency package. Some Scanjet features will not work.
sudo -H pip2 install imutils (Scanjet-depend step 12)
warning: Failed to install this Scanjet dependency package. Some Scanjet features will not work.
sudo -H pip2 install pypdfocr (Scanjet-depend step 13)
warning: Failed to install this Scanjet dependency package. Some Scanjet features will not work.
sudo -H pip2 install scikit-image (Scanjet-depend step 14)
warning: Failed to install this Scanjet dependency package. Some Scanjet features will not work.
sudo -H pip2 install scipy (Scanjet-depend step 15)
warning: Failed to install this Scanjet dependency package. Some Scanjet features will not work.
OK
```

Without those packages being properly installed it's going to keep on failing.

Better to scrap 14.04 and install a newer, supported, version of Ubuntu like 20.04.

---

### Post by wht-crl on 2021-01-31
it is not clear from [Ubuntu ESM.]("https://ubuntu.com/security/esm") how it is possible to post a problem and get help when we require for support for personal use for free.

---

### Post by QIII on 2021-01-31
The Ubuntu Forums offer free help.  However, as stated above, 14.04 has reached end of life.

The best help we can offer is to let you know that you need to install a currently supported release.

ESM is a service for which one must pay.

---

### Post by wht-crl on 2021-01-31
As I need to use the printer quickly, I just wanted to sort out the problem and then, upgrade ubuntu. Before upgrading, I have to back up, to upgrade and install my programs. So I thought that it would take more time to upgrade than if possible, to solve the dependency problems.

---

### Post by CelticWarrior on 2021-01-31
No, the dependencies problem is solved by using a supported release.

---

### Post by wht-crl on 2021-02-01
> **QIII said:**
> 
ESM is a service for which one must pay.

it seems that it's free for personal use and also works for 14.04:

Anyone can use UA Infrastructure Essential for free on up to 3 machines (limitations apply). And if you’re a recognised [Ubuntu community member]("https://wiki.ubuntu.com/Membership"), it’s free on up to 50 machines.
      Initially, this free subscription is available for Ubuntu 14.04 LTS only.

---

### Post by wht-crl on 2021-02-01
how about my last question which is general:


 3- how to show an application or make it visible in the menu bar?

---

### Post by Autodave on 2021-02-01
I honestly don't believe that you are going to get any more assistance here because, as already mentioned, you are running a release that is no longer supported.  You really need to upgrade like already mentioned.  What you are trying to do is like trying to install and make work a Win10 program on a WinXP machine.

---

### Post by wht-crl on 2021-02-13
I tried to upgrade and the kernel crashed. I asked for help but nobody assisted. That's the problem when we want to solve a problem, not only it is not solved but also there is another problem and no help

---

### Post by Autodave on 2021-02-13
Do not try to upgrade: do a clean, new install.  You cannot upgrade an EOL (end of life) release.  D-L 20.04, backup what you need to keep. do a clean install of 20.04.  

If you have your printer on and connected when you do the install, the printer will most likely work when you are done with the install without having to do anything else.

---

