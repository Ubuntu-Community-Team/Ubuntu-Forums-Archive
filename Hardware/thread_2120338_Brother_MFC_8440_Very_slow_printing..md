---
title: "Brother MFC 8440: Very slow printing."
date: 2013-02-26
forum: Hardware
---

### Post by Shallowmind on 2013-02-26
Hello,
I did a search but could not find anything specific to my printer or problem.

My printer from day 1 has been very slow.  It takes 10 minutes or more to print 5 pages.
I never had this issue with the printer on the "other" OS.  

Also the computer itself gets very slow while the printing operation is taking place.

The printer is:  Brother MFC 8440.

And as a second question.  How do I get it to print from a VM (Windows XP)? 

Pre thanks.

;)

---

### Post by Shallowmind on 2013-02-27
Bump.  Thanks

---

### Post by gordintoronto on 2013-02-27
How is the printer connected? It sounds like USB 1.0....

What application are you printing from? What operating system?

What kind of VM? There are extensions in Virtualbox to support USB.

---

### Post by pdc on 2013-02-27
I wonder if you are using the Brother drivers.......

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

has a link...........to an install script...........you can download and run and it works out what printer you have ..........and installs the drivers for you......

---

### Post by foresthill on 2013-02-27
Couple other things you can try, after you see if the drivers linked above work or not.

If it's PDF files that are printing really, try a couple of different PDF viewer programs, since PDF files often hang in one program but not another. 

Or if everything you print is slow (after trying the Brother drivers linked above) you might try deleting the printer and reinstalling it using a generic USB printer driver when asked to choose a driver. I remember this worked on one of my HP printers, much to my surprise since I had the official HP driver installed and printing was still glacially slow.

---

### Post by kurt18947 on 2013-02-28
I'm not sure what's available for the newish machine.  I had slow problems with an MFC-7820N.  The first page reasonably quick, subsequent pages were at the rate of 1-2 pages/min.  I changed the driver from Brscript3  to a CUPS driver available in the repositories.  MUCH improved.  So you might poke around to see if there are any alternative drivers available.

---

### Post by Shallowmind on 2013-02-28
Thanks for the info.  I will give it a try and let you know the outcome.

---

