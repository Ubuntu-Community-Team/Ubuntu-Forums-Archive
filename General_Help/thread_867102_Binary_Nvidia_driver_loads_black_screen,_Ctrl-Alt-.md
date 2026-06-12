---
title: "Binary Nvidia driver loads black screen, Ctrl-Alt-Bksp sometimes fixes."
date: 2008-07-22
forum: General Help
---

### Post by Bastanteroma on 2008-07-22
I just installed hardy on a toshiba laptop with an integrated NV17 [GeForce4 440 Go] (rev a3) chipset.


The "nv" driver works fine, but when I rebooted after installing the binary "nvidia" driver, x started but the screen was black (I heard the login sounds).

I hit ctrl-alt-bksp to restart X, and this time GDM showed up fine.

I rebooted again, and this time things stayed black even after restarting X.

Switching to "nv" again works for now.

EDIT:
I installed the latest and greatest with EnvyNG and presto! Problem solved (for me).

---

