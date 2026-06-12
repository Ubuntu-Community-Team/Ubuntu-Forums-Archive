---
title: "Stop SMART polling on sleeping drives"
date: 2010-04-03
forum: Hardware
---

### Post by Paul Hugill on 2010-04-03
Hi Guys,
I have my hard disks set to spin down when idle which seems to be working fine except that they all spin up randomly sometimes.

The drives are all ones i just use for additional storage so nothing is running off them so I'm thinking it is the SMART check that is making it spin up.

Ive read some articles saying to add the '-n' flag in /etc/smartd.conf so that it doesn't poll the drive when it is spun down but I dont have that file. I only have a pretty basic knowledge of Linux and it is just a standard install of 9.10. I'm not sure I'm that comfortable with installing smartmontools without a good set of instructions and I'd rather just do it with what is already there.

Any suggestions?

Thanks
Paul

---

