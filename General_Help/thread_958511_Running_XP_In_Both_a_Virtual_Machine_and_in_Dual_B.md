---
title: "Running XP In Both a Virtual Machine and in Dual Boot?"
date: 2008-10-25
forum: General Help
---

### Post by igfud on 2008-10-25
Hello,

I was recently helping a friend with his Apple laptop.  He demonstrated how he can use Parallels to run XP as a virtual machine while booted up in OSX.  Similarly, he can dual boot into XP and OSX.  Having had some experience with virtual machines this wasn't a surprise to me, except for the fact that Boot Camp and Parallels were using the same copy of XP.  So he could essentially use XP for any small tasks as a virtual machine, but actually dual boot into that same copy of XP in order to take maximum advantage of his hardware (ie 3D accelerated graphics).

Is there any similar way to do this in Ubuntu, such that my virtual machine is the same copy of XP as my dual boot option?

Thanks,
igfud

---

### Post by ddixonr on 2008-10-25
As long as your not looking for the virtual copy and the physical copy to be in sync, you could make a ghost image of the physical OS you want as the virtual machine, then set up Vmware or Virtualbox accordingly using that image.

If you are looking for the two to be in sync, I'm out of my league.

---

### Post by jerome1232 on 2008-10-25
I *think* it could be done if XP had both hardware profiles stored in it, one profile for the vm's hardware, one for the real hardware. Usually XP will refuse to boot if a substantial amount of hardware has changed, part of the wga stuff.

I don't know if this link is of any help, it's VirtualBox specific you never mentioned what VM you are wanting to use.
[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

---

