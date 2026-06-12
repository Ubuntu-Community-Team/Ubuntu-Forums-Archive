---
title: "virtual box not working after last upgrade"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by xalaros on 2009-02-17
Hello,

today i have done the latest updated which included kernel 2.6.27.12
and virtualbox updated to 2.1.4.42893 after reboot i am trying to start a
VM and i get :

Failed to open/create the internal network 'HostInterfaceNetworking-eth0' (VERR_SUPDRV_COMPONENT_NOT_FOUND).
Failed to attach the network LUN (VERR_SUPDRV_COMPONENT_NOT_FOUND).
Unknown error creating VM (VERR_SUPDRV_COMPONENT_NOT_FOUND).

on all my VMs does anybody else have the same problem and maybe a solution???

by the way i am on ubuntu 8.10 x64 machine.

---

### Post by xalaros on 2009-02-17
ok i seem to have solved my own problem for some reason the vboxdrv module didn't recompile automatically so after doing a sudo /etc/init.d/vboxdrv setup  everything seems fine.

---

### Post by .nedberg on 2009-02-17
I think that is normal behaviour from virtualbox when you upgrade the kernel.

I also _think_ this will happen automaticaly if you install dkms
```

sudo apt-get install dkms

```
but I have not tried it...

I will upgrade my kernel now and see if it works!

---

### Post by .nedberg on 2009-02-17
I just upgraded my kernel, and dkms did it's stuff! Virtualbox VMs was working fine after a reboot, just as i expected!

I just hadn't upgraded my kernel after I installed Virtualbox so I was not sure if dkms would work with it. Upgrading took a while longer, but it saves you some stress!

---

### Post by sv1cdn on 2009-02-18
Same problem here.
Probably kernel has to be updated first, hard reset Ubuntu and then upgrade Virtualbox!
I did both in one task and networking failed to work unit I run sudo /etc/init.d/vboxdrv setup and restarted networking or the whole Ubuntu.

---

### Post by .nedberg on 2009-02-18
From VirtualBox download page: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

```

Note: Ubuntu users might want to install the dkms package (not available on Debian) to ensure that the VirtualBox host kernel modules (vboxdrv and vboxnetflt) are properly updated if the linux kernel version changes during the next apt-get upgrade.

```

If you don't install dkms (before a kernel upgrade), you will have to run
```

sudo /etc/init.d/vboxdrv setup

```

---

### Post by bascuppen on 2010-01-17
What might help you is a simple
```
$ sudo apt-get remove virtualbox-ose-guest-source
```
before executing 
```
$ sudo /etc/init.d/vboxdrv setup
```

Use it at your own discretion.

---

### Post by cracked@pieces on 2011-03-06
> **bascuppen said:**
> What might help you is a simple
```
$ sudo apt-get remove virtualbox-ose-guest-source
```before executing 
```
$ sudo /etc/init.d/vboxdrv setup
```Use it at your own discretion.


Thanks this fixed the issue for me.

---

### Post by maciekish on 2012-01-19
I'm facing the same issue on a ReadyNAS Ultra 2 (Intel Atom, 2GB RAM, Debian 4). Not related to upgrade though, vm's with nat networking start fine but bridged mode doesnt work:

Error: failed to start machine. Error message: Failed to open/create the internal network 'HostInterfaceNetworking-' (VERR_INVALID_PARAMETER).
Failed to attach the network LUN (VERR_INVALID_PARAMETER)

---

