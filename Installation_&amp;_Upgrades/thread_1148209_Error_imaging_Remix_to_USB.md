---
title: "Error imaging Remix to USB"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by barking owl on 2009-05-04
I am brand new to linux & Ubuntu. After reading articles in TechRepublic & ITWire it sounded like a good idea to install Ubuntu Remix on a USB stick so one brand new 8GB stick, a download of Ubuntu Remix (Jaunty Netbook Remix i386) and a download of win32diskimager-RELEASE-0.2-r23-win32.zip. Unfortunately I did not even get to run Ubuntu.  When I start Disk Imager the error "Couldnt get handler on device" - Error 8 occurs. No other programs are open so what else can be using the USB? So I am hard put to get an image to the USB. A few questions please:

1. Is this the correct forum for this question?
2. What is this error and what is causing it?
3. Is there another utility to copy the image to the USB other than Disk Imager?
4. If I ignore the error and click 'Write' it seems to go through the process but the USB stick will not boot the netbook. The boot process goes to the second device.
TIA
td alias Barking Owl

---

### Post by udippel on 2009-05-04
I dunno about Windows. If you had a Linux/Unix/Solaris, you could easily use the 
dd if=NBR.img of=/dev/sdn
method.
(Read the precise instructions if not familiar with 'dd' and *nix.)
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)
has all the details.

Uwe

---

### Post by ddrichardson on 2009-05-04
We are advising that the disk is created from Windows in a command prompt using flasnul:
[https://wiki.ubuntu.com/UNR#From%20Windows%20Command%20Prompt%20using%20flashnul](https://wiki.ubuntu.com/UNR#From%20Windows%20Command%20Prompt%20using%20flashnul)

---

### Post by barking owl on 2009-05-04
Well! My first foray into linux is most illuminating. I think I can safely discount thoughts of Ubuntu with such extraodinary lengths needed to get a simple install done. If the other flavours of linux are as bad as this.....!!!!:lolflag: and lots of hollow laughter.
Goodbye

---

### Post by turnkit on 2009-05-05
lol.  you will likely be eating crow if you had the same problem I did...

I got the error too and was very sad:
"An error occurred when attempting to write date from handle.  Error 8:" 

So finally I tried the instructions again.

And I ran the 'command line' version from Windows cmd prompt.

Guess what?  I didn't get an "error 8"... wait for it...

I got a "Memory Card is WRITE PROTECTED" -!

doh!

(the SD card has a switch on it's side)  Yes - Win32 Disk Imager could be improved in this regard.  They call it making software "idiot proof" for a reason.  It's a good thing to do.

---

### Post by bobardu on 2009-05-06
I am having the same problem.  The Launchpad site where I downloaded the disk imager says that there is a solution for this "error 8" problem, but I cannot locate it.  I get the same error when using the newer version 0.2.

Bob

---

