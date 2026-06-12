---
title: "installing red hat enterprise linux 5"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by fourthofjuly on 2009-06-08
hello,

i have a dual boot system with ubuntu and xp on my first hard drive

i wish to install red hat enterprise linux on my second drive

however, it overwrites the ubuntu bootloader and does not recognize it in its own bootloader

the ubuntu partitions are labelled, and labels have been used to refer to partitions in grub.conf also

can i make an entry in rhel's grub.conf by pasting the entries from ubuntu's grub.conf file?

thanks in advance...

---

### Post by zvacet on 2009-06-08
I'm sure there is a solution on Red heat forums if you want to keep that bootloader.If you want to use Ubuntu bootloader then [reinstall grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") and chainload other Os.

---

### Post by fourthofjuly on 2009-06-09
zvacet,

yes, i would like to use the redhat bootloader, still hunting for the solution...

thank you.

---

