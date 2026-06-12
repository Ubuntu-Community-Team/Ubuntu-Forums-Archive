---
title: "Nvidia prorietry module will not load"
date: 2015-05-02
forum: Hardware
---

### Post by laurence2 on 2015-05-02
Hi

I'm haveing issues with the nvidia propriety driver installed from the gui in Vivid, this was working up until recently and I'm not sure what has changed.


I get the following message in the Xorg.0 log 

Failed to initialize the NVIDIA kernel module. Please see the system's kernel log for additional error messages and consult the NVIDIA README for details.

but I can find nothing usefull in the kern.log

Can anyone suggest any further places to look or try?


```
loz@gravity:~$ dpkg -l | grep nvidia
rc  nvidia-346-updates                                          346.59-0ubuntu1                                  amd64        NVIDIA binary driver - version 346.59
ii  nvidia-common                                               1:0.4.5                                          amd64        transitional package for ubuntu-drivers-common
rc  nvidia-libopencl1-340-updates                               340.76-0ubuntu2                                  amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-opencl-icd-340                                       340.76-0ubuntu2                                  amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-340-updates                               340.76-0ubuntu2                                  amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-346                                       346.59-0ubuntu1                                  amd64        NVIDIA OpenCL ICD
ii  nvidia-opencl-icd-346-updates                               346.59-0ubuntu1                                  amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                                0.8.1                                            amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             346.59-0ubuntu1                                  amd64        Tool for configuring the NVIDIA graphics driver
loz@gravity:~$



```

---

### Post by kc1di on 2015-05-02
Was the kernel recently updated?  if so it may be that the nvidia kernel module did not get rebuilt properly. 
if that is indeed the case I would try the following in a terminal:```
sudo apt-get purge nvidia
```
```
sudo apt-get install nvidia-346
```

If you originally installed the nvidia driver via the additional driver tool or through apt it should have loaded DKMS which will automatically rebuild the module when the kernel changes. but if you installed in through some other route that may not have happened.
Good Luck 
:)

---

### Post by laurence2 on 2015-05-02
unfortunatly not

I purged all the nvidia packages then did a fresh install as mentioned above...

Unfortunately this brings me back to the same issue....


Anything else to try?

---

### Post by dino99 on 2015-05-02
> **laurence2 said:**
> unfortunatly not

I purged all the nvidia packages then did a fresh install as mentioned above...

Unfortunately this brings me back to the same issue....


Anything else to try?

That should work as the 346 driver have not issue usually, compared to older's ones
Do you use custom packages (ppa, third party) or non genuine ubuntu kernel ?
The real solution is to glance at your logs to find something usefull: purge again nvidia* and install 'nouveau' if not yet done, then reboot.

---

### Post by laurence2 on 2015-05-02
> **dino99 said:**
> That should work as the 346 driver have not issue usually, compared to older's ones
Do you use custom packages (ppa, third party) or non genuine ubuntu kernel ?
The real solution is to glance at your logs to find something usefull: purge again nvidia* and install 'nouveau' if not yet done, then reboot.

At the moment I'm not using any special kernels and using the standard repositories, i can get nouveau  working but then several things like audio over hdmi and video acceleration do not work aswell, plus i occasionally play games on that machine so could do with the proprietary drivers. 


