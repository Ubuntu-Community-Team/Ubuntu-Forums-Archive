---
title: "PulseAudio died recently"
date: 2008-09-14
forum: General Help
---

### Post by gldblade on 2008-09-14
Hey guys,

It seems that my install of PulseAudio has randomly died.  Nothing can connect to my local sound server, not even the PulseAudio tools themselves.  When I try to run PulseAudio manually, I get the following error:

E: mutex-posix.c: Assertion 'pthread_mutex_unlock(&m->mutex) == 0' failed at pulsecore/mutex-posix.c:98, function pa_mutex_unlock(). Aborting.

I did some Googling and supposedly this is caused by libtool being older than 1.5.24.  However, my libtool version is 1.5.26, so I don't think this is the problem.

Any ideas on how to fix PulseAudio?  Thanks in advance!
Ceryen

---

### Post by nbayiha on 2008-09-14
try this 
[http://ubuntuforums.org/showthread.php?t=789578&highlight=youtube+sound+problem](http://ubuntuforums.org/showthread.php?t=789578&highlight=youtube+sound+problem)

---

### Post by gldblade on 2008-09-14
Unfortunately the link didn't help me.  Any other ideas?

---

