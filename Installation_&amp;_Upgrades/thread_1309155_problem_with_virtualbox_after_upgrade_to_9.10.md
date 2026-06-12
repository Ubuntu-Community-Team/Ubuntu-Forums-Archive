---
title: "problem with virtualbox after upgrade to 9.10"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Gresley on 2009-11-01
I have today updated from ubuntu Jaunty to Karmic.

Sun Virtualbox no longer works; Error message as follows appears each time i try to start windows xp from within virtualbox:

"failed to start the virtual machine XP Home"

"Virtualbox cannot operate in VMX root mode. Please disable the kvm kernel extension, recompile your kernel and reboot. (VERR_VMX_IN_VMX_ROOT_MODE)".

I've checked that the current version of DKMS is installed and upgraded virtualbox to version 3 using sudo apt get install virtualbox 3.0, but this makes no difference, and the error remains.

Can anyone tell me in english how to disable the kvm kernel extension (and if I do so what this might affect), or suggest an alternative way to make virtualbox work again?

---

### Post by INTENSETUX on 2009-11-01
Having similar problems installing VirtualBox , get the error message 

''Could not open virtual box_3.0.10-54097_Ubuntu_karmic_i386.deb
The package might be corrupted or you are not allowed to open the file please check the permissions of the file''

Any ideas guys ?

Tried installing from synaptic and  this appears to have resolved the problem. Gresley, you might want to try reinstalling from synaptic ?

---

### Post by Gresley on 2009-11-01
The issue is now resolved. Somewhere along the line the package qemu_kvm was installed.

I can only assume this happened somewhere in the upgrade from Jaunty to Karmic.

following the command: *sudo apt-get remove quemu_kvm* virtualbox runs perfectly!

I suppose sooner or later I'll find out what qemu actually does, and find something else doesnt work because I removed it!

---

### Post by Gresley on 2009-11-03
Having thought that the problem had gone away, it reappeared again next re-boot. Clearly removing qemu was not the full answer, something else is triggering KVM.

In terminal the following is revealed to be running:

kevin@T60:~$ lsmod | grep kvm
kvm_intel              43816  0 
kvm                   162688  1 kvm_intel

and this can be disabled by:

sudo rmmod kvm_intel

The only problem is that this only works in the current session, and kvm reloads on every re-boot.

I've tried to remove the package with apt-get, but apt-get doesnt recognise that it even exists.

The question is, what is triggering the package in the first place. I'm starting virtualbox from a clean boot without loading any apps save for compiz, awn, and a couple of applets

Having done some research, it seems that this is an issue that isnt just peculiar to Karmic, but goes back to older releases, KVM isnt anything new to this release of the Ubuntu distro.

What I dont understand is why I've run Virtualbox in Intrepid and Jaunty without this problem before, and its started happening when the only change to the machine I'm aware of is routine upgrades to Karmic and an upgrade of virtualbox to the current release. Folk who ahve done full installs of both these packages rather than upgrades are not reporting similar problems.

Any ideas please?

---

### Post by PendragonUK on 2009-11-22
Same problem my solution, dirty but simple...

Synaptic, search KVM
Uninstall, anything-everything KVM

Works now :)

---

