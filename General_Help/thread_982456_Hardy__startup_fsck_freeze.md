---
title: "Hardy:  startup fsck freeze"
date: 2008-11-14
forum: General Help
---

### Post by PlantPerson on 2008-11-14
Hello,  I'm running a standard Hardy Heron installation using kernel 2.6.22.14-generic (the newer kernel does not correctly support suspend).  I'm having a problem with the regular filesystem check that occurs every 26 boots.  Instead of finishing the check and then continuing the boot,  as it's supposed to do,  the computer stalls after the check is complete.  By "stalls" I mean that it simply sits there,  apparently waiting for something,  but nothing happens.  The computer remains responsive,  but it never finishes booting if the check runs. Any idea why this would be,  or how I can address the problem?  Thanks.

---

### Post by Dan_Dranath999 on 2008-11-18
Having the same problem here:

1.-Sometimes it hangs after the fsck checkup.
2.-Sometimes after entering login+password
3.-And at least once, it said something like "GUI is down, will use other" 

It'has been like this for just 4 or 5 days... everytime i needed to press the reset button. (this ain't good right?) and after that, the system would load normally.

---

### Post by cariboo on 2008-11-18
You should both run fsck using the LiveCD. Using the LiveCD doesn't mount the drives, so fsck should run to completetion.

Jim

---

