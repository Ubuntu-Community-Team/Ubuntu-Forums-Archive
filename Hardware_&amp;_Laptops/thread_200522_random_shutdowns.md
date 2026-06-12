---
title: "random shutdowns"
date: 2006-06-20
forum: Hardware &amp; Laptops
---

### Post by barna on 2006-06-20
Hi,
Previously (with Breezy) I have experienced random shutdowns on my laptop. I have installed 6.06, and was very happy to have a stable system, with no problems for several weeks. Today, suddenly, while away from my notebook, it shut down again, with the same symptons in /var/log/messages, as before

Jun 20 10:00:06 localhost kernel: [17180153.036000]     ACPI-0258: *** Error: Thread 1096 cannot release Mutex [MUT1] acquired by thread 1321
Jun 20 10:00:06 localhost kernel: [17180153.036000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.RDEC] (Node dbfd6220), AE_AML_NOT_OWNER
Jun 20 10:00:06 localhost kernel: [17180153.036000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.BAT1._BST] (Node dbfda380), AE_AML_NOT_OWNER
Jun 20 10:00:07 localhost shutdown[5445]: shutting down for system halt

Does anybody have an idea, what this is due to? 
I had kubuntu installed. Recently I have tried to install and use xubuntu-desktop. These random shutdowns and the installation of xubuntu-desktop might be an accidental coincidence... but if really so, what is the reason of the sudden appearance of this problem again? 

I have a Toshiba Satellite SA60-185

Thanks
Daniel

---

### Post by be_placid on 2006-06-20
It seems to be a problem with ACPI. Perhaps try reinstalling it (using your favourite app or `sudo apt-get --reinstall install acpi` in a terminal)

Have you installed anything laptop-related that might have affected the normal settings of ACPI?

---

### Post by jml on 2006-06-20
I've read in other forum areas that several people are having problems with 6.06.  It seems that there are problems with ACPI causing the coolong fans not to turn on.  When a certain temperature is reached, the computers shut down as a protective mechanism.  Next time you turn your computer on, see if the fan comes on.  If it doesn't, that might be the problem.

Joe

---

### Post by barna on 2006-06-22
Hi, 
let me answer my own question. 

First of all, it was surely not related to the fan. It was a software shutdown (previously, due to a lot of dust in my cooling system, I had very frequent shutdowns when the processor overheated, but that was a sudden switch-off of the computer. In contrary to that, these random shutdowns now were correctly stopping all processes, unmounting filesystems, etc - that is, a normal shutdown)

I have recalled that just before the reappearance of these random shutdowns I have installed sleepd
(why? because I wanted to have a system-wide mechanism to safely shut down my computer when battery goes low, even if I do not log in to KDE [kde has its own power management, it seemed to me])

After removing sleepd, these random shutdowns were gone. So I guess there is either a bug in sleepd, or it simply badly interfered with other things (maybe kde power management? I don't know)

So a few questions:
- since the power management settings in kde are per user (and not system-wide), I guess they only apply if the user logs in. That is, if I am not logged in, and my battery runs low, there will be no safe shutdown or hibernation. Is this correct?
- If I would like to have such a feature, what is the right way (WITHOUT sleepd)?

Thanks
Daniel

---

### Post by barna on 2006-06-26
I found the reason, see
[http://ubuntuforums.org/showthread.php?t=185689](http://ubuntuforums.org/showthread.php?t=185689)

---

