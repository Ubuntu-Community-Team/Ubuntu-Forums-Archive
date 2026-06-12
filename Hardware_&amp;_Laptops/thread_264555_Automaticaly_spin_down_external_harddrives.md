---
title: "Automaticaly spin down external harddrives"
date: 2006-09-24
forum: Hardware &amp; Laptops
---

### Post by KSDZ on 2006-09-24
I recently bought an external harddrive, and I found out hdparm wasn't able to make  it spin down automaticaly.

That's why I wrote a script for this job. It's not perfect in many ways, but it sort of gets the job done.

It checks multiple harddrives and is able to stop them appart from each other.

So, if you have any ideas how to make this better, please reply.

The code's in the attachment.

---

### Post by MetalMusicAddict on 2006-09-24
Wow. Thats a great idea. I know a friend who would like this. :)

---

### Post by KSDZ on 2006-09-25
I fixed some stuff... take a look at it

---

### Post by nickbooker on 2006-10-04
Small bug on line 125 - 'if verbose:' should read 'if system.verbose:'. As it stands, on CTRL+C it throws an uncaught exception whether -v is supplied or not:
NameError: name 'verbose' is not defined

---

### Post by KSDZ on 2006-10-04
Thx. It's fixed

---

### Post by waldorf on 2007-06-29
So how do I use this script? execute it once? run it as a cron job?

Thanks in advance!

---

