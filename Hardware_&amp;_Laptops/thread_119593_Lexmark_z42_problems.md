---
title: "Lexmark z42 problems"
date: 2006-01-19
forum: Hardware &amp; Laptops
---

### Post by barnem1 on 2006-01-19
After some searching, and a little success, I have gotten stuck.  Bear in mind that I am quite new to both Ubuntu and Linux in general.

Here is where I am:
At first, Ubuntu found my printer (connected to USB port), and installed a driver for it.  However, it would not print at all.  You could send a test page, but nothing would happen.  After looking at linuxprinting.org, I decided to try the gimp-print driver.  I discovered that it was already installed on my system (located in /usr/share/cups/model/gimp-print/4.2/ as a gzipped ppd file).  So I copied this file to my home directory and gunzipped it.  I then chose to install a driver for the printer, and picked the newly unzipped file.  It loaded successfully, and I was able to select the "Lexmark Z42" printer model from the list, with "High Quality Image (GIMP-Print)" as the driver.

Now I have a new problem.  When I choose "Print a Test Page" the printer begins to print, but stops about 2 inches down, and the power LED blinks nine times.

I have tried deleting the printer and re-creating it, but got the same results.

I looked on Lexmark's website, but they show no linux drivers for the Z42.  They do show drivers for the Z52.  I downloaded these, and tried following a post on this site which explained how to install the drivers (they are RPM-based).  I do not believe I did it right, because I did not make it all the way through this process.  If someone thinks this option has promise, I will try again and take some notes on my results/messages.

The particulars of my system:
AMD-Athlon 64 on an Asus K8NE Deluxe motherboard
1.5GiB RAM
Multiple boot system with Breezy, Sarge, and WindowsXP.  Have not tried setting up printing in Sarge yet, because I am trying to get one distro working before moving to the next.
(Running AMD64 version of Breezy)

Any ideas or suggestions?

---

### Post by bernardfrancois on 2006-01-24
I would first try the [other driver mentioned on linuxprinting.org](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z42) ...

[edit]
Or maybe installing the latest gimp-print could help ([HOWTO](http://ubuntuforums.org/showthread.php?t=119595)) ?

And if you really can't get it to work maybe after trying the Z52 could work, but I think it might not work properly or not at all...

It's not a bad idea trying in Sarge first, maybe if it gets detected automaticly there, you could try to find out why it works there and then do the same thing in Ubuntu...
[/edit]

---

