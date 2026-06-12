---
title: "where did my audio devices go with my new realtime kernel?"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by wendallsan on 2009-01-04
Hi all,

I'm trying to build an audio workstation out of my Ubuntu system, and have compiled a realtime version of the 26.6.24 kernel.  So far I can get it booted, can get X running and my wifi up, but now I've noticed that I don't appear to have any audio devices-- quite a problem for an audio workstation!

Here is the process I used to build my kernel:

working as root in /usr/src directory (sudo -s).

created folder 'linux', cd into folder.

got new copy of source for 2.6.24 ([http://www.kernel.org/pub/linux/kern...2.6.24.tar.bz2](http://www.kernel.org/pub/linux/kern...2.6.24.tar.bz2)). unzipped in linux directory, so there is now a linux-2.6.24 directory

got patch for 2.6.24.7 ([http://www.kernel.org/pub/linux/kern...h-2.6.24.7.bz2](http://www.kernel.org/pub/linux/kern...h-2.6.24.7.bz2)) and rt patch for 2.6.24.7 ([http://www.kernel.org/pub/linux/kern....24.7-rt25.bz2](http://www.kernel.org/pub/linux/kern....24.7-rt25.bz2)). These go into /usr/src/linux directory.

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

To fix my wifi drivers, I did this:

downloaded madwifi drivers ([http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.gz](http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.gz)) into /usr/src/madwifi

running as root, cd into madwifi directory, extract tar

cd into madwifi-0.9.4 directory

run make
run make install

start with modprobe (modprobe ath_pci)
added module to /etc/modules to load on boot

So now on to my audio problems.  Here is what I'm experiencing:

volume control icon by the clock on my Gnome desktop has a big red "X" on it.  Clicking on it, I get the message:

No volume control GStreamer plugins and/or devices found.

I have 2 sound cards, one is built in to my motherboard, which I could care less about, and the other is a M-Audio 2496 card.  That's the one I'd like to get running in this config.  Both worked great with my stock Ubuntu kernel.

Where should I start with this?  Any help is greatly appreciated.

---

