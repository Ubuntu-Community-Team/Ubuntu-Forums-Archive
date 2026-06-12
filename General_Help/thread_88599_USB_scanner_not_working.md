---
title: "USB scanner not working"
date: 2005-11-10
forum: General Help
---

### Post by GrootBrak on 2005-11-10
Since I upgraded to breezy sane won't scan.

sane-find-scanner gives me this:
> found USB scanner (vendor=0x04a5 [Color], product=0x20b0 [ FlatbedScanner 22]) at libusb:002:004

scanimage -L gives me this
> device `snapscan:libusb:002:004' is a Acer FlatbedScanner22 flatbed scanner

Trying to run xsane gives me this:

> Failed to open device snapscan:libusb:002:004

Anyone that can help?

---

### Post by ChrisTheGeek on 2005-11-18
I'm having a similar problem.  My scanner is found by sane-find-scanner and scanimage -L but when I run xsane, quiteinsane or any other frontend I've tried, none are able to detect that a scanner is available.

I thought I was having this problem because I compiled by own version of sane to get my scanner working but perhaps we're having the same issue?  Scanning works perfectly for me from the command line, but I can't make any of the front-ends find the scanner!  It's driving me nuts.

Any of you wonderful people out there know the answer to this one?

---

### Post by claydoh on 2005-11-18
you may need to copy a firmware file to get it to work
What exact model is it?

[Look here for some info on this for your type of scanner]("http://snapscan.sourceforge.net/")

the id #s( 0x04a5 [Color], product=0x20b0) makes it a
Acer / Benq 3300 / 4300 (or clone) so you will need a firmware file for it, and need to edit the config file telling sane where it is. Following the instructions on the link above should get you going

---

### Post by GrootBrak on 2005-11-20
Downloaded the firmware file, changed snapscan.conf to point to the device, now 
xsane gives the following:
> scanimage: open of device snapscan:libusb:002:007 failed: Error during device I/

Synaptic don't have a "libusb" as mentioned by the sane website. Should I install libusb? Modprobe also returns a "fatal error, scanner not found"

---

### Post by rplantz on 2005-11-20
I have an Epson all-in-one.

When I upgraded, I had to remove the printer. Then I plugged it in, turned it on, and rebooted.

Then I added the printer. It found it just fine. The scanner part works, too.

I haven't done a stand-alone scanner, but you might want to try removing your scanner and re-adding it.

Bob

---

### Post by GrootBrak on 2005-11-21
Thanx, unpluging and re-plugging won't work for me, neither does unplug, reboot and then replug.

---

### Post by rplantz on 2005-11-22
[QUOTE=GrootBrak]Thanx, unpluging and re-plugging won't work for me, neither does unplug, reboot and then replug.[/QUOTE]

To clarify, I

1. Removed my printers using the print manager.
2. Shut down.
3. Plugged in my printers (I have an Epson all-in-one and a Samsung laser).
4. Turned both printers on.
5. Booted the system.
6. Used the print manager to add both printers.

Both were detected and everything worked.

Bob

---

### Post by GrootBrak on 2006-01-06
Latest on this issue. With Ubuntu Breezy Live CD the scanner works 100%. I installed a fresh Kubuntu Breezy, scanner works. Delete and install a fresh Ubuntu Breezy, scanner don't work. Delete and install Ubuntu Hoary, scanner work.
Now I have KDE and Gnome both in Breezy, but with the Kubuntu disk as repository and I make sure I Synaptic use Kubuntu for all my KDE apps. Switch to KDE, scanner works. Switch to Gnome, scanner don't work. Guess which one I am using now!!!

---

