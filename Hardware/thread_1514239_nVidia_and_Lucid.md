---
title: "nVidia and Lucid"
date: 2010-06-20
forum: Hardware
---

### Post by Gannin on 2010-06-20
It used to be that xorg used the xorg.conf file and if you installed the nVidia drivers, they would update that file to make the drivers work correctly.  Now with Lucid it appears it doesn't use xorg.conf anymore, so how are the nVidia drivers supposed to work?

---

### Post by OSX@Linux on 2010-06-20
Just run "sudo nvidia-settings" and click on "Save to X configuration file" and restart. It won't be able to merge, but it should create the xorg.conf file you're used to.

---

### Post by Gannin on 2010-06-20
I suppose my question isn't so much how to re-create the xorg.conf file, as it is can the nVidia drivers currently work without an xorg.conf file?  Or do they need to be updated by nVidia to work with the new style of configuration that's being used?

---

