---
title: "Install apps on Ubuntu Server from cdrom"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by lamarty on 2009-02-06
hi,
i have installed Ubuntu server 8.04 as VMware machine, i'd like to install many apps (graphical interface for expl) and i see that i need to download ~300Mb for this, and as my internet connection would take time to do this, how can i install the packages from ubuntu cd mounted on the virtual machine, how to make the CD availale t the machine, how to install, what to install.... ?
thanks a lot

---

### Post by lemming465 on 2009-02-09
To make a CD available to a Vmware guest, use the VM menu to edit the hardware.  You may have a CD connect/disconnect/edit submenu you can use.  The CD dialog pane lets you either tie the guest CD drive to a host's physical CD drive, or to point the guest CD drive at an ISO image file.

To include CD's as a package source in the guest, scan them with *sudo apt-cdrom add*.  They should get listed in /etc/apt.sources.list.

Install stuff with *sudo apt-get install ...*.  

As to what, it depends on what you want.  For a minimal X environment start with something like *sudo apt-get install xorg gdm*.  For a minimal suite of gnome applications maybe add *gnome-core*.

For a full ubuntu desktop try the metapackage *ubuntu-desktop*, though that will download a fair amount unless you have run apt-cdrom add against the ubuntu alternate install CD.

---

### Post by lamarty on 2009-02-10
thanks lemming465 for your answer.
i had installed ubuntu-desktop, gnome-core, gdm, executed sudo /etc/init.d/gdm start, but till now i can't have the GUI interface, is there something else to do ?

---

### Post by lemming465 on 2009-02-10
Hmmm.  I took a virtualbox ubuntu server 8.10 vm, installed ubuntu-desktop, and ran sudo /etc/init.d/gdm start.  I got an X/Gnome desktop, and reboots became graphical rather than text.

Are there any error messages in /var/log/messages or /var/log/Xorg.0.log?  Does *sudo dpkg-reconfigure xserver-xorg* help any?  Have you installed the vmware tools?

---

### Post by lamarty on 2009-02-14
thanks for your answer,
i downloaded Ubuntu Server 8.10 and it worked like a charme, i don't know it didn't on 8.04 version.
again, thanks for your help.

---

