---
title: "apt-get install reboots computer"
date: 2005-11-07
forum: General Help
---

### Post by kawinter on 2005-11-07
I ran apt-get install normalize-audio and apt wanted to install some language packs but errors appeared saying that the language-pack-en base had not been configured. Now, whenever I try to run apt-get install anything the computer throws up LOCALE errors and reboots. I have googled the "LOCALE: Cannot set LC-CTYPE to default Locale: no such file or directory" and the answer appeared to be to run locale-gen. However, when I run locale-gen the computer also crashes and reboots. This has totally immobilized apt and I found another thread somewhere in Ubuntu forums where someone was already asking about the LOCALE error and no one had an answer for her. Judging by the amount of documentation in Google, this is not an unusual problem, but it is one where I have not found an answer that works, nor do I see one in this forum? Can anyone help?

---

### Post by mlomker on 2005-11-10
Locale issues are common, I experienced that myself on a 64-bit Hoary->Breezy upgrade.  I opted to deal with my plethora of problems by doing a fresh install.  I've never heard of it causing a reboot, though.  Was your machine an upgrade?

---

### Post by kawinter on 2005-12-10
[QUOTE=mlomker]Locale issues are common, I experienced that myself on a 64-bit Hoary->Breezy upgrade.  I opted to deal with my plethora of problems by doing a fresh install.  I've never heard of it causing a reboot, though.  Was your machine an upgrade?[/QUOTE]

No sir, it was not.  It was an original install of Breezy on and AMD64 machine.  It is the only thing ruining this Ubuntu install for me so if anyone has any suggestions as to how to deal with it I would be ever so grateful.

I have tried running apt-get install -f and the message I got was:
 
 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
 
 So I ran dpkg --configure -a and my computer crashed and rebooted. 

I cannot install new programs, upgrade anything... I am frantic](*,)

---

