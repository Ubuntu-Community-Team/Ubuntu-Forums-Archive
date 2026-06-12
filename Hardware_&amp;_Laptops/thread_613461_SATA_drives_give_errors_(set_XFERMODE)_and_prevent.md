---
title: "SATA drives give errors (set XFERMODE) and prevent booting"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by Ux64 on 2007-11-14
**SATA drives give errors (set XFERMODE) and prevent booting**

Thing is that if I reboot it usually doesn't reappear. Which is really strange. Maybe hardware fault, maybe not?

[[IMG]http://picozilla.com/files/141839timgp0878.jpeg[/IMG]](http://picozilla.com/en/141839/imgp0878.jpeg.html)

Chipset is Intel P35 and motherboard is Intel P35-Express.

Exact error:
```

ata1.00: failed to set xfermode (err_mask=0x40)

```

I get this error twice and then system hangs.

Drive is  Samsung T166 / 500 GB. (SATA naturally w NCQ support)

Ubuntu is 7.10 GG / 64 bit (with latest updates)

---

### Post by Ux64 on 2007-11-26
TOP!

Issue is still open? Any clues or news about this?

It happens about 1 of every 5 system startups.

---

### Post by ImALittleTeaPot on 2007-12-25
yeah. similar problems here

[http://ubuntuforums.org/showthread.php?t=637721&highlight=err_mask+0x40](http://ubuntuforums.org/showthread.php?t=637721&highlight=err_mask+0x40)

---

### Post by Ux64 on 2008-01-21
I don't know if it's related. But I have been suffering from data corruption lately. Now my file system is read only. And I also got some corrupted data on disk. ;(

I lost evolution & firefox configurations etc.

[http://ubuntuforums.org/showthread.php?t=670700](http://ubuntuforums.org/showthread.php?t=670700)

---

