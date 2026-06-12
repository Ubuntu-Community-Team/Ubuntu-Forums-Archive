---
title: "installlation issue with Xubuntu 9.04 - update manager stuck"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by pablolie on 2009-07-11
so i am doing a clean install on amachine that was running xubuntu 9.04 without a problem. i did upgrade the hard drive from a regular (old) drive to an ssd drive.

after the successful install, and the computer restarts, of course the next step is to go for updates. however, update manager gets stuck in "reading state information" and that is that. it doesn't crash (mouse still moves etc), it is just stuck and now it just came out of it stating 

failed to detect distribution
a error '[Errno 12] Cannot allocate memory' occurred while checking what system you are using.

i am without a clue on what to do - i have tried installing the SSD with different file systems and that does not make a difference.

---

### Post by pablolie on 2009-07-11
oh, and then the applications tab disappears from the top system menu. gone.

---

### Post by pablolie on 2009-07-11
here's a theory - the system has low memory (256mb) and because of the ssd has no swap file. could it be that the update process runs out of system memory?

---

### Post by pablolie on 2009-07-11
my suspicion proved right - upon going with swap space everything seems to run better. kind of sucks to *have* to use swap with an SSD, but for now it is the only thing that works.

the advice on system configuration with SSD should be updated to reflect the fact that it doesn't work with smaller RAM configurations.

i have another old system that works without a swap file with 384MB. this one doesn't with -i checked- 192MB. and i kind of doubt the change to 256MB if i get the system to recognize it would change much, but i may go check.

i wish i could contribute this experience to a wiki somewhere, but i can't find the right place. just for people who try to breathe new life into old systems with SSDs.

---

