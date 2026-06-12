---
title: "Upgrade -   using CD only not working"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by paul.prinsloo on 2009-09-29
hi..  trying to upgrade from 8.10 to 9.04 on a standalone PC.. no internet available. 
I downloaded the ubuntu-9.04-desktop-i386.iso at work, burned it to CD, did the checksum thingy, and thought I am ready to upgrade.
When I insert the CD, it just pops up a warning, saying this cd contains software, do I want to run it or not. I say yes go for it.. and it fails immediately with a message about autorun file not found.
Please.. any suggestions?

---

### Post by pmlxuser on 2009-09-29
you downloaded the wrong image  for upgrading with CD only you need the "alternate-cd" iso,

[http://releases.ubuntu.com/9.04/ubuntu-9.04-alternate-i386.iso](http://releases.ubuntu.com/9.04/ubuntu-9.04-alternate-i386.iso)

---

### Post by paul.prinsloo on 2009-09-29
lovely..  thanks for the info.
:(

---

### Post by Bartender on 2009-09-29
> **paul.prinsloo said:**
> When I insert the CD, it just pops up a warning, saying this cd contains software, do I want to run it or not. I say yes go for it.. and it fails immediately with a message about autorun file not found.
Please.. any suggestions?

What do you mean by "it" pops up a warning?  

The PC has to boot from the CD.  Put the CD in the tray, ignore warnings, restart the PC.  If you don't see the optical drive spin up and access the CD, maybe your BIOS is set to go to HDD first?

I'll assume that you burned the .iso correctly since you've done it before.

Shouldn't make any dif whether you downloaded the alt-install or standard LiveCD.

---

### Post by paul.prinsloo on 2009-09-29
I did not try and boot from the Cd.. I inserted the CD while Intrepid was already up, in order to perform an upgrade. This was my understanding of the upgrade process from cd.
Either way.. how now burned the Alternate iso.. will try it tonight and see what happens.

---

### Post by pmlxuser on 2009-09-29
> **Bartender said:**
>  


Shouldn't make any dif whether you downloaded the alt-install or standard LiveCD.

sorry man you can not do an upgrade with a standard liveCD -you can do a clean install.

the only way to do an upgrade without Internet connection is using an alternate cd

---

### Post by paul.prinsloo on 2009-09-30
right.. some feedback. Used the alternate CD last night to try and upgrade. Inserted the thin while Ubuntu 810 was running, popped up options to either start package manager or upgrade. I chose upgrade.. and nothing happened. After that I could not get it to prompt again, does not matter how many times I ejected and inserted the CD. 
Anyone have any ideas please?

---

### Post by theozzlives on 2009-09-30
Maybe a bad download/burn? Did you check the MD5SUM?

---

### Post by paul.prinsloo on 2009-09-30
yes..  I checked the MD5SUM and it is fine.  I even tried to do the GKSU "sh /cdrom/cdromupgrade" which I saw somewhere.. and that also does nothing.

---

### Post by Bartender on 2009-09-30
> **pmlxuser said:**
> sorry man you can not do an upgrade with a standard liveCD -you can do a clean install.

the only way to do an upgrade without Internet connection is using an alternate cd

Oops, sorry, pmlx understood the OP's issue and I did not.  

It almost sounds like the optical drive might be getting a little worn out...

Do you have important personal data in /home?  Do you have any options for saving personal data to a separate HDD and doing a full install?

---

### Post by slakkie on 2009-09-30
Hi,

please follow the guide: [https://help.ubuntu.com/community/JauntyUpgrades](https://help.ubuntu.com/community/JauntyUpgrades)

If you open a terminal, you will get some messages. Best is to paste them here so people understand more clearly what went/goes wrong.

---

### Post by paul.prinsloo on 2009-10-01
Ok I gave up in this...  decided to re-install from scratch and thats that. Will just take the punch and do all the cutomization again. 
Thanks for the helping efforts.

---

