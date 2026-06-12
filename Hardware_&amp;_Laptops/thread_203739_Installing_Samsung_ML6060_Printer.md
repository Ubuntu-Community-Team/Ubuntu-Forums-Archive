---
title: "Installing Samsung ML6060 Printer"
date: 2006-06-25
forum: Hardware &amp; Laptops
---

### Post by Tulip on 2006-06-25
Hello!
I am having difficulties installing a Samsung ML-6060 laser printer. I have visited the Samsung site and there are 2 Linux drivers for this printer, a i386 driver and a PPC driver. Im not sure which one to get. I have downloaded both, but they look pretty much the same. The PPC readme informs me :-

[COLOR="Red"]SUPPORTED CONFIGURATIONS
------------------------

- Linux distributions : Redhat 6.x, Mandrake 7.x, SuSE 6.x, Debian 2.2, 
  Caldera OpenLinux 3.x, TurboLinux, Slackware 7.x, Linux/PPC, Yellow Dog,
  and newer versions.
- Linux kernel 2.2 and up
- GNU Libc version 2.1 and up

Requirements :
- GTK+ 1.2 libraries ; these usually come with the GNOME desktop environment,
  but if your distribution didn't install those by default, you will need to
  install them before you can use the graphical tools from this package.
- A working Ghostscript installation
- CUPS 1.1.x is the preferred printing system for this package, but the
  Linux Package will accommodate any other printing system based on LPD.
  CUPS 1.1.14 packages are provided as a convenience with this program, and can
  be installed or upgraded from the installer. However, users of Debian and
  Slackware distributions should make sure they have an active printing system
  (such as LPD) before proceeding with the installation.
[/COLOR]

The readme requires me to be logged in as super-user (root). I have run the setup.sh file in terminal and supplied my regular log-in password, is this what is required? I was expecting a setup menu to appear afterwards but nothing happened. 

I was able to manually add 2 ppd drivers (pcl and ps) to the printer wizard that I found in the extracted installation folder, but I dont think I am going about this correctly. When I install the printer with the pcl driver, nothing prints. When I install the printer with the ps printer I get 
%!PS-Adobe-3.0 %%Title: PPR Test Page %%DocumentNeededResources: font Helvetica% printed on the top of the first page, and a stack of blank pages following.

Can anyone make some recommendations for me to try please?
Cheers

---

### Post by arepaking on 2008-07-18
I'm having this issue as well. Did you find a solution for it?

---

