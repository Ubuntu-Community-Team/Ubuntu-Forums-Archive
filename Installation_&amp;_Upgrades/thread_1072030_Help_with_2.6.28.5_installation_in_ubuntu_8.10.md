---
title: "Help with 2.6.28.5 installation in ubuntu 8.10"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by KuroYoma on 2009-02-17
I have tried 3 different ways today and everytime I get the same error.

```
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28.5.postinst line 1181.
dpkg: error processing linux-image-2.6.28.5 (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.28.5

```

I get this error after the grub update of the kernel install.  I first downloaded the full 2.6.28.5 kernel, configured and compiled it.  Failure.
Then I tried downloading the 2.6.28 version and applying the patch-2.8.26.5 and then configured and compiled.  Failure.

Everytime I get this error.  Anyone think they might know whats going on.

I have a dell latitude 120l With a broadcom wireless card and Ubuntu 8.10 installed.

---

### Post by KuroYoma on 2009-02-17
Bump Plz Help

---

### Post by KuroYoma on 2009-02-18
I have still been trying and can't seem to get it right.  Any suggestions would be greatly appreciated.

---

### Post by KuroYoma on 2009-02-19
OK, well here is an update. I went ahead and tried a different version.  I downloaded 2.6.28.1 and unpacked it. configured it, compiled it, and installed it but once again I got this error.
```
 dpkg -i linux-image-2.6.28.1_Kuro5_i386.deb 
Selecting previously deselected package linux-image-2.6.28.1.
(Reading database ... 156847 files and directories currently installed.)
Unpacking linux-image-2.6.28.1 (from linux-image-2.6.28.1_Kuro5_i386.deb) ...
Done.
Setting up linux-image-2.6.28.1 (Kuro5) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.28.1
Found kernel: /vmlinuz-2.6.27-12-generic
Found kernel: /vmlinuz-2.6.27-11-generic
Found kernel: /vmlinuz-2.6.27-7-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28.1.postinst line 1181.
dpkg: error processing linux-image-2.6.28.1 (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.28.1

```

I can't seem to figure out what is going on.  I spent 2 hours on the configuring of this kernel and went through every option researched my laptop and eliminated what I didn't need. I Have nothing nvidia in my laptop or in my configuration yet as far as I can tell thats what is going wrong.  I tried to install the nvidia-common package but to no availe.  I would really like someones help with this.

This is my /etc/kernel/postinst.d/nvidia-common file content:
```
#!/bin/bash -e
. /usr/share/debconf/confmodule
db_set nvidia-common/obsolete-driver false
db_input high nvidia-common/obsolete-driver || true

if [ -x /usr/bin/nvidia-detector ]; then
    LATEST=$(nvidia-detector)
    if [ ${LATEST} != "none" ]; then
        db_fset nvidia-common/obsolete-driver seen false
        db_subst nvidia-common/obsolete-driver latest $LATEST
        db_input high nvidia-common/obsolete-driver || true
        db_go || true
    fi
fi

```

---

### Post by xanderp123 on 2009-02-19
I have been having the same problem while trying to install a custom kernel.

*Uninstalling* nvidia-common seemed to work for me though.

```
$ sudo apt-get autoremove --purge nvidia-common
```

More info:
[http://packages.ubuntu.com/intrepid/nvidia-common](http://packages.ubuntu.com/intrepid/nvidia-common)
[https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/303795](https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/303795)

---

### Post by xanderp123 on 2009-02-19
I'm not sure how important the nvidia-common package is... it may be a good idea to reinstall it after installing your kernel. (It is probably more important for someone with nVidia hardware).

---

### Post by KuroYoma on 2009-02-19
Ok.  The installation process was going to the /etc/kernel/postinst.d/  folder and going through the files there before installation.  So I removed nvidia-common from the folder and the installation went great.  I don't have anything nvidia in my laptop so I know I don't need it.  For now its only 3 seconds but I shaved that much off my boot up.  Next I am going to implement ext4fs and see if that does anything.

---

### Post by slacker1965 on 2009-03-04
FWIW, I had the same problem compiling the 2.6.27.10 kernel in ubuntu 8.10:

[INDENT]...
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28.1.postinst line 1181.
dpkg: error processing linux-image-2.6.28.1 (--install):
 subprocess post-installation script returned error exit status 2
...
[/INDENT]

I had encountered this before, and I have a Nvidia graphics card, but everything worked.  All I did was ignore the above and continue with the instructions from [http://beginlinux.wordpress.com/2008/12/03/how-to-compile-an-ubuntu-810-kernel/]("http://beginlinux.wordpress.com/2008/12/03/how-to-compile-an-ubuntu-810-kernel/").  I had issues with my custom GRUB, but I worked those out and I'm booting the new kernel now with no apparent problems.

In many respects I still consider myself a newbie, but hope someone finds this helpful...

---

### Post by chuckmoney on 2010-02-24
Well...not trying to revive a dead thread here but I had a little piece of input for any who have a similar issue.

I compiled a custom kernel based on the official ubuntu kernel with only 2 changes.  First, core 2 duo processor type.  Second, preemptive kernel for low-latency desktop.  Otherwise, mine is identical to the official current, and I followed the ubuntu wiki page for customkernel to do this.  I encountered the same error on 9.10, yet the kernel would still boot and run...but it's really annoying seeing EVERY apt throw an error.

So, in an effort to stop the errors (and also to stop re-installing the otherwise perfectly working kernel every time I'm trying to install or remove a program) I moved /etc/kernel/postinst.d/nvidia-common to /root and ran apt-get (installed the wine1.2 package, which works fine.)  I do have an nvidia card and I'm trying to get WoW to work, so nvidia support is needed.  However, even without the file there, apt throws a very similar error and still fails.  For now I'm moving it back and I'm probably just going to manually edit the apt DB directly and make it forget the package is even there.

But just so people know, moving or removing this file, whether you have an nvidia card or not, does NOT fix the issue.  apt still fails and remains broken.

---

