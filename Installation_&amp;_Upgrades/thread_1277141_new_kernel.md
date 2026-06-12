---
title: "new kernel"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by hsdrgmi on 2009-09-28
i tried to install a new kernel, but make install displayed
*"WARNING*: No module *ata_piix* found for *kernel*, *continuing* anyway"

if i postpone this, and just keep using old kernel, could there be some problems, as i already did "make install" ?

---

### Post by renkinjutsu on 2009-09-28
make install? Can you actually do that?
download the package kernel-package and fakeroot (assuming you already have build-essentials)
```
sudo aptitude install kernel-package fakeroot
```

to configure you kernel (you'll need qt3 installed if you want to use xconfig) do either ```
make xconfig
or
make menuconfig
```

and instead of `make install` do ```
fakeroot make-kpkg --initrd kernel_image kernel_headers
```

---

