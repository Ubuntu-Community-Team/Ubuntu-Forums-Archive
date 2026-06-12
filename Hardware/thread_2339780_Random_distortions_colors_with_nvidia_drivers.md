---
title: "Random distortions colors with nvidia drivers"
date: 2016-10-12
forum: Hardware
---

### Post by kozlovsky-a-a on 2016-10-12
The problem is that after installing nvidia drivers (v370.28), the screen image started looks very bad with a kind of distortions. The drivers have been installed through ppa.
  OS: Ubuntu 16.04 x64.
  Video card:
```
lspci -k| grep -EA2 'VGA|3D'
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 755M] (rev a1)
    Subsystem: Lenovo GK107M [GeForce GT 755M]
    Kernel driver in use: nvidia
--
07:00.0 3D controller: NVIDIA Corporation GK107M [GeForce GT 755M] (rev a1)
    Subsystem: Lenovo GK107M [GeForce GT 755M]
    Kernel driver in use: nvidia

```
Image is attached.

---

