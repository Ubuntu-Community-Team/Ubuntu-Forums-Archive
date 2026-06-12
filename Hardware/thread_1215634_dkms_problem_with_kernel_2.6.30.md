---
title: "dkms problem with kernel 2.6.30"
date: 2009-07-17
forum: Hardware
---

### Post by iamkrazee on 2009-07-17
I have an hp pavilion dv5 series laptop, with ati hd 3450 graphics, 512m dedicated memory.

I have a problem with my sound card, that it won't play sound through it's own speakers. So i figured I need to install a new kernel, which I did.

Inherently I installed the latest graphic drivers(8.62), from the amd website as well as the ones from the standard repo(8.60). I tried to build the drivers for both kernels with :
```
sudo dkms build -m fglrx -v 8.600 -k 2.6.28-11-generic
```
```
sudo dkms install -m fglrx -v 8.600 -k 2.6.28-11-generic
```

This works.

```
sudo dkms build -m fglrx -v 8.62 -k 2.6.28-11-generic
```

This gives the following error :
```

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
pushd /var/lib/dkms/fglrx/8.62/build; sh make.sh --nohints; popd....

Error!  Build of fglrx.ko failed for: 2.6.28-11-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.62/build/ for more information.

```

Now, it gets weirder, when I try to build the dkms for 2.6.30
```
sudo dkms build -m fglrx -v 8.600 -k 2.6.30-020630-generic
```
output:```

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
pushd /var/lib/dkms/fglrx/8.600/build; sh make.sh --nohints --uname_r=2.6.30-020630-generic; popd....

Error!  Build of fglrx.ko failed for: 2.6.30-020630-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.600/build/ for more information.

```

and for 6.2
```
sudo dkms build -m fglrx -v 8.62 -k 2.6.30-020630-generic
```
output is : 
```

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
pushd /var/lib/dkms/fglrx/8.62/build; sh make.sh --nohints; popd....

Error!  Build of fglrx.ko failed for: 2.6.30-020630-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.62/build/ for more information.
```

Help in any form will be more than appreciated.

P.S. : I use KDE and I need 3d effects. System-settings cannot enable the 3d effects under the 2.6.30 kernel.

---

### Post by iamkrazee on 2009-07-17
```
cat /var/lib/dkms/fglrx/8.62/build/make.log
DKMS make.log for fglrx-8.62 for kernel 2.6.30-020630-generic (x86_64)
Fri Jul 17 21:44:49 IST 2009
/var/lib/dkms/fglrx/8.62/build
```

```
cat /var/lib/dkms/fglrx/8.600/build/make.log
DKMS make.log for fglrx-8.600 for kernel 2.6.30-020630-generic (x86_64)
Fri Jul 17 21:41:04 IST 2009
/var/lib/dkms/fglrx/8.600/build
```

---

### Post by Alexis Phoenix on 2009-11-16
*bump*
I am having the same problem:
```
sudo dkms build --config /boot/config-2.6.31.6-mycomputer-2 -m fglrx -v 8.593

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
pushd /var/lib/dkms/fglrx/8.593/build; sh make.sh --nohints --uname_r=2.6.31.6-mycomputer-2; popd....

Error!  Build of fglrx.ko failed for: 2.6.31.6-mycomputer-2 (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.593/build/ for more information.
```
make.log is totally useless.
Any progress with this?  Solutions?
Hmm, just re-read your post.  Looks like there's a newer fglrx than I got last night!
Cheers,
Alexis

---

