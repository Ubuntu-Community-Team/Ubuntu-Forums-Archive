---
title: "Installation Woes on NB305 and others"
date: 2011-02-23
forum: Hardware
---

### Post by mike1947 on 2011-02-23
I tried installing Ubuntu 10.10 on my Netbook Toshiba NB305.   I installed using an external CD via CD as I could not create a working Pen drive due I suspect to defects in the sticks.   The CD was  copied twice from the Ubuntu Site and validated correct via MD5 checksums.  It was copied to the CD via Brasero which also validates via checksum.   

In AHCI mode the install repeatedly hung and often could be restarted via hitting keys but eventually hung permanently.   In compatibility mode install froze near the end twice and hitting keys etc did not help at all.   Note 10.04 installed without a hitch.  As I wanted 10.10 I finally did a net upgrade to 10.10 which seemed to work flawlessly.  This appears very buggy to me

I installed 10.10, on a an HP desktop and two Leonoo Think Center MiniTowers successfully but the installed crashed or froze at the end of the stall or ended with errors.   I had to do a dpkg --configure -a followed by an apt-get autoremove which following updates seeme to clear up installation.  Again very buggy.

---

