---
title: "Epson 4180 not working in Ubuntu 9.10"
date: 2009-11-12
forum: Hardware
---

### Post by Jimtuv on 2009-11-12
I have just got around to installing my scanner and followed this thread to the letter and nothing is working. 

[http://ubuntuforums.org/showthread.php?t=594951](http://ubuntuforums.org/showthread.php?t=594951)

here is what I get when I do sane-find-scanner

```
me@My-desktop:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8, product=0x0118) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

then if I try scanimage -L

```
me@My-desktop:~$ scanimage -L
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
me@My-desktop:~$ 

```

No working scanner yet. been reading every thread I can find but am just getting confused now.

---

### Post by cbtengr on 2009-11-12
I had the same problem with an Epson 4490.  The software at this site got it working:

[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

Scroll down the page - Epson 4180 is listed.

---

### Post by Jimtuv on 2009-11-12
already installed both of these packages using alien to convert to deb

RPM package  	
iscan-2.10.0-1.c2.i386.rpm 	359,714 bytes
iscan-plugin-gt-f600-1.0.0-1.c2.i386.rpm 	151,280 bytes


didn't do anything

---

### Post by myoldhouse on 2009-11-21
Have you tried running scanimage -L as root? In other words, sudo scanimage -L. If running it as root works, then you probably have a permissions problem. I have an Epson 4490 that worked fine in Ubuntu 9.04 but not in Ubuntu 9.10. I could only run scanner programs under sudo. The fix I found is documented below, taken from a message of mine from another thread.

Begin quote===

I have the same scanner (Epson Perfection 4490 Photo) and the same problem with permissions in the release version of 9.10 Karmic.

All worked well in 9.04, a normal user could access the scanner from Xsane or Epson's iScan or (with a bit of jiggery-pokery required on a 64 bit system) VueScan.

In 9.10, it seems the way the scanner is made available to non root users has changed in ways that are not clearly documented. In 9.04, I believe the HAL daemon (hald) used to take care of the detection of the scanner and setting the permissions for normal users but I recall reading somewhere that in 9.10 this method is now "deprecated" and udev is used instead. I don't pretend to know what this means, but it gave me a clue to a workaround that got my 4490 scanner working for normal users again in 9.10 64 bit.

The clue was that udev is now used. I looked in /lib/udev/rules.d and found a rules file "50-udev-default.rules" and it had a line for usb ports that said:

SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"

This was at line 58 in my rules file. I changed the MODE= entry to read MODE="0666" and saved the file (you have to edit this file as the root user as it is a system file). Basically this change makes all usb ports readable and writable by ordinary users.

I documented this change with comments so the full change now looks like this:

# libusb device nodes
# Changed MODE to 0666, instead of 0664, so scanner would work
# for normal user and not just root. RJ Oct 29, 2009.
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"

You don't have to reboot or logoff for this change to take effect. Just turn your scanner on and off or unplug and replug its usb cord and the system will re-detect the scanner using the new permissions.

I also tried to make a rule in the /etc/udev/rules.d folder, which is normally where one would make changes for a specific device but I couldn't manage to concoct a rule that worked. Only the change to the "50-udev-default.rules" file in the /lib/udev/rule.d worked for me.

Give it a try, it may work for you as well. 

End quote ===

---

### Post by 0nelove on 2009-12-18
> **myoldhouse said:**
> 
# libusb device nodes
# Changed MODE to 0666, instead of 0664, so scanner would work
# for normal user and not just root. RJ Oct 29, 2009.
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"

You don't have to reboot or logoff for this change to take effect. Just turn your scanner on and off or unplug and replug its usb cord and the system will re-detect the scanner using the new permissions.

I also tried to make a rule in the /etc/udev/rules.d folder, which is normally where one would make changes for a specific device but I couldn't manage to concoct a rule that worked. Only the change to the "50-udev-default.rules" file in the /lib/udev/rule.d worked for me.

End quote ===

this worked for me on an Epson 4490.  Looks like this fix will be temporary since these files are apparently overwritten automagically.

There are bug reports on this issue...
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/493430](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/493430)
[http://old.nabble.com/Xsane-Ubuntu-9.10-debug-Lide-35-%28genesys%29-td26441450.html](http://old.nabble.com/Xsane-Ubuntu-9.10-debug-Lide-35-%28genesys%29-td26441450.html)

---

### Post by 0nelove on 2010-05-02
This same fix works in 10.04.
:guitar:

---

### Post by Jimtuv on 2010-05-08
Tried sudo scanimage -L and got this.

jim@James-desktop:~$ sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

So mine is not a issue with permissions. Still getting all the same results as before no change no matter what I do.

---

### Post by 0nelove on 2010-05-08
> **Jimtuv said:**
> Tried sudo scanimage -L and got this.

jim@James-desktop:~$ sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

So mine is not a issue with permissions. Still getting all the same results as before no change no matter what I do.

sounds like something went wrong with driver installation ... did you install the drivers from post #2 successfully?  does ```
sane-find-scanner
``` find your scanner?  just some guesses here...

---

### Post by Jimtuv on 2010-05-10
This is the output

```
jim@James-desktop:~$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x0118 [EPSON Scanner]) at libusb:002:007
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```

---

### Post by 0nelove on 2010-05-10
yeah, I'd take another run at installing the correct drivers.  go back to the link in #2.  you don't need alien - there are 64 bit debs on that site.

---

### Post by Corn Flake on 2010-05-31
Where can I find the .deb packages?  For the Perfection 4180 Photo, it only shows 32-bit .rpm.

---

### Post by 0nelove on 2010-05-31
> **Corn Flake said:**
> Where can I find the .deb packages?  For the Perfection 4180 Photo, it only shows 32-bit .rpm.

yeah, bummer.  You might need to compile from source and use the -force architecture option.  If you search for these, you'll find the prior threads discussing this, I bet.

---

