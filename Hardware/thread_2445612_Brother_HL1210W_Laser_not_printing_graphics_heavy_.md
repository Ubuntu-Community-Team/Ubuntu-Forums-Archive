---
title: "Brother HL1210W Laser not printing graphics heavy pages."
date: 2020-06-17
forum: Hardware
---

### Post by ldmoretti on 2020-06-17
I've got a Brother HL1210W that I'm trying to print to over the network. I'll print a PDF and I'll get pages 2-4 but not page 1 that has some photos on it. Or I'll get pages 1 & 4 but not 2&3. The only common thread about what won't print seems to be that they're heavier on graphics. I've tried passing the PDF documents through a PDF Shrinker thinking it may be an OOM error or related but that doesn't seem to make a difference. I've also tried printing JUST the page that has issues and it still doesn't print.

I'm using DNSSD to locate the printer. 

I've checked /var/log/cups/error_log.1 and the only error is the following:
```
W [28/Apr/2020:14:01:16 +0100] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id \'Brother-HL-1210W-series-Gray..\' already exists
```

My wife has no issues printing them from her Windows computer.

Not sure where else to look for error data to troubleshoot.

---

### Post by slickymaster on 2020-06-17
*Thread moved to **Hardware**.*

---

