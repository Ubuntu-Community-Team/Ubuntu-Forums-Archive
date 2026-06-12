---
title: "[SOLVED] Apt-get upgrade and apt-get install are broken"
date: 2008-10-26
forum: General Help
---

### Post by svriderpokey on 2008-10-26
If I try to upgrade or install new packages with apt-get, synaptic or update manager it will fail 100% of the time. I get a few error messages, and I've tried to search for similar problems, but their fixes are not working for me.  The platform is eeepc 701 4g.  OS is 8.04.1 but with 3rd party kernel and tweaks.  Everything worked great until Ubuntu released a kernel update that took higher precedence than the 3rd party kernel and much stopped working.  I used synaptic to remove all kernels that I wasn't using, and one package failed to remove.  Now it tries to remove it before doing anything else, and it fails every time. Please help me if you can.

---

### Post by alecjw on 2008-10-26
Does it say anythign about dpkg --reconfigure -a?
If so, run the command:
sudo dpkg --reconfigure -a

Heck, run it anyway just for fun!

---

### Post by drs305 on 2008-10-26
You can try this:
```
sudo dpkg --force-all --purge ***appname***
```

If that doesn't fix it, try removing the package listing from the following file. It will be a section, usually starting with "Package: " and ending with an empty line.
```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.10.26.08
gksu gedit /var/lib/dpkg/status
```

---

### Post by svriderpokey on 2008-10-26
No, it doesn't say anything about that.  I did try that before posting. It had no effect. I didn't try it because I know what I'm doing (because I don't) I tried because I saw that it fixed a similar problem for someone else. Here is what it does say:

p@peee:~$ sudo apt-get upgrade
[sudo] password for p: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-20-eeepc
The following packages have been kept back:
  bind9-host dnsutils libbind9-30 libdns35 libisccc30 libisccfg30
The following packages will be upgraded:
  cpp-4.2 g++-4.2 gcc-4.2 gcc-4.2-base libffi4 libgcc1 libglib2.0-0 libgomp1 liblwres30 libstdc++6 libstdc++6-4.2-dev pciutils
12 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 0B/8567kB of archives.
After this operation, 15.6MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 94256 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-20-eeepc ...
FATAL: Could not open '/boot/System.map-2.6.24-20-eeepc': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-20-eeepc
Cannot find /lib/modules/2.6.24-20-eeepc
update-initramfs: failed for /boot/initrd.img-2.6.24-20-eeepc
dpkg: error processing linux-ubuntu-modules-2.6.24-20-eeepc (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-20-eeepc
E: Directory '/var/log/apt/' missing
E: Sub-process /usr/bin/dpkg returned an error code (1)
p@peee:~$

---

### Post by svriderpokey on 2008-10-26
> **drs305 said:**
> 
```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.10.26.08
gksu gedit /var/lib/dpkg/status
```
YOU FIXED ME!!! 
THANK YOU! 
You're great.

---

