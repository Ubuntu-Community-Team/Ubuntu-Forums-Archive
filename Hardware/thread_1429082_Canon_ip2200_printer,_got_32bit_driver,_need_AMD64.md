---
title: "Canon ip2200 printer, got 32bit driver, need AMD64 please!"
date: 2010-03-13
forum: Hardware
---

### Post by markmcv on 2010-03-13
Hi,
Total pulling my hair out, only need my canon pixma ip2200 working and xp can get formatted!

Got the driver from canon website, but its 32 bit so wont compile on my amd 64 :(

Same problem here ... [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200)

Tried [http://www.linux.co.uk/forums/hardware-compatibility/580210050](http://www.linux.co.uk/forums/hardware-compatibility/580210050) but get ...

mark@mcvdesktop:~$ sudo aptitude install libcnbj-2.6 bjfilter-2.6
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Couldn't find any package whose name or description matched "libcnbj-2.6"
Couldn't find any package whose name or description matched "bjfilter-2.6"
Couldn't find any package whose name or description matched "libcnbj-2.6"
Couldn't find any package whose name or description matched "bjfilter-2.6"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done

this page outdated too ... [http://en.gentoo-wiki.com/wiki/Canon_Pixma_Series](http://en.gentoo-wiki.com/wiki/Canon_Pixma_Series)


any ideas please??

---

### Post by IcarusR on 2010-03-13
You could consider using TurboPrint, yes it's not free but if it's the only way....

[http://www.turboprint.info/]("http://www.turboprint.info/")

Free to try.

---

### Post by viktoria.s on 2011-04-09
Hi!
I have no idea if you are still interested some solution (since your post was aound a year ago), but maybe it is still a problem for others.

I have just istalled Ubuntu 10.10 64 bit version onto my laptop. I have the same printer.

Basically what you have to do is similar to this page:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200)

I have downloaded the canon drivers from
[http://files.canon-europe.com/files/soft24301/software/24301.tgz](http://files.canon-europe.com/files/soft24301/software/24301.tgz)
extract it, and with the file roller application extraced all of the rpm contents except the source rpm. Then manually copied all the fires into the corresponding directories. The I ran ldconfig.

The 32 bit libraries on the 64 bit version is in the /lib32 or int the /usr/lib32 directories.

I have downloaded
[http://mirror.linux.org.au/ubuntu//pool/main/g/glib1.2/libglib1.2_1.2.10-10.1build1_i386.deb](http://mirror.linux.org.au/ubuntu//pool/main/g/glib1.2/libglib1.2_1.2.10-10.1build1_i386.deb)

[http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.7.7.dfsg-4ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.7.7.dfsg-4ubuntu0.1_i386.deb)

[http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.9.4-2ubuntu0.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.9.4-2ubuntu0.3_i386.deb)

But instead of normally installing them, I opened them in Midnight Commander and I have copied the contents of the CONTENTS/usr/lib directories into the /lib32 folder.
I have created simbolic links into this directory:
(sysmbolic filename -> to what it is pointing)
libxml.so.1 -> libxml2.so.2.7.7
libgmodule-1.2.so.0 -> libgmodule-1.2.so.0.0.10
libglib-1.2.so.0 ->libglib-1.2.so.0.0.10
libpng.so.3 -> libpng12.so.0.44.0
libtiff.so.3 -> libtiff.so.4.3.3

then I ran ldconfig.

I have added a printer System/Administration/Printing. 
After all that I was able to print a page with some simple text from gedit,
but unfortunatelly not all of the programs in /usr/local/bin direcory is working well due to gtk errors.
Maybe later I will work on this.

Regards

---

