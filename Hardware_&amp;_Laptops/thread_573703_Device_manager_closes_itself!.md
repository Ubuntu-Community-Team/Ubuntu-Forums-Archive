---
title: "Device manager closes itself?!"
date: 2007-10-11
forum: Hardware &amp; Laptops
---

### Post by Juntistik on 2007-10-11
Hello everyone,

im relatively new to Ubuntu and im running 7.14, after much work to get my wireless and all that working, i realized that for some reason i cannot open my device manager. when i go to system > preferences > hardware info, the device manager opens briefly and then closes.  When i try to open it via terminal by typing hal-device-manager i get this :

<gtk.Menu object (GtkMenu) at 0xc60140>
Traceback (most recent call last):
  File "/usr/share/hal/device-manager/DeviceManager.py", line 132, in on_device_tree_selection_changed
    self.update_device_notebook(device)
  File "/usr/share/hal/device-manager/DeviceManager.py", line 508, in update_device_notebook
    self.update_tab_device(device)
  File "/usr/share/hal/device-manager/DeviceManager.py", line 316, in update_tab_device
    d = self.udi_to_device(d.properties["info.parent"])
KeyError: 'info.parent'
Traceback (most recent call last):
  File "/usr/bin/hal-device-manager", line 20, in <module>
    DeviceManager()
  File "/usr/share/hal/device-manager/DeviceManager.py", line 97, in __init__
    self.update_device_list()
  File "/usr/share/hal/device-manager/DeviceManager.py", line 247, in update_device_list
    self.update_device_notebook(self.virtual_root.children[0])
  File "/usr/share/hal/device-manager/DeviceManager.py", line 508, in update_device_notebook
    self.update_tab_device(device)
  File "/usr/share/hal/device-manager/DeviceManager.py", line 316, in update_tab_device
    d = self.udi_to_device(d.properties["info.parent"])
KeyError: 'info.parent'

any ideas?

---

### Post by fahadysf on 2007-10-18
Reinstalling hal worked for me. But some people have reported that even that doesn't always solve the problem. I was getting the same debug output as you. 

```
sudo apt-get --reinstall install hal
```

Good luck.

---

### Post by genkidesu on 2007-12-10
This may be related to the following thread on [HAL not initializing.]("http://ubuntuforums.org/showthread.php?t=583940&highlight=initialize+hal&page=2")

I tried the following from that thread and it worked.

sudo /usr/lib/hal/hald-generate-fdi-cache

---

