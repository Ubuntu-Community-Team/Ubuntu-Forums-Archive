---
title: "Epson WorkForce 845 printer / scanner on Ubuntu 12.04 LTS"
date: 2013-08-25
forum: Hardware
---

### Post by sebastiaankop on 2013-08-25
Hi guys and girls,

I have setup Epson WorkForce 845 printer / scanner on Ubuntu 12.04 LTS connected via the network. I have 4 computers so USB is not an option for me.

What works:
Printing works
Scanning from the flatbed works (on some scanning programs)

What does not work:
- Some scanner programs do not recognise the scanner.
- Some scanner programs recognise the scanner but can only scan in flatbed mode. If I scan in document feeder mode the paper gets pulled in the feeder and then the scanner stops and flickers all his lights.

In Windows 7 this is not a problem. Printing, scanning from flatbed and scanning from document feeder works OK. But I have only one computer with Windows 7 and that is for games. So using windows is not an option for me.

I did some thorrow searching on the net and in this forum and I cant figure out this problem. First I will show you what I have done to fix it.

----- INSTALL THE SCANNER -----
iscan-data_1.23.0-1_all
iscan_2.29.1-5~usb0.1.ltdl7_i386
iscan-network-nt_1.1.0-2_i386

Terminal
su root
cd /etc/sane.d/
nano epkowa.conf
<ctrl> + <w> "example"
192.168.115.12:1865
<ctrl> + <o> then <enter> then <ctrl> + <x>

Terminal > Root
apt-get install gnome-system-tools
cd /etc/sane.d
nano epson.conf
usb 0x04b8 0x0892
<ctrl> + <o> then <enter> then <ctrl> + <x>

nano /lib/udev/rules.d/40-libsane.rules
Scroll down and add as the last device.
# Epson WorkForce 845
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0892", ENV{libsane_matched}="yes"
<ctrl> + <o> then <enter> then <ctrl> + <x>

Ubuntu Menu > System > Administration > Users and Groups > Manage Groups > scanner > properties > Checkbox username is ON.
Ubuntu Menu > System > Administration > Users and Groups > Manage Groups > saned > properties > Checkbox username is ON.

----- START ISCAN -----
Image scan could not send command to scanner. Check scanner status.
So i did. Scanner does not display errors and is working properly.

----- CHECKED -----
I checked the IP address and that is correct. I checked the port 1865 and that is correct.

----- START SIMPLE SCAN -----
Simple scan is a program that comes with Ubuntu.

Started Simple scan with -no- problems. Scanning is OK but only on flatbed mode. If I scan a document in sheet feeder mode the scanner responds properly by pulling the document in the scanner. Once the scanning start the scanners display starts flickering on and off.

----- START XSANE -----
Xsane is a more complex scanning program that can be installed in Ubuntu.

Started Xsane with -no- problems. Scanning is OK but only on flatbed mode. If I scan a document in sheet feeder mode the scanner responds properly by pulling the document in the scanner. Once the scanning start the scanners display starts flickering on and off.

----- START VUESCAN -----
VueScan is a third party (payed) program that I use in combination of my Nikon Coolscan V. The Nikon scanner is plugged in with USB.
VueScan should be capable of handling the WorkForce 845. It is in the compatibility list that I find on [www.hamrick.com](www.hamrick.com) (Programmer that makes VueScan).
VueScan does not recognise the Epson WorkForce 845.

This is what I have done to make the scanner work.

My questions are the following:

How can I make the scanner work in every of the programs?
How can I make the scanner scan from the document feeder?

Thanks in advance,

Sebastiaan Kop.

---

### Post by t-kyle on 2013-10-17
I have the exact same problem with an Epson WF-3540. Hoping someone has answers. 

One difference: I'm using Ubuntu 13.04 AMD64 w/kernel 3.11.2.

---

### Post by kamiller42 on 2013-10-18
I found the fix for this. I followed this post's instructions and did one extra step.
[http://blog.kylemanna.com/linux/2013/05/08/epson-wf3520/](http://blog.kylemanna.com/linux/2013/05/08/epson-wf3520/)

The basic outline is this:
1. Download iscan-data, iscan-usb0 file and iscan-network-nt from Epson's Linux drivers site.
2. Install in that order.
3. Edit /etc/dll.conf and make sure epkowa is listed.
4. Edit /etc/epkowa.conf and add "net <IP or machine name>" to the file. See "net" section in file.
5. Edit /etc/epson2.conf and comment out "net autodiscovery". If you don't do this, you'll end up with 2 Epson scanner entries with 1 not working.
6. Run scanimage -L and you should see the scanner using epkowa engine.

If it doesn't work, make sure you can ping the address. Also, try uninstalling all of these packages (purging is preferrable) and reboot and then follow the steps above again.

The scanner software I've tried works with no problems except SimpleScan. For some reason, it scans only 1 side even when requesting 2.

---

