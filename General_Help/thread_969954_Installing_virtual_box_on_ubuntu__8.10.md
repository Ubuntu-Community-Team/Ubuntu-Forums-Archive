---
title: "Installing virtual box on ubuntu  8.10"
date: 2008-11-03
forum: General Help
---

### Post by adam98 on 2008-11-03
When i install the dev file i get this message

```
VirtualBox will not start until this problem is fixed. Please consult /var/log/vbox-install.log to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them (the package name is probably linux-headers-<version> whereby <version> can be determined by 'uname -r') and execute

  /etc/init.d/vboxdrv setup

as root.
```

and when i execute the command to install them i get

```
sudo apt-get install linux-headers-2.6.24-16-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.24-16-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.24-16-generic has no installation candidate
```

---

### Post by tuxxy on 2008-11-03
What happens when you run 

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by adam98 on 2008-11-03
```
sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong

```
I checked my package manager to see which generic headers i have and i have installed 2.6.27.7.11 which is weird because 

```
 uname -r
2.6.24-16-generic
entreri@homeland:~$ 
```

---

### Post by adam98 on 2008-11-03
```
Attempting to install using DKMS
  removing old DKMS module vboxdrv version 

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 2.0.4
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/2.0.4/source ->
                 /usr/src/vboxdrv-2.0.4

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.24-16-generic cannot be found at
/lib/modules/2.6.24-16-generic/build or /lib/modules/2.6.24-16-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:142: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop.
```
the content of my install log file.

---

