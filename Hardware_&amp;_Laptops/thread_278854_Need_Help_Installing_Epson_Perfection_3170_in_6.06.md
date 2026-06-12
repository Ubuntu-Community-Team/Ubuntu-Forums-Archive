---
title: "Need Help Installing Epson Perfection 3170 in 6.06"
date: 2006-10-17
forum: Hardware &amp; Laptops
---

### Post by Iowa Dave on 2006-10-17
I'm looking for help getting an Epson 3170 scanner to run in 6.06. So far I've only tried this in the "Live CD" version, which I'm evaluating before installing to the hard drive. The scanner attaches to a 32-bit x386 machine via USB. I followed the directions on a very nice site: [http://ubuntu.flowconsult.at/en/epson-3170-installation/](http://ubuntu.flowconsult.at/en/epson-3170-installation/).

====================
The steps were:
1. Open the webpage of the EPSON AVASYS Corporation, fill in the form (Perfection 3170 Photo, debian or other) and download the rpm package (for gcc 3.4 or later), specifically iscan-2.3.0-1.c2.i386.rpm. CD to the directory where that was downloaded.
2. Install alien, if not already installed.
     sudo apt-get install alien

3. Convert the rpm file to the standard debian/ubuntu format.
     sudo alien -d iscan*.rpm

4. Install the deb file.
     sudo dpkg -i iscan*.deb

5. The following edits the file /etc/sane.d/epkowa.conf and adds a comment to the line with scsi EPSON.

sudo perl -p -i.bak -e 's/scsi EPSON\n/#scsi EPSON\n/g' /etc/sane.d/epkowa.conf


6. Next in the file /etc/sane.d/dll.conf epson is changed to #epson and epkowa added.

sudo perl -p -i.bak -e 's/epson\n/epkowa\n#epson\n/g' /etc/sane.d/dll.conf


7. Connect the usb cable and switch on the scanner.

8. Start xsane from your graphical menu or start iscan.

     iscan

===============
But it didn't work. The first time I ran iscan a dialog box appeared stating that it could not send a message to the scanner. Subsequent calls to iscan, and also running XSane from the graphical environment, produced nothing at all. I checked lsusb, and the scanner definitely appears there. I tried cat /etc/sane.d/dll.conf and saw #epson and epkowa as they should be. I checked cat /etc/sane.d/epkowa.conf and the only line uncommented is usb. I checked the epkow man page and the Epson 3170 is listed among the supported scanners. So I am stumped. Would be grateful for any success stories that can be followed to a happy ending.

Thanks,

Dave

---

