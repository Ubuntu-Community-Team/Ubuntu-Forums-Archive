---
title: "[SOLVED] Compiling a custom kernel using git fails"
date: 2008-10-16
forum: General Help
---

### Post by pdoes on 2008-10-16
I'm trying to build a custom kernel for 8.04 and set it up like the xen, rt kernels but it fails

Here are the steps I took:
```
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-hardy.git hardy
cd hardy
git checkout Ubuntu-2.6.24-21.42 -b mine
cp debian/binary-custom.d/xen debian/binary-custom.d/mine -r
cp /boot/<mycurrentconfig> .config
make menuconfig
made some changes in the kernel and saved it.
mv .config debian/binary-custom.d/mine/config.i386
rm debian/binary-custom.d/mine/patchset/*
vi debian/binary-custom.d/mine/rules Removed all lines except line 1
vi debian/binary-custom.d/mine/vars Changed the target and description.
CONCURRENCY_LEVEL=2 AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules custom-binary-mine
```

It then fails with the following error:
```
make ARCH=i386 EXTRAVERSION=-22-mine SUBLEVEL=24 -C /d1/packaging/kernel/hardy/debian/build/custom-source-mine O=/d1/packaging/kernel/hardy/debian/build/custom-build-mine silentoldconfig prepare scripts
make[1]: Entering directory `/d1/packaging/kernel/hardy/debian/build/custom-source-mine'
make[3]: Nothing to be done for `/d1/packaging/kernel/hardy/debian/build/custom-source-mine/Makefile'.
  Updating /d1/packaging/kernel/hardy/debian/build/custom-build-mine/scripts/Makefile.mine
  GEN     /d1/packaging/kernel/hardy/debian/build/custom-build-mine/Makefile
scripts/kconfig/conf -s arch/x86/Kconfig
  Using /d1/packaging/kernel/hardy/debian/build/custom-source-mine as source for kernel
  /d1/packaging/kernel/hardy/debian/build/custom-source-mine is not clean, please run 'make mrproper'
  in the '/d1/packaging/kernel/hardy/debian/build/custom-source-mine' directory.
make[4]: *** [prepare3] Error 1
make[3]: *** [sub-make] Error 2
make[2]: *** [prepare] Error 2
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/d1/packaging/kernel/hardy/debian/build/custom-source-mine'
make: *** [/d1/packaging/kernel/hardy/debian/stamps/stamp-custom-prepare-mine] Error 2
```

Any suggestions are welcome.
BTW I just tried tried the same steps with the xen, rt flavors and they fail as well.

Peter

---

### Post by pdoes on 2008-11-13
Ok I solved it myself, I even forgot I had this question posted. I needed to clean the directory properly.

If you want to compile your own kernel using git, I wrote down a step by step how to on my [blog]("http://blog.avirtualhome.com/2008/10/28/how-to-compile-a-custom-kernel-for-ubuntu-intrepid-using-git/")

---

