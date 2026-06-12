---
title: "CDROM read problems. Could be the upper and lower filters?"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by luzdegas on 2008-01-03
Hi,
I have a Dell XPS M1210 running Gutsy, I suddenly start to have problems reading CDs (it seems that reading DVDs works fine). I can always mount a data cd, and look at the directory content, but when I try to read the data, the optical unit starts retrying and making funny noises. Sometimes I can see the data on the cd, and sometimes I can't. Usually when I try to eject the CD the unit does not stop, and I have to reboot the system to be able to eject the CD (sometimes the unit stop and I can eject the CD, but after waiting a lot).

I contact Dell support, and they told me (assuming that I have Windows installed) to "remove the lower and upper filters". I' ve searched for an equivalent of these in Ubuntu, but I could not find anything similar. So the question is, is there something like this in ubuntu? Could this be the cause of the problem?

---

### Post by disturbed1 on 2008-01-03
Sounds like a bad CD. Try a pressed CD. Also run dmesg tail in a term to get the last output from when the CD was inserted.

"remove the lower and upper filters" has to do with the Windows registry. Some software burning programs install these "filters". The wrong one, or a cobonation of 2 together such as packet writing software and windows IMAPI, could cause these problems. They are related to ASPI issues.

Besides defect CDs, other causes for this in Linux. Corrupt/incorrect/tampered with FSTAB, wine program running in the background with bad "filters", previously finished burning program did not close properly, previously ran burning program was ran with root access and either terminated or did unmount the drive properly, and on and on. Mostly to do with software that access the drive itself. Usually a reboot will fix this.

---

