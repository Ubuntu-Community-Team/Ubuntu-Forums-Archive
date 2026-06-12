---
title: "HP Printer half page problem"
date: 2007-09-24
forum: Hardware &amp; Laptops
---

### Post by dips on 2007-09-24
Hi there

I have searched the forums, google etc but I haven't come across a similar problem so here goes:

I have a laptop (see details below) running Fiesty and this connects wirelessly to an HP 2710 Photosmart.

It has been working perfectly for over a year until recently when I downloaded and installed the latest HPLIP drivers.

Now the printer will only print the first half of any document or image. Sometimes the printer will just stop half way through and I have to reset it. Other times it will "spit" the paper out half completed.

I have checked it isn't the document by transferring to another PC (same OS) and printing it out on the same HP with no problems. I have re-installed the HPLIP drrivers but no joy. I read that there maybe a conflict between the HPLIP and HPIJS drivers (both loaded) but to remove the HPIJS driver isn't an option as it seems to want to remove gnome at the same time.

The Hardware is an old Toshiba Satellite 1110 running Ubuntu 7.04.
Wireless Card is Symbol 
Router is a Linksys 

Any ideas? Can someone point me in the right direction etc.?


Thanks in advance




Derek

---

### Post by flowbot on 2007-10-04
having the same problem on feisty. printing from a pioneer laptop with d-link dwl-g650 pcmcia card to a photosmart 2710 hooked into a netgear wireless router via ethernet.

did you find a solution?

---

### Post by dips on 2007-10-05
Hi there,

No. I am still trying. I have removed and replaced the HPLIP driver and used the HPLIP versions from the Ubuntu repositories and the HP website itself but to no avail.

The odd thing is that it worked perfectly for over a year and then suddenly this fault develops. I now suspect a conflict between the HPLIP driver and the other HP driver that is installed. Trouble is when I go to remove that package It also wants to remove all of Gnome at the same time and I don't know how to get around that.:confused:

I may have to wait for Gutsy to come out and hope that this solves the problem.

I'll post any solutions I might find.

Hope that you have better luck.

---

### Post by flowbot on 2007-10-09
From what I can tell, it looks like data is being sent to the printer *very slowly* ... looking at the network monitor when any print job over a couple hundred kilobytes gets sent, the data seems to be getting sent at only about 5kb/s. So, most text-only documents are quite quick to print, but anything with pictures takes *ages* (up to 15 minutes). Don't know if this is a wireless driver or HPlip problem, though.

---

