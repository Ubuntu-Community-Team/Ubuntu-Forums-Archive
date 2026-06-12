---
title: "Read USB drive's temperature"
date: 2009-12-25
forum: Hardware
---

### Post by karmic-koala on 2009-12-25
Hi, anybody know how to read temperature of an external USB drive. hddtemp won't work as S.M.A.R.T. is not available. Its a 1TB drive by WD.

Season's Greetings!

---

### Post by IcarusR on 2009-12-25
Install 'smartmontools' then 'smartctl' will work & give you lots of info on the drive.

---

### Post by karmic-koala on 2010-01-12
I already have that installed, here's the output
===================================
sudo smartctl --all /dev/sdb1
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Device: WD       10EADS External  Version: 1.75
scsiModePageOffset: response length too short, resp_len=4 offset=4 bd_len=0
>> Terminate command early due to bad response to IEC mode page
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.



Any ideas?

---

