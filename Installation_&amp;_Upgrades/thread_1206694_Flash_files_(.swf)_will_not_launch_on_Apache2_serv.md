---
title: "Flash files (.swf) will not launch on Apache2 server"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by beantown on 2009-07-07
**Flash files (.swf) will not launch on Apache2 server** 			
 			 			 		   		 		 		Recently updated to 9.04 from 8.10.

Running Apache2 hosting a website.

/var/www files all remained the same.

.swf files will not play from any web client.
All .html files are fine.

Any ideas?

Thanks!

---

### Post by beantown on 2009-07-07
Problem was due to corruption of flash files.

Made the mistake of transferring using ascii instead of binary. Doh!
Transferred via ftp binary mode and all set now.

---

