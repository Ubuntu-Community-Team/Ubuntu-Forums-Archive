---
title: "Unable to print large documents"
date: 2008-11-26
forum: General Help
---

### Post by kwaanens on 2008-11-26
In relation to this thread, from the archived section:
[http://ubuntuforums.org/showthread.php?t=625493](http://ubuntuforums.org/showthread.php?t=625493)

I'm using a networked Lexmark C530dn on Ubuntu 8.10
When I try to print a 116 page OpenOffice.org document, with a lot of images, totalling in a little over 50 MB, I get the following in /var/log/cups/error_log:
E [26/Nov/2008:11:31:03 +0100] [Job 20] Unable to write print data: Broken pipe
E [26/Nov/2008:11:31:03 +0100] PID 18738 (/usr/lib/cups/backend/socket) stopped with status 1!

Breaking the document down to smaller print jobs (printing page 1-10, then 11-30) works.

How can I get this fixed? This is not very user friendly...

Thanks!

-- Ketil

---

### Post by avrelus on 2009-03-27
> **kwaanens said:**
> In relation to this thread, from the archived section:
[http://ubuntuforums.org/showthread.php?t=625493](http://ubuntuforums.org/showthread.php?t=625493)

I'm using a networked Lexmark C530dn on Ubuntu 8.10
When I try to print a 116 page OpenOffice.org document, with a lot of images, totalling in a little over 50 MB, I get the following in /var/log/cups/error_log:
E [26/Nov/2008:11:31:03 +0100] [Job 20] Unable to write print data: Broken pipe
E [26/Nov/2008:11:31:03 +0100] PID 18738 (/usr/lib/cups/backend/socket) stopped with status 1!

Breaking the document down to smaller print jobs (printing page 1-10, then 11-30) works.

How can I get this fixed? This is not very user friendly...

Thanks!

-- Ketil

Hi, the solution might be printing in 'lpd' mode instead of 'socket' mode.
see 
[http://p-s.co.nz/wordpress/?p=227](http://p-s.co.nz/wordpress/?p=227)
or
[http://www.dejadejoder.com/drup/node/53](http://www.dejadejoder.com/drup/node/53) (in french)

---

