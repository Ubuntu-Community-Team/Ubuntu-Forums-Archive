---
title: "gspca compilation fails in Hardy"
date: 2008-04-27
forum: Hardware
---

### Post by Lukul on 2008-04-27
Hey,

the compilation of the webcam driver collection gspca doesn't work in Hardy, it fails with this output when trying it to install from the package gspca-source. The crucial error message seems to be:

```
make[3]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.24-16-generic'    
scripts/Makefile.build:46: *** CFLAGS was changed in                       
"/usr/src/modules/gspca/Makefile". Fix it to use EXTRA_CFLAGS.  Schluss.
```

I found the same error here:
[http://ubuntuforums.org/showthread.php?t=700329&highlight=gspca+hardy](http://ubuntuforums.org/showthread.php?t=700329&highlight=gspca+hardy)
and there is a bug report on launchpad, but there seems to be no solution yet! Can anybody help?
Thank you

Lukul

---

### Post by Lukul on 2008-05-01
Anybody any idea how to proceed? Would be great...

---

### Post by slack---line on 2008-06-13
Not sure how to proceed, but its will be the following lines that are causing the problem...

```

# grep DEFINES /usr/src/modules/gspca/Makefile
DEFINES    =
DEFINES   += -DGSPCA_ENABLE_DEBUG
#DEFINES   += -DGSPCA_ENABLE_REGISTERPLAY
DEFINES   += -DGSPCA_ENABLE_COMPRESSION
DEFINES   += -DCONFIG_USB_GSPCA_MODULE=1 -DMODULE -D__KERNEL__
DEFINES   += -DVID_HARDWARE_GSPCA=0xFF -DGSPCA_VERSION=\"$(VERSION)\"
CFLAGS += $(DEFINES) 

```
...where one of these conflicts with that in the system CFLAGS.

Could you paste a link to the bug report so that people searching this forum (including me) can get to that directly.

Will let you know if I suss this out.

Cheers

slack

---

### Post by slack---line on 2008-06-13
[Bug Report here]("https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/213762")

---

