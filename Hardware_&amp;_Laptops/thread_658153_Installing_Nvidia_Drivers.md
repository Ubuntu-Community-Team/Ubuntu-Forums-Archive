---
title: "Installing Nvidia Drivers"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by Shyper on 2008-01-04
Hey, I have a Dell XPS 210 that I just upgraded with a 8600GT. Before this, it was using integrated graphics and had the Intel proprietary drivers installed. Now, when I go to boot up Ubuntu, it takes me to a tty console. Furthermore, my internet connection no longer seems to work in tty (it's based off a wireless USB thing working through ndiswrapper). So, my big question is: 

How do you get nvidia drivers installed/X back working when you have:
1. No GUI
2. No Internet?

Thanks a lot.

---

### Post by PmDematagoda on 2008-01-04
Execute:-
```
sudo dpkg -reconfigure -phigh xserver-xorg
```

Then do:-
```
sudo startx
```

That should get you to a GUI through the vesa driver where you can install the proper Nvidia driver.

---

### Post by Shyper on 2008-01-04
I get this:

dpkg: conflicting actions -e (--control) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages....

What's wrong?

---

### Post by walkerk on 2008-01-04
> **Shyper said:**
> I get this:

dpkg: conflicting actions -e (--control) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages....

What's wrong?

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

no space between dpkg-reconfigure

---

