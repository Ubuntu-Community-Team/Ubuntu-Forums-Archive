---
title: "Installation problems for Realtec wireless card"
date: 2009-11-15
forum: Hardware
---

### Post by sebast on 2009-11-15
Just bought a Toshiba A500 and it comes with a Realtek RTL8101E network card.

Seems that wireless doesn't work out of the box with Ubuntu 9.10. I looked it up and found the driver on the Realtec website.

I installed the build-essential package and then went on with the driver installation instructions, but I get stuck at : 

```
# make clean modules
```

This is what I get :

```
sebb@sebb-laptop:~/Downloads/r8101-1.013.00$ sudo make clean modules
[sudo] password for sebb: 
make -C src/ clean
make[1]: Entering directory `/home/sebb/Downloads/r8101-1.013.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers Module.markers *.order
make[1]: Leaving directory `/home/sebb/Downloads/r8101-1.013.00/src'
make -C src/ modules
make[1]: Entering directory `/home/sebb/Downloads/r8101-1.013.00/src'
make -C /lib/modules/2.6.31-14-generic-pae/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic-pae'
scripts/Makefile.build:44: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic-pae'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/sebb/Downloads/r8101-1.013.00/src'
make: *** [modules] Error 2
```

Any help on how to fix this would be much appreciated.

---

### Post by budhe888 on 2009-11-18
I am having the same problem here.  Have a brand new Toshiba Satellite A500-6622, and I also had to get the drivers from Realtek's web site.  When trying to compile, I get the same error.

Will keep investigating.

---

### Post by budhe888 on 2009-11-19
@sebast:

Just to let you know, I was able to get this to work.  The 8101 is the wired ethernet adapter.  If your machine is like mine, then the wireless card is the Realtek 8191, which also needs a driver.

In order to get the 'make', 'make install', etc. to work for the 8101 driver, extract the driver to /root and execute it from there, then it seems to work.

For the wireless driver, this bug thread was very helpful:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126/)

One of the people posting has access to drivers from realtek for the 8192 (also work for 8191) and posted several versions of the driver that people have tried.  I followed the steps in post #99 and it seems like my wireless works now.  I have a 64-bit version of karmic installed, so you may need to use a different driver posted earlier on in the discussion thread if you have 32-bit.

When installing this driver, too, make sure you don't just 'sudo' it, but run 'sudo -i' first and then make/make install.

Hope this helps!

---

