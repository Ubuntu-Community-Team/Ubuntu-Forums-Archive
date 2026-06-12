---
title: "Making the switch to Linux (ubuntu)"
date: 2005-05-30
forum: Hardware &amp; Laptops
---

### Post by rockstarartist on 2005-05-30
Hello everyone,

I am quite new to Linux. I have successfully installed the latest version of Ubuntu after utilizing the latest version live CD and noting that there seemed to be no hardware conflicts.

I own a Dell D-610, with the Intel PRO/Wireless 2200BG. Oddly enough I get no wireless functionality in the full installation of Ubuntu Linux. My Wi-Fi light up on my laptop is not lighted when in Ubuntu, yet when I dual boot to into Windows it functions properly. I set up my BIOS to automatically start the Wireless card and I have attempted to utilize the Function key to switch on the Wireless adapter in Linux to no avail.

I have also looked at the following posts to attempt to resolve this issue before posting:

[http://www.ubuntuforums.org/showthread.php?t=22425&highlight=Dell+D610](http://www.ubuntuforums.org/showthread.php?t=22425&highlight=Dell+D610)
[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)
[http://ubuntuforums.org/showthread.php?p=125537#post125537](http://ubuntuforums.org/showthread.php?p=125537#post125537)

the sourceforge information was definately over my head at the moment, although I consider myself a techie, I am still new to Linux terms.

Any help in this matter would be appreciated. I just find it odd that I can utilized the Live CD for wireless but not the full installation.

Thanks.

---

### Post by DJ_Max on 2005-05-30
Hey, and welcome to Ubuntu Linux  ;-) 

I've never used anything wireless on my computer, but I'm going to try my best in helping you.

There are a number of reasons why you can't use your wireless card.

1.) Installer didn't recognize the card, so it didn't compile your kernel with the appropriate module/driver.
2.)Ubuntu not loading driver on boot.
3.)ipw2200 module causing conflict.

See if you have ipw2200 loaded during boot. Check your hotplug config. If it is, blacklist it. I don't know which driver should be loaded, but you will probably have to fine out.

BTW, here's some reference [http://www.dslreports.com/forum/unixdsl](http://www.dslreports.com/forum/unixdsl)

---

### Post by rockstarartist on 2005-05-31
Hey,

Thanks for the information. Ill give it an eye and see if I can get a resolution.

---

### Post by luca_linux on 2005-05-31
Just follow this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623).
You have to update the ipw2200 driver.

---

### Post by rockstarartist on 2005-06-02
Gentlemen,

I tried the how to post above and ended in failure. I would get an error that seemed to be attributed the KSRC: part of the MAKEFILE.

According to the makefile comments i am supposedly supposed to insert in the KSRC: the location of the source files. The default setting is looking for a build folder that i could not find. this build folder was also part of the error message i would recieve, stating something about unable to find or create that folder.

If i am supposed to write something after the KSRC, would that be the location where i unpacked the IPW2200 files? I set the KSRC to the IPW2200 folder and it started doing something(maybe compiling?) but after it got to module 1448 the computer slowed down to a crawl, and kept going after half an hour. Is it supposed to be doing this? What location do I put in this KSRC?

thanks for the help.

---

### Post by KLineD on 2005-06-02
Well, compiling takes a while sometimes, depends on the program you are compiling. I never had wireless so I can't really tell...

My advice: Leave the computer running until it spills an error or finish succesfully. I remember back a while I was trying to recompile the kernel and it took my computer something along 45 minutes and it did slow down a lot.

---

### Post by rockstarartist on 2005-06-02
I guess I will try it again with the KSRC: part of the make file pointing to the folder i unpacked the ipw2200 files. 

Whats interesting is that none of the compiled modules were anywhere to be found after I cancelled out of the operation. Does Linux compile everything into memory or a page-file before placing them into their final destination?

Ill give this thing another whirl here, and let the computer compile? this stuff until it finishes.

Thanks.

---

### Post by rockstarartist on 2005-06-02
Who else has installed this driver and made it work? I feel that something is missing in that how to instruction manual.

after looking at this (its inside the install instructions of IPW2200):
(or here: [http://ipw2200.sourceforge.net/INSTALL](http://ipw2200.sourceforge.net/INSTALL))

BUILDING EXTERNAL
----------- -----   ----   ----      ---       --       -             -

First, you need to unpack the source code:

	% tar xzvf ipw2200-1.0.4.tgz
	% cd ipw2200-1.0.4

The driver package contains a Makefile that can be used for building the driver
outside of the kernel tree.  To build it for the currently running kernel,
simply type:

	% make  <--- You may need to run this as root

NOTE: If you see any errors during the build process be sure to check the
Issues section on the [http://ipw2200.sf.net](http://ipw2200.sf.net) website as a patch may be available
for your specific kernel configuration.  

To build it for a different kernel than the running one, use the KSRC
parameter:

	% make KSRC=/path/to/kernel

If you wish to install the modules into your currently running kernel you can
do so via:

	# make install <--- You need to run this as root
------------------------------------------

This whole section is not working for me.

---

### Post by rockstarartist on 2005-06-03
Anybody got suggestions for this? Im at a deadlock now.

---

