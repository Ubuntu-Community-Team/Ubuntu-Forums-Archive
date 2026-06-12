---
title: "Linksys Printserver not working with ubuntu Hoary"
date: 2005-08-03
forum: Hardware &amp; Laptops
---

### Post by muffinresearch on 2005-08-03
Hi I am having trouble getting my linksys EFSP42 Printserver to work with Ubuntu. Has anyone had experience of configuring ubuntu to work with any linksys printservers? 

None of the options in Ubuntu seem to work. In windows it operates like a share but this fails in ubuntu when using SMB. 

Regards,

Muffinresearch

---

### Post by amohanty on 2005-08-03
What have you tried to do so far?

AM

---

### Post by jhuff on 2005-10-04
I have finally got my Brother HL-1440 printer working after I installed the Linksys PrintServer PSUS4.  It was not easy to get working with the windows computers connected to my network, but I finally did get it working.  I am connecting the server to a Belkin wireless router (this could be one of my problems).  I must have turned everything on an off a dozen times trying to get everything squared away.  I did set a static IP address for the server becuase I was getting network address conflicts.  So I am still at a loss as to how I finally got the windows computers working correctly.  As far as my linux box I did the following:

Added a new printer using "Unix Printer (LPD)"
        Host = Server IP address (192.168.2.xxx)
        Queue = L1

I initially tried using CUPS Printer (IPP) but whatever I printed just kept printing multiple copies until I cancled the print job.

It was easier getting my linux box working then the windows computers.

If you are stuck getting the server itself working let me know.  I used the CD that came with it on one of my windows machines.  I tried Linksys Tech Support and was totally disastified. 

I still can't believe I got my printer working.  I have been trying for months to get the Brother HL-1440 to work.  It had been shared from a windows computer.  Now I can finally move totaly away from Windows!!  I am totaly impressed with Breezy Badger.

---

