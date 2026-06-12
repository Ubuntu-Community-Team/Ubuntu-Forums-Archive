---
title: "Thinkpad R52 poor disk performance"
date: 2010-05-13
forum: Hardware
---

### Post by sennen on 2010-05-13
My old Thinkpad R52 laptop got pushed back to me the other day from a family member asking me to look into why it was running so slow.

It has been running Ubuntu since 8.something, and was pretty quick when I first gave it away. It has been regularly updated and upgraded through 9.x and now onto 10.04. 

I have observed the overall performance before and after this last upgrade to be shockingly poor: the screen saver can kick-in (10 minutes) while waiting for the OpenOffice banner to appear upon starting the word processor. Sometimes boot-to-login screen time seems like an age - where previously it took less than 90 seconds.

There are no disk-related errors logged anywhere, but I do notice disk performance is atrocious: hdparm -t shows anything between 700KB/s to 4MB/s, when it should easily be up in the 20-30MB/s range. SMART checks on the disk, however, show that it is in fine health. 

The only issues I have seen in the logs relate to some USB communication problems with a mobile modem, but I can repeat the poor performance even with all USB devices unplugged.

Has anybody else with a Thinkpad R52 suffered similar problems lately & could offer some ideas?

TIA.

---

