---
title: "dpkg --configure gnome-themes-selected"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by lbloy on 2009-04-25
I upgraded to 9.04 64 last night and everything went reasonably smoothly.

However, a couple of packages (gnome-themes-selected, ubuntu-desktop) failed to configure. So i get error message every time I install anything.

lbloy@Aerilon:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up gnome-themes-selected (2.26.0-0ubuntu1) ...
gtk-update-icon-cache: No theme index file.dpkg: error processing gnome-themes-selected (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-themes-selected; however:
  Package gnome-themes-selected is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 gnome-themes-selected
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)


It seems like this is the core problem

Setting up gnome-themes-selected (2.26.0-0ubuntu1) ...
gtk-update-icon-cache: No theme index file.dpkg: error processing gnome-themes-selected (--configure):
 subprocess post-installation script returned error exit status 1

any thoughts on getting gnome-themes-selected to configure?

thanks
Luke

---

### Post by tastygroove on 2009-05-24
i am having the same issue, same error messages and all.  again, it started after upgrading to 9.04 64-bit version.  i'd really like to find a solution...

---

### Post by srinivas_iiith on 2009-10-28
Hi,

I am also facing the same problem when I tried updating my machine from ubuntu 8.10 to 9.04.

Setting up gnome-themes-selected (2.26.0-0ubuntu1) ...
gtk-update-icon-cache: No theme index file.dpkg: error processing gnome-themes-selected (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gnome-themes-selected

If anyone was able to fix this problem, please reply with the solution.

Thanks in advance,
Srinivas

---

### Post by srinivas_iiith on 2009-10-29
Hi,

I was able to fix this problem. This problem due to the missing of index.theme in /usr/share/icons/Mist folder. I fixed this by copying this file from another machine. 

Srinivas.

---

