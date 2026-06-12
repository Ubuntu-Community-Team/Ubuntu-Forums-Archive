---
title: "After software update, QuiteInsane refuses to access scanner"
date: 2007-01-24
forum: Hardware &amp; Laptops
---

### Post by theosib on 2007-01-24
I was hoping someone could help me figure out why I can't scan anymore from GIMP.

QuiteInsane is the SANE (scanner) plugin used by GIMP. I recently did an update of various things, including a kernel update, using Adept. Now, QuiteInsane gives me errors when I want to scan.

Here are things I have learned when diagnosing it:

- All of this worked well enough before the update.
 - "lsusb" sees it as this: Bus 006 Device 005: ID 04b8:0122 Seiko Epson Corp.
 - If I plug a thumbdrive into the USB port, it works just fine.
 - The scanner works fine when connected to another computer (WinXP).
 - Power cycling the scanner and unplug/replug the USB don't help.
 - If I run GIMP from the command line, here's what I see on stdout/stderr:

[snapscan] Cannot open firmware file /usr/share/sane/snapscan/your-firmwarefile.bin.
[snapscan] Edit the firmware file entry in snapscan.conf.

To my knowledge, there is no firmware needed for this scanner.

Note that there is no /usr/share/sane/snapscan directory on my system. The one related, /usr/share/sane/gt68xx (whatever that is), is empty.

Here is the sequence of events I observe:

- From the GIMP main window, I select File > Acquire > QuiteInsane > Scan...
- I get a small window, title "SANE Message", message "Unknown error." I click OK.
- I get a "QuiteInsane-Plugin" window that lets me select the device. I select the Epson and click "Select device".
- I get another of the same "Unknown error" boxes, and that's it.

Any suggestions?

Thanks!

---

### Post by theosib on 2007-01-25
BUMP.

Anyone use scanners?

---

### Post by JGKC9AYC on 2007-01-27
I use a scanner...in XP.
Mine's a RadioShack (Visioneer) flatbed scanner.
From what I hear, Ubuntu's picky about scanners.
I'd like to know for sure which one's work before I go out & get one.

---

### Post by floundered on 2007-02-11
theosib, I have exactly the same problem in QuiteInsane and a very similar scanner communication problem in Xsane.  However Kooka scans fine.   So maybe there's a problem in the core SANE thing that is triggered by Xsane's and QuiteInsane's communication methods, while Kooka must do things a little different because it also uses SANE but scans fine.

What's strange is that a few days ago I was searching for a solution to the communication problems in Xsane and tried Kooka instead.  It immediately worked great but couldn't print, so I tried QuiteInstane (QI) instead.  QI worked great right away.  Scanning and printing were excellent.  But a few days and reboots later it produced the "unknown error" at startup, and I'm stuck again.

So I tried reinstalling it, no luck.

I completely removed QI, rebooted, then installed it again.  Problem still there.  So it seems the problem surfaced from an update of some kind or another.

I'm currently 0 for 3 with ubuntu scanner software.

---

### Post by myke on 2007-02-16
I have no clue why but something with the kernel upgrade affected my samsung printer's settings (which never quit working itself).  However ... poking around I found the following info on the printer and did a simple solution which in turn got my scanner software off the ground and working excellently again::

For some reason ... & I don't know why ... after the kernel upgrade, it apprantly affected a setting with my Samsung printer which in turn affected the scanner software even though the printer never stopped working.   After poking around the forums a while, I found this thread:

[http://www.ubuntuforums.org/showthread.php?p=2167697#post2167697]("http://www.ubuntuforums.org/showthread.php?p=2167697#post2167697")

I used the chmod solution and commenting out one line in a root file and now both kooka & xsane are working again.

Specifically, this is what was suggested and what fixed my problem & hey ... I don't know what the kernel upgrade had to do with it but I'm just glad the solution turned out to be relatively simple:

you'll find xsane now executes as root. (This is also true if you have a multifunction printer, but see below instead of this step.) To fix this, since you don't want to run xsane as root, do the following:
a: in a terminal, type "sudo chmod -s /usr/bin/xsane"
b: sudo edit /etc/sane.d/dll.conf, and comment out (add a "#") in front of the line that says "smfp" (probably the last line).
If you only do (a) and not (b), xsane will crash.

Good luck, and let me know if you have success and/or failure, and I'll try to modify accordingly.

---

### Post by floundered on 2007-02-16
Also see this thread, which has a work around to get Xsane running again, but which needs to be done every time you want to run it:

[https://launchpad.net/ubuntu/+source/xsane/+bug/47174](https://launchpad.net/ubuntu/+source/xsane/+bug/47174)

Since wiping out my settings every time is a bit of a bummer, I'm still hunting for something better than this.

---

