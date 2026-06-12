---
title: "the nvidia's software problem"
date: 2009-09-11
forum: Hardware
---

### Post by fanglinyong on 2009-09-11
hello, everybody, yesterday ,i installed the new kernel2.6.31 which was build by myself, and i found that my sound card din't work! and then i download the new kernel by *.deb from the kernel.org ! after i installed it, my sound card can work, but i can't install my nvidia sofrware, when i go to the text model, and ```
sudo ./NV***.bin
```,the output  infomation said that i din't install the kernel-source!
but i am sure that i installed my kernel ,the kernel version is 2.6.31,look at the following pic!

---

### Post by hal10000 on 2009-09-11
> the output infomation said that i din't install the kernel-source
This looks as if something in your /usr/src directory is not as it's used to be.

Could it be that by some reason the link /usr/src/linux points to a wrong directory?
To verify your currently booted kernel type
[COLOR="Red"]uname -r[/COLOR] and post the output here.
You also should post the output of 
[COLOR="Red"]ls -ld /usr/src/*[/COLOR] to verify wether the appropriate directories and links are correctly set up

---

### Post by fanglinyong on 2009-09-12
> **hal10000 said:**
> This looks as if something in your /usr/src directory is not as it's used to be.

Could it be that by some reason the link /usr/src/linux points to a wrong directory?
To verify your currently booted kernel type
[COLOR=Red]uname -r[/COLOR] and post the output here.
You also should post the output of 
[COLOR=Red]ls -ld /usr/src/*[/COLOR] to verify wether the appropriate directories and links are correctly set up
first, thanks your help!
after i post this thread, i reinstalled my kernel which i download from the kernel.org network!
then i found that i din't install linux-headers file! after i reinstall the package , i found that my nv-software install success!
at last, thank  you very much!

---

### Post by hal10000 on 2009-09-12
> i found that my nv-software install success!
Great!!!!

But i just ask myself why you needed to install the linux-headers package if you compiled your own kernel, because if you compiled your own kernel, the needed header-files would usually resist inside the linux-sources directory.

---

### Post by fanglinyong on 2009-09-13
> **hal10000 said:**
> Great!!!!
 
But i just ask myself why you needed to install the linux-headers package if you compiled your own kernel, because if you compiled your own kernel, the needed header-files would usually resist inside the linux-sources directory.
 well, when i first build the kernel for myself ,and after i installed the kernel , i found that my sound card and apparmor modules didn't work! so i download the the deb packages from the kernel.org network,after i installed the deb packages ,i found that all the problems which i mentioned above were all soloved!
the one question is how to build my kernel!and when i build my kernel package ,what shall i do ,and what shall i pay attention to !

---

### Post by hal10000 on 2009-09-13
> the one question is how to build my kernel!and when i build my kernel package ,what shall i do ,and what shall i pay attention to !

The Master kernel thread is what you want: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

