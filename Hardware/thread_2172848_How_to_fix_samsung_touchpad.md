---
title: "How to fix samsung touchpad"
date: 2013-09-06
forum: Hardware
---

### Post by joaov-ferreira on 2013-09-06
I spent most of my time last week searching for a solution to fix the multi-touch feature on my samsung RV411

My problem was that when I first installed ubuntu on my laptop, the trackpad didn't worked at all, but was recognised as ETPS/2 Elantech Touchpad.
I first found a "fix" to this problem that changed the loaded module for psmouse from elantech to a generic PS/2 mouse, using the comands
```

sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps
```

After this the trackpad worked as a simple mouse, whitout multi-finger support

Now I found that the newest kernel (3.11) had fixed this bug, and upgrading to this newer release (or build a custom one) will fix this issue

To upgrade the kernel first check the current kernel version with
```

uname -r
```

If you are using an older version, you can download the newest .deb packages from 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

then you need to check if your system is 32-bit or 64-bit, you can do that with
```
uname -m
```

x86_64 => 64 bit kernel
i686     => 32 bit kernel

then you must download the correspondent kernel packages, you need 3 files files, the two files with amd64 in the name for 64 bit system or the two files with i386 for 32 bit system and the file ended with all.deb

if you prefer, can use this command line codes
**32 bit:**
```

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-saucy/linux-headers-3.11.0-031100-generic_3.11.0-031100.201309021735_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-saucy/linux-headers-3.11.0-031100_3.11.0-031100.201309021735_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-saucy/linux-image-3.11.0-031100-generic_3.11.0-031100.201309021735_i386.deb
```

**64 bit :**
```

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-saucy/linux-headers-3.11.0-031100-generic_3.11.0-031100.201309021735_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-saucy/linux-headers-3.11.0-031100_3.11.0-031100.201309021735_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-saucy/linux-image-3.11.0-031100-generic_3.11.0-031100.201309021735_amd64.deb
```

to install the kernel use :
```

sudo dpkg -i linux-headers-3.11.0* linux-image-3.11.0*
```

then reboot yout system and you are good to go

I hope this help to avoid other people to look all over the internet for a fix to this issue :D

---

