---
title: "nVidia drivers won't load"
date: 2008-04-29
forum: Hardware
---

### Post by toarlach on 2008-04-29
I just upgraded to Hardy, and I cannot seem to get my nVidia drivers to load. 

I have an nVidia gForce 6200. 

I killed (killall gdm) GDM, so that isn't running and everything went smoothly after I ran the .run file, but when I start GDM again after reboot, it goes back into Low graphics mode, and the only resolutions I see are 640x480 and 800x600. 

Any suggestions would be helpful.

---

### Post by z0mbie on 2008-04-29
This is a good tutorial:

[http://www.funnestra.org/ubuntu/hardy/#nvidia-driver](http://www.funnestra.org/ubuntu/hardy/#nvidia-driver)


Good lucks.

---

### Post by subzero316 on 2008-04-29
Did you try with ENVY?

---

### Post by toarlach on 2008-04-29
> **subzero316 said:**
> Did you try with ENVY?
Envy? It worked fine on Gutsy before upgrading to Hardy.

---

### Post by thisismalhotra on 2008-04-29
> **toarlach said:**
> Envy? It worked fine on Gutsy before upgrading to Hardy.

Use EnvyNG-gtk if u r using ubuntu and it will be awesome and easy to do !!

---

### Post by harmony on 2008-04-29
I have a gForce 6600gt and the drivers that are working for me are 173.08 version from the nvidia site here [http://www.nvidia.com/object/linux_display_ia32_173.08.html](http://www.nvidia.com/object/linux_display_ia32_173.08.html) after installing I still was not getting resolutions above 800x600, but by editing my xorg.conf under section Monitor and adding correct values for HorizSync and VertRefresh everything is working great now. all of this info shoud be available from the manufacturers website of the monitor.

---

### Post by subzero316 on 2008-05-02
looks like your xorg.cnf file settings are not getting saved.
Try editing it in superuser(sudo).. and save it..then try restrating gdm.Also make sure you evrything in console screen(crtl+alt+F1).

---

