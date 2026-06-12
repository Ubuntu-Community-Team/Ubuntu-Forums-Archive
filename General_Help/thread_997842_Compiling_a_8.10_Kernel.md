---
title: "Compiling a 8.10 Kernel"
date: 2008-11-30
forum: General Help
---

### Post by ub007 on 2008-11-30
I'm trying to compile kernels on 8.10 ubuntu.Tried the following steps-

> # apt-get install kernel-package libncurses5-dev fakeroot wget bzip2

[COLOR="Red"]**# apt-get install linux-source**[/COLOR]

# cd /usr/src

# bzip2 -d linux-source-2.7.27.tar.bz2
# tar xvf linux-source-2.7.27.tar
# ln -s linux-source-2.7.27 linux

# cd linux

# cp /boot/config-`uname -r` ./.config

#make menuconfig

# make-kpkg clean

# fakeroot make-kpkg --initrd --append-to-version=-da1 kernel_image kernel_headers

# dpkg -i linux-image-2.6.27.2-da1_2.6.27.2-da1-10.00.Custom_i386.deb
# dpkg -i linux-headers-2.6.27.2-da1_2.6.27.2-da1-10.00.Custom_i386.deb

This works a charm!!!!!!!!!

However,when i tried to build a [COLOR="Red"]**generic kernel from kernel.org**[/COLOR],substituting the highlighted step with

wget [http://kernel,org/pub...v2.6/linux-2.6.26.19](http://kernel,org/pub...v2.6/linux-2.6.26.19) ,it fails...
I experimented with various versions,but all failed at the same step-fakeroot make-kpkg --initrd --append-to-version=-da1 kernel_image kernel_headers.

> #apt-get install kernel-package libncurses5-dev fakeroot wget bzip2

[COLOR="red"]**#wget [http://kernel,org/pub...v2.6/linux-2.6.26.19](http://kernel,org/pub...v2.6/linux-2.6.26.19)**[/COLOR] 

# cd /usr/src

# bzip2 -d linux-source-2.7.27.tar.bz2
# tar xvf linux-source-2.7.27.tar
# ln -s linux-source-2.7.27 linux

# cd linux

# cp /boot/config-`uname -r` ./.config

#make menuconfig

# make-kpkg clean

# fakeroot make-kpkg --initrd --append-to-version=-da1 kernel_image kernel_headers

Error


Any ideas???

---

### Post by Keyper7 on 2008-11-30
Could you please post **exactly** what you're doing?

The first set of commands doesn't make sense. There's no 2.7.27 kernel.

PS: it might take an entire day to check your reply to this, but I will

---

### Post by ub007 on 2008-12-02
> The first set of commands doesn't make sense. There's no 2.7.27 kernel.

Sorry there.That was a typo.

> # apt-get install linux-source

downloads the 2.6.27 kernel.

> # bzip2 -d linux-source-2.6.27.tar.bz2
# tar xvf linux-source-2.6.27.tar
# ln -s linux-source-2.6.27 linux

I do not know how the typo creeped in,the latest kernel version is 2.6 in kernel.org.I was wondering how on earth it downloaded 2.7(This is my first experience with ubuntu 8.10 & thought mayb it downloaded a development-odd version kernel).Anyways I double checked with a re-install and its 2.6.The rest of the steps are exacly as in my first post.

>  it might take an entire day to check your reply to this
Totally agree,I'm patient and thanks for offering support

---

### Post by Keyper7 on 2008-12-02
Actually, there's no such thing as a 2.7 kernel series, not even a development version. The latest, bleeding edge ones are always 2.6.*.

Anyway, I'll start with an obvious question: are you moving the tar.bz2 file to /usr/src after downloading it with wget?

---

### Post by ub007 on 2008-12-02
Yes,I moved the tar.bz2 file to /usr/src after downloading...

---

### Post by Keyper7 on 2008-12-03
So what exactly is the error you get when you try the last step?

---

