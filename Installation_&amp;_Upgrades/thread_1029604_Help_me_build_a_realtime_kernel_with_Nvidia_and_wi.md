---
title: "Help me build a realtime kernel with Nvidia and wireless supoort"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by wendallsan on 2009-01-03
I'm trying to build a realtime kernel that will support my Nvidia card and wireless.  Here's my process so far:

working as root in /usr/src directory (sudo -s).

created folder 'linux', cd into folder.

got new copy of source for 2.6.24 ([http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.24.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.24.tar.bz2)).  unzipped in linux directory, so there is now a linux-2.6.24 directory

got patch for 2.6.24.7 ([http://www.kernel.org/pub/linux/kernel/v2.6/patch-2.6.24.7.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/patch-2.6.24.7.bz2)) and rt patch for 2.6.24.7 ([http://www.kernel.org/pub/linux/kernel/projects/rt/patch-2.6.24.7-rt25.bz2](http://www.kernel.org/pub/linux/kernel/projects/rt/patch-2.6.24.7-rt25.bz2)). These go into /usr/src/linux directory.

patch by going into linux-2.6.24 directory and running:

bzcat ../patch-2.6.24.7.bz2 | patch -p1

did the same with the rt patch:

bzcat ../patch-2.6.24.7-rt25.bz2 | patch -p1

imported current kernel config:

cp /boot/config-$(uname -r) .config && yes "" | make oldconfig

ran make xconfig, saved new .config file without making any changes in xconfig

ran make-kpkg clean

ran CONCURRENCY_LEVEL=3 make-kpkg --initrd --revision=linux-2.6.24.7-rt25.10.00.Custom kernel_image kernel_headers modules_image

this created the linux and headers debian packages.

installed the deb packages:

dpkg -i linux-image-2.6.17.14-ubuntu1-custom_2.6.17.14-ubuntu1-custom-10.00.Custom_i386.deb

dpkg -i linux-headers-2.6.17.14-ubuntu1-custom_2.6.17.14-ubuntu1-custom-10.00.Custom_i386.deb

problems: 

xserver had to be manually set up on boot-- didn't recognize video card, running generic vesa drive, so no Compiz, etc.

no wifi

What can I do to get my Nvidia and wifi working again with this new kernel?  This is my 1st attempt at building my own kernel, so if I'm doing something horribly wrong here, please point it out.

Any help is greatly appreciated!

---

### Post by logos34 on 2009-01-03
video was the wall I ran up against when I tried to compile my own kernel about 6 months ago...Never could get the nvidia 177.- graphics driver to install against the headers

---

### Post by wendallsan on 2009-01-03
Hmm, how about the wifi?  That is what I really need to get working.  I can live without a cube desktop and floppy windows if I need to-- I can always boot into the regular kernel if I have company and want to show off.

thanks!

---

### Post by wendallsan on 2009-01-04
Hi all, I was able to figure this out.

Followed instruction on post 15 of this thread: [http://ubuntuforums.org/showthread.php?p=6240366](http://ubuntuforums.org/showthread.php?p=6240366).

basically downloaded the madwifi drivers, compiled them, then ran modprobe to load them up.  Works great!

Now I notice that I have no audio devices available to me in this new kernel, and the whole point is to build an audio workstation.  I'm closing this thread and starting another to address that problem.  Thanks!

---

### Post by logos34 on 2009-01-04
one of my my attempts ended the same way--no sound.  Put in the wrong snd- module (duh!)

---

