---
title: "installation of 855gm fix failed to build, what did i do wrong?"
date: 2011-02-07
forum: Hardware
---

### Post by azeritah on 2011-02-07
Hi, I have a laptop that has the 855gm intel chip with its problem (freezes after closing lid).
I just did a fresh install from cd on an old toshiba a55 laptop, and during the last step of 
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
which is:
sudo apt-get update && sudo apt-get install dkms 855gm-fix-dkms
[SIZE=2]
then it fails[/SIZE]...
it said to consult the make.log, and it has an error that i have no clue how to fix.

DKMS make.log for 855gm-fix-0.7.7 for kernel 2.6.37-graphics2+12-generic (i686)
Sun Feb  6 23:51:12 PST 2011
make: Entering directory `/usr/src/linux-headers-2.6.37-graphics2+12-generic'
  LD      /var/lib/dkms/855gm-fix/0.7.7/build/agp/built-in.o
  CC [M]  /var/lib/dkms/855gm-fix/0.7.7/build/agp/intel-agp.o
/var/lib/dkms/855gm-fix/0.7.7/build/agp/intel-agp.c: In function ‘agp_intel_resume’:
/var/lib/dkms/855gm-fix/0.7.7/build/agp/intel-agp.c:2719: error: implicit declaration of function ‘agp_rebind_memory’
make[2]: *** [/var/lib/dkms/855gm-fix/0.7.7/build/agp/intel-agp.o] Error 1
make[1]: *** [/var/lib/dkms/855gm-fix/0.7.7/build/agp] Error 2
make: *** [_module_/var/lib/dkms/855gm-fix/0.7.7/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.37-graphics2+12-generic'

when i run again the apt-get install it tries to reinstall again, but it fails again.

can anyone help me point out what i need to do to successfully build the fix?

Thanks

---

### Post by Sirius1977 on 2011-02-15
It doesn't build because the 2.6.37-graphics2+12-generic kernel from the ppa already contains a fix. You don't need the 855gm-fix-dkms package.

---

