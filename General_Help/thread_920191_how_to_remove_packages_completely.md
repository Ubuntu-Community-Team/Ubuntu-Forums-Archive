---
title: "how to remove packages completely"
date: 2008-09-15
forum: General Help
---

### Post by nice007 on 2008-09-15
I thought one of my linux-kerner image may be spoiled,so I want to remove it completely and download it again and resinstall it.
but neither using "```
atp-get remove linux-image-2.6.24-19-generic"
``` nor using synaptic  manager with marked completed remove,it seems the package is still there just with a deleted symbol marked.
Cause when i want to download and reinstall it using ```
apt-get install linux-image-2.6.24-19-generic
```,it looks like no download process and give a message :
```
Selecting previously deselected package linux-image-2.6.24-19-generic.
(Reading database ... 124220 files and directories currently installed.)
Unpacking linux-image-2.6.24-19-generic (from .../linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb) ...
Done.
```

It seems the reinstall process just marked the symbol from deleted to installed,so how can I completely remove the packages and download it again?

---

### Post by iaculallad on 2008-09-15
Use Synaptics Package Manager, search for the string "linux-image". Search the kernel you want removed from the list and mark it for complete removal (right-click on the item). This action will automatically update your GRUB menu so it will remove any entries of the kernel in your menu.lst file.

---

### Post by nice007 on 2008-09-15
> nor using synaptic manager with marked completed remove,it seems the package is still there just with a deleted symbol marked.

thanks for ur reply,but I have tried this method,same result.

---

### Post by adult swim on 2008-09-15
once you marked the kernels in snyaptics did you click apply?

---

### Post by nice007 on 2008-09-15
> once you marked the kernels in snyaptics did you click apply?
of course I did

---

### Post by Bizurke on 2008-09-15
First off I am assuming that you have an other working kernel at this point and are just trying to re do a bad one. If the kernel is installed then you probably aren't going to be able to use apt/aptitude/synaptic to remove it. I would try rebuilding it from the start. Try using apt-build to configure the image correctly. apt-build can help with a lot of stuff like this as well as get your system better optimized for your specific processor. 

you can install apt-build with *sudo apt-get install apt-build*

using *sudo apt-build --recbuild linux-image-2.6.24-19-generic* you might be able to fix it with out haing to delete and reinstall it. Basically this just rebuilds it from the ground up for you. 

apt-build works similar to apt-get with options like install, update, search, upgrade, etc. If this works let us know because I have never had to use it for a kernel.

---

