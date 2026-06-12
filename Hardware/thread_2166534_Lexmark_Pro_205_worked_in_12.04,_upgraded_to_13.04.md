---
title: "Lexmark Pro 205 worked in 12.04, upgraded to 13.04 and now won't print"
date: 2013-08-09
forum: Hardware
---

### Post by Joseph_Raymond on 2013-08-09
We have just recently upgraded from 12.04 to 13.04 and now our Lexmark Prospect Pro 205 printer won't print.  We are getting this error: Idle - File "/usr/local/lexmark/v3/bin/printfilter" has insecure permissions (0100775/uid=0/gid=0).

What does that mean?  What permissions should that file have?  It also gives a "cups-insecure-filter" error as well.

We'd really like to get this printer working with Lubuntu 13.04 so we don't have to go back to 12.04.

---

### Post by Stephen_Barteau on 2013-09-22
> **Joseph_Raymond said:**
> We have just recently upgraded from 12.04 to 13.04 and now our Lexmark Prospect Pro 205 printer won't print.  We are getting this error: Idle - File "/usr/local/lexmark/v3/bin/printfilter" has insecure permissions (0100775/uid=0/gid=0).

What does that mean?  What permissions should that file have?  It also gives a "cups-insecure-filter" error as well.

We'd really like to get this printer working with Lubuntu 13.04 so we don't have to go back to 12.04.

I have this same issue and would really like to know the answer.  My WindowsXp has issues and I hate to keep going back to it.

---

### Post by Joseph_Raymond on 2013-09-23
> **Stephen_Barteau said:**
> I have this same issue and would really like to know the answer.  My WindowsXp has issues and I hate to keep going back to it.

I still haven't figured this one out.  For now we just have to print from our Windows 7 laptop.

---

### Post by Lenwon on 2014-01-01
I have Ubuntu 13.10 using lexmark pro 205 printer and also receive: Idle - File "/usr/local/lexmark/v3/bin/printfilter" has insecure permissions (0100775/uid=0/gid=0). error when trying to print.  I know Lexmark does not have any drivers for this particular build but would still like to persue a fix for this to avoid downgrading back to 12.04 which worked.

---

### Post by Lenwon on 2014-01-01
This worked for me for my Lexmark pro 205:

1. sudo chmod 755 /usr/local/lexmark/v3/bin/printfilter
2. sudo chgrp root /usr/local/lexmark/v3/bin/printfilter
3. sudo /etc/init.d/cups restart

---

### Post by Joseph_Raymond on 2014-01-08
> **Lenwon said:**
> This worked for me for my Lexmark pro 205:

1. sudo chmod 755 /usr/local/lexmark/v3/bin/printfilter
2. sudo chgrp root /usr/local/lexmark/v3/bin/printfilter
3. sudo /etc/init.d/cups restart

This worked!  Thanks so much!

---

