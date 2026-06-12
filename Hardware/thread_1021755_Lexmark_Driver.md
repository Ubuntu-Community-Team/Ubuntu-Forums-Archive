---
title: "Lexmark Driver"
date: 2008-12-25
forum: Hardware
---

### Post by indiana_crook on 2008-12-25
I have a Lexmark 2600 printer.  I have downloaded the driver from the Lexmark website.  The filename is "lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip"  Can anyone tell me what I'm supposed to do with this file?

---

### Post by SuperSonic4 on 2008-12-25
Lexmarks are basically paperweights on ubuntu I'm afraid :(

Did it specifically mention a linux driver?

---

### Post by Sef on 2008-12-26
>  I have a Lexmark 2600 printer. I have downloaded the driver from the Lexmark website. The filename is "lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip" Can anyone tell me what I'm supposed to do with this file?  1) I found the [link]("http://downloads.lexmark.com/perl/downloads/downloads.cgi").  Please include that next time.  

2) Also do you have a X2600 or an All-In-One 2600?  That driver is for the X2600.

3) As for your question, read [How to Install Anything in Ubuntu]("http://amitech.50webs.com/installing/index.php.html").

> Lexmarks are basically paperweights on ubuntu I'm afraid :sad:

Did it specifically mention a linux driver?

Looks like that Lexmark is getting smart.

---

### Post by indiana_crook on 2008-12-26
okay, I made progress but now it says installation failed.

---

### Post by deboard on 2009-01-05
What exactly did you do?  And at what point did the install fail?  Make sure the file is complete, it was around 30megs for me. 

I don't have this printer, but I downloaded the driver, and did the following:

1.  Unzipped the file
2.  Opened a terminal and changed directory to where the unzipped file was located.
3.  typed ./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh
4.  After this a nice gui installer popped up and I had to agree to a license agreement. It did say I should NOT have the printer connected at this point.  That was ok since I didn't have one to connect.  
5.  I hit next and it did a lot of install things, uncompressing some stuff, etc.  Then it said installation was successful.
6.  Hitting next, it wanted me to connect the printer, but since I don't have one of these, this was as far as I got.

If all else fails, contact Lexmark either through email or phone.

Also, please make sure this is an X2600 series, which is an printer/scanner combo

---

### Post by flattop1 on 2009-03-15
> **Sef said:**
> 1) I found the [link]("http://downloads.lexmark.com/perl/downloads/downloads.cgi").  Please include that next time.  

2) Also do you have a X2600 or an All-In-One 2600?  That driver is for the X2600.

3) As for your question, read [How to Install Anything in Ubuntu]("http://amitech.50webs.com/installing/index.php.html").



Looks like that Lexmark is getting smart.

Thanks ..This driver worked perfect for me.

I had it allup and running in about 10 minutes..No Problem

---

### Post by jbdavis52 on 2009-04-19
Sadly the link [http://www.download.Lexmark.com/pearl/etc.etc](http://www.download.Lexmark.com/pearl/etc.etc)...
is no longer available. A check on the Lexmark "find a driver" widget reveals only windows or mac drivers. 

Are there any other repositories for this driver? I'm running Ubuntu Linux because it is free. I certainly can't afford a new printer right now.
Thanks

---

### Post by NavySeniorChief on 2009-06-08
I have a 64 bit system, and am using the current release of Kubuntu (downloaded and installed today)

I went to the lexmark site and downloaded the lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip file for my X2690. I unpacked it, went to terminal to the proper directory and typed...

./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh

Instead of the installation gui, I got this...

Verifying archive integrity... All good.
Uncompressing nixstaller...............................................................
Collecting info for this system...
Operating system: linux
CPU Arch: x86_64
Warning: No installer for "x86_64" found, defaulting to x86...
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
Error: Couldn't find any suitable frontend for your system

I'm lost as to the next step here, so I could use a little help.

Thanks :-)

---

### Post by nathan726 on 2009-07-31
I managed to get my lexmark X2630 to work. I just downloaded the lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip from [http://downloads.lexmark.com/perl/downloads/downloads.cgi](http://downloads.lexmark.com/perl/downloads/downloads.cgi)

and then did this: [http://ubuntuforums.org/showthread.php?p=7713382#post7713382](http://ubuntuforums.org/showthread.php?p=7713382#post7713382)

---

### Post by solutionorppt on 2010-04-17
I just tried this with a Lexmark X2600, but grub rejects my administrative password when prompted by the GUI after initiating the installation in terminal (yes, I've made sure it was typed correctly about 17 times).  This has not happened to me during any other software installation.

Any ideas?

Oh, I forgot to type sudo before the command.

---

### Post by wbar2 on 2010-05-01
> **solutionorppt said:**
> I just tried this with a Lexmark X2600, but grub rejects my administrative password when prompted by the GUI after initiating the installation in terminal (yes, I've made sure it was typed correctly about 17 times).  This has not happened to me during any other software installation.

Any ideas?

Oh, I forgot to type sudo before the command.

If you are still having problems, here is a tutorial: [http://ubuntuforums.org/showthread.php?p=9211584](http://ubuntuforums.org/showthread.php?p=9211584)

---

### Post by yyyc186 on 2010-09-05
Here is a quick "work around"

In one terminal window cd to the directory you unzipped the .sh file into.

sudo ./lexmark-inkjet-09-driver-1.5-1.i386.deb.sh

Let the installation fail if you are on 64-bit, but leave the window open.  In another window 

cd /
sudo find -name *inkjet*

you will see something like the following:

/tmp/selfgz19007/pkg/files/lexmark-inkjet-09-driver-1.5-1.i386.deb

In another window, with the install stuff still open, 

sudo dpkg -i --force-architecture /tmp/selfgz19007/pkg/files/lexmark-inkjet-09-driver-1.5-1.i386.deb

Once it completes you can exit the failed installation and let the tmp file be cleaned up.

---

### Post by edsonmatos on 2012-08-31
After installing the driver, do this:

sudo modprobe usblp
sudo chown -Rh root:root /usr/local/lexmark
sudo chown -Rh root:root /usr/lib/cups
/etc/init.d/cups restart

gedit /etc/apparmor.d/usr.sbin.cupsd

*****Find:

  # FIXME: no policy ATM for hplip and Brother drivers
  /usr/bin/hpijs Ux,
  /usr/Brother/** Ux,

*****Copy and Past after this:

  /usr/local/lexmark/lxk08/bin/printdriver Ux,
  /usr/lib/cups/backend/lxkusb Ux,
  /usr/local/lexmark/lxk08/bin/lxkusb Ux,

*****Save the file

/etc/init.d/apparmor restart

---

