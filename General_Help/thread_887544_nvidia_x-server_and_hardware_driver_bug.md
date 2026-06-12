---
title: "nvidia x-server and hardware driver bug ?"
date: 2008-08-12
forum: General Help
---

### Post by nacho32 on 2008-08-12
Ok since I did the last update, If I go to Hardware drivers it shows my card not in use. But If I go to Nvidia x-server it shows all the correct stuff and I can change my display size and refresh and all the other options.

But if I click enable card in the hardware driver section I loose my nvidia x-server . So is my card working right even though the hardware driver thing says cards not in use?

---

### Post by sdennie on 2008-08-12
How did you install the drivers?  Also, what is the output of:

```

glxinfo | grep direct

```

If you installed the drivers manually, sometimes package updates can clobber some parts of the installation you'll have to re-install the drivers.

---

