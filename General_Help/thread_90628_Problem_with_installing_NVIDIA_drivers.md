---
title: "Problem with installing NVIDIA drivers"
date: 2005-11-15
forum: General Help
---

### Post by caspian on 2005-11-15
I followed these instructions to install the latest NVIDIA drivers:
[http://ubuntuforums.org/showthread.php?t=75074&highlight=latest+nvidia+drivers](http://ubuntuforums.org/showthread.php?t=75074&highlight=latest+nvidia+drivers)

Now, when I run the installer, I get this error message:
> 
ERROR: Unable to load the kernel module 'nvidia.ko'.  This is most likely
       because the kernel module was built using the wrong kernel source files.
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 Invalid module format


What am I doing wrong? I made sure to install the kernel source files... so I'm not sure what it's complaining about.

Thanks!

~Caspian

---

### Post by Kyral on 2005-11-15
The ones with Ubuntu work just fine (Version 7667 as opposed to Version 7676).

```
sudo apt-get install nvidia-glx
```
```
sudo nvidia-glx-config enable
```

Then restart X with CTRL+ALT+Backspace

---

