---
title: "More problems-"
date: 2005-08-25
forum: Hardware &amp; Laptops
---

### Post by simoncullen on 2005-08-25
My system is no longer starting x at boot (and going to the pretty login screen).  Instead I have to startx manually after logging in.  I have also lost the options in the 'system'-->'logout' menu.  It used to have the options to reboot, suspend, etc, now it just has 'logout'.

My other problem, apart from the enduring no-sound thing, is that Ubuntu is no longer mounting my external USB harddisk when I plug it in.  Rather I have to mount it manually using root (sudo) and then cannot access it without root privileges.  

Any help with these issues will really be appreciated!  

Thanks
Simon

---

### Post by s_p_a_r_k_y on 2005-08-25
The reason you don't get suspend, shut down, and the rest in the logout screen is because X was started as your user id. Usually GDM is run as root which spawns the X session, thus we can issue shutdown commands to GDM which is root. 

Check /etc/rc2.d/ for entries of GDM as I believe runlevel 2 is ubuntu's default. If you don't see any links in the folder to /etc/init.d/gdm you can create one with

ln -s /etc/init.d/gdm /etc/rc2.d/S34gdm
and that should auto start gdm. Not sure about your other problems but they could be related as well

---

