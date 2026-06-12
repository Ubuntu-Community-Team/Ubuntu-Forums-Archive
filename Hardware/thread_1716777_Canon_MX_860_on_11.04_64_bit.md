---
title: "Canon MX 860 on 11.04 64 bit"
date: 2011-03-28
forum: Hardware
---

### Post by yg17 on 2011-03-28
I'm trying to get my Canon MX 860 printer/scanner combo working in 11.04 64 bit. Getting printing working is a must, getting scanning to work would be nice but not the end of the world since I can save scans to a USB thumb drive. I also have to be able to print wirelessly (the printer is on my WiFi network now and I can print from Windows and OS X).

Canon only has 32 bit drivers. I tried to follow [these](http://ubuntuforums.org/showthread.php?t=1488850) instructions to no avail. When I run:

sudo dpkg --force-architecture -i cnijfilter-common_3.10-1_i386.deb

I get this error:

dpkg: dependency problems prevent configuration of cnijfilter-common:i386:
 cnijfilter-common:i386 depends on libc6 (>= 2.3.4-1).
 cnijfilter-common:i386 depends on libcupsys2 (>= 1.2.1) | libcups2.
 cnijfilter-common:i386 depends on libpopt0 (>= 1.7).

When I try to upgrade those packages with apt-get, it says those are already the latest version. So now I'm stuck. Has anyone had any luck getting this printer (or a similar Canon MX model) on 11.04 amd64? Thanks

---

### Post by yg17 on 2011-04-03
Anyone?

I got the scanner and printer working on 32 bit without a hitch but would really prefer to use 64 bit.

Thanks

---

### Post by sectas on 2011-04-12
Hello! :)

I wanted to install the MX860 on 10.04 64-Bit and also did not find a solution. Fortunately for me, I also speak German and stumbled upon this blog right as I was about to give up and downgrade to 32-Bit. 

[http://blog.fitzer.org/linux/canon-pixma-mx860-mit-ubuntu-linux-verwenden/](http://blog.fitzer.org/linux/canon-pixma-mx860-mit-ubuntu-linux-verwenden/)

Following these steps you will have to use the Terminal to forcefully install a 32bit driver on a 64bit system. This has worked very well on 10.04 on my father's computer and once my updates are completed I  will follow the steps to get the printer running on 10.10 64bit.


**Assuming you don't speak German, let me translate this for you:**

#1 - Download the 3.1 .deb (Debian) package as well as the 3.1 Source File from this webpage: [http://software.canon-europe.com/products/0010699.asp](http://software.canon-europe.com/products/0010699.asp)
#2 - Open the Terminal
#3 - cd download_directory  # Switch to directory where the Canon .deb and Source files are located
#4 - tar xf cnijfilter-mx860series-3.10-1-i386-deb.tar.gz  # Extract Debian package
#5 - tar xf cnijfilter-source-3.10-1.tar.gz  # Extract Source package
#6 - cd cnijfilter-mx860series-3.10-1-i386-deb/packages/  # Switch to directory of Debian package
#7 - sudo dpkg –force-architecture -i cnijfilter-common_3.10-1_i386.deb  # installs general drivers
#8 - sudo dpkg –force-architecture -i cnijfilter-mx860series_3.10-1_i386.deb  # installs MX860 drivers
#9 - Now you will find the MX860 under the Network Printers. The blogger says it is necessary to use the PPD file located in the Source Package subfolder ppd but I did not need that last step. I hope this helps. 

**Have a nice day. :)**

---

### Post by sectas on 2011-04-12
Sorry, I just realized you already followed those steps. I believe the printer is not working because 11.04 is still Beta but I could be wrong. Have you tried downloading the drivers again?

---

### Post by Salamanca on 2011-05-15
I also had this problem with the MX870 canon.  It worked fine on 10.10 but 11.04 has fake dependency issues.  I just solved the problem.  Here's what I did:

- Get the Canon drivers (in my case MX870_Linux_Package.tar) from the Canon web site (Europe)
- Extract the package - use the File Manager (Extract Here)
- There should be a deb tar gz file: cnijfilter-mx870series-3.30-1-i386-deb.tar.gz, Extract the package - use the File Manager (Extract Here)
- There should be 2 files in the packages directory: cnijfilter-common_3.30-1_i386.deb, cnijfilter-mx870series_3.30-1_i386.deb, again Extract the packages - use the File Manager (Extract Here)
- In each of the new directories there should be a usr and DEBIAN directory.  In the DEBIAN directories edit the control file to remove the items after the line Depends:
- Now open a terminal and from the command line rebuild the packages from the packages directory: 
  > dpkg-deb -b cnijfilter-common_3.30-1_i386
  > dpkg-deb -b cnijfilter-mx870series_3.30-1_i386
- Now install the packages:
  > dpkg -i --force-architecture cnijfilter-common_3.30-1_i386.deb
  > dpkg -i --force-architecture cnijfilter-mx870series_3.30-1_i386.deb
- Now make sure the cups items are owned by root: 
  > chgrp root /usr/lib/cups/backend/cnij*
  > chown root /usr/lib/cups/backend/cnij*
- Go to System > Administration > Printing and install the printer

You should be good to go now.

---

### Post by thatSeniorGuy on 2011-06-30
@ Salamanca: Thank-you thank-you thank-you! I followed your instructions and managed to get the my Canon MX860 working! However, I also needed to change the ownership of /usr/lib/cups/filter/pstocanonij (but then again I was playing around with source code for this printer, so it might just be me). Also, the dpkg, chgrp and chown commands should be run as root (that's just a hint for newbies, I'm sure everyone else can figure it out).

Thanks again!

---

### Post by birchhook on 2011-08-15
I just followed the instructions for the MX882 here:
[http://blog.kenweiner.com/2011/04/using-canon-pixma-mx882-all-in-one-with.html](http://blog.kenweiner.com/2011/04/using-canon-pixma-mx882-all-in-one-with.html)

This driver works great for my mx860 on 64bit Natty.

---

### Post by Black_Sector on 2011-10-19
I followed the instructions on Kens blog, but my computer is unable to see the printer when plugged in, so I cannot finish those instructions.

So I guess I need to use that file to recognize the printer, and possibly get into my file system and 'change ownership'? Sounds like a royal pain, but I really need to get this working.

---

### Post by mlempenau on 2012-06-21
I just bought a Canon MX437 multifunction printer.  I searched all over the net for drivers without success.  Then I did a search on ubuntu forums and found this thread that talked about going to the Canon European website to get Linux drivers. Amazing.  There it was.  All ready and easy to install and even with a current update.  What is going on with the US websites?  Is there a conspiracy against Linux?

---

