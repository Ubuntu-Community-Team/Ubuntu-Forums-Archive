---
title: "Slow/stuttering printing through parallel port"
date: 2009-12-04
forum: Hardware
---

### Post by rmflagg on 2009-12-04
Hi everyone,

   I am having an issue with a Star Micronics TSP700 printer using the local raw printer driver under Jaunty.  The printer prints VERRRY slowly, stuttering the whole way, but it prints everything correctly.

   Here is where I become very confused.  I have two other printers on different machines, both the same model and same printer settings that print just fine at the right speeds!  The only difference is that they are running Hardy Heron!

   The printers are the same models, and the dip switches are all set the same and the software being used is all the same.

   Does anyone have any ideas as to what could be causing this?

Thanks,
RMFlagg

---

### Post by Crath on 2009-12-15
> **rmflagg said:**
> Hi everyone,

   I am having an issue with a Star Micronics TSP700 printer using the local raw printer driver under Jaunty.  The printer prints VERRRY slowly, stuttering the whole way, but it prints everything correctly.

   Here is where I become very confused.  I have two other printers on different machines, both the same model and same printer settings that print just fine at the right speeds!  The only difference is that they are running Hardy Heron!

   The printers are the same models, and the dip switches are all set the same and the software being used is all the same.

   Does anyone have any ideas as to what could be causing this?

Thanks,
RMFlagg

I'm also curious about this, thanks for asking!

---

### Post by pjoul on 2012-10-14
> **Crath said:**
> I'm also curious about this, thanks for asking!
Hello, I am experiencing the same issue as described here. Printing from Centos 6.3 (kernel 2.6.32) is without any hassles.

Otherwise in openSUSE 12.2 (kernel 3.4.6) or in Ubuntu 12.04 LTS (kernel 3.2) printing is very slow and NOT smooth. 

It seems to be kernel/parallel port driver issue (I have inspected all that CUPS logs and haven't found any problems here). This idea should be supported by what user rmflagg says: no problems with Hardy Heron (older kernel: 2.6.24), but slow printing under Jaunty (newer kernel: 2.6.28).

Please tell me if there are some new facts that should solve this issue.
Thanks!

---

### Post by pavelsefranek on 2012-10-21
Definitely fixed by a kernel patch: look here for details [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339752](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339752)

---

