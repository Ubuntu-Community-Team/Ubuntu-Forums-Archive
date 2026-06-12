---
title: "Setting up Canon LBP2900 printer in 64 bit Xubuntu"
date: 2012-05-24
forum: Hardware
---

### Post by forbajato on 2012-05-24
Just started using 64 bit Xubuntu and can't get my printer to work.  I downloaded the drivers as explained [[COLOR="Blue"]here[/COLOR]]("https://help.ubuntu.com/community/CanonCaptDrv190") but in the 64bit folder there is only rpms of the drivers.  Is there another place to get debs of the drivers or a way to change rpms to debs?  Can I just install the 32bit debs?  This is my first foray into 64bit Linux and I am still learning what is possible.

thomas

---

### Post by Sivella on 2012-05-24
Hello,

The tutorial (part: 12.04) is only applicable for 32bits.
Canon don't provide DEB drivers for 64bits.


For a LBP2900, the simplest way is to download drivers from the PPA mickael-gruz.
The 64bits Maverick version works well with 12.04.

1) Purge any Canon drivers installed :
> sudo apt-get purge cndrvcups*2) Download and install transitional package "gs-esp" :[INDENT][http://packages.ubuntu.com/lucid/gs-esp](http://packages.ubuntu.com/lucid/gs-esp)
[/INDENT]3) Download and install from the PPA depot the 2 packages :[INDENT][https://launchpad.net/~michael-gruz/+archive/test/+build/2216444/+files/cndrvcups-common_2.20-1ubuntu4_amd64.deb]("https://launchpad.net/%7Emichael-gruz/+archive/test/+build/2216444/+files/cndrvcups-common_2.20-1ubuntu4_amd64.deb")

[https://launchpad.net/~michael-gruz/+archive/test/+build/2216478/+files/cndrvcups-capt_2.20-1ubuntu3_amd64.deb]("https://launchpad.net/%7Emichael-gruz/+archive/test/+build/2216478/+files/cndrvcups-capt_2.20-1ubuntu3_amd64.deb")
[/INDENT][INDENT]**Install first cndrvcups-common.**
[/INDENT]4) See my post #5 [http://ubuntuforums.org/showthread.php?t=1983091](http://ubuntuforums.org/showthread.php?t=1983091)[INDENT]Starting at point#1 and of course  change LBP6300 with LBP2900
[/INDENT]As you can see 64bits install is more complicated than 32bits but it works.
Come back if you have any question/problem.
If every things work I will explain how to manage ccpd daemon ;)

Good luck.

---

### Post by forbajato on 2012-05-24
For others following Sivella's 64bit Canon printer driver install tutorial ...

These are the only packages I needed to install on my stock Xubuntu 12.04 install:

lib32asound2,
lib32z1,
lib32ncurses5,
lib32ncursesw5,
lib32tinfo5 (added as a dependency)

This worked beautifully, thanks so much for the input!  

One issue - I did do the "echo ia32-libs hold | sudo dpkg --get-selections" step but soon after I finished setting up the printer update manager notified me that it needed to update ia32-libs.  Is there another way to keep it out of the update list?

thomas

---

### Post by forbajato on 2012-05-24
> **Sivella said:**
> 
If every things work I will explain how to manage ccpd daemon ;)


It worked, ready to hear how to manage the ccpd daemon!

thomas

---

### Post by Sivella on 2012-05-25
Fine :D

> One issue - I did do the "echo ia32-libs hold | sudo dpkg  --get-selections" step but soon after I finished setting up the printer  update manager notified me that it needed to update ia32-libs.Yes, but you can't "mark" this package for update ==> update is locked.

> Is there  another way to keep it out of the update list?Yes, install Synaptic packages manager. Select ia32-libs and lock the version. It will disappear from the update list.

Now for "auto-manage" ccpd daemon :
see my post#6 [http://ubuntuforums.org/showthread.php?t=1982917](http://ubuntuforums.org/showthread.php?t=1982917)

Good luck

---

### Post by forbajato on 2012-05-25
Excellent, thanks so much for the assistance!

thomas

---

### Post by carbonmetrics on 2012-06-02
Hi Sivella, thanks for your assistance. I get stuck here:

henk@crunchbang:~$ sudo /usr/sbin/ccpdadmin -p LBP2900 -o /dev/usb/lp0

LBP2900 can't find in CUPS Spooler Entry!!

It is actually a 2900b printer, but putting "2900B" or "2900b" gives the same results. Do you know what's happening here? 
[btw I am on Debian Crunchbang 64 bits].

Henk

---

### Post by Sivella on 2012-06-02
@ carbonmetrics

After drivers install, if you don't have reboot PC,  you must restart cups to register the drivers in cups.
> sudo service cups restartmay be it is why you have this error message.

