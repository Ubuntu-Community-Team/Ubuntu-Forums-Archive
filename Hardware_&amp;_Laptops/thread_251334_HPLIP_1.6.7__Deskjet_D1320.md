---
title: "HPLIP 1.6.7 / Deskjet D1320"
date: 2006-09-05
forum: Hardware &amp; Laptops
---

### Post by Emerzen on 2006-09-05
Well, for the first time since I started using Linux about 2 years ago, I've been able to get a printer working and don't have to switch over to Windows to print stuff off.

Anyway, Walmart has the HP D1320 printer (basic color deskjet - single function) for app $30.  I picked one up on impulse but couldn't get it working w/ current HPLIP, but the latest version has it humming:

0.  (I did this first but don't know if it's necessary)  Uninstall all HP packages and foomatic packages.

1.  d/l latest tarball [here]("http://hplip.sourceforge.net/")

2.  Follow the Ubuntu specific instructions [here]("http://hplip.sourceforge.net/install/step3/index.html")

3.  I used checkinstall instead of a simple make install

4.  Setup printer through Sytem Settings or type 

```
hp-setup
```  at terminal.

---

### Post by ross22 on 2006-09-05
Hi Emerzen,

I've tried to install hplip but my system is missing some of the requirements such as cups-devel support.  I've looked on Synaptics but I cannot find the package.  I've enabled universe and multiverse repositories, what am I doing wrong?

Thanks in advance for any help

Ross

---

### Post by Emerzen on 2006-09-05
Try installing this package, then reconfigure/make.  

```
sudo apt-get install libcupsys2-dev
```

If you come up w/ other missing dependencies, lemme know.  There's another thread about this that I don't have direct access to that lists all the build dependencies, which I'll try to find again.

Here's the complete list:

```
sudo apt-get install python2.4-dev python2.4-qt3 libcupsys2-dev libsnmp9-dev libjpeg62-dev lsb libtool automake1.9 libusb-dev checkinstall
```

---

### Post by ross22 on 2006-09-06
Thankyou very much, this worked perfectly fr me!  I have a HP-f388 printer and scanner which is working perfectly now.

Forgive my ignorance, but does the Synaptic package manager display all of the packages available from the repositories?  If for example I need to install a different program that requires certain libraries/packages not listed in synaptic; should I use apt-get instead?

Also (possibly a very stupid question), does the hplip folder now in my home directory include files from the installation I just made?  Can I delete the folder without affecting the installation?  Or is it possible to move it; I only ask as I'd like to keep the home folder free from clutter if possible.

Thankyou very much for your help!:) 

Ross

---

### Post by Emerzen on 2006-09-06
Synaptic is a GUI for apt-get, so anything available in one is available in the other.  If you need something not listed in Synaptic, you'll have to add a repository that has the package.  Check to see if your universe/multiverse repo's are included.  There are several repositories that you can possible add, including the debian repo's, but they are not Ubuntu specific.  The subject of repositories is a long one.  Here's a website that will generate a source.list for you.  If you don't know what this refers to, I'd be happy to explain but don't want to bore you if you do.

If no package has been made for the specific program, and you compile from source, you're working outside of apt altogether.  In the folder where you did the configure->make stuff, you actually created a set of binary files that run on the PC.  When you do a make install, part of that process is copying those files to the proper directories.  With make install, you have to know where everything is copied if you ever want to remove it, and then delete them.  With checkinstall, a debian package is created before install, ant then debpackage installs it.  That way, apt knows where the files are if you ever want to remove them.  So, what's in that folder are the original files, the compiled programs, etc...which have all been copied to their proper location by apt.  You can safely delete the folder.  I generally copy all of my source folders, so I don't have to redownload/recompile stuff in the future but it's not necessary.     It's just a matter of my obsessive qualities.  If you are going to save the folder, I'ld browse to it and run a "make clean" in the directory to delete all the unnecessary config files.  If you used checkinstall, you should also find a debian package in there.

---

### Post by JRS on 2006-09-25
I have the same printer from Walmart. Paid the same price for it. Followed your directions...presto. Works great! Thanks for the information.
                                       Your the man,
                                       JRS

