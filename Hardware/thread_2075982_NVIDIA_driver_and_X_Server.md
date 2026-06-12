---
title: "NVIDIA driver and X Server"
date: 2012-10-25
forum: Hardware
---

### Post by Aries01 on 2012-10-25
Hello

I wish to use the Octane rendering program on Ubuntu 12.04, and a prerequisite for using the program is the installation of a graphics card driver downloaded from NVIDIA. My problem is that during the installation X Server must be disabled, and I don't know the correct procedure for doing that. Is it even possible to disable X Server when using Ubuntu via the GUI?

---

### Post by nativehound on 2012-10-25
alt+f2 then login then enter:

```
sudo stop lightdm
```

To restart the gui
 
```
sudo start lightdm
```

alt+f7 if necessary

---

