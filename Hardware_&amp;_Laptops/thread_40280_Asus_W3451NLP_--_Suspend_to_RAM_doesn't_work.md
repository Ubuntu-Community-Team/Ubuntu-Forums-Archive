---
title: "Asus W3451NLP -- Suspend to RAM doesn't work"
date: 2005-06-08
forum: Hardware &amp; Laptops
---

### Post by RedMars on 2005-06-08
I've got an ASUS W3451NLP notebook. While I can send it into S3 standby mode, it doesn't want to wake up again. Has anybody got any clue what could cause this and what I could look at to find a remedy?

---

### Post by RedMars on 2005-06-11
Hasn't anybody got a clue what you could do about such a problem with a notebook? Or has anybody got any experience with other notebooks in this regard?

---

### Post by andreas_ on 2005-11-29
Hi,

with the new ATI-Driver work Suspend to Ram, but there is a new Problem.
See my post -> [http://ubuntuforums.org/showthread.php?t=95713](http://ubuntuforums.org/showthread.php?t=95713)

cu
Andreas

---

### Post by Maverick911 on 2005-11-29
I've got the latest ATI driver from their site and I still can't get my HP zx5369 notebook to wake up from standby (suspend to RAM) or from hibernation (suspend to disk). If anyone knows of something I could try it would be deeply appreciated.

Thanks

---

### Post by andreas_ on 2005-11-30
Hi,

you can try to change /etc/default/acpi-support

ACPI_SLEEP=true
ACPI_HIBERNATE=true
ACPI_SLEEP_MODE=mem
SAVE_VBE_STATE=false
POST_VIDEO=false
USE_DPMS=false

or you can take a look at [http://tuxmobil.org](http://tuxmobil.org) ...

cu
Andreas

---

