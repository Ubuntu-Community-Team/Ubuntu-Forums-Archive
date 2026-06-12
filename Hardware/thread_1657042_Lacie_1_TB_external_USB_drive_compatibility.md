---
title: "Lacie 1 TB external USB drive compatibility"
date: 2010-12-31
forum: Hardware
---

### Post by niklasro on 2010-12-31
Hi
Is the LaCie  Hard Disk design by Neil Poulton 1TB USB 2.0
Ubuntu compatible?

I tried connecting it and it doesn't show up.

Thank you

---

### Post by Joe of loath on 2010-12-31
It is USB, so will almost certainly be.

Is it formatted?

---

### Post by niklasro on 2010-12-31
> **Joe of loath said:**
> It is USB, so will almost certainly be.

Is it formatted?

Thanks for answering. The drive appeared in partition manager. Adjusting the cable made it appear in partition manager GParted. Now I wonder which filesystem to choose, if NTFS is good also for Linux since it has compatibility. Or are there strong reasons the select a Linux filesystem like ext4?
Regards,
Niklas

---

### Post by Joe of loath on 2011-01-01
If you ever plan to use it with Windows, then NTFS is best. If not, ext4.

---

### Post by TNT1 on 2011-01-01
> **Joe of loath said:**
> If you ever plan to use it with Windows, then NTFS is best. If not, ext4.

+1

On my 1Tb drive I partitioned it half ext4, half ntfs,in case I needed to use it on a windows machine. Never needed it, so made it full ext4. Use a smaller 160Gb as ntfs drive now.

---

### Post by niklasro on 2011-01-01
> **Joe of loath said:**
> If you ever plan to use it with Windows, then NTFS is best. If not, ext4.

I do. So NTFS it will be. GParted reports 

```
/dev/sda1 (with exclamation mark and key sign) ntfs 1 KiB
unallocated 320 MiB
/dev/sda2 hfs+ 2.84 MiB
unallocated 931.2 GiB
```

When trying to create a partition with Disk Utility it says

```
Daemon is inhibited

```

It seems I can't create the partition that way. Can you recommend how I can proceed?
Thank you

---

