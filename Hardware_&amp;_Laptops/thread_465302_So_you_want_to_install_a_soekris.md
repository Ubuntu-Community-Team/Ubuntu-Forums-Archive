---
title: "So you want to install a soekris"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by t4thfavor on 2007-06-05
I got a soekris net4801 the other day, and was looking through tutorials on how to install bsd, linux, etc. It turned out that it would be an utter nightmare involving compiling kernels, and all the kind of crap I don't want to deal with. So after a few failed attempts, I moved over to the ubuntu site and downloaded the 7.04 server iso. I set up my PXE environment, booted with PXELinux, and am now installing away. 

I am at about 70% installed ATM, and will post back with more details if anyone is interested.

---

### Post by t4thfavor on 2007-06-06
Since nobody obviously cares about this, I am still going to talk about it.
I need to install the I386 kernel to my local repository, so that I can get it on the soekris box, the kernels that come on the default server cd don't seem to work for this box.

If anyone can tell me which file happens to be the I386 kernel I need it would be greatly appreciated.

I have the file called 
"linux-ubuntu-modules-2.6.22-6-386_2.6.22-6.11_i386.deb"

---

### Post by Nebulus on 2007-07-10
Hi
I am thinking of buying a Soekris as well but not experienced enough to recompile n' stuff.

Anybody had luck with doing a standard install of Ubuntu Server on the new Soekris 5501?
(with harddisk).

---

### Post by derjoerg on 2007-08-26
Actually I get it to work, find my descriptions in the ubuntu-wiki
[https://wiki.ubuntu.com/Soekris](https://wiki.ubuntu.com/Soekris)

Regards

Joerg Schoppet

---

### Post by baberone on 2008-05-27
Hi All, 

I've also successfully installed Ubuntu on a Soekris (net5501). I didn't use PXE but with chroot on another ubuntu...

Since a couple of days I'm trying to recompile the kernel. I encountered some space issues (recompiling everything takes ages and will fail, because not enough space :( even with 4GB CF. I know I could mount an external drive but ...

I want to remove all unnecesserary modules and make a tailored  soekris net5501 kernel ! 

but there are too many options in that menuconfig :)

Did someone already tried to do the same ? I've attached a draft .config file. Any ideas/suggestions/comments are welcome.

---

### Post by baberone on 2008-05-29
Just for information...

The recompilation went fine, but booting didn't work. After trying to fix this, I started all over again with an external harddisk. To do so, just append o=/path/output to the make commando

So, basicly here are the steps:

1. Get Kernel Sources

```

cd /usr/src
wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.25.4.tar.gz
tar xvf linux-2.6.25.4.tar.gz
cd linux-2.6.25.4/

```

2. Copy wanted .config file if any

```
cp /home/username/.config.final ./.config
```

3. Check config (needed, because additional config parameters could be missing in .config file) and make it (echo -e '\a' command makes terminal beep when finished.. can be handy on a Soekris :) )

```

make menuconfig
make o=/usr/src/linux_src_ext/ubuntu_kernel_build && /bin/echo -e '\a'
```

Afterwards usual steps to install the new kernel (make install and change /boot/grub/menu.lst). It's also possible to make kernel packages with make-kpkg (check [this]("http://www.howtoforge.com/kernel_compilation_ubuntu") at howtoforge dot com)

---

### Post by t4thfavor on 2008-06-27
> **t4thfavor said:**
> I got a soekris net4801 the other day, and was looking through tutorials on how to install bsd, linux, etc. It turned out that it would be an utter nightmare involving compiling kernels, and all the kind of crap I don't want to deal with. So after a few failed attempts, I moved over to the ubuntu site and downloaded the 7.04 server iso. I set up my PXE environment, booted with PXELinux, and am now installing away. 

I am at about 70% installed ATM, and will post back with more details if anyone is interested.

Sorry to leave the thread so long without answering back. I got the 7.04 installed, and it will boot, just not from a kernel located on the Soekris. So I had to boot from a PXE kernel, using the flash card as my root. Then I installed the standard I386 kernel which would then boot just fine. I no longer have the Soekris box (it was not mine in the first place) So I cant post the kernel version or specs. I will say however that I had the 256MB RAM one and it ran a bit slow for my liking. Though it still had enough guts to run phpadmin, and a bunch of other firewall related stuff.

---

