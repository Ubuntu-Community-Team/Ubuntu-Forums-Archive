---
title: "Help Installing Canon i250 printer"
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by James_N on 2006-07-02
Hi

Just installed ubuntu, and all is well so far, apart from my printer wont work. Im following this guide: [http://www.ubuntuforums.org/showthread.php?t=126063](http://www.ubuntuforums.org/showthread.php?t=126063)

But i keep getting this: 

> 
jimbo@jimbo-desktop:~/Desktop/i250$ sudo dpkg -i libtiff3g_3.5.5-7woody2_i386.deb
(Reading database ... 88766 files and directories currently installed.)
Preparing to replace libtiff3g 3.5.5-7woody2 (using libtiff3g_3.5.5-7woody2_i386.deb) ...
Unpacking replacement libtiff3g ...
Setting up libtiff3g (3.5.5-7woody2) ...

jimbo@jimbo-desktop:~/Desktop/i250$ sudo dpkg -i canon-i250_2.3_i386.deb
(Reading database ... 88766 files and directories currently installed.)
Preparing to replace canon-i250 2.3 (using canon-i250_2.3_i386.deb) ...
Unpacking replacement canon-i250 ...
dpkg: dependency problems prevent configuration of canon-i250:
 canon-i250 depends on libglade0; however:
  Package libglade0 is not installed.
 canon-i250 depends on libpng2 (>= 1.0.12); however:
  Package libpng2 is not installed.
 canon-i250 depends on libxml1 (>= 1:1.8.14-3); however:
  Package libxml1 is not installed.
 canon-i250 depends on xlibs (>> 4.1.0); however:
  Package xlibs is not installed.
dpkg: error processing canon-i250 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 canon-i250
jimbo@jimbo-desktop:~/Desktop/i250$     

Ive tried getting the missing packages through apt but they arent available :( What can i do? as this is all thats stopping me from having a perfect working system!

Many thanks
James Nolan

---

### Post by Ptero-4 on 2006-07-02
you need to enable universe and multiverse first. Then search (In Synaptic/adept/aptitude) for the names of the packages without the version ( f.e: xlibs (>> 4.1.0) would be xlibs, libpng2 (>= 1.0.12) would be libpng2, and so on.). And finally do the sudo dpkg -i canon-i250_2.3_i386.deb to install the driver.

---

### Post by James_N on 2006-07-03
[QUOTE=Ptero-4]you need to enable universe and multiverse first. .[/QUOTE]

Thanks for that, but im really new to all this, so how do i enable those? :)

Thanks

---

### Post by James_N on 2006-07-03
Right ive installed everything apart from:

libpng2 

as when i try and install it, i get:

> 
PNG library, older version - runtime
libpng is a library implementing an interface for reading and writing PNG (Portable Network Graphics) format files.
This is a dummy package; it is superseded by libpng10-0. 

I have installed libpng10-0 but when i try and install the canon driver, it still says i need libpng2 :(

---

### Post by James_N on 2006-07-03
Anyone  know how i can force install this one package?

---

### Post by Jesterday on 2006-07-14
Download the libpng2 package from [http://packages.debian.org/stable/libs/libpng2](http://packages.debian.org/stable/libs/libpng2)

It should install along side libpng3 and higher

---

### Post by martbd on 2006-08-07
unable to print :confused:

---

### Post by Divade on 2006-08-13
Hi, I'm also having trouble installing a Canon i250

Most of these instructions have worked so far but I cannot find xlibs >>4.1.0 which is the only one of the original 5 missing packages that I have been unsuccessful in installing.

Anyone know where I can get hold of it? 

I've tried installing this [http://packages.debian.org/stable/libs/xlibs](http://packages.debian.org/stable/libs/xlibs)
but

I get

Selecting previously deselected package xlibs.
dpkg: regarding xlibs_4.3.0.dfsg.1-14sarge1_all.deb containing xlibs:
xkeyboard-config conflicts with xlibs (<< 6.8.2-39)
xlibs (version 4.3.0.dfsg.1-14sarge1) is to be installed.
dpkg: error processing xlibs_4.3.0.dfsg.1-14sarge1_all.deb (--install):
conflicting packages - not installing xlibs
Errors were encountered while processing:
xlibs_4.3.0.dfsg.1-14sarge1_all.deb


I can't find xlibs 4.1.0 anywhere else.

If I do a search in the ubuntu repositories (multiverse and universe enabled) in synaptic package manager the only xlibs there is xlibs-dev and when I select that for install I get a huge list of pakages

libc6-dev
libice-dev
etc.
And none appear to be appropriate for what I want as far as I know.

Many thanks for any help in advance

---

### Post by Divade on 2006-08-13
Hmmm, first post to these forums, and guess what.

Idly before going off and doing something else, I tried a test page print once more and lo and behold it now works.

So I've got something akin to xlibs that is working anyhow.

Interestingly Synaptic package manager still claims that my i250 package is broken but while it's working I aint fixing it ;-)

---

### Post by Divade on 2006-08-13
OK, I spoke too soon.

Because the i250 package I installed is 'broken' it means that I can use the printer OR I can use the automatic updates manager and Synaptic  but neither at the same time.
To use the automatic update requires me to fix broken packages and hence remove my printer package. :-/


So, it looks like I do need help on the xlibs >>4.1.0 after all...

*looks hopeful*

---

### Post by James_N on 2006-08-30
well i managed to get everything installed, but when i try and print a test page, i get this:

Paused: Unable to open USB port device file: No such file or directory

The printer wont unpause or print. Any suggestions?

---

### Post by zxee on 2006-08-31
> **James_N said:**
> well i managed to get everything installed, but when i try and print a test page, i get this:

Paused: Unable to open USB port device file: No such file or directory

The printer wont unpause or print. Any suggestions?

I highly recommend [http://www.linuxprinting.org/](http://www.linuxprinting.org/) 
there's a lot of help there for printing in linux. 
Canon does not have a good reputation for supporting their printers in linux IMO. I searched for your printer at the above site but it doesn't show perhaps though there is a way to get another driver working in it. Hope that's helpful.

---

### Post by thunkt on 2007-03-29
Divade,

I found a link for a breezy version of xlibs if you still need it:

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fx%2Fxorg%2Fxlibs_6.8.2-77.2_all.deb&md5sum=8ae9ea382bdb470da912d2f5a2b377f3&arch=all&type=security](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fx%2Fxorg%2Fxlibs_6.8.2-77.2_all.deb&md5sum=8ae9ea382bdb470da912d2f5a2b377f3&arch=all&type=security)

---

