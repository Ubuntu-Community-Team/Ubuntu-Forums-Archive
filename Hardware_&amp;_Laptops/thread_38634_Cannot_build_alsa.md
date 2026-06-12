---
title: "Cannot build alsa"
date: 2005-06-01
forum: Hardware &amp; Laptops
---

### Post by fastluck on 2005-06-01
After several times running the .configure script and failed, I installed the linux kernel sources and headers using synaptic. In my case, it was 2.6.10. Then I opened a terminal, typed

cd /usr/src

and typed

ln -s linux-source-2.6.10
cd alsa/alsa-driver*

./configure --with-cards=hda-intel

Finally got a successful result from .configure.  Good.

Then I typed

make

That failed, because it couldn't find the .config file. So I looked in boot for config files. There were two:

config-2.6.10-5-386
config-2.6.10-5-686

I typed:

cp /boot/config-2.6.10-5-686 /usr/src/linux-source-2.6.10/.config

...went back into the alsa drivers directory (for me, that's /usr/src/alsa/alsa-driver-1.0.9rc4a

...and typed
make

That failed. I got:

/bin/sh: scripts/basic/fixdep: No such file or directory.

Any takers?

---

### Post by tread on 2005-06-01
I think (and I am not completely sure, however, what I am saying cannot harm you :)) that you have to go through the first steps of a kernel install.

go to the kernel source,
type "make menuconfig" or make xconfig
save the config file for the kernel
type "make dep"

---

### Post by fastluck on 2005-06-01
Thanks--That makes sense.  But make dep is "no longer needed."  I can't think of how I can get it to build those things without typing make.  As long as I don't type 'make install', I'm not going to overwrite anything important, right?

---

### Post by tread on 2005-06-01
yup make should just compile everything .. jeez its been ages since I compiled a kernel :(

---

### Post by fastluck on 2005-06-01
I'm trying it now.

Thanks

---

### Post by fastluck on 2005-06-01
That worked--drivers compiled.

---

