---
title: "Software Sources doesn't open"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by eekfonky on 2009-03-13
I can't work out why this has happened. I've tried uninstall and reinstall.
When I go to a terminal and type:```

gksu /usr/bin/software-properties-gtk
``` I get this
```
chris@chris-laptop:~$ gksu /usr/bin/software-properties-gtk
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet  warnings.warn("apt API not stable yet", FutureWarning)
reWarning: apt API not stable yetTraceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.5/site-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 78, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 516, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.5/site-packages/aptsources/distro.py", line 85, in get_sources
    "Error: could not find a distribution template")
aptsources.distro.NoDistroTemplateException
```

---

### Post by iaculallad on 2009-03-13
Try:

```
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
```

HTH.

EDIT:

By the way, I got that command by accessing the alacarte application.

```
gksudo alacarte
```

I searched for Software Sources, right-click on it and selected the Properties option.

---

### Post by eekfonky on 2009-03-13
It doesn't work with the GUI or in a terminal. It was working but now for some reason isn't. When I type the code you gave me into a terminal, same message appears.

---

### Post by iaculallad on 2009-03-13
What about doing Ctrl+Alt+Backspace then try re-accessing Software Sources.

---

### Post by eekfonky on 2009-03-13
didn't work sorry

---

