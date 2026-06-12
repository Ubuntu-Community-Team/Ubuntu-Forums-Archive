---
title: "[SOLVED] Having trouble with my system."
date: 2008-10-09
forum: General Help
---

### Post by MedianMajik on 2008-10-09
I just hooked up my Ubuntu 8.04.1 64-bit box in my new house and it hasn't been updated in 52 days.  Running apt-get update gave me a 404 error while connecting to *[http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy all*.  I selected the main server for updating, deselected the erroneous repo, and was able to make a couple dozens updates.  The problem is that many apps are still out-of-date on my system and I'd love to just use the command line or synaptic to work all this out.  I've been surfing the forums and can't find a solution to this problem.

Thanks in advance for your help

---

### Post by WWSmith36 on 2008-10-09
> The problem is that many apps are still out-of-date on my system

Applications will only receive patches and security updates.  Since ubuntu updates every six months, it locks the versions of all installed applications to the most stable release.

So basically you will not get version updates for applications.  You might be able to get version updates from other sources like backports or the developer.

---

### Post by MedianMajik on 2008-10-10
Thanks, I was wondering if I'd need to go through developers until 8.10 rc

---

### Post by Metaleks on 2008-10-10
If you're interested, some programs have their own repositories. Programs such as WINE (assuming you have their repo added) will automagically update whenever a new version comes out.

---

