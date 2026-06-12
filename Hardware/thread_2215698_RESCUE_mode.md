---
title: "RESCUE mode"
date: 2014-04-07
forum: Hardware
---

### Post by marko.brose on 2014-04-07
Hello,  I'm Trying the command "lsiutils" in Rescue Mode,but says command not found I need to partition my HDD that is set on Riad0 so how to go about this ? please Help  Thanks Marko  This is via putty terminal  typo Error Sorry LoL

---

### Post by steeldriver on 2014-04-08
Hi Marko

It sounds like you have some kind of LSI hardware RAID controller - I don't have any experience to offer but you might want to start by identifying exactly which one using 'lspci'

```
lspci -nnv | grep -i raid
```

There's some information about hardware RAID in this Debian wiki --> [https://wiki.debian.org/LinuxRaidForAdmins](https://wiki.debian.org/LinuxRaidForAdmins)

Hope this helps

---

### Post by marko.brose on 2014-04-08
Hello,

I'm Trying to partition a hdd that's 4 TB it's already set on Raid0,sit I'm in "Isutil " and have already installed the os but I'm in rescue mode and trying to get the full 4TB I'm totally frustrated just about to give up and put it back to raid1 and just it has a redundancy drive has 1 and mirror it instead 

Regards
Marko

---

