---
title: "Hard lockup during /home backup"
date: 2010-05-27
forum: Hardware
---

### Post by ectospasm on 2010-05-27
I'm trying to back up my home directory (~200GB) to my 1TB USB hard drive, and I'm running into problems.  I've tried both nautilus and rsync to transfer the files, and at some point my machine hard locks during the transfer.  There's nothing I see in /var/log/messages or /var/log/syslog, and I doubt CPU or memory issues could be it since I ran mprime on this machine for a week to root out any issues there.  If it's the SATA or USB controller, is there any way to verify that's the problem?

---

