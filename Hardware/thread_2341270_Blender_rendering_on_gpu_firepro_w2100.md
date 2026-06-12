---
title: "Blender rendering on gpu firepro w2100"
date: 2016-10-26
forum: Hardware
---

### Post by boneywigs on 2016-10-26
Hi,

I have a firepro w2100 graphics card and it is in the spec for running blender but I can't get blender see it.  There is no option to select the GPU in user preferences->system->compute device  only CPU.  I have read about opencl and cuda but am confused to what I need to do/install to get it to work.  I think it's an AMD but not sure, I am quite new to Blender and just getting used to Ubuntu/Linux and I like it a lot, I would like to learn more.  Any reference to stuff to read or advice on how to get it working would be great   

Thank you

---

### Post by boneywigs on 2016-10-30
Ok so here's what I've tried so far.  learnt that Blender doesn't like the pen source driver xorg so I checked that my graphics card is an AMD and installed the drivers from here [http://support.amd.com/en-us/download/workstation/previous/detail?os=Linux+x86_64&rev=15.302.2301](http://support.amd.com/en-us/download/workstation/previous/detail?os=Linux+x86_64&rev=15.302.2301) but whilst install it says an warning about firmware not install, I can't remember the exact warning without installing it again.  As it was a warning I ignored it.  On reboot my system Ubuntu 16.04 kernel 4.4 went into low graphics mode and the only way I could get it to start again was if I removed the driver with sudo apt-get remove fglrx-core.   

So I still can't get Blender to render on the GPU although it renders ok on the CPU so I guess I will just give up and just use CPU rendering unless any one can help?

Thanks

---

### Post by boneywigs on 2016-10-30
It's extremely slow though :confused:

---