Xorg log here: [http://paste.ubuntu.com/10970996/](http://paste.ubuntu.com/10970996/)
dmesg log : [http://paste.ubuntu.com/10971001/](http://paste.ubuntu.com/10971001/)

kernel log here: [http://paste.ubuntu.com/10971007/](http://paste.ubuntu.com/10971007/)

Not sure if this is important
```
loz@gravity:~$ sudo modprobe nvidia
[sudo] password for loz:
modprobe: ERROR: ../libkmod/libkmod-module.c:816 kmod_module_insert_module() could not find module by name='nvidia_346'
modprobe: ERROR: could not insert 'nvidia_346': Function not implemented
loz@gravity:~$

```

---

### Post by kc1di on 2015-05-02
Check to make sure the 346 driver is not blacklisted in /etc/modprobe.d/blacklist file.

---

### Post by Bashing-om on 2015-05-02
laurence2; Hey guys;

A thought. What release are we working with here ? As the 14.04 software repository does not have the 346 driver available.
I note that the driver is not installed.
That driver is installed as 3rd party ( xorg-edgers is a great candidate) for 14.04 .
Check and see if the 3rd party PPA source is available to the system:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
else: we enable a PPA, update the system, to effect this and install the 346 driver.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by laurence2 on 2015-05-03
> **kc1di said:**
> Check to make sure the 346 driver is not blacklisted in /etc/modprobe.d/blacklist file.

nope, the framebuffer is blacklisted but that seems to be there on other working systems

> **Bashing-om said:**
> laurence2; Hey guys;

A thought. What release are we working with here ? As the 14.04 software repository does not have the 346 driver available.
I note that the driver is not installed.
That driver is installed as 3rd party ( xorg-edgers is a great candidate) for 14.04 .
Check and see if the 3rd party PPA source is available to the system:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
else: we enable a PPA, update the system, to effect this and install the 346 driver.
[INDENT][INDENT]my bit to try and help
[/INDENT]
[/INDENT]


Its vivid so 346 seems to be in but my list of sources are here
[http://paste.ubuntu.com/10975408/](http://paste.ubuntu.com/10975408/)

> **alex375 said:**
> Failed to initialize != not found
This means you have problem
Any idea how to resolve that problem?

---

### Post by tokyobadger on 2015-05-03
You have an AMD APU. Any BIOS updates recently that may have undone your settings for the discrete card?

---

### Post by laurence2 on 2015-05-03
is it possible that the following is the issue, dkms does not seem to be building for the current kernel, see highlights below

```
loz@gravity:~$ sudo apt-get install nvidia-346Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed
  nvidia-346
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
Need to get 0 B/56.9 MB of archives.
After this operation, 283 MB of additional disk space will be used.
Selecting previously unselected package nvidia-346.
(Reading database ... 360120 files and directories currently installed.)
Preparing to unpack .../nvidia-346_346.59-0ubuntu1_amd64.deb ...
Unpacking nvidia-346 (346.59-0ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.7.0.2-5) ...
Setting up nvidia-346 (346.59-0ubuntu1) ...
update-alternatives: using /usr/lib/nvidia-346/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-346/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-346/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.19.0-14-generic
grep: /boot/config-3.19.0-14-generic: No such file or directory
INFO:Enable nvidia-346
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
Adding system user `nvidia-persistenced' (UID 132) ...
Adding new group `nvidia-persistenced' (GID 141) ...
Adding new user `nvidia-persistenced' (UID 132) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-346-346.59 DKMS files...
It is likely that 3.19.0-14-generic belongs to a chroot's host
[COLOR=#ff0000]Building only for 3.19.0-**15**-generic[/COLOR]
Building for architecture x86_64
Building initial module for 3.19.0-15-generic
Done.


nvidia_346:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-15-generic/updates/dkms/


nvidia_346_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-15-generic/updates/dkms/


depmod....


DKMS: install completed.
Processing triggers for initramfs-tools (0.103ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-15-generic
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB


Total disk space freed by localepurge: 0 KiB


loz@gravity:~$ modprobe -r nvidia
loz@gravity:~$ modinfo nvidia
modinfo: ERROR: Module nvidia not found.
loz@gravity:~$
loz@gravity:~$ uname -a
Linux gravity [COLOR=#ff0000]3.19.0-**14**-generic[/COLOR] #14-Ubuntu SMP Mon Apr 13 22:18:24 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
loz@gravity:~$



```

---

### Post by laurence2 on 2015-05-03
> **tokyobadger said:**
> You have an AMD APU. Any BIOS updates recently that may have undone your settings for the discrete card?

I cant say I ever update the bios but I'll log into the bios screen and check

---

### Post by tokyobadger on 2015-05-03
Can you give the hardware of the machine and the partition set-up?

---

### Post by laurence2 on 2015-05-03
Sussed it.....


/boot was on a seperate partition (sda5) and / was on sda6

somehow the partition in the fstab had been commented out which was reverting back to the boot on sda6 but the boot flag was on sda5

god knows what commented that out but it left the following comment
# /boot was on /dev/sdb5 during installation

---

