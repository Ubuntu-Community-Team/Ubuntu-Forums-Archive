---
title: "Building nvidia 6629 module"
date: 2005-01-24
forum: Hardware &amp; Laptops
---

### Post by pseudonym on 2005-01-24
Hi. I'm following advice originally posted in this thread - 

[http://www.ubuntuforums.org/showthread.php?t=7635&page=3&pp=10](http://www.ubuntuforums.org/showthread.php?t=7635&page=3&pp=10)

I'm running the stock 2.6.8.1-4-k7 kernel and getting the same kinds of errors when trying to install the 6629 binary package from nvidia's website-

ERROR: Unable to load the kernel module 'nvidia.ko'. This is most likely
because the kernel module was built using the wrong kernel source files.
Please make sure you have installed the kernel source files for your
kernel; on Red Hat Linux systems, for example, be sure you have the
'kernel-source' rpm installed. If you know the correct kernel source
files are installed, you may specify the kernel source path with the
'--kernel-source-path' commandline option.  

As I understand it, the work involved in getting this driver to install is to configure your kernel correctly so that the new nvidia module can be built, rather than having to recompile the whole kernel, right?. I've never done this before so can someone please verify that I'm doing it correctly?

Here's what I have planned-

1. I've installed the following packages:

nvidia-kernel-source 1.0.6629-0ubuntu7 (from repository [http://people.ubuntu.com/~daniels/l-r-m/i386/](http://people.ubuntu.com/~daniels/l-r-m/i386/) )
linux-headers-2.6.8.1-4-k7
linux-source-2.6.8.1 (still tarred, not sure if this is required)
gcc
libncurses5-dev
build-essential
bin86

I noticed that the version of nvidia-kernel-common I have relates to the 6111 driver. Is this a problem? Or perhaps it's something that gets updated as a result of the new build?

2. Untar /usr/src/nvidia-kernel-source.tar.gz

3. Run make menuconfig

4. Run make KSRC=/usr/src/linux-headers-2.6.8.1-4-k7 in the directory created by untarring nvidia-kernel-source.

5. Run the nvidia 6629 package (pointing it to the new kernel source path if it asks me too) and cross my fingers. :)

Assuming this works, is there anything you need to after the new driver is installed (other than updating XF86Config-4 as needed and maybe /etc/modules), such as run nvidia-glx-config enable?

I know I can update to nvidia 6629 if I do a dist-upgrade, but I'd prefer not to make *too* many changes to my otherwise stable Warty system.

As you can see, I'm no expert. So any help will be greatly appreciated! :)

Thanks in advance.

---

### Post by pseudonym on 2005-01-25
Can anyone help? Don't mean to be pushy, but I really need to get this driver installed. No doubt lots of others might want the help too :) Thanks!

---

### Post by pseudonym on 2005-01-26
Problem solved! I just followed these instructions -

[http://www.uberdose.com/kbase/ubuntu-and-nvidia-geforce-6600/](http://www.uberdose.com/kbase/ubuntu-and-nvidia-geforce-6600/) 

, although I don't have a 6600, just a Ti4400 (which still does a great job).

Strange, though, I did the essential part of what this guy says (which is also duplicated in one or two threads here), and it didn't work the first time. Was getting the 'no kernel source' error and the new driver wouldn't compile.

But it has now so I can start fraggin'! Yippee! :)

---

