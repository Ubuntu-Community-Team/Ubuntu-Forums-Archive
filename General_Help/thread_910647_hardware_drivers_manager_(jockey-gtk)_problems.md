---
title: "hardware drivers manager (jockey-gtk) problems"
date: 2008-09-04
forum: General Help
---

### Post by evanct on 2008-09-04
hardware drivers manager won't open, it just quietly dies. the output is this:

```
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 300, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.5/site-packages/jockey/ui.py", line 269, in run
    self.ui_init()
  File "/usr/bin/jockey-gtk", line 93, in ui_init
    self.update_tree_model()
  File "/usr/bin/jockey-gtk", line 240, in update_tree_model
    is_enabled = handler.enabled()
  File "/usr/share/jockey/handlers/nvidia.py", line 51, in enabled
    devices = self.xorg_conf.getSections('device') 
AttributeError: 'NoneType' object has no attribute 'getSections'
```

i found it in a bug report([https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/215027](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/215027)) and tried the fix offered in the 3rd reply down. it seems to work for everyone else, but when i tried it and rebooted, i still get the same error. this is frustrating, i've been trying to fix this since last night and i can't. does anyone know what to do??

this is 8.04, fully updated.

---

### Post by evanct on 2008-09-04
bump

---

### Post by JJoel on 2008-10-26
Same problem here. Very frustrating.

---

### Post by JJoel on 2008-10-26
Actually, I just tried the fix again, and it worked.

Possibly remove all installed packages, and purge all their files. 
Enter this into the terminal.

```
sudo apt-get remove --purge jockey-gtk jockey-common
```

then reinstall

```
sudo apt-get install jockey-gtk
```

Next, Change line 60 in /usr/lib/python2.5/site-packages/jockey/xorg_driver.py from
                self.xorg_conf = xorgconfig.readConfig(OSLib.inst.xorg_conf_path)
to
                self.xorg_conf = xorgconfig.readConfig(OSLib.inst.xorg_conf_path)[0]

To do this enter in the terminal,
```

sudo gedit /usr/lib/python2.5/site-packages/jockey/xorg_driver.py
```

Go to line 60 and add in the rquired text. 

And thats that

---

