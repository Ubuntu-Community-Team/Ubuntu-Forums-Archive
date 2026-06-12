---
title: "Make-a-copier"
date: 2007-08-27
forum: Hardware &amp; Laptops
---

### Post by cilynx on 2007-08-27
I've got an OfficeJet 5610 MFP (supported by HPLIP) and a LaserJet 1000 (supported, but not by HPLIP) both jacked into my PC and working fine.  I'm looking for a clean solution to stick 50 pages in the ADF of the MFP and have the Laser kick out the 50 appropriate copies.  I was hoping that hp-makecopies would do what I want, but it seems to only work within a single machine.  Any ideas?   TIA.

---

### Post by tgalati4 on 2007-08-27
So, you want a script that will scan 50 pages from your multifunction printer which uses ink that is more expensive than gold, then send that file to your laser printer so you can print it out cheaply.

It would look something like:

hp-scanner -d myMFPprintername | lpr -d mylaserprintername

You will need to find the appropriate program that will scan your document.  hp-scanner is just a placeholder.

Of course, when dealing with HP printers, you will probably have paper jams in both the automatic feeder and in the laserjet.  Let us know what finally works.

---

### Post by cilynx on 2007-08-27
Almost.  I would prefer (for no particular reason) for it to scan all 50 pages, print them on the laser as they finish scanning, and delete the temporary files as they're printed so they're not hanging around.  It would be bonus if it would stop the batch scan job when it runs out of pages as well, instead of continuously trying to load another page until I manually kill the job.

I was afraid it was going to come down to scanimage and lpr.  I just may have to write a little GUI that handles this process w/o having to remember the command line options.  (Man, Ubuntu has spoiled me.  Five years ago, I never would have thought I would choose a GUI solution to CLI.  Maybe I'll just write a perl script instead =)  I'll keep this thread posted.

WRT HP's lousy paper handling:

I've never had the LaserJet jam up.  This thing was one of the better $80 I've ever spent.  I used it for everything my last two years of undergrad and I'm only on my second toner cart.  It ticks and preens itself like an old Canon BubbleJet, but it prints fast, straight, and clean.

The OfficeJet is another story.  The ADF jams up if the paper is curled at all to start with and no matter what, the paper is curled when it's done with it.  Also, scans using the ADF always come out rotated by 5 deg or so, but copies always come out perfectly straight.  It's like they know about the problem and correct it in firmware.  Also, scanning at anything less than 150dpi leaves what I would best describe as an oil slick rainbow on the scan, in full color, even if you scan in b&w.  150dpi and above, it's perfect.

---

