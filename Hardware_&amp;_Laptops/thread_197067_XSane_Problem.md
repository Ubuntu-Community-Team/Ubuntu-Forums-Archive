---
title: "XSane Problem"
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by alec on 2006-06-15
Hi,

My chosen scanner front end is Xsane. I have installed this on Kunbuntu 6.6 and it works well with my sanner. However, when I try to use the copy facility it shows the error: Broken Pipe when trying to send the image to the printer.

In all other respects the printer is fine working well with other applications, and the scanner is fine except it cannot print.

Any idea on how to go about fixing this error?

Any help will be greatly appreciated, Kunbuntu froum did not seem to have any answers to this.

Alec

---

### Post by xlyz on 2006-06-17
same problem here. any hint?

EDIT: 

set your printer under preferences, setup, copy. 

command should be: lpr -P name_of_your_printer

---

### Post by SpEcIeS on 2006-06-17
I receive a segmentation fault using ubuntu's xsane.
```

(xsane:9547): Gtk-CRITICAL **: gtk_accel_label_new: assertion `string != NULL' failed

(xsane:9547): Gtk-CRITICAL **: gtk_misc_set_alignment: assertion `GTK_IS_MISC (misc)' failed

(xsane:9547): Gtk-CRITICAL **: gtk_container_add: assertion `GTK_IS_WIDGET (widget)' failed

(xsane:9547): Gtk-CRITICAL **: gtk_accel_label_set_accel_widget: assertion `GTK_IS_ACCEL_LABEL (accel_label)' failed
Segmentation fault

```
Scanning does not seem possible. Tried the debian 0.99 packages and they worked, however they had to be removed because synaptic complained about broken packages, xsane. The version numbering does not match debian, so this allows for error. Any suggestions?

---

### Post by SpEcIeS on 2006-06-17
Problem solved with Xsane 0.991. I compiled the source deb's myself, but the errors still were there. There must be bugs in the ubuntu package, however using the debian unstable source repo I built xsane and xsane-common. The problem is now gone and my ubuntu box is using the current xsane.

If anyone wants the debs let me know. :) -> 0.991 you know you want to use it :razz:

---

### Post by redPirate on 2006-07-03
I had installed xsane 0.99 from debian repos but due to ddpendency problems removed it and installed the version which comes in ubuntu repos 0.97.

My scanner was working fine before this change however now when I try to run xsane it shows the following error:

(xsane:7974): Gtk-CRITICAL **: gtk_accel_label_new: assertion `string != NULL' failed

(xsane:7974): Gtk-CRITICAL **: gtk_misc_set_alignment: assertion `GTK_IS_MISC (misc)' failed

(xsane:7974): Gtk-CRITICAL **: gtk_container_add: assertion `GTK_IS_WIDGET (widget)' failed

(xsane:7974): Gtk-CRITICAL **: gtk_accel_label_set_accel_widget: assertion `GTK_IS_ACCEL_LABEL (accel_label)' failed
Segmentation fault


I don't have any clue what this means. Any help is appreciated.

EDIT ---
I am using ubuntu 6.06 Dapper drake

---

### Post by SpEcIeS on 2006-07-03
Had the same problem, so I built the **xsane_0.99+0.991-1_i386.deb** and **xsane-common_0.99+0.991-1_all.deb** packages. The problem is now gone.

I do not have my webspace setup just yet, but if you would like them let me know and I can email them to you. :)

---

### Post by drtpw on 2006-08-08
Species,

I would love the Xsane 0.991 packages you have and some simple install instructions.  I'm an 'experienced noob'.  I have Dapper doing just about everything I can think of that I want to do except a very simple scan to PDF which I know 0.991 does.  I'm going nuts trying to get it installed with all the dependancies, etc.  My address is [email]tpw3@sbcglobal.net[/email].  Thanks in advance.

---

