---
title: "Hard disc SMART status : is this disc faulty?"
date: 2012-05-13
forum: Hardware
---

### Post by ticket on 2012-05-13
I recently installed a new 500GB internal drive:

> Seagate 500GB 3.5" SATA-III 6Gb/s Barracuda Hard Drive 7200RPM 16MB Cache

After formatting, etc to ext3 and copying data to it, I noticed the Disk Utility program (v3.0.2) reported the following SMART data for it:

> Read Error Rate Value: 30965016
Seek Error Rate Value: 231703

I ran an extended SMART self-test, which completed successfully. The Disk Utility program also displays 'Disk is healthy' and no bad sectors.

In contrast, for the following older 250GB disc: 

> Samsung Spinpoint F1 series 250GB 7.2K 8MB SATA Hard Drive - HD251HJ SATA 300 - 3.0Gbps

the Disk Utility program reported the Read Error Rate Value and Seek Error Rate Value as zero.

Is the 500GB disc faulty, or am I wrongly interpreting the output for the Disc Utility program?

My m/b only supports SATA speeds of 3.0 GB/s, if that is relevant.

Screen shots of the SMART data for the two drives are attached.
Running Ubunu 11.10 with latest updates.

---

### Post by ahallubuntu on 2012-05-13
I don't think that's a real value.  It's an error RATE not number of errors.  If that number were real, it would be catastrophic.  

Note that S.M.A.R.T. is not completely standard among manufacturers.  (S.M.A.R.T. is built into the drive's firmware.)  One manufacturer may report a value differently than another or give it a slightly different meaning and the S.M.A.R.T. software in Ubuntu may not be able to interpret the difference.

Anyway, no other errors are showing - all is green.  If you are worried, do an extended S.M.A.R.T. test (probably take 1-2 hours) and if that passes, don't worry about it.

---

### Post by ticket on 2012-05-13
Thanks ahallubuntu.

I did do an extended S.M.A.R.T. test (took 1.5 hours), and no errors were reported.

I hope you are right that I can ignore the weird stats from Disc Utility!

---

### Post by ahallubuntu on 2012-05-13
However, keep this in mind: ANY hard drive can fail with little or no warning!  S.M.A.R.T. may help you detect problems early or it may not.  It's very wise to make regular backups and not assume any drive is completely "safe."  Make backups of important files on a second device frequently or backup online.  Have at least two copies of important files is my rule.

---

### Post by sudodus on 2012-05-13
> **ahallubuntu said:**
> However, keep this in mind: ANY hard drive can fail with little or no warning!  S.M.A.R.T. may help you detect problems early or it may not.  It's very wise to make regular backups and not assume any drive is completely "safe."  Make backups of important files on a second device frequently or backup online.  Have at least two copies of important files is my rule.
+1
Backup at least your private files regularly. It can also be a good idea to have a complete backup of the whole drive (a clone or an image). That makes it easy to restore your system after a crash.

---

### Post by ticket on 2012-05-18
More recent SMART report attached - the read error rate is 10 times less than before ...

---

