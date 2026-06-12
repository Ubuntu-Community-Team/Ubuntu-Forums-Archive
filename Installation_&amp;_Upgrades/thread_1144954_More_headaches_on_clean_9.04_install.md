---
title: "More headaches on clean 9.04 install"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by bikeman1 on 2009-05-01
I am still having problems getting my admin account fully capable to do root activities - like specifically adding/editing users and groups!  The GUI users-groups utility grays out everything in there I might change including my own group membership!  

Secondly, I am having difficulty starting Samba from the command line -- in response to

sudo/etc/inet.d/samba restart

I get "command not found". The startup script file is present and my admin account has read+write access.  Nothing appears on the Samba log, so I assume I am just not getting Samba up and for some reason - permissions or otherwise - I am not startinmg the script.  Would there be a log for this failure somewhere?  Could a dependency not be properly installed?

This new install of Jaunty has been quite flaky.  I jumped several versions so I had no in tention of keeping the old install (7.04) and specified to format over the old root partition, but it apparently found and grabbed some links from my old desktop (not users).  It really does not want to give my admin user full control.  Is there a way to edit sudoers to empower my poor wimpy superuser??

Aaagh!:guitar:

---

### Post by emarkay on 2009-05-01
There's new features in some of these dialog boxes - "unlock" that aren't obvious - just in case that may be it...

FWIW what hardware ado you have - PC and graphics?

---

### Post by bikeman1 on 2009-05-05
I am using a Gigabyte AM2 motherboard with an integrated video adaptor. 

I have gotten the Samba config to run.  The only hangup now is the dysfunctional Users-Groups front-end.  I can administer users just fine from within a sudo terminal -- it is just the GUI version that is not authenticating.  Usingt gksudo as the link prefix.  WTH????

---

