---
title: "Clam AV Removal"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by therockindonkey on 2009-04-02
I am trying to remove Clam AV from my system (Ubuntu) as I screwed up the install and now I get errors any time I try to update software (the errors aren't causing problems, they're just annoying)

Is there a manual process for removal?  I've tried a number of things in the terminal and haven't had any luck.  I keep getting "unable to find package"

Thanks in advance for any help you can provide.

---

### Post by sadicote on 2009-04-02
sudo apt-get --purge remove clamav clamav-base clamav-daemon clamav-freshclam libclamav2

---

### Post by therockindonkey on 2009-04-03
> **sadicote said:**
> sudo apt-get --purge remove clamav clamav-base clamav-daemon clamav-freshclam libclamav2


Thank you!  Did the trick!

---

