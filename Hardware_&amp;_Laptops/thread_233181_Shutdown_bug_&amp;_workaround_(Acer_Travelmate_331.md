---
title: "Shutdown bug &amp; workaround (Acer Travelmate 331T)"
date: 2006-08-09
forum: Hardware &amp; Laptops
---

### Post by Kalypso on 2006-08-09
I have successfully installed dapper drake/Kubuntu 
on an Acer Travelmate 331T with 512 MB and 
an IBM Travelstar 20 GB disk.

Kubuntu works quite decent compared to the age
(seven years) of the laptop. One problem still persists
thought I installed all of the latest bugfixes -
the shutdown bug that was reported by many users.

When shutting down KDE is closed, the Kubuntu
start screen reappears but not the list with
the processes been terminated. After a few
seconds the screen goes black and (except for
a few hard disk accesses) that's it.

The solution to the problem is simple but
not obvious: Just shutdown from the shell 
with "sudo halt".

The bug is appearently caused by a problem with
user rights otherwise the sudo command would
not work.

Cheers

Kalypso

---

### Post by Kalypso on 2006-11-03
Update:

Edgy Eft works much better on the Acer Travemate 331
than Dapper Drake.

The shutdown bug has been fixed - you don't need
the workaround anymore.

And the look and feel of KDE is that the machine runs
faster and smoother now! A big improvement in usability!

Even the old hardware (PII 333 MHz) delivers enough
performance to really work with Kubuntu.

Cheers 

Kalypso

---

