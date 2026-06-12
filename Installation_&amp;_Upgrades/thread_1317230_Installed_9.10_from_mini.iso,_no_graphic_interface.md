---
title: "Installed 9.10 from mini.iso, no graphic interface???"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by apexironman on 2009-11-06
I just installed 9.10 on a G4 Powerbook using the mini.iso CD.  The install completed, the system restarted, a text version of yaboot appeared.  I default-booted to Linux, I logged in as requested, then the command prompt came up.  I tried to get GRUB information, but using the command "grub-install -v" returned a no such command message.  I am able to boot into OSX from the yaboot menu just fine.  What command am I not using???

Oh, yes,  I did try "startx", said command not found??

---

### Post by Mighty_Joe on 2009-11-06
Did you read the [Mac FAQ]("http://ubuntuforums.org/showthread.php?t=1046568") and [forum?]("http://ubuntuforums.org/forumdisplay.php?f=328")  I seem to remember using Mac hardware is fraught with peril.
The mini.iso does not include X, it only contains the packages necessary for installation.  If you want the full desktop, install the ubuntu-desktop package. 
[see here]("http://ubuntuforums.org/showthread.php?t=1155961")

---

