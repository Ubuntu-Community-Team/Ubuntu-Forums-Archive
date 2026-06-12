---
title: "Remove /swfdec?"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by kjkoec on 2009-04-26
I recently upgraded to 9.04 Jaunty and realized that swfdec had been installed.  It doesn't work too well, and Firefox says I still have the official flash plugin installed, but when I use the Synaptic Package Manager to try to remove it, it lists "gnome" as a dependency.

Is it safe to uninstall swfdec then?  On most forums, people don't even mention gnome as a dependency, so ???

---

### Post by joshrobinson on 2009-04-26
I wouldnt remove it if it wants to take gnome with it.
Have you tried just disabling it in firefox and letting it use a different flash plugin?

---

### Post by kjkoec on 2009-04-26
Strange...
about:plugins and the addons/plugins list just show the official flash installed.  Neither mention swfdec or any other flash version.

---

### Post by wonderbriefs on 2009-04-27
I'm having the same problem. When I mark swfdec-mozilla for removal it wants to remove Gnome as well. What gives?

---

### Post by wonderbriefs on 2009-04-27
Okay, here's the deal:

For some reason I had two different packages for Gnome installed on my system. I don't know how this happened.

* Gnome (description says something like Gnome Desktop Environment plus extras)
* Gnome Desktop Environment

swfdec-mozilla for some reason depends on the Gnome (plus extras) package. I was hesitant to remove this because I didn't want to lose Gnome. I took the chance and removed swfdec-mozilla, and it also removed the extra Gnome package.

The remaining Gnome package stayed installed, and I have had no other problems since.

Check to see if you have more than one Gnome installed. If you do, then it should be safe to remove swfdec-mozilla even if it says that it will remove Gnome.

---

### Post by aselvan on 2009-05-25
I had the same problem with fresh install of Ubuntu 9.04. The swfdec was installed somehow and was pretty sluggish and literally unusable. I was able to remove just that (i.e. no gnome dependency mentioned above) and installed libflashplayer.so ... flash is much better.

[FONT="Fixedsys"]aselvan@panther:~$ sudo apt-get remove swfdec-mozilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswfdec-0.8-0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  swfdec-mozilla
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 303kB disk space will be freed.
Do you want to continue [Y/n]? y[/FONT]

---

### Post by asmodaeus on 2009-07-28
Generally, for this kind of thing, I'd prefer to use aptitude, just because it removes all the nasty little swfdec libraries as well, but I did not run into the Gnome dependancy problem either.

---

### Post by pavel989 on 2009-10-25
> **wonderbriefs said:**
> Okay, here's the deal:

For some reason I had two different packages for Gnome installed on my system. I don't know how this happened.

* Gnome (description says something like Gnome Desktop Environment plus extras)
* Gnome Desktop Environment

swfdec-mozilla for some reason depends on the Gnome (plus extras) package. I was hesitant to remove this because I didn't want to lose Gnome. I took the chance and removed swfdec-mozilla, and it also removed the extra Gnome package.

The remaining Gnome package stayed installed, and I have had no other problems since.

Check to see if you have more than one Gnome installed. If you do, then it should be safe to remove swfdec-mozilla even if it says that it will remove Gnome.

yeah i had gnome-desktop-environment and gnome installed, i removed the swfdec-mozilla package which by dependency removed gnome and everything works fine.

---

### Post by falcon84 on 2010-06-05
Thank you very much...

---