### Post by Iowa Dave on 2006-10-22
:( Well, it's been five days with no replies. I have to admit being underwhelmed with the response. The Ubuntu "community" has done a much better job on its PR about how wonderfully helpful it is, than it does actually delivering help. 

Frankly, it feels like a typical "Corporate" software experience. So... where does this leave us? Still on our own with Linux, as always. 

No doubt some Ubuntu fanboy will post a dazzling flame about me now. But that would kinda prove the point, wouldn't it? Linux still can't do what my 8-year old Windows 98 has been doing for 8 years -- run my printer and scanner. The specific printer and scanner are on "official" lists of Linux-capable devices from good-guys hardware makers (Epson and Brother) that actually support Linux. But the "community" seems oddly content to leave each user to hook everything together. I think that the early adopters of Linux enjoy this challenge. But they already have Linux working. A far larger number of people would like to use Linux, but find these kinds of challenges discouraging.

Guys, I'm not knocking Ubuntu Linux. I'm talking about what needs to happen next to make a good operating system into a great solution for a lot more people. Edgy is already here, so take this idea up for Faultless Ferret or Grizzly Groundhog or whatever. Take a list of scanners and printers that already do support Ubuntu (with some assembly required) and make Ubuntu support them. Build support into the distro for Linux-friendly document-handling devices like printers, scanners and cameras. Proudly publish the list of supported hardware. It's what home users buy computers for.  These things--at least the ones that made a conscious decision to support Linux--should not be a mystery on Linux 2007 when they already works without a hitch on Windows 98 and Mac OS X (the Other Unix).

Thanks,

Iowa Dave

---

### Post by Iowa Dave on 2006-10-23
Still no comments? Well, just to show I'm not a total noob, I wanted to let the community know that I'm posting from a fresh installation of 6.06. Also, I did get the Brother HL-2070N network laser printer working this evening.

Things went great with the installation, but not so smoothly with the printer. Some things did not work the way Ubuntu documentation says they will. For example, the directions in /etc/share/cups/README.Debian for adding yourself to the list of authorized users for managing CUPS via the browser interface? Those don't work. You really, really, have to use the graphical desktop tools as I'll describe next. Thanks goodness enough other people have posted various how-to's here in the forum and elsewhere. Eventually it came clear what I needed to do and now my Ubuntubox can use the network printer.

To set up the 2070 as a network printer on Ubuntu 6.06 follow the directions at [http://ubuntuforums.org/showthread.php?t=123539](http://ubuntuforums.org/showthread.php?t=123539) with a couple of changes. At steps 1 and 2 get the driver for the 2070. At steps 3, 4 and 5 use "sudo" in front of each of the code lines. Remember to type in the names of the actual files you downloaded at steps 1 and 2. Don't follow step 6. Instead use System > Administration > Printing. The HL-2070N should be showing when the window opens up. Delete it. Double-click New Printer. Add a CUPS network printer. Give the url as ipp://your.printer's.lan.address. (Mine was ipp://192.168.106 for example.)  You have to do step 6 this way because they changed Ubuntu at Dapper so that going to CUPS through localhost no longer works.

Step 7 is still the same. I hope you do that often!

The directions at [http://www.martinhenze.de/2006/06/10/brother-hl-2070n-and-ubuntu-linux/](http://www.martinhenze.de/2006/06/10/brother-hl-2070n-and-ubuntu-linux/) will work for installing the printer as a locally-connected USB device.

I'll clean this up in a fresh post with the printer in the title Since I had so much trouble finding the answer, I might as well share it.

Dave

---

### Post by super carrot on 2006-11-03
Sorry to hear about your problems and not getting the help that you needed. But I will tell you one thing. Thank!
I couldnt seem to find that information when I checked out the Avasys website. But since you posted it. It now means that I have got my scanner working on sane! Nice one. I am about to see if my printer will work just as easily. Currently using Turbo Printers drivers, and they are very good! But I am still interested in checking out the alternatives anyway.:-D

---

### Post by rwillia2001 on 2006-11-09
Hi  - Very Interesting Post. Have you been able to solve the install 3170 problem? I ask because I have the exact same problem and have 100% accurately duplicated your findings using 6.06.

Cheers for any information on solving this.

---

### Post by bmt on 2006-12-08
> **rwillia2001 said:**
> Hi  - Very Interesting Post. Have you been able to solve the install 3170 problem? I ask because I have the exact same problem and have 100% accurately duplicated your findings using 6.06.

Cheers for any information on solving this.
I've had similar problems with a 3490 Photo, which I have now solved, I think.  (I'll see if it still works tomorrow ...)

When you go to the download page (at Avasys), there is also a package for a plug-in.  Don't be fooled by the 'gt-9400' in the package name -- it still needs to be installed.  Use the same method for the plug-in package as for the iscan package (alien then dpkg).  I spent days trying to get my 3490 working, not realising that the gt-f520 plug-in was also necessary.

Also, for the main iscan package, did you use the --scripts option with alien?  If not, you will need to run alien on it again, otherwise there is an error from alien (unable to handle the scripts).

Incidentally, there is now a newer version of iscan available (v.2.4), so you may want to start again with that.  It updates over the v.2.3 with dpkg.

HTH.

---

### Post by bsulzen on 2006-12-19
I got my Epson 3170 working using the method described at [http://ubuntu.flowconsult.at/en/epson-3170-installation/](http://ubuntu.flowconsult.at/en/epson-3170-installation/)

Running Kubuntu Edgy (32bit) on my machine.

Copied and pasted the commands into the terminal. I made a minor change to the last bit of code.  Added the -c option after the first alien call and changed "xane" to "iscan" at the end. Also left off apt-getting alien because I already had it and I manaully CD'd to the Desktop directory.
See code below:
```
sudo alien -d -c iscan*.rpm && sudo dpkg -i iscan*.deb && sudo perl -p -i.bak -e 's/epson\n/epkowa\n#epson\n/g' /etc/sane.d/dll.conf && iscan
```

Typing "iscan" at the terminal prompt prints two separate errors, but opens the Iscan GUI tool and functions perfectly.  Can also scan directly from Gimp.

---

### Post by Iowa Dave on 2007-03-23
Bsulzen, thanks a million!  With the information you gave us, the Epson 3170 works on my Dapper (6.06 LTS) installation.

Wow! this was the last thing I needed in order to leave Windows 98 behind in the dust. Wonderful! (Can you tell I'm delighted?)

I kinda gave up on Linux for a while last fall and early this winter. But I came back to it. I built my first barebone computer a couple of weeks ago and installed Dapper as the only operating system. With one driver upgrade, it turned into a wonderful desktop computer.

In reply to "bmt" above, I looked on the Epson Avasys download page and your 3490 is one of the selections on the driver form. I can't check that it works because I don't have a 3490, but it would sure be worth a try.

BTW, I don't get the error messages that Bsulzen mentioned. iscan in a terminal, and xsane Acquire in GIMP both "just work". The scan adjustment tools are, if anything, easier to use than in the Windows driver for my 3170.

This series of postings on the Community Forum is exactly how Ubuntu differs from most other distros. Thanks to all who replied.

---

### Post by momchilk on 2007-03-24
Bsulzen, many thanks from me too. Works great under Ubuntu 6.10 Edgy!

---

### Post by Devius on 2007-03-24
Iowa Dave, I understand what you mean by "The Ubuntu "community" has done a much better job on its PR about how wonderfully helpful it is, than it does actually delivering help." I never got a reply to any of my questions on my country's ubuntu forum, so I decided to try this global forum... it's the same thing. No reply. 

Here's my problem: I'm trying to use my Epson Perfection 610 which is supposed to work straight away, except that it doesn't. I did all the steps in this thread and managed to install iscan 2.5 and edit the mentioned files, but it still doesn't work. 

More details here:

[http://www.ubuntuforums.org/showthread.php?t=389067&highlight=perfection+610](http://www.ubuntuforums.org/showthread.php?t=389067&highlight=perfection+610)

I would be very grateful if someone could give a clue on what's going on!

PS: In my case there is no GT-xxx plugin on the avasys download page.

---

### Post by Iowa Dave on 2007-04-07
Wish I could help, Devius. But I'm as new to this (at "8 beans") as you are.

Keep checking the forums.  My answer took a while to arrive but eventually the right person came along. 

I think that scanners and wireless are two of the areas where Linux continues to struggle with hardware compatability. But each, new distro makes progress. Perhaps the upcoming 7.04 "Feisty" release of Ubuntu will bring a solution, as it is supposed to offer more support for "non-free" hardware drivers.

My concern that the Ubuntu community might be unresponsive was premature. Now that I've been using it a while, I am happy to say that Ubuntu is the first distro where people have actually helped. I'm learning more every day. Hope the same happens for you, and soon!

---

### Post by th0mas on 2007-04-24
My Perfection 3170 never worked with Ubuntu so far...

BUT

it seems that with Feisty, it might work.

I following the usual tutorial to install it. Now when I start xsane or iscan, I can hear that my scanner is recognized (I can hear the mecanical "bzzz !").

BUT

actually, it doesn't work cause then iscan/xsane get stuck. I have this error in my /var/log/messages :

```

$ sudo tail /var/log/messages
...
Apr 25 00:49:56 localhost xsane: unable to open /var/run/hplip/hpiod.port: No such file or directory: api/hplip_api.c 93

```

any clue ?

---

### Post by th0mas on 2007-04-27
ok i retried today to launch iscan but as root this time and it worked !

but actually, it works as well as non root. The problem is that it's very slow to launch, it seems to be stuck for almost 4 minutes then it works.

Any clue about this ?

And I still have this problem in my /var/log/messages anyway : unable to open /var/run/hplip/hpiod.port: No such file or directory: api/hplip_api.c 93

---

