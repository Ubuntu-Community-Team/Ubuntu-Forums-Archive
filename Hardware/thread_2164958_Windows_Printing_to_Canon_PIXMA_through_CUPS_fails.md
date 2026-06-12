---
title: "Windows Printing to Canon PIXMA through CUPS fails after first print"
date: 2013-08-02
forum: Hardware
---

### Post by todd.seidenberg@gmail.com on 2013-08-02
Hi, 

For a few years, my setup has been: 

Ubuntu 11.04
Cups
Canon Pixma MX310 

for a print server.  My windows laptop on the network would happily print to this printer.  

I upgraded to 12.10, and now printing is broken in the following way: 

I can print from any of my ubuntu systems without a problem. 
However, if I use my windows 7 laptop, the first print works fine.  After that, I can't print anymore.  It seems that the printer still thinks that there's a print job coming through, so it doesn't 'release' itself, and allow other jobs to come through.  Of course, no jobs are in the queue when this happens. 

Cancelling the print job has no effect.  The only thing that seems to work is removing and adding the printer again. Then the same problem occurs. 

Any thoughts? 

Thanks.

---

