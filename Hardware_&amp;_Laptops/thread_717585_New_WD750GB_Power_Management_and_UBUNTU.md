---
title: "New WD750GB Power Management and UBUNTU"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by BilboBoggles on 2008-03-07
I just bought one of the new 750GB WD drives with the new "Green" technology. Basically that means that the drive spins down within a few seconds of access.

That's all OK - but the problem I have is that under UBUNTU - I am getting a SATA fault indicating a frozen interface when it spins up.

these are appearing in my syslog

[ 3541.483329] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3541.483422] ata4.00: cmd b0/da:00:00:4f:c2/00:00:00:00:00/00 tag 0 cdb 0x0 data 0
[ 3541.483425] res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 3542.182473] ata4: soft resetting port


I also notice that the hard drives load cycle count (there is an upper limit of something like 300k load cycles before the drive is rooted) is increase dramatically, for example after 10 mins in my server its at


193 Load_Cycle_Count 0x0032 200 200 000 Old_age Always - 57

.

Has anyone else tried the new WD green drives in their linux box, do you get the same issues? I've tried hdparm etc to try to stop the bloody thing spinning down, but no go.

I'm running this kernel
2.6.20-15-server

Which I think was ubuntu feisty.

---

