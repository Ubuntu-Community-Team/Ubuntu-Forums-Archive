---
title: "Installing SANE for Benq 5150C scanner"
date: 2009-03-22
forum: Hardware
---

### Post by Andrey Gazizov on 2009-03-22
Help me for installing SANE in Ubuntu 8.10. In SANE's site says that I must install SnapScan backend, but I can't find link for download them.  [http://sourceforge.net/projects/snapscan](http://sourceforge.net/projects/snapscan) site does't have link for downloading. Where is I can get SnapScan.

Sorry for my language. English isn't my mother language.

---

### Post by desertdog on 2009-03-28
The backend for this scanner should be installed by default with your distribution. Plug the scanner in and open a terminal. Then type:

$sane-find-scanner

It should say the name of the scanner and the usb id. Then try 

$sudo scanimage -L

then, $scanimage -L

It should be detected with both of these commands. If it is detected using sudo, but not as a regular user, then you have a permission problem. Go to System/Administration/Users and Groups and add your user to the Scanner group.

If everything works up to this point, you can scan from the command line or open xsane to get a nice GUI frontend.

Good luck.

---

### Post by colorprint on 2009-04-14
I have Benq 5300U scanner.
It is visible by sane-find-scanner but not shows by 
$sudo scanimage -L

Xsane not works too :(
firmware is downloaded, corresponding string in the snapscan.conf added.

How could it be fixed?

---

### Post by desertdog on 2009-04-18
Colorprint,
try this tutorial for snapscan backend:

[http://ubuntuforums.org/showthread.php?t=26911&highlight=scanner](http://ubuntuforums.org/showthread.php?t=26911&highlight=scanner)

---

### Post by colorprint on 2009-04-28
> **desertdog said:**
> Colorprint,
try this tutorial for snapscan backend:

[http://ubuntuforums.org/showthread.php?t=26911&highlight=scanner](http://ubuntuforums.org/showthread.php?t=26911&highlight=scanner)

yes, I have installed the firmware, but it not works.
lsusb result:
Bus 001 Device 015: ID 04a5:20fe Acer Peripherals Inc. (now BenQ Corp.) SW2 5300U

sane-find-scanner result:
found USB scanner (vendor=0x04a5, product=0x20fe) at libusb:001:015


sudo scanimage -L result is just a empty string.
xsane not works too.

---

