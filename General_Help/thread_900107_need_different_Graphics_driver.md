---
title: "need different Graphics driver"
date: 2008-08-25
forum: General Help
---

### Post by StageCraft on 2008-08-25
It seems that in my install of Xubuntu, I had to tell it that I was using an NVIDIA graphics card in order for the install to work (different story, different thread), but I chose the wrong one and now the graphics are all messed up. How can I change the driver and/or get Xubuntu to see what card I really have?

---

### Post by fsmithred on 2008-08-25
Did you try this to get it going? 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

After that, you can switch to the proprietary nvidia driver.

---

### Post by tuxxy on 2008-08-25
Try and install through Envy if no luck as it should select the correct driver for you.

---

### Post by StageCraft on 2008-08-25
> Did you try this to get it going?
Code:

sudo dpkg-reconfigure -phigh xserver-xorg

After that, you can switch to the proprietary nvidia driver.

I tried that and had no luck, I'll try this Envy thing and report back when I have the chance

---

