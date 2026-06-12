---
title: "How to increase Printing Bandwidth for Brother HL4040CDN to increase printing speed"
date: 2011-05-25
forum: Hardware
---

### Post by samMD on 2011-05-25
So its been two weeks far with me using ubuntu fully (I plan to keep it that way thanks to me migrating all my windows apps via wine). My only gripe is the printing speed in ubuntu and my brother network printer (HL-4040CDN). It takes like 15 min almost to complete 6 printing jobs (2 pgs each). IS there anyway to increase the bandwidth to the printer from ubuntu to make it like 5-10 sec like in windows 7?

Thanks

---

### Post by samMD on 2011-05-26
bump

---

### Post by walt.smith1960 on 2011-05-26
I had a problem like yours with a MFC-7820N.  It'd print about 2 pages/minute but Windows would print about 20 pages/min.  I found this driver in Synaptic (I think) "Brother MFC7820N for CUPS."  This was in addition to the CUPS driver I downloaded from Brother's site.  When I selected the Brother for CUPS driver, the speed matches Windows' speed.  I do not have this issue with a Brother inkjet MFD so the speed issue may be device vintage or model specific.  Just something to look at.

---

### Post by samMD on 2011-05-26
did you select that driver from synaptic or from the brother site?

---

### Post by walt.smith1960 on 2011-05-27
> **samMD said:**
> did you select that driver from synaptic or from the brother site?

I'm pretty sure that one came from Synaptic.  The Brother site has both CUPS and LPR drivers.  I had both of them installed and the MFC-7820N was still slow on second and subsequent pages.  I then installed Brother Laser drivers from Synaptic.  After doing that I noticed "Brother MFC7820N for CUPS" and that's when the speed really picked up.  All this may or may not be applicable to other Brother models.  The MFC-6490CW inkjet has no speed issues using the Brother supplied drivers.

I think the Brother drivers were originally .rpm packages then converted with alien.  I don't know if that makes a difference or not.

---

### Post by samMD on 2011-06-04
what if you have a 64-bit system Brother doesnt supply Cups for 64 -bit :/

---

### Post by samMD on 2011-06-04
Im trying to install the drivers directly for the Brother Site and I get the following after copying and pasting this code into the terminal: Command (for dpkg)  :  dpkg  -i  --force-all  (lpr-drivername) I used sudo and without sudo


OUTPUT:

> sam@samdesktop:~$ sudo dpkg  -i  --force-all hl4040cdnlpr-1.0.3-1.i386.deb
dpkg: error processing hl4040cdnlpr-1.0.3-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 hl4040cdnlpr-1.0.3-1.i386.deb
sam@samdesktop:~$ dpkg  -i  --force-all hl4040cdnlpr-1.0.3-1.i386.deb
dpkg: error: operation requires read/write access to dpkg status area
sam@samdesktop:~$ 


what do I do?

---

### Post by samMD on 2011-06-05
bump

---

### Post by samMD on 2011-06-05
For some reason it is fixed I shall keep monitoring for a week or two before I mark this thread solved..I just went into printing and selected the DNS-DS method and the ip was local host so I guess it saw/knew the printer was local so it sent to it directly...

---

### Post by samMD on 2011-06-21
Ok so I can announce safely that the slow network printing is fixed..

I picked the second option where its "LPD network printer via DNS-SD" and just filled in the apporpriate info in the following setup screens.. 

it worked perfectly after that..

i have attached a picture to show "what option" I picked

---

