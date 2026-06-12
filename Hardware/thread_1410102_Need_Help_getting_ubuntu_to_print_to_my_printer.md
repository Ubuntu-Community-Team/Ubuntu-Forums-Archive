---
title: "Need Help getting ubuntu to print to my printer"
date: 2010-02-18
forum: Hardware
---

### Post by egims on 2010-02-18
I love ubuntu, but am new to Linux and would appreciate help working through some problems. First, my printer.

I own a Lexmark X5470 printer. I am using ubuntu 9.10.

When I plugged my Lexmark X5470 printer into the computer ubuntu saw it and suggested the Lexmark 5400 Series driver. It installed the driver and life seemed good. However, it failed to print the test page and does not seem to be able to communicate with the printer.

If there is a fix, or a work around I would very much appreciate the benefit of your help and knowledge.

Ed

---

### Post by Objekt on 2010-02-18
Unfortunately, I don't think there is any way to make your Lexmark x5470 work under Ubuntu.  The Linux Foundation OpenPrinting database entry is here: [http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-5470_5400]("http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-5470_5400")

I am not 100% sure that means there is NO Linux driver for your printer, but it does look that way.

I am not sure why Ubuntu suggested the Lexmark 5400 series drivers.  As far as I can tell, NONE of the Lexmark 5000-series printers can be made to work in Linux.

It is really frustrating to have perfectly good hardware that you cannot use, due only to manufacturer obstinance.  They refuse to either write a Linux driver, or give out the specifications so that someone else can write a driver.  Sadly, this happens with a lot of PC hardware.

If you can afford to buy a different printer, look at an HP.  Almost all of their printers will work in Ubuntu.

If you really have to make that Lexmark x5470 work, you will have to either dual-boot Windows, or run a Windows virtual machine under Ubuntu.  I use the second option to make my Canon Multipass F60 work.

---

### Post by egims on 2010-02-18
You said:

"If you really have to make that Lexmark x5470 work, you will have to either dual-boot Windows, or run a Windows virtual machine under Ubuntu.  I use the second option to make my Canon Multipass F60 work."

How would one do that?
Once done would it be possible for other printers on the (windows network) to be able to share that printer?

THANKS!

---

### Post by Objekt on 2010-02-18
Yes, you can network-share a printer from a Windows virtual machine.  I do that so that the (non-virtual) Windows machines on my home network can also access the Canon printer.

To start, you will need virtualization software.  There are several options, but the one I'm most familiar with is Virtualbox.  

It would be better to start a new thread in the Virtualization forum than to continue here, so please have a look at the Virtualization section of these forums: [http://ubuntuforums.org/forumdisplay.php?f=308]("http://ubuntuforums.org/forumdisplay.php?f=308")

Feel free to ask for help there.  

You may also find useful info in the Virtualbox.org forums for Linux users: [http://forums.virtualbox.org/viewforum.php?f=7&sid=5cefc86b2a796ad97c25d34c88eab5ac]("http://forums.virtualbox.org/viewforum.php?f=7&sid=5cefc86b2a796ad97c25d34c88eab5ac")

Here is a set of instructions for installing the latest version of Virtualbox on Ubuntu 9.10:

[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

That should get you started.

---

### Post by egims on 2010-02-18
Thank you very much Objekt. Have a great day.__

---

