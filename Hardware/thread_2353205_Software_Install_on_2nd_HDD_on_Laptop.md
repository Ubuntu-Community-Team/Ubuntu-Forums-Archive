---
title: "Software Install on 2nd HDD on Laptop"
date: 2017-02-19
forum: Hardware
---

### Post by thebunker on 2017-02-19
I am new to Ubuntu (16.04) and am in the process of loading various software on my laptop (a 2+ year old MSI GT70).  However, I have a 128GB SSD and a 1TB HDD in it. I would prefer loading as much as I can on the 1TB HDD if possible.  So far, however, everything I have loaded has gone to the SSD.  I am planning on a LAMP stack on this machine and would like it over on the HDD.  Does anyone know to override where applications load?

Note: I am only experimenting and will be doing a clean install when 17.04 comes out.

---

### Post by igdfpm on 2017-02-20
The whole idea of having a (smaller) SSD and (larger) HDD is that you have all your OS and applications on the SSD (faster response/access) drive and data on the (slower, larger and cheaper) HDD... why change it?

If you are saying that your /home partition is also on the SSD then you may want to move that over to the HDD but OS and APPS are best placed on the SSD performance wise ;)

You can move the root of your L{A,E}MP stack to wherever you like - although it is usually simpler (and saner) to leave root in it's default position and use subdomains/virtualhosts that point to your chosen folder structure on your /home partition for your own projects.

---

### Post by gordintoronto on 2017-02-20
During installation, you can choose where / and /home go. (Choose "something else.") If you plan to run a web site, it will default to the / partition, but even that can be changed. Just make sure grub goes on the boot drive.

A root partition of 16 GB should be quite adequate, if you do some housekeeping at least once a year, mostly removing old kernels.

---

