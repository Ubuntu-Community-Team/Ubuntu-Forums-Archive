---
title: "Lost task bars"
date: 2008-12-02
forum: General Help
---

### Post by Tony_photoplus on 2008-12-02
I have booted up this lunchtime and found that the top and bottom task bars have disappeared!!  So cannot see any program or system access at all.  How can I retrieve them please?

I am sure I am suppose to say something else here but I can't think of anything other it might be pay back getting rid of that awful brown!

---

### Post by geirha on 2008-12-02
Have you uninstalled something lately? This commonly happens if you uninstall evolution. Uninstalling evolution, which is fairly integrated into the gnome desktop, will uninstall other gnome packages, including gnome-panel. Try installing the package [apt://ubuntu-desktop](apt://ubuntu-desktop) to ensure that gnome-panel is installed.

---

### Post by Tony_photoplus on 2008-12-02
> **geirha said:**
> Have you uninstalled something lately? This commonly happens if you uninstall evolution. Uninstalling evolution, which is fairly integrated into the gnome desktop, will uninstall other gnome packages, including gnome-panel. Try installing the package [apt://ubuntu-desktop](apt://ubuntu-desktop) to ensure that gnome-panel is installed.

Funny enough I have gotten rid of evolution as I didn't want it clogging up my hard drive,  I see I think I can install as you said I will have a go at least


Thanks

Tony

---

### Post by geirha on 2008-12-02
> **Tony_photoplus said:**
> Funny enough I have gotten rid of evolution as I didn't want it clogging up my hard drive,  I see I think I can install as you said I will have a go at least


Hit Ctrl+Alt+F1 to get to a virtual terminal and log in there. Then run
```
sudo aptitude install ubuntu-desktop
```

---

