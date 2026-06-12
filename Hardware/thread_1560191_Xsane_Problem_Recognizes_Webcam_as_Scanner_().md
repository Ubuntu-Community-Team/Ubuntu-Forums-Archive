---
title: "Xsane Problem: Recognizes Webcam as Scanner (?)"
date: 2010-08-24
forum: Hardware
---

### Post by Groucho Marxist on 2010-08-24
Due to a sale at my university's computer store, I decided to purchase a new HP Deskjet F4480 all-in-one unit. I have tested its printing abilities and it works remarkably well in Ubuntu. However, the scanning function is malfunctioning and I know that it is not a hardware issue.

I have found that I have been able to scan documents with other HP models via Trisquel (the FSF's answer to Ubuntu) within VirtualBox. My theory is that there is something wrong with my build of SANE and/or Xsane and have tried compiling the former from source to fix my problem.

Every time I run "sane-find-scanner", I get the following output in my terminal:

```
device `v4l:/dev/video0' is a Noname BisonCam, NB Pro virtual device
```

Does anyone know how I can 1.) disable my webcam as being recognized as my scanner, and 2.) how to get my scanner functioning properly in Ubuntu 10.04?

---

### Post by drpaul on 2010-08-25
Since it is an HP unit, I would start be installing the hplij package. Then try managing the printer/scanner from the HP software interface.

HTH

Paul

---

