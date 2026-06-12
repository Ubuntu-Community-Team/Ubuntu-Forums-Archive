---
title: "After adding user to the group Virtualbox still cannot run?!"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by Jeffzhg on 2009-02-10
After installing Virtualbox 1.5.0 ose in my Ubuntu 7.10 Gusty Gibbon, I attempted to build a virtual machine of win_XP. then it failed to start the virtual machine with this error message:

[COLOR="Lime"][COLOR="Blue"]The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
[/COLOR][/COLOR]

After adding myself to the user group vboxusers group, I logged out and in again, but still see the error message. 

Fellows, anyone have idea what might be going on? 

Thanx,
Jeff

==============================================================
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

