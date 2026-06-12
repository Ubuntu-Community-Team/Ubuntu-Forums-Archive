---
title: "Issues using a Phillips SNC315NC webcam"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by leannecoady on 2008-01-08
I recently bought a Phillips SPC315NC webcam and installed the latest pwc-source drivers via synaptic.  After installing the drivers, I tried to use the webcam with the Cheese programme however it doesn't detect the webcam.

I ran lsusb and these are the results:

> 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 0471:032e Philips 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 


Are there any suggestions for getting the webcam to run?  Thanks!

---

### Post by linuxwizard on 2008-01-08
Did you try using your webcam to see if it would work before installing pwc-source drivers ? I don't see your cam listed here for PWC
[http://www.lavrsen.dk/twiki/bin/view/PWC/WorkingWebcamsWithPWC](http://www.lavrsen.dk/twiki/bin/view/PWC/WorkingWebcamsWithPWC)

Your webcam is listed here (the spca5xx driver is included in the Ubuntu kernel) 
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

---

### Post by leannecoady on 2008-01-08
Okay, thanks, I'll give that a try.  I installed the pwc drivers since the phillips website recommended it.

**Edit:**
I've tried the spca5XX driver and the webcam still won't work for me.

---

### Post by linuxwizard on 2008-01-08
Did you remove pwc driver ? Also try using Camorama or Ekiga instead of Cheese.

---

### Post by leannecoady on 2008-01-08
Yeah PWC has been removed.  I've tried Ekiga and Camorama without any luck.

---

### Post by anirbanjoy on 2008-02-19
same experience with SPC315NC .. cam found but not configured ..

Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0471:032e Philips 
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 1058:1001 Western Digital Technologies, Inc. 
Bus 003 Device 001: ID 0000:0000 

installed easypwc and easycam w/o any luck ..

Any help ?

---

### Post by linuxwizard on 2008-02-19
anirbanjoy
What app. have you used with you webcam to see if it works ? Have you used Ekiga ? Are you getting any error messages ?

---

