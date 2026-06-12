---
title: "dmraid not detecting my raid array on dell xpsm1730 (ich8m-e)"
date: 2008-07-02
forum: Hardware
---

### Post by DJMatty on 2008-07-02
Hi

I have a Dell XPSM1730 laptop with raid 0 configured on with the two drives. This is working fine for the vista install that is on the machine, however when I boot to the hardy live cd, install dmraid and issue the command I get an error for each drive and it says there is no raid present.

```
ubuntu@ubuntu:~$ sudo dmraid -ay
ERROR: isw: Error finding disk table slot for /dev/sdb
ERROR: isw: Error finding disk table slot for /dev/sda
No RAID disks
```

I've done some digging and one article mentioned that dmraid relies on AHCI, after checking my bios, it's a bit cryptic about if that is enabled when raid is enabled...

Can anyone point me in the right direction to get the raid array visible to ubuntu?

Many thanks

Matt

---

