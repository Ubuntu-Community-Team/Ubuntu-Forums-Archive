---
title: "Compiling ubuntu"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by omzatru on 2009-02-04
Hi all,

I am trying to compile Ubuntu with some specials changes on menuconfig, I clone it from the repository, with:

git clone  git://kernel.ubuntu.com/ubuntu/ubuntu-hardy.git

then I create a branch on the tag:
git checkout -b Ubuntu-2.6.24-22.44 Ubuntu-2.6.24-22.44

and do the following instruction, to compile:

 make-kpkg -initrd -revision=2.6.24-22.44 kernel-image kernel-headers modules_image

And i got the following log:

create_md5sums_fn () { cd $1 ; find . -type f ! -regex '.*/DEBIAN/.*' ! -regex './etc/.*'      ! -regex '.*lib/modules/[^/]*/modules\..*' -printf '%P\0' | xargs -r0 md5sum > DEBIAN/md5sums ; if [ -z "DEBIAN/md5sums" ] ; then rm -f "DEBIAN/md5sums" ; fi ; } ; create_md5sums_fn              /usr/src/ubuntu-hardy/debian/linux-image-2.6.24.3
chmod -R og=rX                 /usr/src/ubuntu-hardy/debian/linux-image-2.6.24.3
chown -R root:root             /usr/src/ubuntu-hardy/debian/linux-image-2.6.24.3
dpkg --build                   /usr/src/ubuntu-hardy/debian/linux-image-2.6.24.3 ..
dpkg-deb: building package `linux-image-2.6.24.3' in `../linux-image-2.6.24.3_2.6.24-22.44_i386.deb'.
dpkg-deb: control directory has bad permissions 2755 (must be >=0755 and <=0775)
make[1]: *** [debian/linux-image-2.6.24.3] Error 2
make[1]: Leaving directory `/usr/src/ubuntu-hardy'
make: *** [binary/linux-image-2.6.24.3] Error 2


Does any one can help me with this, I am very stock with this, 

thanks for you help and time

Diego - [email]omzatru@gmail.com[/email] -

---

