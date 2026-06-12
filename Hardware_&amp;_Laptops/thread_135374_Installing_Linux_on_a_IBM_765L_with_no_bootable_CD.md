---
title: "Installing Linux on a IBM 765L with no bootable CD"
date: 2006-02-23
forum: Hardware &amp; Laptops
---

### Post by RichGags on 2006-02-23
Hi!
I have a major problem.  I have a IBM Thinkpad 765L laying around and Id like to install any version of Linux on it.  This laptop has a CD rom drive and a floppy drive.  The bios does not allow booting to the CD.  I can boot to a floppy, then remove the floppy drive and put the CD drive in.  

How do I, or can I mount the CD and install Linux to the HD?  There is no OS on the HD.

I also have another neet device called a USB->IDE adapter, whereas I can take the HD out of the IBM and hook it up USB to my Dell (which I am on now) and write any files I want to that HD....  Then how would I get the IBM to boot from there?  Is this possible?   Any help would be awesome.  

Thanks!

---

### Post by Nightwind on 2006-02-25
[QUOTE=RichGags]Hi!
I have a major problem.  I have a IBM Thinkpad 765L laying around and Id like to install any version of Linux on it.  This laptop has a CD rom drive and a floppy drive.  The bios does not allow booting to the CD.  I can boot to a floppy, then remove the floppy drive and put the CD drive in.  

How do I, or can I mount the CD and install Linux to the HD?  There is no OS on the HD.

I also have another neet device called a USB->IDE adapter, whereas I can take the HD out of the IBM and hook it up USB to my Dell (which I am on now) and write any files I want to that HD....  Then how would I get the IBM to boot from there?  Is this possible?   Any help would be awesome.  

Thanks![/QUOTE]
Well there are several ways to do it, SBM, Toms etc. None are as simple as some people would have you believe. 
You won't find a Ubuntu boot floppy anywhere, if you do I and several other hundred people would like to know where. I decided to go with Debian Sarge and Free BSD because they give the option to make boot floppies where as Ubuntu doesn't. I'd say if you want it short sweet and simple, try Debian Sarge or Free BSD. There are others but those are the ones that worked for me. I'd think with your ide-usb adapter that you could copy it over and some way make it work, which is beyond my brain power ability.

---

### Post by RichGags on 2006-02-25
Problem solved.   With the help of my USB to IDE tool.  Here's what I did (for future readers who may have the same problem.)

1.  Obtain a Windows 98 SE boot disk.
2.  Boot to the Windows 98 SE boot disk.  Format c: /s (copies the system files to the c drive and makes it bootable).
3.  Remove the hard drive, hook it up via USB to IDE to any other machine.  
4.  Create a directory and copy the contents of the install disk of any OS you'd like to it.  
5.  Put it back in the 765L, boot to c drive, cd to your new directory and run the OS setup.

I wonder if somewhere in the world exists an upgarde to the bios of the 765L to make the cd drive bootable....

---

