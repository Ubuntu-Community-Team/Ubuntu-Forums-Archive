---
title: "Scanner HP6200C scanner not working on Gutsy"
date: 2008-03-17
forum: Hardware &amp; Laptops
---

### Post by smi402 on 2008-03-17
I am running 64 bit Gutsy on an Intel CoreDuo based machine.
*xsane-0.99+0.991-3ubuntu* is installed along with these versions of *xsane-common *and *xsane-doc*

My **HP ScanJet 6200C** scanner, which is supported by the Sane hp(1.06) backend and  has worked on earlier 32 bit versions of Ubuntu and Gentoo in the past, is not working under Gutsy on this new 64 bit machine. The scanner is recognized correctly by [COLOR="Red"]lsusb[/COLOR] and by [COLOR="Red"]sane-find-scanner[/COLOR]. However running [COLOR="Red"]scanimage -L[/COLOR] results in a **Segmentation fault (core dumped)** error. A similar error is produced when [COLOR="Red"]xsane[/COLOR] is run from a terminal. Running [COLOR="Red"]xsane[/COLOR] from the Graphics menu results in a very brief message about **¨Scanning Devices**¨which is then immediately removed from the screen.

Can someone please help me get this scanner working under Gutsy?

---

### Post by smi402 on 2008-03-17
Some Progress:

By deleting all entries in the file /etc/sane.d/dll.conf except for hp, [COLOR="Red"]scanimage -L[/COLOR] now recognises the HP 6200C scanner. [COLOR="Red"]xsane[/COLOR] also finds the scanner and starts up. However there is still some problem since approximately 4 times out of 5 when acquiring a preview or doing a scan it brings up a message **¨Failed to start device: Error during device I/O**¨. By persisting a little it will eventually start the scan and complete it though.

Anyone know what is going on??

---

### Post by smi402 on 2008-03-17
Aha! Problem now fixed.

I have a Samsung CLP-510 printer on my network which I installed using the Samsung Unified Printer Driver. Installing this driver adds a line **smfp** at the end of the original file */etc/sane.d/dll.conf*. As this is not a multifunction printer that line needed to be commented out by placing a # in front of it.

The Samsung Unified Printer Driver also changes a number of file ownerships that need to be changed back to root.root. The files involved and details are contained in the following excellent thread:

[http://ubuntuforums.org/showthread.php?t=34162](http://ubuntuforums.org/showthread.php?t=34162)

When I did these changes both the scanner and printer are working fine. I suspect that this may be a problem with a number of different model scanners running in conjunction with a Samsung printer that uses the Samsung Unified Printer Driver.

Problem was nothing to do with Ubuntu or xsane - Nice one Samsung!! :)

---

### Post by smi402 on 2008-03-17
Sorry - the URL on the Unified Samsung Printer Driver referred to in my last post should be:

[http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)

:oops:

---

