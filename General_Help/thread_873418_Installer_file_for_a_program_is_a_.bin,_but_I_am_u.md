---
title: "Installer file for a program is a .bin, but I am unable to open it"
date: 2008-07-29
forum: General Help
---

### Post by dai_vernon on 2008-07-29
When I attempt to open this file, it gives me this error message:

 There is no application installed for this file type

I didn't think you needed a program to use .bins; what program is it looking for?  It's an installer for a 32 bit Maple 11 from Maplesoft.  I am running a 64 bit system, but I am running many 32 bit programs.

---

### Post by tuxxy on 2008-07-29
Run the .bin file from in the terminal, first change dir to the one containing the .bin, then make it read/write executable, finally run it by typing ./appname. This example would assume its called maplesoft.bin on desktop


```
cd Desktop
```
```

chmod +x maplesoft.bin

```
```
sudo ./maplesoft.bin
```

---

### Post by dai_vernon on 2008-07-29
Thanks so much!

---