### Post by SpEcIeS on 2006-08-08
Crap. :sad: I am currently running **Debian Etch/Unstable** and the xsane packages that I build, and others, in Dapper are gone. I knew I should have kept them. Sorry.

You could add the Developing Ubuntu to your repo and use *apt-get source -b packagename*. This how I built them. Since I cannot remember if 0.99.1 is in the developing Ubuntu, you could use the etch repo and apply the *apt-get source -b packagename*

If you need further help let me know. :D

---

### Post by drtpw on 2006-08-09
Species,
Thanks anyway.  Got it installed and runs perfectly.  As a noob, there were some errors during ./configure that I didn't understand.  Once I got the correct files installed, the configuration, make, and install went perfectly.

---

### Post by zeroconf on 2006-08-25
> **SpEcIeS said:**
> Had the same problem, so I built the **xsane_0.99+0.991-1_i386.deb** and **xsane-common_0.99+0.991-1_all.deb** packages. The problem is now gone.

I do not have my webspace setup just yet, but if you would like them let me know and I can email them to you. :)

Could you send them to the [email]master999@hot.ee[/email]

I have HP ScanJet 5p SCSI scanner and Kubuntu 6.06 and I cannot get this scanner to work - [http://kubuntuforums.net/forums/index.php?topic=8244.0](http://kubuntuforums.net/forums/index.php?topic=8244.0)

---

### Post by SpEcIeS on 2006-08-25
Sorry, as stated above, *I am currently running **Debian Etch/Unstable***, and I have long since, unfortunatly,  deleted the xsane packages that I have built for Ubuntu. *I knew I should have kept them :( *

You can build your own by adding the Debian testing or Ubuntu etch to your repos and then using the **apt-get -b source xsane** command. Any errors are a result of unmet dependencies, so just **apt-get install (dependency list)**. In fact, xsane-0.99 should be in Ubuntu Etch, but if you do not want to deal with Ubuntu Etch dependencies then use the *apt* command above. Remember to add the repo sources with the *deb-src*

Hope this helps. :D

---

### Post by SpEcIeS on 2006-08-25
Another thought on the matter that you have. Have you added yourself to the scanner group, if there is one? If there is not a group try changing the permissions to **chmod 664 *device***.

---

### Post by zeroconf on 2006-08-28
> **SpEcIeS said:**
> 
You can build your own by adding the Debian testing or Ubuntu etch to your repos and then using the **apt-get -b source xsane** command. Any errors are a result of unmet dependencies, so just **apt-get install (dependency list)**. In fact, xsane-0.99 should be in Ubuntu Etch, but if you do not want to deal with Ubuntu Etch dependencies then use the *apt* command above. Remember to add the repo sources with the *deb-src*

My result
```
$ sudo apt-get -b source xsane
Reading package lists... Done
Building dependency tree... Done
Need to get 3255kB of source archives.
Get: 1 [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) dapper/main xsane 0.97-4ubuntu6 (dsc) [841B]
Get: 2 [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) dapper/main xsane 0.97-4ubuntu6 (tar) [3200kB]
Get: 3 [http://ee.archive.ubuntu.com](http://ee.archive.ubuntu.com) dapper/main xsane 0.97-4ubuntu6 (diff) [54,0kB]
Fetched 3255kB in 7s (413kB/s)
dpkg-source: extracting xsane in xsane-0.97
dpkg-source: unpacking xsane_0.97.orig.tar.gz
dpkg-source: applying ./xsane_0.97-4ubuntu6.diff.gz
dpkg-buildpackage: source package is xsane
dpkg-buildpackage: source version is 0.97-4ubuntu6
dpkg-buildpackage: source changed by Sebastien Bacher <seb128@canonical.com>
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
dpkg-buildpackage: host architecture i386
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
dpkg-checkbuilddeps: Unmet build dependencies: dpatch libgimp2.0-dev (>= 2.0.0) libgtk2.0-dev libjpeg62-dev libpng12-dev libtiff4-dev libsane-dev (>= 1.0.11-3) zlib1g-dev xlibs-dev (>= 4.0.1-11) autotools-dev
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
Build command ‘cd xsane-0.97 && dpkg-buildpackage -b -uc’ failed.
E: Child process failed
```

Then I installed gcc:
```
$ sudo apt-get install gcc
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  cpp cpp-4.0 gcc-4.0
Suggested packages:
  cpp-doc gcc-4.0-locales manpages-dev autoconf automake1.9 libtool flex bison gdb gcc-doc gcc-4.0-doc libc6-dev-amd64
  lib64gcc1
Recommended packages:
  libc6-dev libc-dev libmudflap0-dev
The following NEW packages will be installed
  cpp cpp-4.0 gcc gcc-4.0
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 2535kB of archives.
After unpacking 6111kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://ee.archive.ubuntu.com dapper/main cpp-4.0 4.0.3-1ubuntu5 [1987kB]
Get: 2 http://ee.archive.ubuntu.com dapper/main cpp 4:4.0.3-1 [31,0kB]
Get: 3 http://ee.archive.ubuntu.com dapper/main gcc-4.0 4.0.3-1ubuntu5 [513kB]
Get: 4 http://ee.archive.ubuntu.com dapper/main gcc 4:4.0.3-1 [5048B]
Fetched 2535kB in 6s (395kB/s)
DESTROY created new reference to dead object ' Qt::VBoxLayout', <> line 4 during global destruction.
Selecting previously deselected package cpp-4.0.
(Reading database ... 94142 files and directories currently installed.)
Unpacking cpp-4.0 (from .../cpp-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package cpp.
Unpacking cpp (from .../cpp_4%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package gcc-4.0.
Unpacking gcc-4.0 (from .../gcc-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.0.3-1_i386.deb) ...
Setting up cpp-4.0 (4.0.3-1ubuntu5) ...
Setting up cpp (4.0.3-1) ...

Setting up gcc-4.0 (4.0.3-1ubuntu5) ...
Setting up gcc (4.0.3-1) ...
```

Then I tried again:
```
$ sudo apt-get -b source xsane
Reading package lists... Done
Building dependency tree... Done
Skipping already downloaded file 'xsane_0.97-4ubuntu6.dsc'
Skipping already downloaded file 'xsane_0.97.orig.tar.gz'
Skipping already downloaded file 'xsane_0.97-4ubuntu6.diff.gz'
Need to get 0B of source archives.
Skipping unpack of already unpacked source in xsane-0.97
dpkg-buildpackage: source package is xsane
dpkg-buildpackage: source version is 0.97-4ubuntu6
dpkg-buildpackage: source changed by Sebastien Bacher <seb128@canonical.com>
dpkg-buildpackage: host architecture i386
dpkg-checkbuilddeps: Unmet build dependencies: dpatch libgimp2.0-dev (>= 2.0.0) libgtk2.0-dev libjpeg62-dev libpng12-dev libtiff4-dev libsane-dev (>= 1.0.11-3) zlib1g-dev xlibs-dev (>= 4.0.1-11) autotools-dev
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
Build command ‘cd xsane-0.97 && dpkg-buildpackage -b -uc’ failed.
E: Child process failed
```

Then I tried:
```
$ sudo apt-get -b source xsane -d
Reading package lists... Done
Building dependency tree... Done
Skipping already downloaded file 'xsane_0.97-4ubuntu6.dsc'
Skipping already downloaded file 'xsane_0.97.orig.tar.gz'
Skipping already downloaded file 'xsane_0.97-4ubuntu6.diff.gz'
Need to get 0B of source archives.
Download complete and in download only mode
```

Then I gave up :?

---

### Post by zeroconf on 2006-08-28
> **SpEcIeS said:**
> Another thought on the matter that you have. Have you added yourself to the scanner group, if there is one? If there is not a group try changing the permissions to **chmod 664 *device***.

Perhaps you noticed, that I posted into Kubuntu's forum all information, what I did - [http://kubuntuforums.net/forums/index.php?topic=8244.0](http://kubuntuforums.net/forums/index.php?topic=8244.0)
Yes, my current user is in scanner group and permissions are fine. Even under root does xsane not work...

The most strange thing - under Edubuntu 5.10 it worked like a charm but now under Ubuntu 6.06 they changed udev file structure and I did not understand what and where I should write.

Another strange thing is, that sane recognizes my scanner and SCSI adapter very well, just xsane don't respond and also scanimage -L will wait forever.

I also filed a bug about this - [https://launchpad.net/bugs/57743](https://launchpad.net/bugs/57743) - there is also all my configuration files included.

---

### Post by SpEcIeS on 2006-08-28
First off you were almost there as far as compiling xsane-0.97, however when I recompiled 0.97 it failed to run also.

Add these dependencies and you will be able to compile xsane 0.97 or other packages:
**apt-get install dpatch libgimp2.0-dev libgtk2.0-dev libjpeg62-dev libpng12-dev libtiff4-dev libsane-dev zlib1g-dev xlibs-dev autotools-dev**

You need these packages, as indicated from your last build attempt, to make debs. In the future you will also need other packages to build other software. Look for these type of lines when your ***apt-build source -b [package]*** fails:

*_dpkg-checkbuilddeps: Unmet build dependencies: dpatch libgimp2.0-dev (>= 2.0.0) libgtk2.0-dev libjpeg62-dev libpng12-dev libtiff4-dev libsane-dev (>= 1.0.11-3) zlib1g-dev xlibs-dev (>= 4.0.1-11) autotools-dev_*

Also, try adding these two lines to your repos:
[B]# Debian Testing
deb [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) etch main contrib non-free
deb-src [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) etch main contrib non-free
[/B]

**[COLOR="Red"]Debian[/COLOR]** testing, or etch, uses xsane 0.99. You could try and install there packages or, you could build your own. 

One thing to note, what version of sane do you have installed? This is the heart of running the scanner. With **[COLOR="Red"]Debian[/COLOR]** testing the libsane is 1.0.18, but I do not know what version **[COLOR="DarkOrange"]Ubuntu[/COLOR]** uses. It should be the same.

If all this just troubles you, you may want to add the Edgy repos and give that a whirl. Nothing says you need to install everything; just what you need. Then comment out "**#**" the repo.

I sure hope something here helps you out. ;)

---

### Post by zeroconf on 2006-08-28
> **SpEcIeS said:**
> First off you were almost there as far as compiling xsane-0.97, however when I recompiled 0.97 it failed to run also.

Add these dependencies and you will be able to compile xsane 0.97 or other packages:
**apt-get install dpatch libgimp2.0-dev libgtk2.0-dev libjpeg62-dev libpng12-dev libtiff4-dev libsane-dev zlib1g-dev xlibs-dev autotools-dev**

After I installed those packages, I could rebuild xsane 0.97 but you were right - it did not solve the problem.

> **SpEcIeS said:**
> 
Also, try adding these two lines to your repos:
[B]# Debian Testing
deb [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) etch main contrib non-free
deb-src [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) etch main contrib non-free
[/B]


This locked down my apt system and I could not install nothing.

> **SpEcIeS said:**
> 
**[COLOR="Red"]Debian[/COLOR]** testing, or etch, uses xsane 0.99. You could try and install there packages or, you could build your own. 
Could not install those packages, when downloaded from Debian Etch repository. Unmet dependencies libusb...

> **SpEcIeS said:**
> 
One thing to note, what version of sane do you have installed?
I had 1.0.17 but now I upgraded from Edgy repository and now I have 1.0.18 (1.0.18-2ubuntu1).

> **SpEcIeS said:**
> 
If all this just troubles you, you may want to add the Edgy repos and give that a whirl. Nothing says you need to install everything; just what you need. Then comment out "**#**" the repo.

I did so. After sudo apt-get update I run sudo apt-get install xsane:

```
$ sudo apt-get install xsane
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gcc-4.1-base gnome-keyring libatk1.0-0 libatk1.0-dev libavahi-client3 libavahi-glib1 libbeagle0 libbonobo2-0 libbonobo2-common libc6 libc6-dev libc6-i686 libcairo2
  libcairo2-dev libcamel1.2-8 libdb4.4 libdbus-1-2 libdbus-glib-1-2 libdirectfb-0.9-24 libebook1.2-9 libedataserver1.2-7 libfreetype6 libfreetype6-dev libgcc1 libglib2.0-0
  libglib2.0-dev libgnome-keyring0 libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnutls13 libgpg-error0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libgtk2.0-dev libopal-2.2.0 libopencdk8 liborbit2 libpango1.0-0 libpango1.0-common libpango1.0-dev libpopt0 libsdl1.2debian libsdl1.2debian-alsa libssl0.9.8 libstdc++6
  libtasn1-3 libusb-0.1-4 libusb-dev libxml2 libxml2-utils libxslt1.1 linux-libc-dev python-support xsane-common xsltproc
Suggested packages:
  glibc-doc manpages-dev libcairo2-doc libglib2.0-doc gnome-icon-theme libgnomevfs2-bin gnutls-bin libgtk2.0-doc libopal-dev ttf-thryomanes ttf-arphic-gkai00mp
  ttf-arphic-bkai00mp libpango1.0-doc hotplug hylafax-client mgetty-fax gv gocr
Recommended packages:
  libatk1.0-data libglib2.0-data libgnomevfs2-extra libtasn1-3-bin mozilla-browser www-browser
The following packages will be REMOVED
  linux-kernel-headers
The following NEW packages will be installed
  gcc-4.1-base libbeagle0 libdb4.4 libdirectfb-0.9-24 libebook1.2-9 libgnutls13 libtasn1-3 libxml2-utils linux-libc-dev python-support xsane xsltproc
The following packages will be upgraded:
  gnome-keyring libatk1.0-0 libatk1.0-dev libavahi-client3 libavahi-glib1 libbonobo2-0 libbonobo2-common libc6 libc6-dev libc6-i686 libcairo2 libcairo2-dev libcamel1.2-8
  libdbus-1-2 libdbus-glib-1-2 libedataserver1.2-7 libfreetype6 libfreetype6-dev libgcc1 libglib2.0-0 libglib2.0-dev libgnome-keyring0 libgnomeui-0 libgnomeui-common
  libgnomevfs2-0 libgnomevfs2-common libgpg-error0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtk2.0-dev libopal-2.2.0 libopencdk8 liborbit2 libpango1.0-0 libpango1.0-common
  libpango1.0-dev libpopt0 libsdl1.2debian libsdl1.2debian-alsa libssl0.9.8 libstdc++6 libusb-0.1-4 libusb-dev libxml2 libxslt1.1 xsane-common
47 upgraded, 12 newly installed, 1 to remove and 908 not upgraded.
Need to get 39,9MB of archives.
After unpacking 30,5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
```

I have now also xsane 0.991 but problem still exists.

I also rebuild packages:
xsane-common_0.99+0.991-1ubuntu1_all.deb
xsane_0.99+0.991-1ubuntu1_i386.deb

... by using command:
apt-get -b source xsane

... and then installed using command:
sudo dpkg -i xsane-common_0.99+0.991-1ubuntu1_all.deb xsane_0.99+0.991-1ubuntu1_i386.deb

But still problem remains.

I also added to file /etc/udev/rules.d/20-names.rules the following row:

BUS="scsi", SYSFS{model}="C5110A", NAME="%k", MODE="0666"


Still not working :(

So I have xsane 0.991, sane 1.0.18 and this row in /etc/udev/rules.d/20-names.rules and still nothing...

When was Edubuntu 5.10, then this row was in file /etc/udev/udev.rules and scanner worked!

But now there is no /etc/udev/udev.rules in Kubuntu 6.06... But I found, that the file /etc/udev/rules.d/20-names.rules has similar structure and i wrote this line there. But it did not help :(

I'm sad, that scanner does not work even system recognizes it and also SCSI adapter works fine.

---

### Post by zeroconf on 2006-08-28
Now it seems, that Gimp is not working:

```
$ gimp

(gimp:29809): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(gimp:29809): Gtk-WARNING **: Unable to locate theme engine in module_path: "qtengine",

(gimp:29809): Gtk-WARNING **: Unable to locate theme engine in module_path: "qtengine",
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "et_EE:et:en_GB:en",
        LC_ALL = (unset),
        LANG = "et_EE.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
gimp: terminated: Interrupt
```

At the same time it tries to load xsane and hangs...

I tried also:
```
$ lang=c gimp
```
...but same thing...

So, it seems like I need to reinstall my whole system :(

This is the third time already... Second time was, when CUPS did not work... No CUPS works but scanning lacks... I'm afraid, that I will install also Windows XP next to Kubuntu Linux - I need to scan... Why Canonical cannot fix it, I don't know... It seems like its similar to Mandriva - you get it free but it has so much bugs, that you cannot work. But pay and a lot of pay - then perhaps you get something, what will work...

But there's some kind of small bug, what does not let this xsane and scanner to work together. Also Kooka hang, when I tried to run it.

And this advertising, that 6.06 is enterprise ready - it's far from it and I'm really sad about it :(

---

### Post by Ambimom on 2006-09-06
My printer is installed locally and works perfectly.  My scanner is installed and works, except I can't export the images to either my printer or my computer.

I have Canon Lide 30 which works with XSane. I can scan perfectly. The drivers are loaded and everything is recognized but when I try to print, I get message that pipe is not connected.  I tried to add my printer name (HP 320C) but it didn't work.  Then I tried to save the scan as jpg.  It saved it, but the document was blank. 

I'm noob, so I may not have done this properly.  

Any suggestions?

---

### Post by blekc on 2006-11-20
> **redPirate said:**
> I had installed xsane 0.99 from debian repos but due to ddpendency problems removed it and installed the version which comes in ubuntu repos 0.97.

My scanner was working fine before this change however now when I try to run xsane it shows the following error:

(xsane:7974): Gtk-CRITICAL **: gtk_accel_label_new: assertion `string != NULL' failed

(xsane:7974): Gtk-CRITICAL **: gtk_misc_set_alignment: assertion `GTK_IS_MISC (misc)' failed

(xsane:7974): Gtk-CRITICAL **: gtk_container_add: assertion `GTK_IS_WIDGET (widget)' failed

(xsane:7974): Gtk-CRITICAL **: gtk_accel_label_set_accel_widget: assertion `GTK_IS_ACCEL_LABEL (accel_label)' failed
Segmentation fault


I don't have any clue what this means. Any help is appreciated.

EDIT ---
I am using ubuntu 6.06 Dapper drake

Remove the .sane (hidden) folder which is in your home directory and restart xsane. This worked fine for me, when xsane (which was working fine) started to crash with the same message, after a version update.

---

### Post by Coburn on 2007-12-27
My EpsonCX5000 is not opening to scan at all.  XSane hangs while searching for devices.

Removing ~/.sane did not fix it.

Removing Kubuntu might, but I don't want to tear up the front lawn that bad.

I am sorry, zeroconf, that you are disappointed in Ubuntu's enterprise readiness.  You might try Vista ;-)

Actually I've been tinkering with computers since the TRS-80 came out, and I have yet to find an OS that does not have enterprise readiness issues that require getting under the hood.  It's just a part of life.

So, yeah, I will take a look at the udev/rules stuff, too...

---

