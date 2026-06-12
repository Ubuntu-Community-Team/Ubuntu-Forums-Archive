---
title: "3tb or 4tb on Ub 18.04 ?"
date: 2019-11-20
forum: Hardware
---

### Post by ra7411 on 2019-11-20
My 2tb HD that I backup to is 90 pct full.

I'm thinking of getting a 3 or 4 tb to replace it. Are there any considerations to watch out for? For reliability, is a 3 or 4 better?

My main machine is a 4 yr old AMD desktop running under BIOS.

Thanks

---

### Post by sudodus on 2019-11-20
The size should make no difference for reliability. It is probably better to double the size to 4 TB. And get a drive with good quality. It is more expensive, but you can expect it will also last longer and cause less problems.

Remember that you need the GUID partition table, GPT, for all drives above 2 TB.

---

### Post by ra7411 on 2019-11-23
>[COLOR=#000000]Remember that you need the GUID partition table, GPT, for all drives above 2 TB.<

Is there a problem mixing mbr and gpt hd's on the same machine?[/COLOR]

---

### Post by TheFu on 2019-11-23
You can mix mbr and gpt on the same machine. Windows has some limitations around GPT and EFI booting, but that's usually the only OS-related issue.

3TB disk did have about 50% worse initial reliability a few years ago with almost all disk vendors.  Check out some old backblaze reliability reports from when 2, 3, 4TB disks were used.  In those sizes, seagate was usually the worst for reliability.  With 8TB and larger disks, seems that almost all vendors have excellent reliability.  Again, seek out the backblaze reports.  Google finds them easily.

---

### Post by MartyBuntu on 2019-11-25
I would go with Western Digital's "Red" series for archival storage. If you want performance to go with large volume storage, Western Digital also makes the "Red Pro" line of drives that run at 7200 RPM.

---

