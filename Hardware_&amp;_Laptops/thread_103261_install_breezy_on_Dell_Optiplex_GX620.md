---
title: "install breezy on Dell Optiplex GX620"
date: 2005-12-13
forum: Hardware &amp; Laptops
---

### Post by linuxlady2714 on 2005-12-13
I'm trying to install Breezy on a new Dell Optiplex GX620, it has a SATA II hard drive.  I've upgraded the BIOS to the latest version.

In the BIOS, when I select the "Normal" setting to use the SATA, there is a problem with reading the install CD.  When I select "Combined" it can use the install CD, but it can't recognize the hard drive, it just puts two blank lines where the hard drives specs would normally appear.

There seems to be some related posts on bugzilla.  But if this is fixed in the updates, I still don't understand how I'm suppose to install this thing.

Please help.  I've googled, but I just see people with similar problems.

It's not suppose to be this hard to install linux.

:confused: 

linuxlady2714

---

### Post by Hobbes on 2005-12-13
Not really an expert, but might it have something to do with setting your optical drives ( = cd/dvd drives) to SATA when that is not what you have? That would at least make sense as to why setting it that way would not let you read the CD, perhaps you are not changing the correct parameter? Sorry if this is just dumb and isn't what is happening at all.

---

### Post by linuxlady2714 on 2005-12-14
I think the CD is an IDE drive - PATA - how would I change it to be SATA?

linuxlady2714

---

### Post by LiquidIQ on 2005-12-14
What is the error that it gives when in "Normal" mode?

I know Dell's new BIOS is kinda weird when it comes to the SATA/PATA stuff...

---

### Post by linuxlady2714 on 2005-12-14
I think the main problem is the DVD drive:
Philips DVD+/-RW DVD8701

Has anyone got this DVD drive to work with ubuntu?

---

### Post by linuxlady2714 on 2005-12-14
When I use the normal mode, it gets to the "Scanning CD-ROM" part, then gives the error message:
--------------
!! Load installer components from CD

There was a problem reading data from the CD-ROM. Please make sure it is in the drive.  If retrying does not work, you should check the integrity of your CD-ROM. 

Failed to copy file from CD-ROM.  Retry?
Yes, NO
---------------
I used several different Breezy CDs.  I checked the integrity, and that was fine.  With no, it does " Installion step failed"

Obviously it has read from the CD up to some point.

---

