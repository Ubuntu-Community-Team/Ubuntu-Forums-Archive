---
title: "How To: Troubleshoot HP LaserJet 1000-series"
date: 2010-03-24
forum: Hardware
---

### Post by Kevinator on 2010-03-24
**INTRODUCTION**

This guide is for printers in the HP LaserJet 1000 line. The printers I'm aware of that are likely to be affected are the LaserJet 1000, 1005, 1018, 1020, P1005, P1006, P1007, P1008, and P1505.

These printers have always been a bit problematic, and with recent CUPS versions have become even more problematic. I've been investigating the problem because my LaserJet 1020 stopped working. In the process I've found many people on the Internet reporting similar problems, so this guide is intended to document the issues people are likely to encounter, and their solutions.

This only covers printing with CUPS using the foo2zjs driver. If you don't know what CUPS is, you shouldn't need to worry about it since it's typically installed by default. You may need to install foo2zjs using whatever method you normally install packages with.

This does NOT cover using HPLIP. It also does NOT cover using foo2zjs when it has been installed from the original source package (if you don't know what that means, it doesn't apply to you). If you've installed from the upstream source tarball, you can still use this guide, but you will have to figure out for yourself where file paths are different.

I'll also make some non-Ubuntu notes along the way, so people using other distros might get some use out of it.

**OVERVIEW**

There are three things that need to happen in order to print on one of these printers.

1) The firmware must be loaded onto the printer. In order to decrease the cost of the hardware, these printers don't include the memory to store the firmware while powered off, so every time they are powered on the firmware has to be copied over from your computer.

2) CUPS must detect the printer. This may happen automatically, or you may use CUPS tools to detect available printers. If the printer isn't detected, something is wrong.

3) A document has to be sent to the printer. I won't say anything more about this, because I've never encountered an issue with it. The problems are typically in the first two steps.

**FIRMWARE**

_Installing_

The firmware MUST be installed separately. It is not included in any software package (currently) due to copyright concerns. foo2zjs includes a script to easily download (and convert, if necessary) the firmware files.

Firmware files are stored in the directory /usr/share/foo2zjs/firmware.  If you don't see a firmware file there (or if it could be the wrong firmware), you can fetch the firmware with this command:

sudo /usr/bin/getweb 1020

Replacing "1020" with the model of your printer.

_Loading_

Now that you've verified that you have the firmware on disk, you need to make sure it gets onto the printer. With the printer connected and switched off, switch it on and listen. The printer rollers should start turning as usual. Then, they should STOP briefly, then start turning again for about five seconds. This indicates that the firmware is loading.

So, what if this doesn't happen? The typical reason (assuming you have the firmware file) is that the usblp kernel module isn't loaded.

