---
title: "DKMS trying to build absent modules"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by ridetheteapot on 2009-01-29
DKMS autoinstaller is trying on every boot to make a new vboxnetflt module. Vboxnetflt is from the virtualbox package, which is no longer installed on this system. I can not figure out how to make DKMS stop looking for the dkms.conf file.

dkms uninstall and remove will not work without a valid dkms.conf for vboxnetflt (and i guess this would not be the correct fix anyway)

PS --- are the error messages on startup in a file somewhere that i can look at? i can't find the file its a pain to parse these errors.

---

