---
title: "Unable to reconfigure Sun Virtualbox"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by tayran on 2009-10-31
Hi,

I have upgraded my Kubuntu Jaunty to Karmic yesterday. I now want to reconfigure virtualbox for the new kernel but when i run /etc/init.d/vboxdrv setup it says:

Error! Your kernel source for kernel 2.6.31-14-generic cannot be found at
/lib/modules/2.6.31-14-generic/build or /lib/modules/2.6.31-14-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:147: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

I checked that i had only kernel image package for 2.6.31-14 kernel so i also installed headers package for that kernel but still the same problem goes on.

When i manually installed 2.6.30 kernel before on Jaunty i remeber there were three deb's but now i see only two packages in kpackagekit as installable.

---

### Post by udippel on 2009-11-01
> **tayran said:**
> 

I now want to reconfigure virtualbox for the new kernel but when i run /etc/init.d/vboxdrv setup it says:

Error! Your kernel source for kernel 2.6.31-14-generic cannot be found at
/lib/modules/2.6.31-14-generic/build or /lib/modules/2.6.31-14-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:147: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

I checked that i had only kernel image package for 2.6.31-14 kernel so i also installed headers package for that kernel but still the same problem goes on.

When i manually installed 2.6.30 kernel before on Jaunty i remeber there were three deb's but now i see only two packages in kpackagekit as installable.



Bitten by the same bug.
I installed
$ sudo apt-get install linux-source-2.6.31
but no changes. It might have to make with the '-generic', but
$ sudo apt-get install linux-source-2.6.31-generic
[...]
E: Couldn't find package linux-source-2.6.31-generic

Now, what to do next?

---

### Post by udippel on 2009-11-01
Lousy. It is a fault of the package that ought to do this:
$ sudo apt-get install linux-headers-rt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-2.6.31-9-rt linux-rt-headers-2.6.31-9
The following NEW packages will be installed:
  linux-headers-2.6.31-9-rt linux-headers-rt linux-rt-headers-2.6.31-9
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.2MB of archives.
After this operation, 82.8MB of additional disk space will be used.
Do you want to continue [Y/n]? n

Of course not:
$ uname -r
2.6.31-14-generic

So you need to cheat:
$ sudo apt-get install linux-headers-2.6.31-14-generic
This will do:
The following extra packages will be installed:
  linux-headers-2.6.31-14
The following NEW packages will be installed:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic

and then 
$ sudo /etc/init.d/vboxdrv setup
should go through.

You might hit another snag:
VirtualBox can't operate in VMX root mode.

Try 
sudo rmmod kvm-intel
(respectively ... kvm-amd)
and it should work.

YMMV

---

### Post by blackened07 on 2010-01-18
> **udippel said:**
> Lousy. It is a fault of the package that ought to do this:
$ sudo apt-get install linux-headers-rt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-2.6.31-9-rt linux-rt-headers-2.6.31-9
The following NEW packages will be installed:
  linux-headers-2.6.31-9-rt linux-headers-rt linux-rt-headers-2.6.31-9
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.2MB of archives.
After this operation, 82.8MB of additional disk space will be used.
Do you want to continue [Y/n]? n

Of course not:
$ uname -r
2.6.31-14-generic

So you need to cheat:
$ sudo apt-get install linux-headers-2.6.31-14-generic
This will do:
The following extra packages will be installed:
  linux-headers-2.6.31-14
The following NEW packages will be installed:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic

and then 
$ sudo /etc/init.d/vboxdrv setup
should go through.

You might hit another snag:
VirtualBox can't operate in VMX root mode.

Try 
sudo rmmod kvm-intel
(respectively ... kvm-amd)
and it should work.

YMMV

Excellent ! Worked for me too, Thanks a Lot

Greetings.

---

