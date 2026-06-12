---
title: "Scanner Issue - Ubuntu forgets /dev/bus/usb permissions change"
date: 2009-10-07
forum: Hardware
---

### Post by Randypan on 2009-10-07
I have an HP G3110 scanner, Sane and XSane installed. My user account is included in the scanner and sane Groups. At first Iwas only able to acces the scanner when logged in as Root. Then I searched around the net a bit and nothing would help, except changing Permissions of the /dev/bus/usb file corresponding to the scanner (in this case /001/004), from root to my user account. 
 The problem is that this works for only one session and when the computer reboots, the file permissions revert back to root, so I have to manually change them every time I want to use the scanner.
 How can I make this change permanent?

---

### Post by Bucky Ball on 2009-10-07
Is the scanner always plugged into the same USB port? Silly question but ...

---

### Post by Randypan on 2009-10-07
Yes it is and it's powered up all the time

---

### Post by Randypan on 2009-10-07
I GOT IT FIXED!
It seems I had mixed critical files up while I was trying to solve this issue.
What happened is that when I installed the necessary backends for sane (or something), a file called libsane.rules popped up in the etc/udev directory. This file made the udev process consume 99.9% of my CPU resources and slowed everything down, so I had to remove it. 
 All I did was edit the file, which contained about 100 different models and brands of scanners.
EXAMPLE:

# Hewlett-Packard ScanJet 5590
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="1705", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"

 I deleted all of them except for the one for my scanjet G3110. I restored the file and everything worked just fine.
As it turns out, to use a scanner with Xsane without being root, you have to:
-Install the sane backends that support your scanner.
-Include your user account to the saned and scanner groups
-Edit the libsane.rules file as I did above
And I think that's all

---

### Post by Randypan on 2010-11-26
...coming to think of it, deleting all these entries isn't all that clever. Commenting them out works fine as well.

---

