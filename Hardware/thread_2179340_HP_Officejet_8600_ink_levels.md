---
title: "HP Officejet 8600 ink levels"
date: 2013-10-07
forum: Hardware
---

### Post by TheOnlyChosenOne on 2013-10-07
Is there a way to view the ink levels of your printer (especially the one mentioned). So far I haven't seen a solution that works.

Thanks.

---

### Post by TheOnlyChosenOne on 2013-12-11
*bump*

---

### Post by tgalati4 on 2013-12-11
Do you have *hpijs* installed?  It has ink-level monitors for most hp printers.

Open a terminal:

```
sudo apt-get install hpijs
```

---

### Post by TheOnlyChosenOne on 2013-12-11
Can you give an example how it works? The man page of hpijs is a bit poor.

---

### Post by mrsfixit on 2013-12-11
> **TheOnlyChosenOne said:**
> Can you give an example how it works? The man page of hpijs is a bit poor.

Do you have HPLIP installed? Hpijs seems to be a part of HPLIP.

I have a networked Officejet 6500 and I am able to check my ink levels from all 4 of my Linux computers.

---

### Post by tgalati4 on 2013-12-12
My fault--*hpijs* was the older application and handles older, hp inkjet printers.  You want to install *hplip* which replaces it.  Once installed you will see an icon HP Toolbox under "Preferences".  Go to "Device" set up Device.  Once your printer is set up within the HP Toolbox, you can view the ink levels tab.

---

### Post by TheOnlyChosenOne on 2013-12-12
Thanks! I installed HP Toolbox and it is fixed.
Any chance to do the same thing on the command line?

---

### Post by tgalati4 on 2013-12-12
```
man hp-levels
hp-levels
```

---

### Post by TheOnlyChosenOne on 2013-12-12
Thanks!

---

