---
title: "Sane - Scanner bumps head Lexmark x1155 Print Trio"
date: 2008-09-19
forum: Hardware
---

### Post by gvigorus on 2008-09-19
Folks, can someone help. I read a lot prior to this post, so I'm out of ideas.
My scanner does not scan, though it used to. Basically, I'm using sane with Lexmark X1155 built in scanner. So, everything detects:
$ scanimage -L
device `lexmark:libusb:001:015' is a Lexmark X1100/rev. B2 flatbed scanner

$ sane-find-scanner
found USB scanner (vendor=0x0b05, product=0x1723) at libusb:003:002
found USB scanner (vendor=0x043d, product=0x007c, chip=rts8858c) at libusb:001:015
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

$lsusb
Bus 001 Device 016: ID 043d:007b Lexmark International, Inc. 
Bus 001 Device 015: ID 043d:007c Lexmark International, Inc. 
Bus 001 Device 014: ID 043d:007a Lexmark International, Inc. 

as you can see, everything is there, but sane for some reason just bumps head of the scanner and does not produce anything.

One thing i noticed was that in GIMP - File - Acquire - Xscanimage i have two option:
Device Dialog
lexmark:libusb:001:007

When i click on lexmark:libusb:001:007 i get Failed to open device 'lexmark:libusb:001:007': invalid argument.

But lsusb command shows my scanner on 001:015 so does that mean that the sane front end is looking for a non existing device? Shouldn't it be looking at 001:015?

Thanks for any help. I really need my scanner and I'm getting pretty frustrated.

---

### Post by gvigorus on 2008-09-22
Peculiar thing. I just booted from a Knoppix CD a while ago and tested the scanner with Xsane that came with Knoppix. Well, it worked. So, maybe i could somehow copy all of the drivers or files from Knoppix to my Xubuntu? Anyone knows what i'd need to copy? Just a thought...

---

### Post by gvigorus on 2008-09-24
So, what I decided to do on my quest to get the scanner working is to remove all sane pertinent files and directories and install everything afresh.
Sane site has Q&A regarding removing files, here's what it says:

[http://www.xs4all.nl/~ljm/SANE-faq.html#43](http://www.xs4all.nl/~ljm/SANE-faq.html#43)

---------------------------------------------------------------------------------------
4.13. I want to do a clean installation. How do I get rid of all the older versions?

Since SANE 1.0.5 there is a "make uninstall" which removes SANE completely. However it only removes from the current prefix, so if the old SANE is located in /usr and you use the standard SANE sources, it won't be removed. Configure will warn about old versions at different locations if it can find them.

There is no filelist for older versions, and there are more places where you can install sane. The following will remove most ofthe sane-files:

 find /usr -name "*sane*" -type f -print -exec rm {} \;
 find /usr -name "*sane*" -type d -print -exec rmdir {} \;

Some caution is needed: this removes anything that looks like sane. This may include other applications, files or the tgz of your new version, as I found out myself :-(

Alternatively remove the following directories:

 /usr/(local)/lib/sane

 /usr/(local)/lib/libsane*

 /usr/(local)/include/sane

 /usr/(local)/etc/sane.d

 /usr/(local)/share/sane*

 /usr/(local)/bin/scanimage

 /usr/(local)/bin/xscanimage 

 /usr/(local)/bin/xsane

 /usr/(local)/share/sane/xsane

This may leave some files for natural language support (xsane.mo and possibly sane-umax.mo and sane-pnm.mo). Use find to find them.
---------------------------------------------------------------------------------------
I first used synaptic to remove sane and xsane with whatever else they come.
Then i followed the above methods and cleaned everything by hand. I used the alternative method above by the way, not the aggregate where you wipe out everything with "sane" in it. That seemed kind of rather harsh. 

Anyways, I'm going to try reinstalling sane with Synaptic and hopefully that will resolve the issue. Again, i want to point out that my scanner used to work perfectly under Ubuntu 8.04 It's only after I installed something, like new backends that it started to give me trouble. Also, scanner works fine when i boot from CDs like Knoppix.

---

### Post by gvigorus on 2008-09-24
Update: I noticed that my scanner worked well under Knoppix CD. I looked at what backends Knoppix was using and it was 1.0.18 version (current version as of writing is 1.0.19)
I got 1.0.18 version tarballs from Sane site, compiled and installed. Then I installed Xsane and all worked. I can scan now, however there was one issue. I could only scan while root.
The error message I was getting was "Failed to open device Access to resource has been denied". After a little search, i've found that I needed to change read write privileges for the USB file. Mine was at /dev/bus/usb/001/003
so i did sudo chmod 666 /dev/bus/usb/001/003 and all worked.
I don't think I'm going to try to recompile sane backends version 1.0.19 Just happy my scanner is back in busness!
[http://ph.ubuntuforums.com/showthread.php?t=410398](http://ph.ubuntuforums.com/showthread.php?t=410398)

---

