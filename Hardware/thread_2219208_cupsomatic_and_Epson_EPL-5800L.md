---
title: "cupsomatic and Epson EPL-5800L"
date: 2014-04-23
forum: Hardware
---

### Post by csmth on 2014-04-23
I have an old printer Epson EPL-5800L which relies on epsonepl project to print under 13.04 environment, and it works.
[http://sourceforge.net/projects/epsonepl/](http://sourceforge.net/projects/epsonepl/)

After I migrated the ubuntu to 14.04, I cannot get it work. The key point is that its PPD relies on cupsomatic, which is a part of foomatic-filters. Under 14.04 foomatic-filters is now in conflict with cups. I have no way to install cupsomatic and keeping cups. The error log at CUPS admin read as:

```
E [23/Apr/2014:20:28:42 +0800] EPSON_EPL-5800L: File "/usr/lib/cups/filter/cupsomatic" not available: No such file or directory
E [23/Apr/2014:20:28:42 +0800] [Job 10] Unable to start filter "cupsomatic" - Success.
E [23/Apr/2014:20:28:42 +0800] [Job 10] Stopping job because the scheduler could not execute a filter.
```

Is it possible to install "cupsomatic" at 14.04 without offending package "cups"?
If it is not possible, it seems that I must find out whether it is possible to adopt cups-filter and modify the PPD file by myself.

P.S.> I modified one line of the PPD file to make sure all line lengths are 255 or less. This is not related to my cupsomatic question and this change is a must because it is required by CUPS.

---

### Post by leeyc0 on 2014-04-23
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html#cupsomatic-dia](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html#cupsomatic-dia)

cupsomatic is no longer developed, maintained, or supported. It now been replaced by foomatic-rip. You may need to consider porting epsonepl to use foomatic-rip.

---

### Post by leeyc0 on 2014-04-23
Seems that the latest cvs source already changed to foomatic-rip. You may have a try by compiling cvs source.

---

### Post by csmth on 2014-04-24
> **leeyc0 said:**
> Seems that the latest cvs source already changed to foomatic-rip. You may have a try by compiling cvs source.

I overlooked that the PPD should comes from "Most current" repository (1) instead of tarball (2). The PPD at most current repository use foomatic-rip which is supported by cups-filters.

(1) [http://epsonepl.cvs.sourceforge.net/viewvc/epsonepl/epsoneplijs/foomatic_PPDs/](http://epsonepl.cvs.sourceforge.net/viewvc/epsonepl/epsoneplijs/foomatic_PPDs/)
(2) [http://sourceforge.net/projects/epsonepl/files/latest/download](http://sourceforge.net/projects/epsonepl/files/latest/download)

(To keep the knowledge) I also need to install package colord. Otherwise I will get following error:

```

W [24/Apr/2014:20:20:15 +0800] CreateProfile failed: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files
W [24/Apr/2014:20:20:15 +0800] CreateDevice failed: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files
```

Now the printer can print from CUPS. Thanks leeyc0.

---

