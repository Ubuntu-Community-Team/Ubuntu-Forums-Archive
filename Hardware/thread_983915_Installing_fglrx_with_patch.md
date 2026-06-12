---
title: "Installing fglrx with patch"
date: 2008-11-16
forum: Hardware
---

### Post by Worp8d on 2008-11-16
Hi,

I'm trying to install the latest fglrx (8-11) to Intrepid 8.10 running on an AMD64 Asus F5 laptop with an ATI Mobility Radeon HD 3200 graphics card.  The standard fglrx drivers simply won't download and install from the Restricted Drivers program.

I download the driver and follow the install instructions found at the "Unofficial ATI Linux drivers wiki", 
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually") ,
and everything runs smoothly, no errors at all, until I restart the computer and I get what I can only presume is the "black screen of death" that I keep reading about.  This is a text login to Ubuntu with a series of error saying something about not being able to find a 'knit image'?  Sorry but I foolishly didn't write down the error before I angrily re-re-installed the system.

I understand that to get fglrx 8-11 working with the 2.6.27 Linux kernel you need to use a patch for the file **firegl_public.c** which can be found at [http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg586833.html]("http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg586833.html")

I think that that I need to either add this patch function to the original firegl_public.c or replace a section of it, I'm not sure which, and then recompile the fglrx-kernel-source package?  As you can probably tell this is where I get lost.  I don't see where in the fglrx installation istructions I would be recompiling this source package and I don't know how to get the patched code into the install.  Any help?  Also, does anyone know if the patch is the solution to the problem of fglrx destroying my system?  I'm getting rather tired of OS reinstalls.

Thanks in advance.

---

