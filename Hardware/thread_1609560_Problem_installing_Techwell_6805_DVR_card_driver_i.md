---
title: "Problem installing Techwell 6805 DVR card driver in Ubuntu 10.04 LTS Server (64-bit)"
date: 2010-10-30
forum: Hardware
---

### Post by btrotter on 2010-10-30
I have a Techwell 6805 DVR PCI card I want to install so I can use it with Zoneminder.
I installed 10.04 Server on the server. I chose to install LAMP and OpenSSH during the build.
Ultimately, I want the card to work and that is it. I have been reading through the forums and not making sense of some of the things I am reading and trying some things which seem to be clearly explained.
** ALL ITEMS IN BLUE ARE OUTPUT FROM A COMMAND

I found an article describing how to download working drivers from this site:
[http://gitorious.org/tw68/tw68-v2/trees/master](http://gitorious.org/tw68/tw68-v2/trees/master)

In order to get git to work, I had to install git-core and gitosis by running:
1: sudo apt-get install git-core
2: sudo apt-get install gitosis

After that I downloaded the driver by running:
1: sudo git clone git://gitorious.org/tw68/module.git
***
[COLOR="Blue"]Initialized empty Git repository in /home/btrotter/module/.git/
remote: Counting objects: 39, done.
remote: Compressing objects: 100% (39/39), done.
remote: Total 39 (delta 22), reused 0 (delta 0)
Receiving objects: 100% (39/39), 43.76 KiB, done.
Resolving deltas: 100% (22/22), done.[/COLOR]
***

Then I changed to the /home/btrotter/module directory and ran:
1: sudo make

***
[COLOR="blue"]make -C /lib/modules/2.6.32-24-server/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-server'
/usr/src/linux-headers-2.6.32-24-server/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc: not found
make[3]: *** [scripts/basic/fixdep] Error 127
make[2]: *** [scripts_basic] Error 2
make[1]: *** No rule to make target `include/config/auto.conf', needed by `include/config/kernel.release'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-server'
make: *** [all] Error 2[/COLOR]
***

I read up on the internet and found an article saying I needed to install dkms,
so I installed it:
1: sudo apt-get install dkms

****
[COLOR="blue"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binutils fakeroot gcc gcc-4.4 libc-dev-bin libc6-dev libgomp1 linux-libc-dev
  manpages-dev
Suggested packages:
  binutils-doc gcc-multilib autoconf automake1.9 libtool flex bison gdb gcc-doc
  gcc-4.4-multilib libmudflap0-4.4-dev gcc-4.4-doc gcc-4.4-locales libgcc1-dbg
  libgomp1-dbg libmudflap0-dbg libcloog-ppl0 libppl-c2 libppl7 glibc-doc
The following NEW packages will be installed:
  binutils dkms fakeroot gcc gcc-4.4 libc-dev-bin libc6-dev libgomp1 linux-libc-dev
  manpages-dev
0 upgraded, 10 newly installed, 0 to remove and 4 not upgraded.
Need to get 10.0MB of archives.
After this operation, 36.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main binutils 2.20.1-3ubuntu7 [1,665kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libgomp1 4.4.3-4ubuntu5 [25.5kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main gcc-4.4 4.4.3-4ubuntu5 [2,877kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main gcc 4:4.4.3-1ubuntu1 [5,064B]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main dkms 2.1.1.2-2fakesync1 [70.1kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main fakeroot 1.14.4-1ubuntu1 [101kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main libc-dev-bin 2.11.1-0ubuntu7.5 [223kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-libc-dev 2.6.32-25.45 [814kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main libc6-dev 2.11.1-0ubuntu7.5 [2,716kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main manpages-dev 3.23-1 [1,547kB]
Fetched 10.0MB in 5s (1,777kB/s)         
Selecting previously deselected package binutils.
(Reading database ... 46933 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.20.1-3ubuntu7_amd64.deb) ...
Selecting previously deselected package libgomp1.
Unpacking libgomp1 (from .../libgomp1_4.4.3-4ubuntu5_amd64.deb) ...
Selecting previously deselected package gcc-4.4.
Unpacking gcc-4.4 (from .../gcc-4.4_4.4.3-4ubuntu5_amd64.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.4.3-1ubuntu1_amd64.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.1.1.2-2fakesync1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_amd64.deb) ...
Selecting previously deselected package libc-dev-bin.
Unpacking libc-dev-bin (from .../libc-dev-bin_2.11.1-0ubuntu7.5_amd64.deb) ...
Selecting previously deselected package linux-libc-dev.
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.32-25.45_amd64.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.11.1-0ubuntu7.5_amd64.deb) ...
Selecting previously deselected package manpages-dev.
Unpacking manpages-dev (from .../manpages-dev_3.23-1_all.deb) ...
Processing triggers for man-db ...
Setting up binutils (2.20.1-3ubuntu7) ...

Setting up libgomp1 (4.4.3-4ubuntu5) ...

Setting up gcc-4.4 (4.4.3-4ubuntu5) ...
Setting up gcc (4:4.4.3-1ubuntu1) ...

Setting up dkms (2.1.1.2-2fakesync1) ...

Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up libc-dev-bin (2.11.1-0ubuntu7.5) ...
Setting up linux-libc-dev (2.6.32-25.45) ...
Setting up libc6-dev (2.11.1-0ubuntu7.5) ...
Setting up manpages-dev (3.23-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place[/COLOR]
****

I then went back to the modules directory and tried running make again:
1: sudo make

***
[COLOR="blue"]make -C /lib/modules/2.6.32-24-server/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-server'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function &#8216;conf_askvalue&#8217;:
scripts/kconfig/conf.c:105: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function &#8216;conf_choice&#8217;:
scripts/kconfig/conf.c:307: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-server'
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-server'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-server'
make: *** [all] Error 2[/COLOR]
***

I went back and read through the forums and saw comments about needing to install the linux-source, so I downloaded it:
1: sudo apt-get install linux-source

***
[COLOR="blue"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-source-2.6.32
Suggested packages:
  libncurses-dev ncurses-dev kernel-package libqt3-dev
The following NEW packages will be installed:
  linux-source linux-source-2.6.32
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 65.9MB of archives.
After this operation, 66.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-source-2.6.32 2.6.32-25.45 [65.9MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-source 2.6.32.25.27 [4,108B]
Fetched 65.9MB in 47s (1,396kB/s)                                                    
Selecting previously deselected package linux-source-2.6.32.
(Reading database ... 50137 files and directories currently installed.)
Unpacking linux-source-2.6.32 (from .../linux-source-2.6.32_2.6.32-25.45_all.deb) ...
Selecting previously deselected package linux-source.
Unpacking linux-source (from .../linux-source_2.6.32.25.27_all.deb) ...
Setting up linux-source-2.6.32 (2.6.32-25.45) ...
Setting up linux-source (2.6.32.25.27) ...[/COLOR]
****

At this point, I really have no idea what I am doing. I am simply following instructions I see on the net. 

I uncompressed the file:
1: cd /usr/src
2: sudo tar -xvjf linux-source-2.6.32.tar.bz2

***
It uncompressed a lot of files, too many to copy below.

In the thread I was reading, I saw mention of needing to compile the kernel. I dont really understand how to do that, or what commands need to be run. I followed a thread online and ran these commands
1: cd /usr/src/linux-source-2.6.32/
2: sudo make

***
[COLOR="blue"] HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function &#8216;conf_askvalue&#8217;:
scripts/kconfig/conf.c:105: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function &#8216;conf_choice&#8217;:
scripts/kconfig/conf.c:307: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  SHIPPED scripts/kconfig/zconf.tab.c
  SHIPPED scripts/kconfig/lex.zconf.c
  SHIPPED scripts/kconfig/zconf.hash.c
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
***
*** You have not yet configured your kernel!
*** (missing kernel config file ".config")
***
*** Please run some configurator (e.g. "make oldconfig" or
*** "make menuconfig" or "make xconfig").
***
make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
make: *** No rule to make target `include/config/auto.conf', needed by `include/config/kernel.release'.  Stop.[/COLOR]
****

Again, still not really sure what I am doing other than reading a thread and trying what it said.
1: cd /usr/src/linux-source-2.6.32/
2: sudo cp -vi /boot/config-2.6.32-24-server .config
***
[COLOR="blue"]`/boot/config-2.6.32-24-server' -> `.config'[/COLOR]
***
3: sudo make oldconfig
***
[COLOR="blue"]scripts/kconfig/conf -o arch/x86/Kconfig
#
# configuration written to .config
#[/COLOR]
***

4: cd /lib/modules/2.6.32-24-server/
5: sudo rm build
6: sudo ln -s /usr/src/linux-headers-2.6.32-24-server/ build

I then tried going back to the module site and running make:
1: sudo make
***
[COLOR="blue"]make -C /lib/modules/2.6.32-24-server/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-server'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving direc[/COLOR]tory `/usr/src/linux-headers-2.6.32-24-server'
make: *** [all] Error 2
***

I saw another comment in the thread about compiling the kernel. I thought that I had done it with the commands above, but I guess not. So I read in the thread more and saw to do this:
1: cd /usr/src/cd linux-source-2.6.32/
2: sudo make menuconfig
***
[COLOR="blue"] *** Unable to find the ncurses libraries or the
 *** required header files.
 *** 'make menuconfig' requires the ncurses libraries.
 *** 
 *** Install ncurses (ncurses-devel) and try again.
 *** 
make[1]: *** [scripts/kconfig/dochecklxdialog] Error 1
make: *** [menuconfig] Error 2[/COLOR]
***
3: sudo -s make

At this point, it has been doing something for nearly an hour. I will post some of the output below, but it is only a very small sample:

***
[COLOR="blue"]scripts/kconfig/conf -s arch/x86/Kconfig
  CHK     include/linux/version.h
  UPD     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
  CC      kernel/bounds.s
  GEN     include/linux/bounds.h
  CC      arch/x86/kernel/asm-offsets.s
  GEN     include/asm/asm-offsets.h
  CALL    scripts/checksyscalls.sh
  HOSTCC  scripts/genksyms/genksyms.o
  SHIPPED scripts/genksyms/lex.c
  SHIPPED scripts/genksyms/parse.h
  SHIPPED scripts/genksyms/keywords.c
  HOSTCC  scripts/genksyms/lex.o
  SHIPPED scripts/genksyms/parse.c
  HOSTCC  scripts/genksyms/parse.o
  HOSTLD  scripts/genksyms/genksyms
  CC      scripts/mod/empty.o
  HOSTCC  scripts/mod/mk_elfconfig
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/modpost.o
scripts/mod/modpost.c: In function &#8216;get_markers&#8217;:
scripts/mod/modpost.c:1562: warning: ignoring return value of &#8216;asprintf&#8217;, declared with attribute warn_unused_result
scripts/mod/modpost.c: In function &#8216;add_marker&#8217;:
scripts/mod/modpost.c:1982: warning: ignoring return value of &#8216;asprintf&#8217;, declared with attribute warn_unused_result
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
  HOSTCC  scripts/selinux/mdp/mdp
  HOSTCC  scripts/kallsyms
scripts/kallsyms.c: In function &#8216;read_symbol&#8217;:
scripts/kallsyms.c:112: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
  HOSTCC  scripts/conmakehash
  CC      init/main.o
  CHK     include/linux/compile.h
  UPD     include/linux/compile.h
  CC      init/version.o
  CC      init/do_mounts.o
  CC      init/do_mounts_rd.o
  CC      init/do_mounts_initrd.o
  CC      init/do_mounts_md.o
  LD      init/mounts.o
  CC      init/initramfs.o
init/initramfs.c: In function &#8216;populate_rootfs_early&#8217;:
init/initramfs.c:620: warning: passing argument 1 of &#8216;async_schedule_domain&#8217; from incompatible pointer type
include/linux/async.h:20: note: expected &#8216;void (*)(void *, async_cookie_t)&#8217; but argument is of type &#8216;void (*)(void)&#8217;
init/initramfs.c:622: warning: no return statement in function returning non-void
init/initramfs.c: In function &#8216;populate_rootfs&#8217;:
init/initramfs.c:627: warning: passing argument 1 of &#8216;async_schedule_domain&#8217; from incompatible pointer type
include/linux/async.h:20: note: expected &#8216;void (*)(void *, async_cookie_t)&#8217; but argument is of type &#8216;void (*)(void)&#8217;
init/initramfs.c:628: warning: no return statement in function returning non-void
  CC      init/calibrate.o
  LD      init/built-in.o
  HOSTCC  usr/gen_init_cpio
  GEN     usr/initramfs_data.cpio
  AS      usr/initramfs_data.o
  LD      usr/built-in.o
  LD      arch/x86/crypto/built-in.o
  CC [M]  arch/x86/crypto/fpu.o
  AS [M]  arch/x86/crypto/aes-x86_64-asm_64.o
  CC [M]  arch/x86/crypto/aes_glue.o
  AS [M]  arch/x86/crypto/aesni-intel_asm.o
  CC [M]  arch/x86/crypto/aesni-intel_glue.o
  AS [M]  arch/x86/crypto/ghash-clmulni-intel_asm.o
  CC [M]  arch/x86/crypto/ghash-clmulni-intel_glue.o
  AS [M]  arch/x86/crypto/salsa20-x86_64-asm_64.o
  CC [M]  arch/x86/crypto/salsa20_glue.o
  AS [M]  arch/x86/crypto/twofish-x86_64-asm_64.o
  CC [M]  arch/x86/crypto/twofish_glue.o
  LD [M]  arch/x86/crypto/aes-x86_64.o
  LD [M]  arch/x86/crypto/twofish-x86_64.o
  LD [M]  arch/x86/crypto/salsa20-x86_64.o
  LD [M]  arch/x86/crypto/aesni-intel.o
  LD [M]  arch/x86/crypto/ghash-clmulni-intel.o
  CC [M]  arch/x86/crypto/crc32c-intel.o
  AS      arch/x86/ia32/ia32entry.o
  CC      arch/x86/ia32/sys_ia32.o
  CC      arch/x86/ia32/ia32_signal.o
  CC      arch/x86/ia32/ipc32.o
  CC      arch/x86/ia32/audit.o
  LD      arch/x86/ia32/built-in.o
  CC      arch/x86/kernel/process_64.o
  CC      arch/x86/kernel/signal.o
  AS      arch/x86/kernel/entry_64.o
  CC      arch/x86/kernel/traps.o
  CC      arch/x86/kernel/irq.o
  CC      arch/x86/kernel/irq_64.o
  CC      arch/x86/kernel/dumpstack_64.o
  CC      arch/x86/kernel/time.o
  CC      arch/x86/kernel/ioport.o
  CC      arch/x86/kernel/ldt.o[/COLOR]
***

After it was finished, I tried going back to the module directory and running sudo make again, but it is still not working:
***
[COLOR="Blue"]make -C /lib/modules/2.6.32-24-server/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-server'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-server'
make: *** [all] Error 2[/COLOR]
***

---

### Post by IcarusR on 2010-10-30
> make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'. Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-server'
make: *** [all] Error 2

I believe bounds.c is in the kernel source package not the headers package.

I would suggest you remove your attempts to compile kernel & read up on compiling kernel from a good guide & start a fresh.

This seems a reasonable guide...

[http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html]("http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html")

Are you sure you need to compile kernel as opposed to just need the kernel source to compile your module ??

What instructions are you following to do your module install ?

---

### Post by btrotter on 2010-10-30
I figured it out. 
I also had to download:
sudo git clone git://gitorious.org/tw68/tw68-v2.git

Once I got it, I did make, then make install, and everything worked. No need to do all the compiling stuff I was trying to do.

Thank you for your reply.

---

### Post by whoelse42 on 2011-03-25
A few quick questions; can we presume you were able to successfully use a TW 6805 chip card with Zoneminder?  How does the card handle, fps, bugs, etc?  

Was this a PCI-e card with multiple inputs or a single input?

I've been running Zoneminder with multiple Booktree chips for years, but wanted to consider a 16 ch TECHWELL 6805 chip based 400/480 fps pci-e card, I knew the driver was under development and wouldn't make a purchase unless someone had success already.  One of the concerns I also had was the bt cards with multiple chips seem to perform about as good or bad as the shared chip ones, in my case, anything over 12fps per input and my machine goes over a cliff; any chance you've had better luck?



Thanks for your time...

---

