---
title: "Iomega Zip 250 ATAPI mount issues"
date: 2010-10-27
forum: Hardware
---

### Post by bpalone on 2010-10-27
I am still using 8.04 Hardy and still using Zip Drives.

The issue:

Nautilus shows the Zip Drive but won't mount it.  It will eject it and when you click to rescan the light lights up.  Now from within Nautilus, when I click on the Computer Icon and then double click the Zip Drive icon, I get the following message:

Unable to mount Location.
No media in drive.


That is when a disk is inserted.  I have gotten to mount manually and then Nautilus will go ahead display the disk contents.  With the manual mount point, Nautilus will only let me unmount, but the other icon that it had to begin with will eject the disk.

This is on a fairly recent system build and I remember that the Live CD didn't handle the Zip Drive either.  I have been poking around and googling and haven't discovered an answer yet.  The following are portions of the output from dmesg:

```

[   16.307758] Floppy drive(s): fd0 is 1.44M, fd1 is 1.2M
[   16.327488] FDC 0 is a post-1991 82077
[   16.974576] hdb: IOMEGA ZIP 250 ATAPI, ATAPI FLOPPY drive
[   17.757028] hda: LITE-ON LTR-48246S, ATAPI CD/DVD-ROM drive
[   17.757038] hda: host max PIO5 wanted PIO255(auto-tune) selected PIO4
[   17.760003] hda: UDMA/33 mode selected
[   17.761806] hdb: applying conservative PIO "downgrade"
[   17.761808] hdb: host max PIO5 wanted PIO255(auto-tune) selected PIO2
[   17.761904] hdb: UDMA/33 mode selected
[   17.762201] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   17.781006] Probing IDE interface ide1...
[   19.186204] hdc: TSSTcorpCD/DVDW SH-S182M, ATAPI CD/DVD-ROM drive
[   19.186228] hdc: host max PIO5 wanted PIO255(auto-tune) selected PIO4
[   19.186514] hdc: UDMA/33 mode selected
[

```

That is from up the list, so it is seeing it.

```

[  156.796169]  hdb: hdb4
[  167.461078]  hdb: hdb4
[  222.191946]  hdb: hdb4
[ 1545.861045]  hdb: hdb4
[ 1648.760988]  hdb: hdb4
[ 1659.410348]  hdb: hdb4
[ 2172.326028]  hdb: hdb4
[ 2266.036954]  hdb: hdb4
[ 2266.685050]  hdb: hdb4
[ 2306.003473]  hdb: hdb4

```

That is from the end of the output.

This build is recent, but old tech, is AMD 939 processor and corresponding motherboard.  Since the Live CD had issue, it could be hardware issue.  I am at a loss.

BTW, I am still with 8.04 for a reason, so upgrading isn't an option. 

I do have a couple of newer Live CDs, I'll give them a go to see if it persists. 
Tried 9.04 and the Live CD did find and work with the Zip Drive.  Then I tried 8.04.4 and got same results as above, no joy.  So, it is an 8.04 issue.

Thanks in advance.

---

### Post by bpalone on 2010-10-28
Well my mounting via CL was a bit of a Kludge.  My work around is also a Kludge, but more tolerable.

Installed "Mountapp" from the repositories.  Then placed it on the bar. Isn't pretty with 9 drives laying there, but it allows me to mount with a click rather than the CL mount command.  It also ejects the Zip Disk so I am going to call this solved. 

8.04 is rapidly becoming the unsupported and newer releases don't have the issue. 

I didn't mention that this is an ASROCK 939 Dual Sata motherboard in the original post.  Just in case someone looks and finds it later.

---

