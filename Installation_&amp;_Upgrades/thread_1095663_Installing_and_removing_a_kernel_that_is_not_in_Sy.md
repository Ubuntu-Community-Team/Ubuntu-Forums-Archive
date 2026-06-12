---
title: "Installing and removing a kernel that is not in Synaptic"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by davidbilla on 2009-03-14
I tried installing kernel 2.6.27.7 in gutsy, but it didn't work. I get:

```
kernel panic-not syncing VFS:unable to mount root fs on unknown-block(0,0)
```

Is there any way to fix it or do I have to recompile the kernel? Or, if I want to remove this new kernel (which is not in synaptic, by the way), how do I go about doing it?

---

### Post by tommcd on 2009-03-14
Why are you trying to install kernel 2.6.27.7 in gutsy? Don't you think it would be easier, faster, and better to simply do a clean install of Ubuntu 8.10 which has 2.6.27-11 kernel?

How did you install the kernel? Did you compile it? Or did you download it from the Ubuntu repos somewhere?
To remove the kernel, simply search for it in your /boot directory, and in /usr/src directory. You should still have an option in your grub menu to boot the old kernel.
To compile a kernel in Ubuntu see this:
[http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way](http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way)

---

### Post by davidbilla on 2009-03-14
> **tommcd said:**
> Why are you trying to install kernel 2.6.27.7 in gutsy? Don't you think it would be easier, faster, and better to simply do a clean install of Ubuntu 8.10 which has 2.6.27-11 kernel?

How did you install the kernel? Did you compile it? Or did you download it from the Ubuntu repos somewhere?
To remove the kernel, simply search for it in your /boot directory, and in /usr/src directory. You should still have an option in your grub menu to boot the old kernel.
To compile a kernel in Ubuntu see this:
[http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way](http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way)


Hi, thanks for the reply. I'm now booting from the old kernel, by the way. The system is not mine and I cannot decide to do a clean install on it. But I need a compiled kernel to insert my own driver modules. I don't want to touch the running kernel. So I thought I'd download a vanilla kernel and compile it. I found somewhere in the web that people have had success with 2.6.27.7 (that's the latest kernel anyone had had success with as far as I can know) in gutsy. So I downloaded it and compiled it with the default options (except for unchecking 'tickless clock...' or some such option as was given in the howto), but it didn't work for me. 

Now I just want to confirm whether it will be enough if I just removed the files in /boot and /usr/src and made the necessary changes in menu.lst for the new kernel to disappear completely? Maybe I'll try my luck with another older kernel after removing this. (I'm also lobbying for a new install on that system anyway!)

---

### Post by davidbilla on 2009-03-16
Hey, any ideas?

If I do a clean format of gutsy and install, for example, hardy on it, will I be able to compile a new kernel with the default options chosen in 'make menuconfig'? All I need to do is to set the system up so that I'll be able to compile some driver modules.

---

