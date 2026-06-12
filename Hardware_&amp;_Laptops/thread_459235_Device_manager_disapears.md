---
title: "Device manager disapears"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by RStanford on 2007-05-30
I have a strange problem in that when I open system>preferences>hardware information the application appears briefly on the screen and then disappears without an error message! The same thing also happens when I run Application>system tools>hardinfo where all the options work fine until I select any device when the application just seems to close on its own without an error message.
Both of these applications were working when first installed.
I have checked the system logs but there do not appear to be any entries in any log associated with the problem.

I am running Fiesty on a Dell X1 laptop. the installation is very stable apart from this problem.

I am new to Linux but managed a DEC VAX VMS system for a while so am fairly systems literate.
 
Help Please!

---

### Post by Austin_KW on 2007-05-30
try running it (hal-device-manager) from a terminal to see if you get any errors messages

---

### Post by RStanford on 2007-05-30
Thanks Austin why didn't I think of that?

This is the output that I get but I'm not familiar enough with the command line to understand it:

robert@robert-laptop:~$ hal-device-manager
<gtk.Menu object (GtkMenu) at 0x83b96bc>
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
robert@robert-laptop:~$ 

Robert

---

### Post by RStanford on 2007-05-31
Reinstalling HAL and HAL-DEVICE-MANAGER has cured the problem. Reinstalling hardinfo has not resolved the device manager problem it has.

---

