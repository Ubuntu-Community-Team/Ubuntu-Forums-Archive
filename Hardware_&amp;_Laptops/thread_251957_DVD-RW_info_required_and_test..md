---
title: "DVD-RW info required and test."
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by Ausus on 2006-09-06
Hi all,

I need some info.
Which DVD-RW you use.
What feedback you get when you run the following command.
Code:
[HTML]hdparm -v dev/dvd[/HTML]

Please post the results.

If anybody knows where to look under Linux, info file which points to your DVD setup.

Regards

---

### Post by Ausus on 2006-09-07
Hi all,

This is what I get when running.
Code:
[HTML]hdparm -v dev/dvd[/HTML]

Result:
[HTML]IO_support   =  1 (default 32-bit)
   unmaskirq    =  1 (off)
   using_dma    =  1 (off)
   keepsettings =  0 (off)
   readonly     =  0 (off)
   readahead    = 256 (on)
   HDIO_GETGEO failed: Invalid argument[/HTML]

This makes me nervous when you get things like this.
[HTML]HDIO_GETGEO failed: Invalid argument[/HTML]
Does some one what this is.Give me positive feedback what this means.](*,) 
My burner supports up to 40 write speed on a normal CD.
I only get avarage 17.
Tried various burners under Linux.

Regards

---

