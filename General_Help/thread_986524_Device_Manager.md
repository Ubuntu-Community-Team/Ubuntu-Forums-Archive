---
title: "Device Manager"
date: 2008-11-18
forum: General Help
---

### Post by Taz. on 2008-11-18
Hi, i need a device manager in ubuntu latest version. Using the 64-bit version. How can i enable the device manager?

Im a lil bit familiar in the terminal so.. Hit it !

thx.

---

### Post by spiderbatdad on 2008-11-18
There is no real equivalent to Windows device manager that I am aware of. In Linux drivers and modules are loaded by the kernel...you can have control over which modules are enabled or which drivers you wish to try, but the choices are limited. Some commands of interest might be:

lspci
sudo lshw
lsusb
lsmod
df -h
sudo fdisk -lu

---

### Post by Taz. on 2008-11-19
I rly need to edit sum devices and thngs like that. I heard in the old version there was device manager... Any way?

---

### Post by fooman on 2008-11-19
its not the same as windows,  but there is a device manager.  to install,  try this in a terminal:

```
sudo apt-get install gnome-device-manager
```

hope that helps.

---

### Post by Taz. on 2008-11-19
Heres what i get:
```

kevin@kevinPC:~$ sudo apt-get install gnome-device-manager
[sudo] password for kevin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libgnome-device-manager0
The following NEW packages will be installed:
  gnome-device-manager libgnome-device-manager0
0 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
kevin@kevinPC:~$ 
kevin@kevinPC:~$
```

---

### Post by fooman on 2008-11-19
is there another instance of synaptic running? 

if not,  then this may have been caused by a prior crash during an update, or you simply stopped an update before it was completed.  in either case,  you may need to delete the lock file it refers to...try this:

```
sudo rm /var/cache/apt/archives/lock
```

then try to install again.

---

### Post by Taz. on 2008-11-19
Now i get this :) :

```
kevin@kevinPC:~$ sudo rm /var/cache/apt/archives/lock
rm: cannot remove `/var/cache/apt/archives/lock': No such file or directory
kevin@kevinPC:~$ 
```

---

### Post by Taz. on 2008-11-20
anyone -_- please

---

### Post by Taz. on 2008-11-21
these forums are hopeless -.-

---

### Post by nothingspecial on 2008-12-04
Try```
sudo dpkg --configure -a
```

I see that this has helped people before with this issue before.

---

