---
title: "Amd driver"
date: 2012-02-27
forum: Hardware
---

### Post by maxtommy on 2012-02-27
Ì`ve tried to upgrade my amd graphic card. But when the popup from amd comes on my screen i cant see the bottom of it so i cant press continue to make it install the driver. The resolution on my laptop i 800*600 and i cant change it because of the driver. Is there a button or something i can press? Ive tried to resize and move, but didnt help.

---

### Post by Yellow Pasque on 2012-02-27
Press Ctrl+Alt+F1 to get to a terminal and install the old-fashioned way..
```
sudo apt-get install fglrx
```

---

### Post by Mark Phelps on 2012-02-28
If your video chipset is recent, the default open-source drivers should provide you 1024x768 resolution by default, not 800x600.

This leads me to suspect that you have an old, unsupported, video chipset -- which, forcing the install of fglrx, is only going to trash your display.

To find out what you have, open a terminal and enter "lspci" -- and look for the output line containing "VGA".  Post that information back here.

We will then be able to tell you if current AMD drivers are available for that chipset.

---

