---
title: "how to uninstall programs in ubuntu studio?"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by iseeclouds on 2009-02-11
is there a way to uninstall individual programs from ubuntu studio without having to uninstall the whole 'ubuntustudio-audio' and 'ubuntustudio-audio-plugins' packages? tried add/remove and synaptic. i have ubuntu 8.04 with ubuntu studio 8.04 installed over it. i like ubuntu studio, it just has too many programs i never use.

---

### Post by Roger Steiner on 2009-02-13
I have Studio loaded on an old Compaq. Unless you have a space issue on your hard drive, there is no problem with just leaving them installed. They don't use much space. Otherwise the add/remove program should remove what you want removed.

---

### Post by tommcd on 2009-02-13
Have you tried using ```
sudo apt-get remove program_name
``` via the terminal? Uninstalling programs in Ubuntu Studio should not be different than in regular Ubuntu. Using **apt-get remove** *should* only trmove the program itself, without removing any of it's dependencies.

---

### Post by aquavitae on 2009-02-13
ubuntustudio and ubuntu-studio-plugins are metapackages, meaning that they don't aactually install anything on their own, they just depend on a lot of other things.  So if you try uninstalling what you don't want and it asks to also uninstall ubuntusudio it doesn't really matter.  Just check that it doesn't also uninstall something else which you want to keep.

---

### Post by iseeclouds on 2009-02-13
> **tommcd said:**
> Have you tried using ```
sudo apt-get remove program_name
``` via the terminal? Uninstalling programs in Ubuntu Studio should not be different than in regular Ubuntu. Using **apt-get remove** *should* only trmove the program itself, without removing any of it's dependencies.
this worked. thanks !

---

