---
title: "WMwareWorkstation installation problem."
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2009-02-04
I am trying to install VMwareWorkstation from this link
[https://help.ubuntu.com/community/VMware/Workstation](https://help.ubuntu.com/community/VMware/Workstation)

When I run this command sudo aptitude install build-essential linux-kernel-headers linux-kernel-devel on console I get the following errors


luc@ubuntu:~$ sudo aptitude install build-essential linux-kernel-headers linux-kernel-devel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "linux-kernel-devel"
Couldn't find any package whose name or description matched "linux-kernel-devel"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

---

### Post by ncubede on 2009-02-04
You may want to drop the linux-kernel-devel part.
All that VMware needs is to compile its modules,
so linux-headers-.* need to be installed for the kernel you are running.

I'd suggest to install build-essential linux-headers-generic and then leave it at that (assuming you installed linux-image-generic as the kernel selector)

---

### Post by hoboy on 2009-02-04
> **ncubede said:**
> You may want to drop the linux-kernel-devel part.
All that VMware needs is to compile its modules,
so linux-headers-.* need to be installed for the kernel you are running.

I'd suggest to install build-essential linux-headers-generic and then leave it at that (assuming you installed linux-image-generic as the kernel selector)

Thanks for  your time how to I install 
build-essential linux-headers-generic ?

---

### Post by binbash on 2009-02-04
you have to install kernel headers matching your kernel.check your kernel with uname -a then open synaptic and search for linux-headers, then install the matching one

---

### Post by ncubede on 2009-02-04
I'd normally do:
```

sudo apt-get update
sudo apt-get install build-essential linux-headers-generic

```

Please note, that this will only work, if you really installed linux-image-generic and have booted this kernel.  

Additionally I'd suggest people from time to time do a dist upgrade to pull in bugfixes
```

sudo apt-get update
sudo apt-get dist-upgrade

```

> **hoboy said:**
> Thanks for  your time how to I install 
build-essential linux-headers-generic ?

---

### Post by ncubede on 2009-02-04
That will be fine for the moment, but if he has a meta package like linux-image-generic installed, he needs the matching meta package for the linux headers as well, or after the next dist-upgrade the same question will be asked again.

> **binbash said:**
> you have to install kernel headers matching your kernel.check your kernel with uname -a then open synaptic and search for linux-headers, then install the matching one

---

### Post by hoboy on 2009-02-04
> **binbash said:**
> you have to install kernel headers matching your kernel.check your kernel with uname -a then open synaptic and search for linux-headers, then install the matching one

I have run uname with sudo and without sudo the result is the same
luc@ubuntu:~$  uname -a
Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
luc@ubuntu:~$ 

what can I seach in synacptic in the string ?

---

### Post by ncubede on 2009-02-04
the package you are looking for then is called: linux-headers-2.6.27-11-generic, which is the one selected from intrepid updates and proposed at the moment.
```
apt-get install linux-headers-2.6.27-11-generic
``` should do it.

If you have linux-image-generic installed, you should also install linux-headers-generic, though, so you stay up to date in the future. 

> **hoboy said:**
> I have run uname with sudo and without sudo the result is the same
luc@ubuntu:~$  uname -a
Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
luc@ubuntu:~$ 

what can I seach in synacptic in the string ?

---

### Post by hoboy on 2009-02-04
> **ncubede said:**
> the package you are looking for then is called: linux-headers-2.6.27-11-generic, which is the one selected from intrepid updates and proposed at the moment.
```
apt-get install linux-headers-2.6.27-11-generic
``` should do it.

If you have linux-image-generic installed, you should also install linux-headers-generic, though, so you stay up to date in the future.

luc@ubuntu:~$ sudo apt-get install linux-headers-2.6.27-11-generic
[sudo] password for luc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.27-11-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
luc@ubuntu:~$

---

### Post by hoboy on 2009-02-04
> **hoboy said:**
> luc@ubuntu:~$ sudo apt-get install linux-headers-2.6.27-11-generic
[sudo] password for luc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.27-11-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
luc@ubuntu:~$

ncubede--- 
I am loosing trac here how this one help to install VMwareWorkstation ?

---

### Post by ncubede on 2009-02-04
Awesome, then just install VMware workstation (run the bundle install) and start it up. It'll say it needs to compile a few modules and then continue startup (at least 6.5 does, before that vmware-config.pl needed to be run).

---

### Post by ncubede on 2009-02-04
The only thing Vmware needs is to be able to compile kernel modules.  For this you need the linux source or the headers and the essential build environment.  That is all.  My recommendation is to just install VMware workstation and only if that fails to build the kernel modules to look at something else, but the howto guide referred to in the first post, assumed a pretty stripped down system.

> **hoboy said:**
> ncubede--- 
I am loosing trac here how this one help to install VMwareWorkstation ?

---

### Post by hoboy on 2009-02-04
> **ncubede said:**
> Awesome, then just install VMware workstation (run the bundle install) and start it up. It'll say it needs to compile a few modules and then continue startup (at least 6.5 does, before that vmware-config.pl needed to be run).

sorry about my question in the link upward ti stated that 
Navigate to where the .bundle VMWare file is, then type this in

gksudo bash ./VMware-Workstation-6.5.0-118166.i386.bundle 
where is located VMware-Workstation-6.5.0-118166.i386.bundle  ?

---

### Post by ncubede on 2009-02-04
you need to browse [http://www.vmware.com](http://www.vmware.com) and download it (6.5.1, not 6.5.0)

---

### Post by wentzr on 2011-08-18
how about just:
```
apt-get install build-essential linux-headers-`uname -r`
```

use backticks ` around uname -r and do it in one fell swoop.

---

