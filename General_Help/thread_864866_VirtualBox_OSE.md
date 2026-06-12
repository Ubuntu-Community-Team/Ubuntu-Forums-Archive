---
title: "VirtualBox OSE"
date: 2008-07-20
forum: General Help
---

### Post by Markissocoollike on 2008-07-20
Hi I got it all installed and everything but when i tried to install windows:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

---

### Post by Markissocoollike on 2008-07-20
I tried changing this thing called dog something in the boot file but i could not find it... they said to change it to something like = 0 the problem is i looked for it and it weren't there and I was like: WOAH! Man why isn't it there!?

---

### Post by Elfy on 2008-07-20
Install the virtualbox-ose-modules - search for that in synaptic. As it says if you have the generic kernel installed install the generic virtual box module. If you're not sure search in synaptic for linux-image.

> Man why isn't it there!?If the second post is actually meant to mean something reword it :)


Also are you aware that the ose version has no usb support - just I'd ask - if you want that uninstall the vbox bits you have installed and get the puel from the vbox site.

---

### Post by Markissocoollike on 2008-07-20
i can't install puel thats the thing i can't seem to get VMWare either thats not compatable and well dude thats like totally bogus man!

---

### Post by Markissocoollike on 2008-07-20
I didn't know bogus was another way of saying programs not working thats cool... tho they still are totally bogus if you know what i mean ;)

---

### Post by Markissocoollike on 2008-07-20
Omg i like totally installed all the latest drivers and it still won't work it like used to work on my old ubuntu was like aint it working now dude? It just comes up with the same message which is like totally bogus man lol!

---

### Post by Elfy on 2008-07-20
reboot

---

### Post by Markissocoollike on 2008-07-20
> **forestpixie said:**
> reboot

tried that notin' man!

---

### Post by p_quarles on 2008-07-20
> **Markissocoollike said:**
> tried that notin' man!
It appears to me that you have not stated whether you installed the correct module. If you could run and post the results of the following, we would appreciate it:
```
apt-cache policy virtualbox-ose-modules-`uname -r`
```

---

### Post by Markissocoollike on 2008-07-20
virtualbox-ose-modules-2.6.24-19-generic:
  Installed: (none)
  Candidate: 24.0.4
  Version table:
     24.0.4 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
thats weird it says i've installed nothing when it says i've installed 24.0.4 0.o

---

### Post by p_quarles on 2008-07-20
No, it says you've never installed the modules. Do this like so:
```
sudo apt-get install virtualbox-ose-modules-`uname -r`
```
and you should get it working.

---

### Post by Markissocoollike on 2008-07-20
heh youll never believe this but i got another error message lol!

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).

How ironic :P

---

### Post by p_quarles on 2008-07-20
> **Markissocoollike said:**
> heh youll never believe this but i got another error message lol!

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).

How ironic :P
Not ironic at all, just another step to take (this is all in the documentation, by the way):
```
sudo adduser `whoami` vboxusers
```
You'll need to log out of your current session, log back in, and then you'll be able to run the program.

---

### Post by Markissocoollike on 2008-07-20
thank dude rock on you got it working thanks for the birthday present lol!

---

### Post by Markissocoollike on 2008-07-20
i've got another problem actually I can't seem to install guest additions

---

