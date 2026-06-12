---
title: "CUPS will not start..."
date: 2008-11-27
forum: General Help
---

### Post by VastOne on 2008-11-27
Message in lpr.log

cupsd: Unable to read configuration file '/etc/cups/cupsd.conf' - exiting!

Info: This is a remastersys Live CD install of working version of 8.10 with CUPS and hplip working perfectly

ls -l /etc/cups/cupsd.conf 
-rw-r--r-- 1 root root 2378 2008-10-20 01:59 /etc/cups/cupsd.conf

 ls -ld /etc/cups/
drwxr-xr-x 4 root lp 4096 2008-11-26 12:26 /etc/cups/

I am thinking hte issue lies in the rights to run the file..

Could use some help on this

Thank you

---

### Post by mechanicalturk on 2008-11-27
I have the same permissions for both /etc/cups and /etc/cups/cupsd.conf, if that helps.  I'm also listed as a member of the lpadmin group in /etc/group.

---

### Post by VastOne on 2008-11-28
Thanks Mechanical. 

Although it does not solve it, it helps me considerably

VastOne

> **mechanicalturk said:**
> I have the same permissions for both /etc/cups and /etc/cups/cupsd.conf, if that helps.  I'm also listed as a member of the lpadmin group in /etc/group.

---

### Post by VastOne on 2008-11-28
Anyone, or is this another off to the Out of Reach bin?

> **VastOne said:**
> Message in lpr.log

cupsd: Unable to read configuration file '/etc/cups/cupsd.conf' - exiting!

Info: This is a remastersys Live CD install of working version of 8.10 with CUPS and hplip working perfectly

ls -l /etc/cups/cupsd.conf 
-rw-r--r-- 1 root root 2378 2008-10-20 01:59 /etc/cups/cupsd.conf

 ls -ld /etc/cups/
drwxr-xr-x 4 root lp 4096 2008-11-26 12:26 /etc/cups/

I am thinking hte issue lies in the rights to run the file..

Could use some help on this

Thank you

---

### Post by VastOne on 2008-11-30
Bump

---

### Post by VastOne on 2008-12-02
Bump

---

### Post by VastOne on 2008-12-16
Bump

---

### Post by romeyde on 2009-01-03
this ever get resolved?   i now have the same problem.   installed old system onto new box using remastersys and now cupsd won't run with the unable to read configuration file issue.   before installing with remastersys the printer worked fine.

---

### Post by VastOne on 2009-01-03
Nope, never seen anything close to resolving

---

### Post by romeyde on 2009-01-04
> **VastOne said:**
> Nope, never seen anything close to resolving

I actually figured out my issue and resolved it in a different thread.   Here's how I managed to fix it.   Maybe it will help you.


----

Re: remastersys and cupsd

after hours of messing with it, i finally resolved the issue, didn't realise cups had it's own error log in /var/log/cups. saw this there:

E [03/Jan/2009:19:19:32 -0500] "/etc/cups/ssl/server.crt" is a bad symlink - No such file or directory
E [03/Jan/2009:19:35:33 -0500] "/etc/cups/ssl/server.key" is a bad symlink - No such file or directory

just deleted those symlinks and the daemon was happy.

---

### Post by newbie_bob on 2009-05-05
where do you go to edit the links?

---

