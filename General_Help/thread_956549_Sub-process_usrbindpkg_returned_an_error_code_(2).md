---
title: "Sub-process /usr/bin/dpkg returned an error code (2)"
date: 2008-10-23
forum: General Help
---

### Post by greenkernel on 2008-10-23
When I tried to install PokerTH, the following error message returned:
> sudo apt-get install pokerth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglib1.2ldbl stardict-common libgtk1.2 libogdi3.2 python-pyogg proj
  libgeos2c2a python-pyvorbis xulrunner-1.9-dom-inspector python-editobj
  libglc0 python-cerealizer libgeos-c1 libphysfs-1.0-0 libopenthreads6
  libhdf5-serial-1.6.5-0 libcal3d12 python-soya flex python-tofu
  libgtk1.2-common libhdf4g libode0debian1 libgdal1-1.4.0 libxerces27
  libnetcdf4 libcoin40c2 libsmpeg0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libboost-filesystem1.34.1 libboost-thread1.34.1
The following NEW packages will be installed:
  libboost-filesystem1.34.1 libboost-thread1.34.1 pokerth
0 upgraded, 3 newly installed, 0 to remove and 26 not upgraded.
2 not fully installed or removed.
Need to get 0B/5327kB of archives.
After this operation, 9851kB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Sub-process /usr/bin/dpkg returned an error code (2)Not only for PokerTH, but also for other applications such as installing update patches from Update Manager. My system is refusing to install any software.
When I tried to reconfigure the dpkg, the following error massage returned:
> sudo dpkg-reconfigure -a
dpkg-query: parse error, in file `/var/lib/dpkg/status' near line 1475 package `gdm':
 `Recommends' field, invalid package name `': must start with an alphanumeric
/usr/sbin/dpkg-reconfigure: acl is not installedPlease help me solve the problem. Thanks.

Regards,

[COLOR="DarkGreen"]greenkernel[/COLOR]

---

### Post by ajgreeny on 2008-10-23
Assuming you have a GUI of some sort and can run synaptic, do that and look to see if there are any broken packages showing in the system bar at the bottom of the synaptic window.  If there are in the Edit menu, select Fix broken packages.  It may not help, but it's something to try.  I don't know if it is worth looking in your **/var/lib/dpkg/status** file line 1475 to see if you can see anything wrong, but the error message also shows that to be at fault.  Unfortunately I don't really know how to put it right.

---

### Post by greenkernel on 2008-10-23
> **ajgreeny said:**
> Assuming you have a GUI of some sort and can run synaptic, do that and look to see if there are any broken packages showing in the system bar at the bottom of the synaptic window.  If there are in the Edit menu, select Fix broken packages.  It may not help, but it's something to try.  I don't know if it is worth looking in your **/var/lib/dpkg/status** file line 1475 to see if you can see anything wrong, but the error message also shows that to be at fault.  Unfortunately I don't really know how to put it right.When I checked line 1475 of /var/lib/dpkg/status, I found the name of a recomendation library package was somethig strange (ie. could not see properly even in gedit). So I deleted that name and saved it. Finally, the problem solved. Now, I'm playing PokerTH and I am able to update my system through Update Manager. I'm happy now. Thank you very much!!

Regards,

[COLOR="DarkGreen"]greenkernel[/COLOR]

---

