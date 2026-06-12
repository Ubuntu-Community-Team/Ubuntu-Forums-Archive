---
title: "NVIDIA 8600GT SLI In Hardy Heron Virtual Machine"
date: 2008-10-04
forum: General Help
---

### Post by patrickmollohan on 2008-10-04
All good.

---

### Post by ju2wheels on 2008-10-04
You donr need to install nvidia drivers in the virtual machine. Well actually, at least in VBox you shouldnt be able to because thats not what it will see for a graphics card. Regardless of what type of graphics  card you have the virtual machine sees an emulated virtual graphics adapter designed by VBox to allow them to fine to and manipulate the graphics.

Why are you trying to do this anyway? Virtual machines do not have 3D support (excluding one of the latest versions of VMWare which I heard added support for DirectX) so even if you installed the drivers it cant take advantage of the features of your graphics card...

---

