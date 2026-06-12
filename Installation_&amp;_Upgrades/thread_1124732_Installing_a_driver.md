---
title: "Installing a driver"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by joni8.10 on 2009-04-13
Just wondering if anyone knows how to install a driver for an x10 Home Automation webcam called the VA11A. I downloaded the tar.gz file from this address: [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz) which I think is the right driver, but I don't know how to install it and make it work. Any help appreciated!

---

### Post by Partyboi2 on 2009-04-15
According to [[COLOR=Blue]this[/COLOR]]("https://help.ubuntu.com/community/Spca5xx") page the spca5xx driver has been replaced  with gspca since gusty. 
Another thing you could try is [[COLOR=Blue]easycam[/COLOR]]("https://help.ubuntu.com/community/EasyCam") to get the correct driver for the webcam.

---

### Post by joni8.10 on 2009-04-21
> **Partyboi2 said:**
> According to [[COLOR=Blue]this[/COLOR]]("https://help.ubuntu.com/community/Spca5xx") page the spca5xx driver has been replaced  with gspca since gusty. 
Another thing you could try is [[COLOR=Blue]easycam[/COLOR]]("https://help.ubuntu.com/community/EasyCam") to get the correct driver for the webcam.
 
Thanks,

I've installed both gspca and EasyCam2 and still no go.

EasyCam2 finds the wrong driver.

---

### Post by 123456789123456789123456 on 2009-11-02
I wrote a simular thread, my friend is haveing the same problem.  Ubuntu does not seem to reconize the device at all, however the site that reported gspca being the correct drive, I had him do a test, and found out that the driver gspca is on the system, and is working.

He has Ubuntu 9.10, and I am starting to wonder if it may have something to do with the current core being uncompatable with that driver.  It seems to be uncompatable with VMware.  I did have him download Device manager, program, suggest you do the same, at least we can see rather or not Ubuntu is reconizing it, and if it is, what device it thinks it is, and where it has it located at.  Perhaps it is placing it somewhere else.  Other than that, we may have to wait for a newer driver.  Or at least report this problem to the bug reports.

---

