---
title: "Need help compiling Kernel 2.6.32"
date: 2010-06-03
forum: Hardware
---

### Post by K. Hendrik on 2010-06-03
Irecently bought a new Laptop (Sony Vaio VPCS11C5E) and I'm trying to compile a patched Kernel for it. The Patches are needed for the Internal Mic (see [http://code.google.com/p/vaio-f11-linux/wiki/EnableMicrophone]("http://code.google.com/p/vaio-f11-linux/wiki/EnableMicrophone")) and for the 3G-Modem (see [http://www.codon.org.uk/~mjg59/gobi_loader/kernel_patches/]("http://www.codon.org.uk/~mjg59/gobi_loader/kernel_patches/")).What I've done so far is this:

```

sudo apt-get install linux-source

mkdir ~/src
cd ~/src
tar xjvf /usr/src/linux-source-2.6.32.tar.bz2
cd linux-source-2.6.32

patch -p1 < /home/kai/src/enable-internal-microphone.patch
patch -p1 < /home/kai/src/usb-wwan-2.6.32.diff

cp -vi /boot/config-`uname -r` .config

make oldconfig

make menuconfig

export CONCURRENCY_LEVEL=3
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-some-string-here kernel-image kernel-headers

```

After this I installed the header and image Deb-Files and rebooted, but i only get a blank screen and the Num-Lock and Casp-Lock LED's keep blinking.

System Specs:
Ubuntu 10.04 64-Bit
NVIDIA Geforce 310M 512MB
Intel Core i5 M520 @ 2.40GHz
Quallcomm Gobi 2000


I really hope someone can help me get this working.

---

### Post by K. Hendrik on 2010-06-03
Nobody any Idea?

---

### Post by dino99 on 2010-06-03
have you seen this:

[http://www.backports.ubuntuforums.org/showthread.php?p=8927809](http://www.backports.ubuntuforums.org/showthread.php?p=8927809)

or try : [https://launchpad.net/~ricotz/+archive/unstable](https://launchpad.net/~ricotz/+archive/unstable)

---

### Post by K. Hendrik on 2010-06-03
Yes, I've seen that it enables sound output but the mic won't work because the current driver for the sound Card ALC275 is based on the ALC269 Driver which is a little different in structure a few pins are changed, the pins for the mic, which get corrected in the enable-internal-microphone.patch.

---

### Post by K. Hendrik on 2010-06-03
Bump, really need help...

---

