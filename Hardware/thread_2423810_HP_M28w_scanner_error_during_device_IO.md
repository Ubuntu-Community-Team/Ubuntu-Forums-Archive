---
title: "HP M28w scanner: error during device I/O"
date: 2019-07-29
forum: Hardware
---

### Post by aeronutt on 2019-07-29
Printer: HP MFP M29w
Ubuntu 19.04
hplip: 3.9.16

When using scanning software (xsane, scanimage, etc), if I scan an image in a format that creates a file larger than roughly 10MB, I get the following error:
Error during device I/O.

If I use command options which create a file size smaller than ~10MB, such as jpeg, 200dpi, compression, B/W, etc, all works fine.

I've installed the printer/scanner drivers with hplip, cups, etc, multiple times, multiple versions of hplip, multiple hplip options.  Always the same problem.

---

### Post by aeronutt on 2019-08-07
Any ideas?

---

### Post by brian_p on 2019-08-07
> **aeronutt said:**
> Any ideas?

FTR:

[https://bugs.launchpad.net/hplip/+bug/1837946](https://bugs.launchpad.net/hplip/+bug/1837946)

A possible solution depends on how desperate you are to scan and on what you get for

```
avahi-browse _uscan._tcp
```

---

### Post by aeronutt on 2019-08-08
That's my bug report. :)

---

### Post by brian_p on 2019-08-08
> **aeronutt said:**
> That's my bug report. :)

I realised that at the time and thought it worth a mention. :) Maybe the next version of HPLIP will have a fix.

---

