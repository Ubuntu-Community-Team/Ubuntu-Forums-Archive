---
title: "Epson Perfection V700 Photo"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by satbunny on 2007-02-04
Chums,

I am trying to get my Epson Perfection V700 Photo to work with xsane .991 and sane 1.0.18-3 ubuntu under Ubuntu 6.10. I have installed every libsane I can find on my repostories. But when I try and scan usng xsane it reports Failed to start scanner: invalid argument. 

The scanner does exist and sane-find-scanner reports:

> 
sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x046d, product=0x0920, chip=ICM532B?) at libusb:005:007
found USB scanner (vendor=0x04b8 [EPSON], product=0x012c [EPSON Scanner]) at libusb:005:008
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.



The scanner works fine on the same PC under Windows.

I read a post on sane dev which suggested:

> 

> I can confirm your hunch, the V700/V750 scanners do use the ESC/I
> protocol, and from what I know (I have not seen one yet) about these
> scanners, chances are pretty good that they will work the current
> version of the EPSON backend. You do need to add the USB information
> to the epson.desc file as Olaf indicates.

Or just stick it in epson.conf, like so:

  usb 0x04b8 0x012c





Do you have any advice? Has anyone got this scanner and got it to work?

Tom

:guitar:

---

### Post by satbunny on 2007-02-04
Ok.

If I goto to

/etc/sane.d/

and edit

epson.conf

and replace 

usb 

with

usb 0x04b8 0x012c

it seems to work.

I am now also going to see if I can install the AVASYS scanner package from EPSON in case that offers greater functionality.

---

### Post by satbunny on 2007-02-04
Ok, this is turning into a tutorial not a cry for help, but I will continue since it'll help somone.

Epson AVASYS do a Linux scanning package called iscan and this is how I installed it.

First of all I used Synaptic and removed the libsane-extras package, since it conflicts with the driver that the EPSON package installs (even if they are the same, which they may be).

I then downloaded the rpm from the website..

[http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)

and popped it in a folder.

I then converted it to a .deb using alien..

# sudo alien -d -c -k iscan-2.5.0-0.c2.i386.rpm

(of course the file name may have changed by the time you read this)

and then installed the resulting.deb file

# dpkg -i iscan-2.5.0-0.c2.i386.deb

I then ran the app as

# iscan

Voila!

---

### Post by Midahed on 2007-08-01
Well, thanks Satbunny, you were right.  It helped a great deal! :)

I've been using Ubuntu 7.04 Feisty Fawn 64-bit workstation for about six weeks.  With your help it's only taken about half an hour to get my Epson Perfection V700 Photo scanner working.

Probably because I'm new to the Linux environment, I came across a couple of problems which I'll document here in case anyone else falls foul of the same issues.

First, I used Synaptic to see what had already been installed.  I found xsane was already there, but sane and sane-utils were not.  It wasn't immediately clear to me whether xsane included sane functionality, so I tried a few things without having sane installed.

First, running the command xsane in a terminal session returned the message 'scanning for devices' and then 'no devices available'.  I got the same thing if I loaded GIMP and selected File, Acquire, Xsane, Device dialogue.

I concluded that sane and sane-utiils needed to be installed.  Maybe I was wrong about this?  It struck me as a bit odd that xsane was already installed when it appears to rely on sane which wasn't there. :???:

Having installed sane and sane-utils, I found that running **sane-find-scanner** returned the message 'found USB scanner (vendor 0x04b8, product 0x012c) at libusb:005:004', but running **scanimage -L** still said 'no scanners were identified'.

Checking in **/usr/lib/sane** showed a number of libsane-epson files present, so I assumed the epson backend was present and correct.

As documented in your post, I then amended the usb line in** /etc/sane.d/epson.conf** to read  'usb 0x04b8 0x012c' (without the quotes).

Running **scanimage -L** then returned the message:- "device 'epson:libusb:005:004' is a Epson GT-X900 flatbed scanner".  Strange that it doesn't report the 'right' model, but it subsequently became obvious that it didn't matter.

However, xsane still reported 'no devices available'.  I then discovered that if I ran xsane as root  it all worked fine.  

**Read the [EDIT] section below before you proceed any further!**  

A bit of trawling the forums revealed that I needed to run the command lsusb.  This returned the following output:-