---

### Post by Sivella on 2012-06-06
Hello,

Due to a new cups update, it seems that usblp module is now blacklisted (like it was with 11.10).
So the printer is not mounted in /dev/usb.

The solution is to cancel this blacklist.

Edit this file : /etc/modprobe.d/blacklist-cups-usblp.conf

Comment (#) the line : blacklist usblp
Here is my file :
> # cups talks to the raw USB devices, so we need to blacklist usblp to avoid
# grabbing them
#blacklist usblp                      

---

### Post by forbajato on 2012-06-12
> **Sivella said:**
> Hello,

Due to a new cups update, it seems that usblp module is now blacklisted (like it was with 11.10).
So the printer is not mounted in /dev/usb.


How frustrating!  Something has happened to my setup, it was working then it just stopped (I probably approved another update I shouldn't have).  Now when I try to go through the tutorial, when I get to registering the printer with ccpdadmin I get the following error:

```
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory

```

I thought it would be as simple as making a soft link to the file in /usr/lib/x86_64-linux-gnu/pkcs11 but that resulted in the following error when trying to register with ccpdadmin:

```
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: wrong ELF class: ELFCLASS64

```

Any thoughts on how to solve this?

thomas

---

### Post by Sivella on 2012-06-12
Hello forbajato,

Does *ia32-libs* package (version 11.10) you have installed, according "my procedure", still locked to prevent update ?

---

### Post by forbajato on 2012-06-12
> **Sivella said:**
> Hello forbajato,

Does *ia32-libs* package (version 11.10) you have installed, according "my procedure", still locked to prevent update ?

Actually I went back and re-did your tutorial to try to fix this including reinstalling the ia32-libs package.  It is locked now too.

thomas

---

### Post by Sivella on 2012-06-14
How about the re-installation ?
Does printer work now ?

---

### Post by forbajato on 2012-06-14
This problem came up during the reinstallation.  Everything worked great until I got to your step 4, installing the ccpd daemon.  That is when I get the error showing that gnome-keyring-pkcs1.so is missing (in the /usr/lib/i386-linux-gnu/pkcs11 folder).  At that point I tried making a soft link to the file in the /usr/lib/x86_64-linux-gnu/pkcs11 folder but that didn't work either.

When I did the reinstall I did uninstall and reinstall the ia32-libs package (from the downloaded one).  The uninstall involved removing skype as well.  No big deal, I just reinstalled skype after the reinstall of the printer.  I wondered if that would help (for some mysterious reason) so just tried doing the printer setup again but still get the same error.

Not sure it makes a difference but when I try to start captstatusui I get a 
Socket Error, I assume this is because it is failing to register with ccpdadmin, correct?
thomas

---

### Post by Sivella on 2012-06-14
Very strange indeed...
My Ubuntu 12.04-64bits is updated and I don't have any problem excepted usblp (solved) as mentioned in my post #9.
May be something different in Xubuntu ???

I had experienced this error message when I tested 12.04 alpha version.
At that time it was a registered bug, but it was solved in 12.04 beta version.

Here the solution :

Edit file : */etc/pkcs11/modules/gnome-keyring-module*
Comment (#) line : *module: gnome-keyring-pkcs11.so*

> # The file is installed/loaded from the default module p11-kit directory
#module: gnome-keyring-pkcs11.so

# And where to store and lookup trust objects
x-trust-store: pkcs11:library-manufacturer=GNOME%20Keyring;serial=1:XDG: DEFAULT
x-trust-lookup: pkcs11:library-manufacturer=GNOME%20Keyring
Restart PC.
Hope it will help you.

---

### Post by forbajato on 2012-06-14
Very interesting.  I modified the /etc/pkcs11/modules/gnome-keyring-module like you suggest.  Then I deleted the printers still hanging around from the last time I tried something.  I then went back to initializing the printer with lpadmin, ccpdadmin, then started ccpd.

After that I fired up captstatusui and realized the printer was not turned on.  When I turned the printer on I got the "New Printer detected" notice and the system set up printer 2 (that has happened every other time so I ignored it).  Then the captstatusui monitor closed on its own and when I tried to restart it I got the socket error.

Back to the top - deleted the existing printers, turned on the printer, initialized with lpadmin and ccpdadmin, started ccpd and everything is golden - printing without problems now.  Just in time too, I have to print out some Latin tests!

I don't know what is going on here but I am glad it is working now, thanks again for your help!

thomas

---

### Post by Sivella on 2012-06-14
Happy your printer works again :cool:

With 64bits, some time it is a nightmare ...
As I had experienced, when this f... LBP printer stop working without any reason, the best way is to remove/purge every things, including drivers cndrvcups, then install from zero.

---

