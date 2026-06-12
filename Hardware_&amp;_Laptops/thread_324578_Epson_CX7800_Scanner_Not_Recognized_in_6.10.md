---
title: "Epson CX7800 Scanner Not Recognized in 6.10"
date: 2006-12-23
forum: Hardware &amp; Laptops
---

### Post by Tanker Bob on 2006-12-23
I'm new to Ubuntu and Linux, but not to computers.  I have spent all day trying to get the scanner in the USB Epson CX7800 recognized by Ubuntu 6.10.  I have gone through all the HOWTOs that I can find, but they all reference packages not installed in 6.10, like hotplug.  I've added the appropriate lines to epson.conf files, but I had to guess at the usb code for the scanner (used the CX6600 code).  ](*,)   The printer itself and its built-in card readers all seem to work fine under Ubuntu.  Even my USB hub works great.  The scanner is the only hardware issue.

Two questions:
1) How can I get Ubuntu 6.10 to recognize the scanner?  This is critical to the difference between operating WinXP under a virtual machine in Ubuntu or as a dual boot.  I want to avoid the latter if at all possible.

2) If the CX7800 scanner can work under 6.10, how do I do so?  I have no problems working in the console, although I'm still learning commands and syntaxes.  Aptitude has been my buddy.

Overall, I'm very impressed with Ubuntu 6.10 and hope to be able to format a new, large post-Christmas hard drive exclusively under Ubuntu with WinXP as a VM for a number of mission-critical programs that aren't available under Linux.  Thanks in advance for your help.

---

### Post by monkotronic on 2006-12-24
see my last post at this thread:

[http://ubuntuforums.org/showthread.php?t=248748&highlight=cx7800](http://ubuntuforums.org/showthread.php?t=248748&highlight=cx7800)

mine works great now!

---

### Post by Tanker Bob on 2006-12-24
Thanks!  I spent all day today playing with it and also got mine to work.  I did what you did, plus downloaded ([http://www.avasys.jp/english/linux_e/dl_spc.html](http://www.avasys.jp/english/linux_e/dl_spc.html)) and MANUALLY (i.e., manually copied all the files from the .rpm package) installed the latest version of Epson's iscan program and drivers.  I tried turning the iscan rpm file into a deb, then use the package installer, but then it always failed to overwrite some existing older files, thus failing the install.  I also edited the configuration files that you mentioned to add the CX7700/7800.  It all works fine now, but I have to change the permissions whenever I reboot or turn the scanner off.  Any workarounds for that?  The hotplug script one apparently doesn't apply to Ubuntu.

Well, almost.  Epson iscan works fine, but XSane cannot save its configuration files on exit so I have to reset them every time I run the program.  Any ideas on that?

---

