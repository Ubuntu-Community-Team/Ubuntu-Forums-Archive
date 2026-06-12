---
title: "error message while installation"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by dersu on 2009-11-08
Hello,

while installing karmic 32 bits, I've got some error messages like:
xx end_request: I/O error, dev sr0, sector xxx
but the installation is done and it seems working.

should I worry about it?

---

### Post by Cr0n_J0b on 2009-11-08
that's an IO error from the CDROM during install.  It likely retried and was fine.  In my experience the installer will stop if it can't read something and retried are unsuccessful

---

### Post by bytan on 2009-11-08
If there is no error output, i think you may enjoy your system:

```
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
```

---

### Post by dersu on 2009-11-08
thank you for your answers.
i tried some application, all is working well.
i think you are right, no worries.
rhythmbox didn't work for an audio cd but it is working now.
maybe it is a problem with my cdrom, or nothing..

---

