---
title: "Ubuuntu won't install!  XP will!"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by monkeywrench10 on 2009-06-13
OK, here are the facts and observations:

    Trying to install Ubuunto on a gateway computer (about 3 years old)

    There is a long series of errors in the install mostly having to do with permissions being denied as a result of a segmentation fault.

    I have also tried to install several other distros and all failed.  Fedora mentioned that the filesystem failed to mount that that installation could not continue.

    Nevertheless,  Windows XP WILL install.  The machine used to have XP on it before attempting to install linux.  Even stranger, the XP install did not ask me for a license key!  It installed without it.  (Note: computer is not connected to any network and all discs are legit)

So, I installed XP, poped in the ubuuntu disc, and took the install to HD option.  Install froze just as before.

oh yeah, one last thing.  I have 4 identical gateway machines and all linux installs have failed on all four machines. All four machines had XP first.

ANyway have any clues.   I have been at it for a day and a half and the only thing I can make work is windows.

mw10

---

### Post by merlinus on 2009-06-13
Do a checksum on your .iso, and burn at 4x or slower.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by donkyhotay on 2009-06-13
> **monkeywrench10 said:**
> OK, here are the facts and observations:

    Trying to install Ubuunto on a gateway computer (about 3 years old)

    There is a long series of errors in the install mostly having to do with permissions being denied as a result of a segmentation fault.

    I have also tried to install several other distros and all failed.  Fedora mentioned that the filesystem failed to mount that that installation could not continue.

    Nevertheless,  Windows XP WILL install.  The machine used to have XP on it before attempting to install linux.  Even stranger, the XP install did not ask me for a license key!  It installed without it.  (Note: computer is not connected to any network and all discs are legit)

So, I installed XP, poped in the ubuuntu disc, and took the install to HD option.  Install froze just as before.

oh yeah, one last thing.  I have 4 identical gateway machines and all linux installs have failed on all four machines. All four machines had XP first.

ANyway have any clues.   I have been at it for a day and a half and the only thing I can make work is windows.

mw10

Sounds like an OEM copy of XP thats slaved to that particular computer. Generally you don't get asked the product key because it's hardwired in a chip on your motherboard however you also can't install that copy on any other computer either. Back to your ubuntu no-intall issue... Does the liveCD boot up properly at least even if the install fails? What hardware specs does that computer have?

---

### Post by monkeywrench10 on 2009-06-13
Some success!!!!

Apparently, it is the well known NVidia card issue.  (well known to everyone but me) I just got ubuntu desktop to run on ONE of my desktop computers...(I tried one without the card).

This explains why my old windows server 2003 small business loaded up Ubuntu server but the other machines would not.....they all had the "fancy" Nvidia cards!!!

But it also reminds me of a problem I had with my laptop....it came with vista, i wanted to put XP on it and it would not take it.  It would take linux.  This machine had to be windows so I put Vista back on it.  It is a Sony Vaio laptop.  Just thought it was weird that it would take one MS OS and not another.  Anyone know anything about htat?
wbw

---

