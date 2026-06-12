---
title: "installing nvidia-glx-177 in text mode"
date: 2008-11-03
forum: General Help
---

### Post by feistybee on 2008-11-03
when installing nvidia-glx-177, i read in some forum saying i need to switch to command line.

so i had gone to command line by ctrl+alt+F1

after logging in, i tried the following command to stop the X server.

sudo /etc/init.d/gdm stop

It is not working. gdm doesn't have any arguments 'stop', so it started another X session. What is the problem here? How I can stop a gdm session? Just by killing all gdm process?

---

### Post by tuxxy on 2008-11-03
why CLI couldnt you enable it at hardware drivers? if none listed maybe they meant download the driver from nvidia and run it from the CLI?

---

### Post by feistybee on 2008-11-03
I am having the following configuration.

AMD X2 Athlon x64 processor
ASUS M2NPV-VM motherboard with nvidia geforce 6150
1 GB RAM

By default the drivers are not installed. So I need to install manually.

---

