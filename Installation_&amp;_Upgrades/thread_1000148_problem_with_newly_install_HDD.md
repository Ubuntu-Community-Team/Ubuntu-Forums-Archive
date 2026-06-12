---
title: "problem with newly install HDD"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by kadafi69 on 2008-12-02
Ive just added a new WD 1TB hard drive, i want to format it to jfs, but Gparted wont let me, so for the mean time ive had to format it to ext3. once this was done there was a folder in the drive called lost+found, which I had to delete manually using root commands, I then had to set the permissions in the same fashion. theres nothing on the drive, yet when you check the properties it says 46.8Gb used and 870.1Gb free. there are no hidden files but something is taking up 46.8Gb of space. any ideas?

---

### Post by kadafi69 on 2008-12-03
bump

---

### Post by theravenproject on 2008-12-03
Every HDD has hidden partitions...I am not an expert on HDD's but my reccomendation is that you get some Forensic software and use it to find out-go into synaptic and find/install sleuthkit and then autopsy (Sleuthkits graphical interface) read up on how to use it and then check your HDD with it!

---

