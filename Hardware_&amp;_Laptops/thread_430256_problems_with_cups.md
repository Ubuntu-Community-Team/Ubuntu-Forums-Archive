---
title: "problems with cups"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by Amilius on 2007-05-01
trying to install drivers for CANON PIXMA iP1000 on Feisty, so I' trying out installing it using the method in this thread [http://ubuntuforums.org/showthread.php?t=335655](http://ubuntuforums.org/showthread.php?t=335655) .  using a japanese ftp server to download the driver package, most of the package is downloaded but one last is needed, it's the pstocanonbj, but every time I try to install that package I get this error:

pstocanonbj:
 Depends: libcupsys2-gnutls10 (>= 1.1.23-1)

but I seem to have libcupsys2, I even reinstall it, and I still have the same problem.

what to do?

---

### Post by dcstar on 2007-05-02
> **Amilius said:**
> trying to install drivers for CANON PIXMA iP1000 on Feisty, so I' trying out installing it using the method in this thread [http://ubuntuforums.org/showthread.php?t=335655](http://ubuntuforums.org/showthread.php?t=335655) .  using a japanese ftp server to download the driver package, most of the package is downloaded but one last is needed, it's the pstocanonbj, but every time I try to install that package I get this error:

pstocanonbj:
 Depends: libcupsys2-**gnutls**10 (>= 1.1.23-1)

but I seem to have libcupsys2, I even reinstall it, and I still have the same problem.

what to do?

Do you also have the **gnutls **package installed?

---