```
Bus 005 Device 004: ID 04b8:012c Seiko Epson Corp. 
Bus 005 Device 003: ID 05e3:0606 Genesys Logic, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 1241:1111 Belkin Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

The Epson line shows that my scanner is on bus 005 and is device 004 (these numbers will probably be different on your PC so, if anyone is following this, you need to run lsusb and get your own bus/device numbers).

I then ran the command **sudo chmod a+w /dev/bus/usb/005/004** to change the permissions (where 005 is my bus number and 004 is my device number).

**[Important EDIT]  The above solution doesn't work very well.  Here's a _better_ way of getting over the 'xsane only runs as root' problem**

After originally posting this, I found a couple of problems with the chmod solution documented above for getting round the situation where xsane will only run from the root account.

First, if you power-off or disconnect the scanner and then power it back on or reconnect it, the device number changes.  Mine increased from 004 to 005 every time I tried it.  Although it seems to return to its original number when the system is re-booted, it does create a problem if you have to disconnect the scanner mid-session.  The upshot is that the chmod command has to be run a second time using the 'new' device number before xsane will run outside the root account.

The second problem is that the chmod fix doesn't seem to persist after a re-boot.  I found that I needed to run the command each time I powered the system and wanted to use my scanner.  This is a bit inconvenient.

Again, after trawling the forums I found what seems to be a better solution - edit the udev rules to change the permissions for the usb sub-system.  To do this, you need to edit the 40-permissions.rules file:-

**sudo gedit /etc/udev/rules.d/40-permissions.rules**

Scroll down the file until you find an entry that says:-

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",		MODE="0664"

Change the MODE="0664" to MODE="0666" and save the file, then _reboot._
[B]
End of [EDIT][/B]

I now find that I can unplug and re-connect the scanner without the fix having to be re-applied because the device number has changed. 

After doing all this, xsane ran OK as non-root and it continued to work after a reboot.  I could also launch it from GIMP via File, Acquire, Xsane, Device dialogue.

If you had the 'will only run as root' problem, you might find that even after fixing it, you get an error that says "Failed to create file - Permission Denied" when you close Xsane.  This is because, if Xsane is run for the first time as root, it creates a .sane folder in your home directory with root permissions.  The solution is to delete the .sane folder and it will be recreated with the correct permissions next time you run Xsane.

I wanted to try iscan as well, but I'm running the 64-bit version of Feisty 7.04, and it's not packaged for that environment.  Did you find it any better than Xsane?  If so, I might try to compile it for 64-bit operation.  But as I haven't compiled anything previously, that will be tomorrow's project. :)

Mike

---

### Post by satbunny on 2007-08-02
Great! At last I helped someone after all the help I got here over time!

I use iScan as my default programme, but recently downloaded Vuescan from Hamricksoftware, for which I have a licence having used it on Windows for years before I migrated to Linux.
This is the best scanner software ever and just works, but it does cost, but I would be doing everyone a disservice to mention it since it understands and gets the best results and speed from almost any scanner and we should support people who write native Linux products.

[http://www.hamrick.com/](http://www.hamrick.com/)

As to iScan as a 64bit, give it a go!

---

### Post by Midahed on 2007-08-02
Hi Satbunny,

Thanks for the info about your use of iScan and Vuescan.  I'd read good stuff about Vuescan in the past...  However, I think I'll have to stick with Xsane for the moment.  Having played with it for a while yesterday, it seems OK.  

I did a bit more reading about the issues around compiling and linking the source of 32-bit programs to work in a 64-bit environment, and it sounds as though it's fraught with problems. So I think I'll be giving iScan a miss and sticking with Xsane for the moment.

Regards,

Mike

---

### Post by satbunny on 2007-08-03
If you're scanning negatives or slides then iScan is useful and Vuescan is superlative. If it's "just" plain paper and photo prints then you don't need them.

---

### Post by _oOMOo_ on 2007-08-04
Great to see others using the V700 in Ubuntu - I did very much the same thing last year with alien and the Epson .rpm, and use Vuescan as it has such an advanced set of features which I'm happy to report all work well in Ubuntu. I do miss the Epson software a little when scanning 35mm negatives as it was quite good at auto-cropping, but Vuescan now auto-crops 35mm slides a treat.

As far as I know the V700 is called the GT-X900 in Japan, and I'm pretty sure libsane-extras package makes some use of the AVASYS driver which would explain the name. Incidentally on Gutsy the scanner is recognised and usable without any additional tinkering (at the moment :))

---

### Post by Midahed on 2007-08-05
I may give Vuescan a try - apparently it works OK in a 64-bit environment provided that some 32-bit libraries are available.

Mike

---

### Post by kaybee on 2007-09-09
Thanks very much guys,

I got my V700 up and running in 20 minutes or so ...

Thanks for the help,
Cheers,
Kris

---

### Post by satbunny on 2007-09-10
Well I just did a virgin install of Feisty and then used this thread to get it all up and running again, also in about 20  minutes, now how can we make this thread sticky?

---

