---
title: "CD burning stopped working"
date: 2008-07-06
forum: Hardware
---

### Post by OiPenguin on 2008-07-06
I've got a combined CD/DVD drive which has worked flawlessly since I bought my laptop (about 6 months ago). However, since recently I've been unable to burn CDs. It still burns DVDs flawlessly, though.

I've tested burning ISO's, mediafiles and other files from Nautilus, with Brasero and with other programs. No errors are produced and it appears to be working, but the disc stays blank. I don't think its a disc issue. I don't know what I've done to cause this problem, nor to undo it. Can anyone help?

I'm using an up-to-date Hardy Heron.

Yours,

Lars

---

### Post by TheForkOfJustice on 2008-07-11
I've got the same problem with my desktop (HP a420n) but its with a regular CD burner.  It worked when Hardy was freshly installed (which was a relief since it was a pill to get to work in Gutsy) but upon recent updates it has stopped working.

I remember that removing an ntfs package got it to work in Gutsy but I had to use wodim. I haven't found the solution this time around.

Can someone help us both troubleshoot?

---

### Post by ccnelson on 2008-12-03
I have a similar problem.  I haven't had any trouble with this CD/DVD burner until just recently.  Then, without warning, I can no longer write to CD-R discs.  Like OiPenguin, there are no errors, and it appears to be working, but the disc stays blank.  I can write to CD-RW and DVD-RW discs, however, and I can read CD-Rs just fine.  So, the laser can work, it just doesn't seem to want to burn CD-Rs.

FYI, cdrecord --scanbus reports the drive as:

0,0,0	  0) 'TSSTcorp' 'CD/DVDW TS-L632D' 'TI03' Removable CD-ROM

and I'm running 8.04LTS.

Any help would be greatly appreciated.

Regards,

Chris

---

### Post by DWade on 2008-12-03
You might want run terminal and type sudo apt-get check  (password) after enter
This will see if any of packages are broken.
sometimes the updates aren't with in the general listing.
Go to administer select software sources and click on preposed and un-maintained.
next tab select the two items for conical and close
in terminal again type sudo apt-get update
then sudo apt-get upgrade
if there any answer Y

If that doesen't fix try another cd burning software for Gnome from add and remove programs.  See if that works.

---

### Post by 9ico on 2008-12-03
[color=#282827]_I need nfl jerseys I do not belive shoping on websit before because i always thought that we could not buy a good products, but now i think it is very convinient for us to shopping on website. I feel truly grateful here _[http://www.9ico.com](http://www.9ico.com/)_._[/color]

---

### Post by TheForkOfJustice on 2008-12-03
> **DWade said:**
> If that doesn't fix try another cd burning software for Gnome from add and remove programs.  See if that works.

You can also try K3B.  It's KDE's burner but sometimes using a program that uses different libraries can prove beneficial.  It worked once for me but nothing has worked lately. Haven't tried it after recent updates, though, so Brasero could be working now.

I wonder if the source of this problem was diagnosed...

---

