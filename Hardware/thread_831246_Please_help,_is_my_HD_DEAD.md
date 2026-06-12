---
title: "Please help, is my HD DEAD??"
date: 2008-06-16
forum: Hardware
---

### Post by pandoola on 2008-06-16
I came back to work this morning and my Gateway 7422gx notebook running Hardy (formerly Gutsy 2 months ago) was locked up at the desktop.  Nothing was open.  I had to hard power off to make anything happen.  Upon reboot I now get "Error 18 Selected Cylinder exceeds maximum supported by BIOS".  I cannot get past this.

I Googled and see that #1 sugg. is to try updating the BIOS.  No luck.  #2 option seems to be "move your boot partition to the front".  Researched this (bit of a noob here, sorry) and seemed like the easiest way would be to use gparted.

I created a gparted live cd and booted, but then get continual messages such as "ide: failed opcode was unknown" and "Driveready Seekcomplete Datarequest error" as it attempts to access the HD.  I googled this.  Seems like I should do a file system check.

I then went about downloading live distros Ubunu, Fedora, and Knoppix, all of which fail to boot.  Hardy live results in tons of "buffer io error on device sda 1" on boot while it attempts to access the hard drive.  Boots fine from CD if I physically take the HD out.  Knoppix and Fedora live also hang in a similar manner.

I seem to be totally unable to access this drive at all, even when attempting to boot from a live CD.  Does anyone have any suggestions?  This is my work computer and holds a good deal of stuff that has not been backed up.

Thanks.

---

### Post by Odrodzona-Sarmacja on 2008-06-17
First I would go into BIOS and see if the BIOS detection of this hard drive works from bios too. Also I would set settings for this hd in BIOS from AUTO to whatever setting that gives max cylinders.

Then I would try hard drive rescue cd from
"http://www.sysresccd.org/Main_Page"
It got few more tools besides Gparted to save at as much as possible on this hard drive.

Good luck!

---

