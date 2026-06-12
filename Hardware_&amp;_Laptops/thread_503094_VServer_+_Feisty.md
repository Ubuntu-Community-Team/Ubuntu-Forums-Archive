---
title: "VServer + Feisty"
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by insitu on 2007-07-17
Hello,
I am trying to create VServers on Feisty but so far have not managed to get anything useful. Maybe I did not understand the instructions on the community page about that topic...

If anybody has some more experience than me, its help would be greatly appreciated.

Insitu.

Here is a quite detailed account of what I did:

VServer is not directly supported on Feisty (see
[https://help.ubuntu.com/community/VServer](https://help.ubuntu.com/community/VServer)), I try to recompile a kernel with vserver patch applied. 

From [http://www.howtoforge.com/kernel_compilation_ubuntu:](http://www.howtoforge.com/kernel_compilation_ubuntu:) creates .deb
packages suitable for normal installation procedure. 

<example>
sudo apt-get install kernel-package libncurses5-dev fakeroot wget bzip2
su
cd /usr/src
wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.21.6.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.21.6.tar.bz2)
tar xjf linux-2.6.21.6.tar.bz2
wget [http://ftp.linux-vserver.org/pub/kernel/vs2.2/patch-2.6.21.6-vs2.2.0.1.diff](http://ftp.linux-vserver.org/pub/kernel/vs2.2/patch-2.6.21.6-vs2.2.0.1.diff)
cd linux-2.6.21.6
patch -p1 < ../patch-2.6.21.6-vs2.2.0.1.diff
make oldconfig
# reply with mostly defaults on NEW features
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-customvs kernel_image kernel_headers
</example>

This method does not work ! Last command hangs. I followed [http://linux-vserver.org/Installation_on_Ubuntu](http://linux-vserver.org/Installation_on_Ubuntu)

<example>
make install
make modules_install
mkinitramfs -o /boot/initrd.img-2.6.21.6-vs2.2.0.1-customvs 2.6.21.6-vs2.2.0.1-customvs
vi /boot/grub/menu.lst
</example>

This works but the compiled kernel is missing ipw3945 for wireless :(

*** Installing ipw3945

Followed instructions at [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/), first need
to donwload driver =ipw3945-linux-1.2.0.tgz= from Intel's site.

<example>
wget
[http://switch.dl.sourceforge.net/sourceforge/ieee80211/ieee80211-1.2.18.tgz](http://switch.dl.sourceforge.net/sourceforge/ieee80211/ieee80211-1.2.18.tgz)
tar xzf ieee80211-1.2.18.tgz
cd ieee80211-1.2.18
make 
make install
cd ../ipw3945-linux-1.2.0/ipw3945-1.2.0
</example>

I had to manually edit the Makefile as make choked on incomprehensible
errors:

<example>
--- Makefile.old	2007-07-17 10:38:26.000000000 +0200
+++ Makefile	2007-07-17 10:43:40.000000000 +0200
@@ -58,35 +58,11 @@
 
 # If IEEE80211_INC has not been specified by the user then we try and 
 # determine if the current kernel contains a subsystem.
-ifeq ($(IEEE80211_INC),)
-	# If the user specified a KSRC target, then ignore the default
-	# search locations and look *ONLY* in KSRC and KSRC/build
-	ifeq ($(KSRC),)
-		# We check both /lib/modules/$(shell uname -r)/build as 
-		# well as /lib/modules/ since the later is where 'make 
-		# install' places the ieee80211 files with the 
-		# out-of-tree ieee80211 subsystem.
-		IEEE80211_RES := $(shell $(DIR)/snapshot/find_ieee80211 \
-			/lib/modules/$(shell uname -r) \
-			/lib/modules/$(shell uname -r)/build)
-	else
-		IEEE80211_RES := $(shell $(DIR)/snapshot/find_ieee80211 \
-			$(KSRC) \
-			$(KSRC)/build)
-	endif
-else
-	IEEE80211_RES := $(shell $(DIR)/snapshot/find_ieee80211 \
-		$(IEEE80211_INC))
-endif
-
-IEEE80211_BASE := $(shell var=($(IEEE80211_RES)) ; echo $${var[1]})
-IEEE80211_PATH := $(shell var=($(IEEE80211_RES)) ; echo $${var[0]})
-
-ifeq ($(IEEE80211_INC),)
-	IEEE80211_SYM=${IEEE80211_BASE}/net/ieee80211
-else
-	IEEE80211_SYM=${IEEE80211_BASE}
-endif
+
+IEEE80211_BASE := /lib/modules/2.6.21.6-vs2.2.0.1-customvs/
+IEEE80211_PATH := /lib/modules/2.6.21.6-vs2.2.0.1-customvs/include
+IEEE80211_SYM=${IEEE80211_BASE}/net/ieee80211
+
 # If the ieee80211 subsystem is not found in the default kernel
 # build location then we need to add the include path and 
 # verify that the running kernel is not built using conflicting module
@@ -100,7 +76,7 @@
 endif
 
 # Parse out the ieee80211 subsystem version from the ieee80211.h header
-IEEE80211_API := $(shell $(DIR)/snapshot/check_ieee80211_compat $(IEEE80211_PATH))
+IEEE80211_API := 2
 EXTRA_CFLAGS += -DIPW3945_COMPAT=$(IEEE80211_API)
 
 ifeq ($(CONFIG_IPW3945_DEBUG),y)
</example>

then 

<example>
make 
make install
cd ../ipw3945d-1.7.22/
cp x86/ipw3945d /sbin/ipw3945d-`uname -r`
cd ../ipw3945-ucode 
mkdir /lib/firmware/`uname -r`/ 
cp ipw3945.ucode /lib/firmware/`uname -r`
</example>

Works until driver is loaded, then kernel freezes :(

I also tried with ubuntu's official kernel but without much success:

<example>
sudo apt-get install linux-source
cd /usr/src
tar xjf linux-source-2.6.20.tar.bz2
cd linux-source-2.6.20
su
patch -p1 < ../patch-2.6.20.15-vs2.2.0.1.diff
# some hunks fail - have to edit by hand
make oldconfig
fakeroot make-kpkg --initrd kernel_image kernel_headers
  CC [M]  ubuntu/fs/unionfs/inode.o
ubuntu/fs/unionfs/inode.c: In function «unionfs_link":
ubuntu/fs/unionfs/inode.c:268: erreur: too few arguments to function «vfs_unlink"
ubuntu/fs/unionfs/inode.c:296: erreur: too few arguments to function «vfs_link"
ubuntu/fs/unionfs/inode.c:320: erreur: too few arguments to function «vfs_link"
ubuntu/fs/unionfs/inode.c: In function «unionfs_symlink":
ubuntu/fs/unionfs/inode.c:399: erreur: too few arguments to function «vfs_unlink"
ubuntu/fs/unionfs/inode.c:445: erreur: too few arguments to function «vfs_symlink"
ubuntu/fs/unionfs/inode.c: In function «unionfs_mkdir":
ubuntu/fs/unionfs/inode.c:524: erreur: too few arguments to function «vfs_unlink"
ubuntu/fs/unionfs/inode.c:563: erreur: too few arguments to function «vfs_mkdir"
ubuntu/fs/unionfs/inode.c: In function «unionfs_mknod":
ubuntu/fs/unionfs/inode.c:659: erreur: too few arguments to function «vfs_unlink"
ubuntu/fs/unionfs/inode.c:693: erreur: too few arguments to function «vfs_mknod"
make[3]: *** [ubuntu/fs/unionfs/inode.o] Erreur 1
make[2]: *** [ubuntu/fs/unionfs] Erreur 2
make[1]: *** [ubuntu] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-source-2.6.20 »

</example>

---