---

### Post by harelb on 2007-01-04
Hello..the above doesn't seem to work for me..

I'm very new to ubuntu (my sweetie installed it for me, she's been
using it about a year) and just got an HP officeJet 4315..the installation disc for MSFT/Mac only, but she found the hplip file for me to install..tried ```
sudo sh ./hplip-1.6.12.run
```
and got 8 missing pieces...finally was able to get it down to 1, namely

"warning: Missing REQUIRED dependency: cups-devel (cups-devel- Common
Unix Printing System development files)"

that's when a google found this thread...however when I typed
```
sudo apt-get install libcupsys2-dev
``` I got the following:
```

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libcupsys2-dev: Depends: libcupsys2 (= 1.2.0-0ubuntu5) but 1.2.2-0ubuntu0.6.06 is to be installed
E: Broken packages
```

I just want a working printer...it's been a bit ](*,)  ...would appreciate help :)  Many thanks,

Harel

---

### Post by 11hjpphty76lkjj on 2007-01-12
Try:

sudo apt-get install -f

then

sudo apt-get install libcupsys2-dev

then run 

sh hplip-1.6.12.run

Aaron

---

### Post by Acupuncture Doc on 2007-02-10
I just purchased this printer.  I am running dapper 6.06 on a celeron 1.3 with 256megs of ram. I keep the system current with all updates. when trying to install hplip 1.7.1.run the system froze. I had to do a cold restart. then I attemped another install. This time, all was well until it determined there was another copy of itself running. I got the following:

DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
warning: A previous install of HPLIP is installed and/or running.
note: You may be prompted for a password. Please enter the appropriate password for your system for 'sudo' when prompted.
Running 'sudo /etc/init.d/hplip stop'
Please wait, this may take several minutes...

Running 'sudo apt-get remove --force-yes --yes hplip hpijs'
Please wait, this may take several minutes...
error: HPLIP removal failed. The previous install may have been installed using a tarball or this installer.
error: Continuing to run installer - this installation should overwrite the previous one.


BUILD AND INSTALL
-----------------
note: You may be prompted for a password. Please enter the appropriate password for your system for 'sudo' when prompted.

Running './configure --enable-network-build --disable-pp-build --enable-fax-build --enable-gui-build --enable-scan-build --prefix=/usr'
Please wait, this may take several minutes...

error: './configure --enable-network-build --disable-pp-build --enable-fax-build --enable-gui-build --enable-scan-build --prefix=/usr' command failed with status code 1
tom@tom-desktop:~$

So what now?

---

### Post by 11hjpphty76lkjj on 2007-02-12
Try:

cd hplip-1.7.1
./configure --prefix=/usr

then post the actual error generated.

A

---

### Post by filthybill on 2007-07-08
Forgive me for sounding mildly retarded but I am BRAND new to Linux. I am currently running Fedora Core 5 and trying to install the same HP Deskjet D1320 printer. The printer manager finds my printer but when I am asked to find the model in the list, it is not there. I read your post and would like to follow your instructions, but how do I Uninstall all HP and foomatic packages?

Many thanks in advance,

- Filthy Bill

---

### Post by filthybill on 2007-07-08
OK So I was able to work thru your instructions, but when I got to the part where I had to enter the command hp-setup, I got the following message:

[root@localhost hplip-1.6.7]# hp-setup

HP Linux Imaging and Printing System (ver. 1.6.7)
Printer/Fax Setup Utility ver. 2.1

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: Unable to connect to hpiod.
[root@localhost hplip-1.6.7]#

Any words of wisdom? I am at a complete loss now.

- Filthy Bill :confused:

---

### Post by 11hjpphty76lkjj on 2007-07-10
Odd.  Try running:

sudo /etc/init.d/hplip restart

and then;

sudo hp-setup

A

---

### Post by thingy on 2007-07-22
If you get the cups-devel dependancy not met issue with the HPLIP automatic installer, see this thread:

[http://ubuntuforums.org/showthread.php?t=507265&highlight=hplip](http://ubuntuforums.org/showthread.php?t=507265&highlight=hplip)

---

