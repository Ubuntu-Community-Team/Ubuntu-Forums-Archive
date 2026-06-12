---
title: "Driver for Kodak ESP C310"
date: 2013-01-18
forum: Hardware
---

### Post by lazaru2000 on 2013-01-18
Hi all. I'm trying to compile the driver for my Kodak ESP C310. I downloaded the appropriate tar.gz folder, extracted it and aided by a very informative YouTube tutorial did the following.

 paul@paul-desktop:~/Downloads/c2esp21$ sudo make uninstall
[sudo] password for paul: 
rm -rf /usr/share/ppd/c2esp/
rm -f /usr/bin/myopldecode
rm -f /usr/bin/c2esp
rm -f /usr/bin/c2esplog
rm -f /usr/lib/cups/filter/c2esp
rm -f /usr/lib/cups/filter/c2espC
cd ppd; for ppdfile in *.ppd; do \
        rm -f /usr/share/cups/model/$ppdfile.gz; \
    done;

Then...
paul@paul-desktop:~/Downloads/c2esp21$ make
#
# Compile Dependencies...
#
      ***
      *** Error: /usr/include/cups/image.h is not installed!
      ***
      *** Install cups raster library package
      *** for Ubuntu: sudo apt-get install libcupsimage2-dev
      ***
make: *** [all-test] Error 1

When I followed the instruction to install the apparently missing packages I am told I have the latest versions...

paul@paul-desktop:~$ sudo apt-get install libcupsimage2-dev
[sudo] password for paul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcupsimage2-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
paul@paul-desktop:~$ 

I have also found the appropriate components in Synaptic & re-installed them to no avail. I have tried several times now, re-starting the machine each time but I cannot get past this problem. 
Can anybody out there please help? 
Thanks in advance.

---

### Post by fyfe54 on 2013-01-18
Try this - worked for me.  
[http://ubuntuforums.org/showthread.php?t=1963303](http://ubuntuforums.org/showthread.php?t=1963303)

Paulnewall did all the hard work. Follow his link.

---

### Post by lazaru2000 on 2013-01-19
I think I asked the wrong question or at least gave it the wrong title! The problem I have isn't the driver, indeed I downloaded the driver by following Paulnewall's link in the first place. The problem is that during the compiling process I get this message 

Error: /usr/include/cups/image.h is not installed!

and when I try to rectify that by running the suggested command...

sudo apt-get install libcupsimage2-dev  

I get this message...

libcupsimage2-dev is already the newest version.

So the installation process is telling me I need to install something that my computer tells me I already have. Stalemate.
Any ideas how I get past this?
Thanks again.

---

### Post by paulnewall on 2013-01-19
My guess is that you are downloading a fairly old version of c2esp?
Maybe c2esp21 since you have a directory named c2esp21.
That will not compile with the most recent version of cups (1.6 I think).
 
If you are using a recent ubuntu 12.04 or 12.10 c2esp is available already compiled in the repository. You just install it with the package manager.
 
I wrote a howto for this here.
[https://sourceforge.net/projects/cupsdriverkodak/files/Help%20documents/]("https://sourceforge.net/projects/cupsdriverkodak/files/Help%20documents/")
 
Or, if you want to compile it, use the latest version which is currently c2esp26 here
[https://sourceforge.net/projects/cupsdriverkodak/files/](https://sourceforge.net/projects/cupsdriverkodak/files/)

---

### Post by lazaru2000 on 2013-01-20
Ah, I followed exactly what the guy on the You Tube tutorial did and he used that version so I did too. That must be where the problem lies! Thanks for the info!

---

### Post by lazaru2000 on 2013-01-25
Hello again. I followed the instructions you kindly provided & everything goes great until I get to the printer dialogue window. My printer is detected & shows up ok but there is no 'forward' button to click therefore I cannot get to the window where I provide the PPD file. I'm using Ubuntu 12.10. Sorry for being such a noob but can you help??
Thanx in advance. :)

---

### Post by lazaru2000 on 2013-01-25
Problem solved! I was using the Gnome desktop, I switched back to Unity & everything went accordingly. I HAVE A PRINTER!! :p:p:p

Thanx once again.

---

