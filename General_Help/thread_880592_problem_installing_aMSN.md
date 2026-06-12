---
title: "problem installing aMSN"
date: 2008-08-05
forum: General Help
---

### Post by onemanclapping on 2008-08-05
hi,

I'm kind of a "noob" in this Linux thing, and I guess something must be escaping me when installing the new aMSN ( [http://prdownloads.sourceforge.net/amsn/amsn-0.97.2-1.tcl85.x86.package](http://prdownloads.sourceforge.net/amsn/amsn-0.97.2-1.tcl85.x86.package) ).

I first removed the old aMSN via Synaptic Package Manager, then followed all instructions in this ( [http://www.autopackage.org/docs/howto-install/](http://www.autopackage.org/docs/howto-install/) ) page, but when I run it, it asks me for the root password, I enter it, and immediately the "Installation successful." box pops up, not installing anything.

I also tried to do it using the command line:

omc@jose-cid:~/Desktop$ sudo package install amsn-0.97.2-1.tcl85.x86.package
[sudo] password for omc:
/tmp/autopackage.500210987/meta/@amsn-project.net/amsn:0.97.2/apkg-prep-install-script: line 127: _checkEULA: command not found

What's the problem here?!

regards,
onemanclapping

---

### Post by Ryadt on 2008-08-05
Why don't you try to install the one in the repos?
```
sudo apt-get install amsn
```

---

### Post by onemanclapping on 2008-08-05
> **Ryadt said:**
> Why don't you try to install the one in the repos?
```
sudo apt-get install amsn
```

because they're not updated and the old version doesn't work anymore (it doesn't let you log in, for some reason).

by the way, why are the repos always outdated?

---

### Post by Hubert Gosselmeyer on 2008-08-05
> **onemanclapping said:**
> hi,
omc@jose-cid:~/Desktop$ sudo package install amsn-0.97.2-1.tcl85.x86.package
[sudo] password for omc:
/tmp/autopackage.500210987/meta/@amsn-project.net/amsn:0.97.2/apkg-prep-install-script: line 127: _checkEULA: command not found


Same here, I think it's a problem with one of the autopackage-scripts.

Here's the quick and dirty way to fix this:

```

xxx:~/Desktop$ sudo ln -s /bin/true /bin/_checkEULA

xxx:~/Desktop$ sudo chmod +x /bin/_checkEULA 

xxx :~/Desktop$ package install amsn-0.97.2-1.tcl84.x86.package

# Preparing package: AMSN MSN client                                                                                                                         
# Checking for required C library versions ... passed
# Checking for X ... passed
# Checking for TCL Scripting Language ... passed
# Checking for Tk GUI Toolkit ... passed
# Installing package: AMSN MSN client (package 1 of 1)                                                                                                       
# 100%[==================================================] Extracting
# Preparing executables...
# Installing data files...
# 100%[==================================================] Copying
# Installing executables...
# Installing menu items...
# Installing icons...
# Updating package database...

The following package was successfully installed:
* AMSN MSN client

The following menu entry is now available:
* aMSN (Network, InstantMessaging)

This installation used 8.12 MiB (8.52 MB) of disk space.


Remove this package by running package remove amsn from the command line.


xxx :~/Desktop$ sudo rm /bin/_checkEULA

```

---

### Post by ant1060 on 2008-08-05
Thanks for your idea : but what do you do about this problem :
The installation of this software requires some additional support
code to be installed.

A] If the support code is found in a local directory, it will be used.
   The file containing the support code will be called:

      "autopackage.tar.bz2"

 or

B] If there is an active Internet connection, the support code will be
   downloaded from:

      "http://autopackage.org/downloads/latest/autopackage.tar.bz2"

   Proxy users should ensure the http_proxy environment variable is
   set, otherwise the download may fail.


Selection B --> OK to download and install support code now? (Y/n): n

Whatever I do next, this loop keeps appearing and I cannot get past it!
Thanks in advance :)

---

### Post by Hubert Gosselmeyer on 2008-08-06
> **ant1060 said:**
> Thanks for your idea : but what do you do about this problem :
The installation of this software requires some additional support
code to be installed.


Hmm... Did you try to download autopackage.tar.bz2 from 
"http://autopackage.org/downloads/latest/autopackage.tar.bz2"
and place it into the same folder as amsn-0.97.2-1.tcl84.x86.package
? 

If so, you could try a manual installation of autopackage... 

1. Download autopackage.tar.bz2...
2. Untar it:

```
tar xjvf autopackage.tar.bz2
```

3. Install it:

```

cd autopackage
sudo ./install

```

Good luck! ;)

---

### Post by kidalabama on 2008-08-06
solution!!! for 7.10


```
sudo chmod a+x amsn-0.97.2-1.tcl84.x86.package
sudo ./amsn-0.97.2-1.tcl84.x86.package
sudo package install amsn-0.97.2-1.tcl84.x86.package
```

---

### Post by tuxxy on 2008-08-06
You dont need to install from source, you should however all be using the supported package of the new aMSN version 0.97.2 which is available for 32/64bit download here [http://www.getdeb.net/app/aMSN](http://www.getdeb.net/app/aMSN) 

Once you downloaded to desktop right click on the file and select install.

---