*** Skippable Details ***
In CUPS 1.4, there were some changes to the USB backend. Previously it used the /dev/usb/lp* interface that usblp provides. The new version uses a userspace USB library, libusb, to communicate (at least on Linux). To make this work, usblp was blacklisted to prevent it from loading (I'm not sure where this happened -- presumably either in the upstream CUPS source or in the distribution packaging). This is a problem for users of foo2zjs, since it needs the /dev/usb/lp* interface to load the firmware. It also seems to break printing through USB-to-parallel adaptors.

In Ubuntu, there are still other changes. Instead of the libusb-based backend, it includes a "hybrid" backend that supports both methods.  Because of this, the blacklist for usblp is unnecessary.

If you are not using Ubuntu, and you have a version of CUPS built without usblp support, you are going to have problems getting the firmware to load. You may be able to load usblp to load the firmware, then unload it to print. It can't be left loaded because it claims the USB interface and prevents CUPS with libusb from using it.
*** End Skippable Details ***

So your firmware isn't loading. Run this command to see if usblp is loaded:

lsmod | grep usblp

If the output lists usblp, then it is loaded and I'm afraid your problem is beyond the scope of this guide.

If the command shows nothing, usblp is not loaded. (But keep in mind, if you are not on Ubuntu or if you've built your own kernel, that it *could* be compiled in instead of built as a module. Typical Ubuntu users can ignore this.)

usblp seems to be loaded automatically when the printer is connected (I'm not sure why), so if that's not happening it may be because it is blacklisted. Try this command:

grep -r usblp /etc/modules /etc/modprobe.d/

Look for something like "blacklist usblp". You're going to have to unblacklist it if you want to use foo2zjs, or load it manually. You can load it now with this command:

sudo modprobe usblp

When you enter that, your printer should come to life and load the firmware. However, there is an issue that I'll describe below that you may have just bypassed, and it may trip you up in the future. To get the most out of this guide, load usblp BEFORE you turn on your printer (or have it configured to load automatically -- which should just mean it's not blacklisted).

**PRINTER DETECTION**

The basic check for whether your printer is being detected by CUPS is this:

lpinfo -v

You should see a line beginning with "direct usb:/". If you see it, great! You are done with this guide! You should be able to configure and print as usual.

For the rest of us, the next thing to try is this:

sudo /usr/lib/cups/backend/usb

This is the same thing lpinfo -v uses to detect the printer, so expect it not to find the printer. It has the advantage of not requiring the CUPS daemon to be running, so do this next:

sudo service cups stop

Now turn the printer off, wait a few seconds, then turn it on again (listen for the "brrrr, pause, brrrr" that indicates the firmware loaded, otherwise you need to return to the previous section). Now try the backend command again:

sudo /usr/lib/cups/backend/usb

If your printer is still not found, I'm afraid your problem is beyond the scope of this guide.

So, your printer is properly detected only when CUPS is not running.  That's not very useful. This seems to be a bug that occurs when CUPS probes for the printer during the period when the firmware is being loaded. It reportedly causes the firmware to be corrupted in transit, though I can't personally confirm this. The following launchpad bug is tracking the issue:

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/543177](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/543177)

There are a few options that I know of to work around this problem:

1) Manually load usblp (and thus the firmware) a few seconds after the printer is connected or turned on, so it happens after the initial probe by CUPS. This requires usblp to NOT be loaded at the time the printer is turned on, and not to be loaded automatically, therefore it may require usblp to be blacklisted.

2) Stop cups before plugging in or turning on the printer. Start it again only after the firmware finishes loading.

3) The only one-time-only fix that I know of is to edit the firmware-loading script to make it delay a few seconds before loading the firmware. This script is located at /usr/sbin/hplj1000. I made the following change to make it work (adding the line marked with XXX):

```
#
#       Procedure to load a single device with firmware
#
load1() {
    _dev="$1"
    sleep 3 # XXX Hack to work-around firmware corruption.
    fw="$FWDIR/sihp$FWMODEL.dl"
    if [ ! -f "$fw" ]; then
```

This isn't perfect, but it should be fine if you only have to load the firmware on one printer. For multiple printers it may add extra (hopefully harmless) delays.

---

### Post by Tony_uk on 2010-03-28
Thank you for this guide.
I can now print on my LJ1020.

Tony

---

### Post by chip616 on 2011-02-24
Kevinator:

My LJ1020 wouldn't print after I upgraded to Kubuntu 10.04, though it worked fine in 8.04.  I had no file in /usr/share/foo2zjs/firmware, as you suggested. I ran the command:

sudo /usr/bin/getweb 1020

And the needed file was loaded and installed.  SUPER!

I then turned the machine off and on again, heard the rollers start a second time, indicating the loading of the firmware, and tried printing.  SUCCESS!!

I just love it SO MUCH when I try something that actually works!

Now the question is:  Why did it work in 8.04, but not in 10.04?  Surely the same copyright issues existed then as now?

Anyway, much thanks!  The 1020 is my portable printer, and I'm away in our trailer in the mountains at the moment, tethered to my Motorola Milestone.  I was able to find the answer, download the files, and get going again.  Thanks again!

Frank.

---

