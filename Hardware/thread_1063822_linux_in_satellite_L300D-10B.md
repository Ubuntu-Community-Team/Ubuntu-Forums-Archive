---
title: "linux in satellite L300D-10B"
date: 2009-02-08
forum: Hardware
---

### Post by binary_dreamer on 2009-02-08
Hi. I got a laptop Toshiba Satellite L300D-10B and i want to install
ubuntu 8.10 without loosing the recovery tools that Toshiba pre-installed.
In case of an emergency i want to be able to recover the system to its
original settings. Any ideas on how to do that?

---

### Post by Xiaolong1.0 on 2009-02-22
The Toshiba l300d has a icon on the desktop to create recovery cd's for the system, After you make the cd's they will run from boot up and they do not require the Toshiba recovery partition, they are completely independent. if you do run into trouble you can boot them up and select the option to restore the system back to the (out of box) state.

---

### Post by binary_dreamer on 2009-04-24
the system currently does have two partitions. the first one is the one with the winvista (c) and the second one has the hddrecovery utilz.
i need to create three partitions for the installation of ubuntu. will it be ok if i will format C and chop it into 4 partitions? 3 for ubuntu and 1 (c) for windows? will i be able to restore windows to its original state?

---

### Post by Xiaolong1.0 on 2009-04-24
it will be perfectly fine to chop the c drive into 4 partitions if needs be. as long as you have created your recovery cd's the hddutils/recovery drive is not needed.

as i seen you where also recommended wubi on the toshiba forums. which as long as you can spare and extra 258 megs of ram and 5 gigs storage space it will work fine, ultimately good if you do not want to tamper with the partitions on your drive. But you should have no problem with formating the drive.

---

### Post by binary_dreamer on 2009-04-25
thanks for your answer, but wubi it is completely irrelevant to what i have asked.
any suggestions?

---

### Post by lisati on 2009-04-25
The Toshiba M200 I have came with tool to make recovery CDs/DVDs from the recovery partition as well. Before you start tinkering with partitions, it might be a good idea to use the copy on your machine if it has one (just in case) 

My machine came with three partitions and a small amount of unallocated space at each end of the disk - one was the recovery partition, one the main Vista partition, and one which appears to have been used only in the initial installation - my research via google & the Toshiba forums, suggests that it is usually safe to delete the third partition thus freeing up a bit of space for Ubuntu.  Make sure you've made your recovery disk(s) and made a backup of important data first!


EDIT: I agree with the earlier post: once you've made your recovery disk(s) it's ok to remove the recovery partition as well. Be aware that moving the Windows partition might take a while - on my machine it took nearly 5 hours!

---

