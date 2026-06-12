---
title: "problems with directories"
date: 2008-11-18
forum: General Help
---

### Post by niki2386 on 2008-11-18
Hello, I got this error message while traying to open Synapctic Package Manager: 

E: ERROR: could not create configuration directory /root/.synaptic - mkdir (2 No such file or directory)


On the terminal I had a similar error:

(gedit:7852): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: No such file or directory
Could not create per-user gnome configuration directory `/root/.gnome2/': No such file or directory
 
after the following command: sudo gedit /boot/grub/menu.lst

I can't realize what's the problem :(

---

### Post by taurus on 2008-11-18
Are you logged in as root?  

It's better to use gksudo when you open gedit GUI editing.

```
gksudo gedit /boot/grub/menu.lst
```

---

