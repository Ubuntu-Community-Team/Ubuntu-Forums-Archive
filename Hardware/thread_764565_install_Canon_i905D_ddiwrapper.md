---
title: "install Canon i905D ddiwrapper"
date: 2008-04-24
forum: Hardware
---

### Post by fhmanas on 2008-04-24
Hello, I am using Gutsy, I am moving from WinXP. I need to install my printer, Canon i905D. Buying a new printer is not an option. I know Turboprint, and it works with the Canon i905D, but i would like to try other options before I cough out $30 for the license.  I know ddiwrapper was developed by Suse and comes in rpm and source.  I also know that ddiwrapper supports my particular printer.  I want to try out ddiwrapper, but i can't install it since it is rpm.  I tried converting rpm to deb with Alien, did not work.  Am trying to compile from source, but am getting all sorts of errors.  Am new at compiling in Linux, I prefer installing from repositories as it is convenient and clean.  

Please help in installing ddiwrapper in Ubuntu and getting my printer to work.

Thanks in advance.

---

### Post by dmizer on 2008-04-24
it will take a bit more effort, but you'll probably be happier building a deb package from source.  try this guide: [http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)

this way, you can install (and even better: cleanly uninstall) the package with synaptic.

---

### Post by fhmanas on 2008-04-26
Thanks for pointing out that link, i tried to follow it but I stopped since the source does not contain a configure file, and I don't where to start to make one.

In any case, if anybody can help me out.  I'm posting the tarball that I got from [http://www.linuxprinting.org](http://www.linuxprinting.org).   I just rezipped it since the forums does not allow .tgz.

---

### Post by dmizer on 2008-05-23
it's been a while, so i wonder if you've solved this or not.

looks like it depends on wine.  you'll have to install wine for the compile to work.  don't know why it doesn't have a config file, but as long as you have the "build-essential" package as well as wine installed, you should have everything you need to make this work.

here's from the readme in the package source:
> 2. QUICKSTART

This section will help you getting a working setup for printing to your
Windows-only printer via CUPS and the Windows XP printer driver.

a. Make sure you have a recent version of WINE installed. Anything released
after August 2004 should work fine.

b. Run "make && make install"

c. Get the Windows 2000 or XP driver archive for your printer from the
driver download section of the Canon web site of your choice.

d. Install the driver, preferably to /usr/share/ddiwrapper/drivers/default

  excanondriver <driver>.exe /usr/share/ddiwrapper/drivers/default

If you install it to a different directory, you will have to change the PPD
file accordingly before injecting it into the CUPS system. excanondriver
uses cabextract, unzip and recode, so make sure you have these installed.

e. Inject the PPD file into the CUPS system

  lpadmin -p ddiwrapper -v usb:/dev/usblp0 -P doc/ddiwrapper.ppd -E

This will create a printing queue called "ddiwrapper" that, if printed to,
will pipe PostScript input through GhostScript, ddiwrapper and the Windows
printer driver out to your USB printer. If you are using a graphical user
interface such as kprinter you can use it to choose paper format, paper
type, duplex mode and printing quality.

f. Finished. Now you should be able to print to your formerly unsupported
Canon printer through CUPS.

---

