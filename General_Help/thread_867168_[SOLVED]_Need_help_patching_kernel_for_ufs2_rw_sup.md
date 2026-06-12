---
title: "[SOLVED] Need help patching kernel for ufs2 r/w support"
date: 2008-07-22
forum: General Help
---

### Post by flaggh on 2008-07-22
I came across a blog entry about patching the kernel to include write support for ufs2:
[http://hawking.nonlogic.org/archives/2007/04/06/ufs2_write_support_for_linux/]("http://hawking.nonlogic.org/archives/2007/04/06/ufs2_write_support_for_linux/")

How do I patch the kernel to include this feature?  Just looking at the patch I can tell that it patches files that I do not appear to have in my /usr/src/linux-headers directory.  Thanks in advance for any help.

---

### Post by Tim Sharitt on 2008-07-22
Those patches are for the kernel source. However, ufs2 r/w support is already in the current kernel (2.6.26).

---

### Post by flaggh on 2008-07-22
Thanks for the info.  I did not know that.  I'm running 2.6.22 on my machine.  I guess its time to upgrade.

---

### Post by Habbit on 2008-07-22
Hardy runs on a 2.6.24 kernel, and as a LTS release, upgrades are not likely. Though there have been talks of moving to 2.6.25, the .26 version brings "many" changes and refactorings, so they would definitely not move to it in a long term release. Maybe for 8.10...

---

### Post by flaggh on 2008-07-22
In that case, patching the current kernel may make the most sense.  How would I go about doing that?

---

### Post by Habbit on 2008-07-22
I don't really remember the process, but it was something like the following:
 * Install the "linux-source" package for your current kernel.
 * Unpack the tarball apt leaves on /usr/src on some directory you can access as your normal user (I'm assuming ~/linux)
 * Copy the "/boot/config-$(uname -r)" file to ~/linux/.config (the last part is the new file name, not a directory
 * On the kernel tree root (~/linux), run "make oldconfig". This step should not be required since the config file is for the same version you're configuring, but extra care is never wasted.
 * Patch and modify the kernel as you want.
 * Run "make menuconfig" and change the default "name" for the kernel (generic) for something you can later recognize
 * Build with "make && make modules_install"
 * The arch/x86/boot/bzImage file is the kernel image. Copy it to /boot
 * This is the part where my knowledge becomes flaky. You need to build a new initrd image for the new kernel, and maybe rebuild all out-of-kernel-tree modules like ndiswrapper with module-assistant

As this route might easily lead to a derailment, you might want to use the tried and useful Holy Way of Debian Kernelbuilding: install the "kernel-package" and "fakeroot" utils packages and thoroughly read through their man pages, particularly the one for make-kpkg. After it's run you'll have a nice .deb package for your new kernel instead of ugly you-manage-it files.

Safety note: always keep your old kernels around - things might not work out as you expect them to (Murphy's Law, you know)

---

### Post by Taxman415a on 2008-07-22
Installing a custom kernel does prevent you from getting much support in the future though. No one will know if your problems are due to that. You may want to set up a virtual machine like Virtualbox and test inside of that first.

---

### Post by flaggh on 2008-07-22
After downloading the latest kernel source code, I can see that the patch I have mentioned at the top has already been applied.  Why then is write support not enabled?  How do I enable it before recompiling?

---

### Post by flaggh on 2008-07-22
nevermind, I think I found the answer:
[http://geek00l.blogspot.com/2007/02/gentoo-mounting-ufs2.html]("http://geek00l.blogspot.com/2007/02/gentoo-mounting-ufs2.html")

I'll let you know how it goes.

---

### Post by flaggh on 2008-07-23
Everything seems to be working so far.  I've mounted the hard drive rw and I'm currently copying files to it.  I'll post if I experience any problems or data corruption.

---

### Post by tom.clements on 2008-10-29
Hi,

Now that Intrepid Ibex (with the 2.6.26 kernel which as noted above includes rw support for ufs2 - can someone confirm this?!) is with us is there anything special I need to do to get a ufs2 partition to mount with read / write access?

I can get it to mount successfully with read only access but if I change the 'ro' flag to 'rw' in fstab the mount fails.

Do I still need to take the steps mentioned above to recompile the kernel? If so does anyone have specific instructions to do this on ubuntu server as I'm a bit of a noob at this! 

Many thanks,

Tom.

---

