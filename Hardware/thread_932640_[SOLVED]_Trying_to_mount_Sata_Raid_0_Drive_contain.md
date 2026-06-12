---
title: "[SOLVED] Trying to mount Sata Raid 0 Drive containing Windows partition"
date: 2008-09-28
forum: Hardware
---

### Post by WWSmith36 on 2008-09-28
Hello

I was hoping a Raid expert who can help me. I would like to mount my hardware controlled Raid 0 disks. I have searched and googled all over the internet without being able to resolve this issue.

I´ve tried to follow this guide 
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

But I was unsuccessful. It seems I have something different going on.

Here is some basic info

lsb_release -a

```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy
```

lspci | grep RAID -i

```
00:1f.2 RAID bus controller: Intel Corporation 82801ER (ICH5R) SATA Controller (rev 02)
02:04.0 RAID bus controller: VIA Technologies, Inc. VT6410 ATA133 RAID controller (rev 06)
```

sudo dmraid -r
 
```
/dev/sdc: isw, "isw_dgjfiifhie", GROUP, ok, 72303838 sectors, data@ 0
/dev/sdb: isw, "isw_dgjfiifhie", GROUP, ok, 72303838 sectors, data@ 0
```

dmraid -ay

```
RAID set "isw_dgjfiifhie_RAID DRIVE" already active
```

If there is any additional information that I need to provide please just ask. Hopefully you will be able to provide me with some guidance.

Thank you

Wyatt Smith

---

### Post by WWSmith36 on 2008-09-29
bump

---

### Post by WWSmith36 on 2008-10-12
I´m a little disappointed no one could help me out.  I discover a solution.  

I went into windows and used the Intel Application Accelerator Raid Driver.  With this tool I was able to change the name of the raid volume name from RAID DRIVE to just RAID.

Apparently there cannot be a space contained in the Volume name or linux won´t be able to handle it properly.

---

### Post by Bitmouse on 2010-03-11
For a perhaps simpler, or more complex way to do it.

Check my guide, [URL="https://help.ubuntu.com/community/Mount%20Windows%20Raid%200%20Volumes%20Howto#preview"]here:
[/URL]
[https://help.ubuntu.com/community/Mount%20Windows%20Raid%200%20Volumes%20Howto#preview](https://help.ubuntu.com/community/Mount%20Windows%20Raid%200%20Volumes%20Howto#preview)

---

