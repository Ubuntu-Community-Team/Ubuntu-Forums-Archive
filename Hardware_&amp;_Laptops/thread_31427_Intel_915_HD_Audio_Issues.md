---
title: "Intel 915 HD Audio Issues"
date: 2005-05-03
forum: Hardware &amp; Laptops
---

### Post by Hardy on 2005-05-03
Hello, I'm a recent Linux convert and I must say I'm really happy with my system so far, I have equivilants and some times improvments over the applications I was using before and and through the wonders of Cedega I can play all the games I played under windows.

Except for one thing... sound. 

After following the advice at [http://www.ubuntulinux.org/wiki/HdaIntelSoundHowto](http://www.ubuntulinux.org/wiki/HdaIntelSoundHowto) i managed to compile and install the newest version of ALSA for my onboard HD Audio but when it comes to running alsaconf my audio device is not detected and I'm back where I'm started. My suspicions point me towards thinking that when running "make install" it is not overwiriting anything as there are many lines which claim nothing needed to be done etc, this should not be the case as I am installing 1.0.9rc3 which I had not installed before.

I hope there is a way to fix this because games without sound and a complete and utter lack of music are starting to get to me and eventually I'll have to retreat back to windows... I hope someone can help here, I must be doing something wrong and I feel like I'm banging my head against a wall.

Thanks In Advance
Ben

---

### Post by Hardy on 2005-05-03
C'mon guys, I really need some help with this...  ](*,)

---

### Post by gasolio on 2005-05-04
verify if modules snd-hda-intel.ko is in /lib/modules/2.6.***/kernel/sound/pci/hda/.
If it's right load it manually "sudo modprobe snd-hda-intel.

sorry for my bad english.

---

### Post by Hardy on 2005-05-05
I'm afraid this doesn't work :(
I tried copying the file there from the alsa installation files but I still could not make it install, it returned the following error "FATAL: Module snd_hda_intel not found."

I'm starting to get abit ansty that's all :(

---

### Post by fackamato on 2005-05-05
[QUOTE=Hardy]I'm afraid this doesn't work :(
I tried copying the file there from the alsa installation files but I still could not make it install, it returned the following error "FATAL: Module snd_hda_intel not found."

I'm starting to get abit ansty that's all :([/QUOTE]

Go to the dir woth the module (.ko), do sudo insmod the_file.ko .

---

### Post by Hardy on 2005-05-05
Still more pain :(

"insmod: error inserting 'snd-hda-intel.ko': -1 Unknown symbol in module"

---

### Post by gasolio on 2005-05-05
have you installed the linux-header (or source)  with the same version of your kernel ?

---

### Post by gasolio on 2005-05-05
Another tip's : run ./configure --with-build=/dir/kernel/source/_or_header

---

### Post by Hardy on 2005-05-06
Well, I've now installed the kernel sources and made a symlink to /usr/src/linux as is required except the alsa-drivers configure script still reports "checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist." The rest of the source is there I just seem to me missing the version.h file which is very strange...

Any chance of someone just sending me theirs, I've got linux-source-2.6.11

Thanks.

---

