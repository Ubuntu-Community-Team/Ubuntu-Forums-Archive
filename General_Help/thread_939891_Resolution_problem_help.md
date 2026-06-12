---
title: "Resolution problem help"
date: 2008-10-06
forum: General Help
---

### Post by renier2211 on 2008-10-06
My brother downloaded 265 updates for Ubuntu 8.04 now his resolution is stuck on 640x480. compiz stopped working tried to reinstall compiz and driver for nvidia geforce  7600 ...nothing..please help

---

### Post by tuxxy on 2008-10-06
Remove all video drivers you installed and then re-enable your video driver, if its not listed you could try envyng application to isntall the driver.

Another option would be to reconfigure the xorg;

```
dpkg-reconfigure xserver-xorg
```

---

### Post by renier2211 on 2008-10-07
thanks got it working...c u on the flip side

---

