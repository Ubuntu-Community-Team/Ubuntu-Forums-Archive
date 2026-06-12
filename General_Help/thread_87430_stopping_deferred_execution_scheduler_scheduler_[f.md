---
title: "stopping deferred execution scheduler scheduler [fail]"
date: 2005-11-08
forum: General Help
---

### Post by RikoW on 2005-11-08
Dear all,

when I shutdown my laptop which runs Breezy, it seems that one of the services fails to stop properly. I see the following line marked with a red [COLOR="Red"][fail][/COLOR]:

Stopping deferred execution (executing?) scheduler     [[COLOR="Red"]fail[/COLOR]]

What is this deferred execution scheduler? Is that atd, which actually I turned off? And how come it fails to stop? Is there a way to fix that?

It doesn't seem to make any difference to the machine as far as I can tell, however, I like to have things in order! :)

Cheers,

            Riko

---

### Post by lifeperfecti0n on 2006-02-17
Hey I have the same problem and like you I think it would be better to remove it...i thought it was a program and searched synaptic but with no results.
Any suggestions guys?

---

### Post by rogeriovinhal on 2006-03-17
I think I started to have this failure notice after I disabled some services with sysv.

Anyone knows how to disable those services also for shutdown?

---

### Post by dcstar on 2006-03-17
[QUOTE=rogeriovinhal]I think I started to have this failure notice after I disabled some services with sysv.

Anyone knows how to disable those services also for shutdown?[/QUOTE]
They are probably still in your /etc/rc0.d directory, this is what is used for shutdowns (rc6.d is for rebooting).

You can remove the links from these directories - but be careful you only remove the right ones!!!!

---

### Post by rogeriovinhal on 2006-03-18
[QUOTE=dcstar]They are probably still in your /etc/rc0.d directory, this is what is used for shutdowns (rc6.d is for rebooting).

You can remove the links from these directories - but be careful you only remove the right ones!!!![/QUOTE]

Thanks, that worked.
I just removed the "K89atd" link from both rc0.d and rc6.d and now the ugly mesage of "fail" is gone. :)

---

### Post by splashi on 2006-10-14
Hi There!

I have the same Problem, after disabling some unneeded services with  sysv-rc-conf
.

Is there a way to find automatcally, which services are not loaded at startup, and remove them also from reboot and shutdown?

I do not want to crash my who le (why is this word banned?) system, by deleting things by hand from /etc/rc*

---

