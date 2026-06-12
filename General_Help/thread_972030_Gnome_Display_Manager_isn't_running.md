---
title: "Gnome Display Manager isn't running"
date: 2008-11-05
forum: General Help
---

### Post by xGutsAndGloryx on 2008-11-05
You might be using a different display manager, such as KDM (KDE Display Manager), CDE login (dtlogin), or xdm. If you wish to use this feature, then your system will need to be configured to use GDM instead.


how do i reconfigure it?

---

### Post by ajgreeny on 2008-11-05
Use ```
sudo dpkg-reconfigure gdm
``` in terminal and choose which you want.

---

### Post by xGutsAndGloryx on 2008-11-05
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo dpkg-reconfigure gdm
[sudo] password for xgutsandgloryx: 
Reloading GNOME Display Manager configuration...* Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.
xgutsandgloryx@xgutsandgloryx-laptop:~$ 



did it work correctly?

---

### Post by ajgreeny on 2008-11-05
Did you get the option in a numbered list something like this:-

1  gdm
2*  kdm

with the asterisk on the display manager being used at present?  If not then you do not have other display managers installed.

Do you actually have a problem at the moment with the use of gdm, or whatever you think is installed as display manager?  For example, is gdm simply not starting automatically at boot time, or is there some other difficulty?  If so you may just need to run in terminal ```
sudo /etc/init.d/gdm start
```and it should then start at future boots.

---

