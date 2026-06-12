---
title: "can't print mulit-page documents"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by sphilli8 on 2007-11-28
I can print documents, as long as they are only one or two pages long. If I try to print many more pages than that, it doesn't work. 

I had a look in /var/log/cups/error_log and these are the messages it gives:
```
E [28/Nov/2007:05:41:24 +0000] [Job 201] Unable to write print data: Broken pipe
E [28/Nov/2007:05:41:25 +0000] PID 13359 (/usr/lib/cups/backend/socket) stopped with status 1!
```

I am trying to print to a Fuji-Xerox C525 A. The driver for the printer was converted to a .deb file from an .rpm that I downloaded from the Fuji-Xerox website.

I have no idea what that error log means, can anyone help me?

---

### Post by boronk on 2007-12-20
Hello, I have a network-enabled Minolta MagiColor 2350 with Postscript support and the same problem. Since using Gutsy Gibbon, multiple-pages printing results sometimes in this error, restarting the complete job.

For me, it looks like a cups problem.

Christian

UPDATE:

It seems really to be a Gutsy Gibbon problem. At least Dapper Drake was able to print the document via cups and my printer flawlessly. The problem is perhaps only when the document gets too big (200MB)  and is sent to a real postscript-network-printer.

---

### Post by Edward C on 2008-01-21
I've got the same printer (C525A) and used the same drivers on Hardy AMD64 and I'm getting that same "Broken pipe" message on most print-jobs longer than a page or two.

---

### Post by doychi on 2008-06-04
Hi All,

I'm having similar issues.  I can print multiple pages for some things, but when the file gets large I have the same problem.
--
Doychi

---

