---
title: "No Audio!!!! Help..."
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by mtbrown73 on 2006-10-23
New to Linux - there's no audio available on the system i installed.

i have a dell optiplex gx1, updated bios, fresh install, no tunes

i know how to troubleshoot this in windows, can someone please help translate what i need in Ubuntu ?

Thanks

---

### Post by Kateikyoushi on 2006-10-23
Follow this guide and you can configure it in a few minutes. [LINK]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")

If you are stuck post the output of these commands.

```
aplay -l
lspci -v
```

---

### Post by jdunn on 2006-10-23
> **mtbrown73 said:**
> New to Linux - there's no audio available on the system i installed.

i have a dell optiplex gx1, updated bios, fresh install, no tunes

i know how to troubleshoot this in windows, can someone please help translate what i need in Ubuntu ?

Thanks

Not sure if that is a laptop or not.  Do you have more than one sound card (ex:  sound blaster live and onboard sound)?  If you have more than one sound card, the simple solution is to disable the onboard sound in your BIOS settings.

---

