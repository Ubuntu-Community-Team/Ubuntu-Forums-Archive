---
title: "Xsane runs only as root"
date: 2005-10-22
forum: Hardware &amp; Laptops
---

### Post by whitewizardcoder on 2005-10-22
Hi,

I have a Brother MFC 8500 Scanner/Printer/Fax.  I've downloaded the backend for Sane from the Brother site, however, I can only run Xsane as root for the scanner.  If I don't, I get an error message that says "Failed to open device `brother:bus3;dev1': Error during device I/O.".  I know that I can run Xsane and scan as root, and if I chmod the usb device in /proc/bus/usb/, i can run it as a user, but every time I unplug the device, it resets the user writeability.  Is there any way to permanently allow the user (me) to run xsane for the brother?

WhiteWizardCoder

P.S. I also have a HP scanner which runs fine, so I'm not exactly sure what could be going wrong.

---

### Post by ChrisTheGeek on 2005-12-01
Is the problem scanner connected by USB?  If so it sounds like the hotplug script for setting permissions isn't being run.

Look at the files in /etc/hotplug.

It may be your device make and model aren't in the mapping file.  You can find out what these should be by running:

sane-find-scanner

Look for the vender and model numbers and add them to the mapping file if they aren't already there.  Use the other lines as a template.

---

