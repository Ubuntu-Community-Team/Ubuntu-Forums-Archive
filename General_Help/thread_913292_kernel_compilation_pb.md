---
title: "kernel compilation pb"
date: 2008-09-07
forum: General Help
---

### Post by cedric_libre on 2008-09-07
Hi,
 I'd like to compile kernel 2.6.10 downloaded at kernel.org, in order to get the same system as in a driver writing tutorial ( Alessandro Rubini's ) .

After having bunzipped linux-2.6.10.bz2 and cd'd in
 /usr/src/linux-2.6.10, I typed make config and here is the result :

 root@lachez-moi:/usr/src/linux-2.6.10# make config
  HOSTCC  scripts/basic/fixdep
In file included from /usr/include/sys/socket.h:35,
                 from /usr/include/netinet/in.h:24,
                 from /usr/include/arpa/inet.h:23,
                 from scripts/basic/fixdep.c:115:
/usr/include/bits/socket.h:311:24: error: asm/socket.h: No such file or directory
scripts/basic/fixdep.c: In function 'parse_config_file':
scripts/basic/fixdep.c:245: warning: pointer targets in passing argument 1 of 'use_config' differ in signedness
scripts/basic/fixdep.c: In function 'parse_dep_file':
scripts/basic/fixdep.c:299: warning: pointer targets in passing argument 1 of '__builtin_strchr' differ in signedness
scripts/basic/fixdep.c:299: warning: pointer targets in assignment differ in signedness
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2

 Has anyone an idea ?
 Thanks

---

### Post by drs305 on 2008-09-07
The normal sequence of commands from inside the folder is:
./configure, make, sudo make install

You can substitute 'sudo checkinstall' for the last command to create a deb if you have checkinstall on your system.


Could that be your problem or is "make config" a command in that particular compilation?

---

### Post by cedric_libre on 2008-09-07
Maybe it's the pb , don't know actually .
 I tried : ./configure from /usr/src/linux-2.6.10 as root but the system tells me that the file or directory is unknown .

I typed which configure -> No answer .
 Seems configure is not installed .
 Do you know a package from which to retrieve it ?

 Thanks again

---

### Post by drs305 on 2008-09-07
> **cedric_libre said:**
> Maybe it's the pb , don't know actually .
 I tried : ./configure from /usr/src/linux-2.6.10 as root but the system tells me that the file or directory is unknown .

I typed which configure -> No answer .
 Seems configure is not installed .
 Do you know a package from which to retrieve it ?

 Thanks again

Configure isn't a system command. Normally when you compile a program from source the main folder has a script in it called 'configure'. You type ./configure (the ./ just means to run in the current folder) and it starts the script by the same name. It is possible that there is no script called configure in the folder, or that you weren't in the correct folder to begin with. 

Check the contents - there may be a 'configure' file or if not text files called 'README', 'INSTALL', or something similar which will instruct you on how to compile the kernel/app.

---

### Post by cedric_libre on 2008-09-08
You are right, there's no configure file in /usr/src/linux-2.6.10

There's a README file.

 In the README of /usr/src/linux-2.6.10 ,
 it's said I should get into /usr/src/linux-2.6.10 and 
 from there type :
 make O=/home/name/build/kernel menuconfig 
 where /home/name/build/kernel would be the destination of the output files

and then :
  
 make O=/home/name/build/kernel

   sudo make O=/home/name/build/kernel modules_install install


But at the first step,
after typing :

 make O=/home/cedric/ordinateur/kernel menuconfig

I still get the same messages:

 root@lachez-moi:/usr/src/linux-2.6.10# make O=~cedric/ordinateur/kernel/ menuconfig
  HOSTCC  scripts/basic/fixdep
In file included from /usr/include/sys/socket.h:35,
                 from /usr/include/netinet/in.h:24,
                 from /usr/include/arpa/inet.h:23,
                 from /usr/src/linux-2.6.10/scripts/basic/fixdep.c:115:
/usr/include/bits/socket.h:311:24: error: asm/socket.h: No such file or directory
/usr/src/linux-2.6.10/scripts/basic/fixdep.c: In function 'parse_config_file':
/usr/src/linux-2.6.10/scripts/basic/fixdep.c:245: warning: pointer targets in passing argument 1 of 'use_config' differ in signedness
/usr/src/linux-2.6.10/scripts/basic/fixdep.c: In function 'parse_dep_file':
/usr/src/linux-2.6.10/scripts/basic/fixdep.c:299: warning: pointer targets in passing argument 1 of '__builtin_strchr' differ in signedness
/usr/src/linux-2.6.10/scripts/basic/fixdep.c:299: warning: pointer targets in assignment differ in signedness
make[2]: *** [scripts/basic/fixdep] Error 1
make[1]: *** [scripts_basic] Error 2
make: *** [menuconfig] Error 2


 So seems that anyway I get the same error :

 asm/socket.h: No such file or directory

 Do you have this file on your system ?

---

### Post by Gunman1982 on 2008-09-08
Building the kernel differs slightly from building other sources, you don't need configure since you handle everything with make.

But you have to make sure that you have the build-essentials packet installed on the system, furthermore you need ncurses I don't know if its part of build-essentials. 

For a "graphical" menu do a 'make menuconfig' there you can choose what your kernel should be capable of and what you don't need. I use the command 'make bzImage' afterwards which creates a kernel image in a subdirectory 'arch/i386/boot/bzImage' then you just need to do a 'make modules' and 'make modules_install' That should do the trick, copy the bzImage, System.map files into /boot make sure you don't need an initrd.img file (hope I got that right) change the /boot/grub/menu.lst and restart the machine. I recommend keeping the old kernel if something goes wrong.

---

### Post by cedric_libre on 2008-09-08
Thanks for your help,
 I think I found the clue for this pb.
 I had a missing link, according to someone's advice, I typed :
 sudo ln -sfn /usr/src/linux/include/asm-i386 /usr/include/asm 

and afterwards make menuconfig worked fine .

Well now I have other problems after command make :

 root@lachez-moi:/usr/src/linux-2.6.10#  make O=~cedric/ordinateur/kernel/2.6.10/ 
  Using /usr/src/linux-2.6.10 as source for kernel
  GEN    /home/cedric/ordinateur/kernel/2.6.10/Makefile
  CHK     include/linux/version.h
  UPD     include/linux/version.h
  SYMLINK include/asm -> include/asm-i386
  GEN    /home/cedric/ordinateur/kernel/2.6.10/Makefile
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/i386/Kconfig
#
# using defaults found in .config
#
  SPLIT   include/linux/autoconf.h -> include/config/*
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
  HOSTCC  scripts/mod/sumversion.o
/usr/src/linux-2.6.10/scripts/mod/sumversion.c: In function «parse_file":
/usr/src/linux-2.6.10/scripts/mod/sumversion.c:260: attention : pointer targets in passing argument 1 of «grab_file" differ in signedness
/usr/src/linux-2.6.10/scripts/mod/sumversion.c:277: attention : pointer targets in passing argument 1 of «parse_string" differ in signedness
/usr/src/linux-2.6.10/scripts/mod/sumversion.c:283: attention : pointer targets in passing argument 1 of «parse_comment" differ in signedness
/usr/src/linux-2.6.10/scripts/mod/sumversion.c: In function «parse_source_files":
/usr/src/linux-2.6.10/scripts/mod/sumversion.c:335: attention : pointer targets in initialization differ in signedness
/usr/src/linux-2.6.10/scripts/mod/sumversion.c:344: attention : pointer targets in passing argument 1 of «strlen" differ in signedness
/usr/src/linux-2.6.10/scripts/mod/sumversion.c:357: attention : pointer targets in passing argument 1 of «parse_file" differ in signedness
/usr/src/linux-2.6.10/scripts/mod/sumversion.c: In function «strip_rcs_crap":
/usr/src/linux-2.6.10/scripts/mod/sumversion.c:463: attention : pointer targets in passing argument 1 of «strlen" differ in signedness
/usr/src/linux-2.6.10/scripts/mod/sumversion.c:463: attention : pointer targets in passing argument 1 of «strlen" differ in signedness
/usr/src/linux-2.6.10/scripts/mod/sumversion.c:463: attention : pointer targets in passing argument 1 of «__builtin_strcmp" differ in signedness
/usr/src/linux-2.6.10/scripts/mod/sumversion.c:463: attention : pointer targets in passing argument 1 of «strlen" differ in signedness
/usr/src/linux-2.6.10/scripts/mod/sumversion.c:463: attention : pointer targets in passing argument 1 of «__builtin_strcmp" differ in signedness
/usr/src/linux-2.6.10/scripts/mod/sumversion.c:463: attention : pointer targets in passing argument 1 of «__builtin_strcmp" differ in signedness
/usr/src/linux-2.6.10/scripts/mod/sumversion.c:463: attention : pointer targets in passing argument 1 of «__builtin_strcmp" differ in signedness
/usr/src/linux-2.6.10/scripts/mod/sumversion.c:463: attention : pointer targets in passing argument 1 of «strncmp" differ in signedness
/usr/src/linux-2.6.10/scripts/mod/sumversion.c:467: attention : pointer targets in passing argument 1 of «strlen" differ in signedness
/usr/src/linux-2.6.10/scripts/mod/sumversion.c:467: attention : pointer targets in passing argument 1 of «strlen" differ in signedness
/usr/src/linux-2.6.10/scripts/mod/sumversion.c:467: attention : pointer targets in passing argument 1 of «strlen" differ in signedness
/usr/src/linux-2.6.10/scripts/mod/sumversion.c:483: attention : pointer targets in passing argument 1 of «strlen" differ in signedness
/usr/src/linux-2.6.10/scripts/mod/sumversion.c:484: attention : pointer targets in passing argument 1 of «strlen" differ in signedness
/usr/src/linux-2.6.10/scripts/mod/sumversion.c: In function «maybe_frob_rcs_version":
/usr/src/linux-2.6.10/scripts/mod/sumversion.c:494: attention : pointer targets in passing argument 1 of «strip_rcs_crap" differ in signedness
  HOSTLD  scripts/mod/modpost
  HOSTCC  scripts/kallsyms
/usr/src/linux-2.6.10/scripts/kallsyms.c: In function «read_symbol":
/usr/src/linux-2.6.10/scripts/kallsyms.c:152: attention : pointer targets in assignment differ in signedness
/usr/src/linux-2.6.10/scripts/kallsyms.c:153: attention : pointer targets in passing argument 1 of «strcpy" differ in signedness
/usr/src/linux-2.6.10/scripts/kallsyms.c: In function «symbol_valid":
/usr/src/linux-2.6.10/scripts/kallsyms.c:190: attention : pointer targets in passing argument 1 of «strstr" differ in signedness
/usr/src/linux-2.6.10/scripts/kallsyms.c:194: attention : pointer targets in passing argument 1 of «strlen" differ in signedness
/usr/src/linux-2.6.10/scripts/kallsyms.c:194: attention : pointer targets in passing argument 1 of «__builtin_strcmp" differ in signedness
/usr/src/linux-2.6.10/scripts/kallsyms.c:194: attention : pointer targets in passing argument 1 of «strlen" differ in signedness
/usr/src/linux-2.6.10/scripts/kallsyms.c:194: attention : pointer targets in passing argument 1 of «__builtin_strcmp" differ in signedness
/usr/src/linux-2.6.10/scripts/kallsyms.c:194: attention : pointer targets in passing argument 1 of «__builtin_strcmp" differ in signedness
/usr/src/linux-2.6.10/scripts/kallsyms.c:194: attention : pointer targets in passing argument 1 of «__builtin_strcmp" differ in signedness
  HOSTCC  scripts/conmakehash
/usr/src/linux-2.6.10/scripts/conmakehash.c: In function «getunicode":
/usr/src/linux-2.6.10/scripts/conmakehash.c:36: attention : pointer targets in initialization differ in signedness
/usr/src/linux-2.6.10/scripts/conmakehash.c:44: attention : pointer targets in assignment differ in signedness
/usr/src/linux-2.6.10/scripts/conmakehash.c:45: attention : pointer targets in passing argument 1 of «strtol" differ in signedness
  CC      arch/i386/kernel/asm-offsets.s
In file included from include2/asm/mpspec.h:5,
                 from include2/asm/smp.h:18,
                 from /usr/src/linux-2.6.10/include/linux/smp.h:17,
                 from /usr/src/linux-2.6.10/include/linux/sched.h:23,
                 from /usr/src/linux-2.6.10/arch/i386/kernel/asm-offsets.c:7:
include2/asm/mpspec_def.h:78: attention : «packed" attribute ignored for field of type «unsigned char[6]"
  CHK     include/asm-i386/asm_offsets.h
  UPD     include/asm-i386/asm_offsets.h
  CC      init/main.o
In file included from include2/asm/mpspec.h:5,
                 from include2/asm/smp.h:18,
                 from /usr/src/linux-2.6.10/include/linux/smp.h:17,
                 from /usr/src/linux-2.6.10/include/linux/sched.h:23,
                 from /usr/src/linux-2.6.10/include/linux/module.h:10,
                 from /usr/src/linux-2.6.10/init/main.c:16:
include2/asm/mpspec_def.h:78: attention : «packed" attribute ignored for field of type «unsigned char[6]"
/usr/src/linux-2.6.10/init/main.c: In function «maxcpus":
/usr/src/linux-2.6.10/init/main.c:150: attention : pointer targets in passing argument 2 of «get_option" differ in signedness
  CHK     include/linux/compile.h
  UPD     include/linux/compile.h
  CC      init/version.o
In file included from include2/asm/mpspec.h:5,
                 from include2/asm/smp.h:18,
                 from /usr/src/linux-2.6.10/include/linux/smp.h:17,
                 from /usr/src/linux-2.6.10/include/linux/sched.h:23,
                 from /usr/src/linux-2.6.10/include/linux/module.h:10,
                 from /usr/src/linux-2.6.10/init/version.c:10:
include2/asm/mpspec_def.h:78: attention : «packed" attribute ignored for field of type «unsigned char[6]"
  CC      init/do_mounts.o
In file included from include2/asm/mpspec.h:5,
                 from include2/asm/smp.h:18,
                 from /usr/src/linux-2.6.10/include/linux/smp.h:17,
                 from /usr/src/linux-2.6.10/include/linux/sched.h:23,
                 from /usr/src/linux-2.6.10/include/linux/module.h:10,
                 from /usr/src/linux-2.6.10/init/do_mounts.c:1:
include2/asm/mpspec_def.h:78: attention : «packed" attribute ignored for field of type «unsigned char[6]"
  CC      init/do_mounts_rd.o
In file included from include2/asm/mpspec.h:5,
                 from include2/asm/smp.h:18,
                 from /usr/src/linux-2.6.10/include/linux/smp.h:17,
                 from /usr/src/linux-2.6.10/include/linux/topology.h:33,
                 from /usr/src/linux-2.6.10/include/linux/mmzone.h:372,
                 from /usr/src/linux-2.6.10/include/linux/gfp.h:4,
                 from /usr/src/linux-2.6.10/include/linux/slab.h:15,
                 from /usr/src/linux-2.6.10/include/linux/percpu.h:4,
                 from /usr/src/linux-2.6.10/include/linux/rcupdate.h:41,
                 from /usr/src/linux-2.6.10/include/linux/dcache.h:10,
                 from /usr/src/linux-2.6.10/include/linux/fs.h:16,
                 from /usr/src/linux-2.6.10/init/do_mounts_rd.c:3:
include2/asm/mpspec_def.h:78: attention : «packed" attribute ignored for field of type «unsigned char[6]"
/usr/src/linux-2.6.10/init/do_mounts_rd.c: In function «identify_ramdisk_image":
/usr/src/linux-2.6.10/init/do_mounts_rd.c:73: attention : pointer targets in passing argument 2 of «sys_read" differ in signedness
/usr/src/linux-2.6.10/init/do_mounts_rd.c:108: attention : pointer targets in passing argument 2 of «sys_read" differ in signedness
/usr/src/linux-2.6.10/init/do_mounts_rd.c: In function «fill_inbuf":
/usr/src/linux-2.6.10/init/do_mounts_rd.c:352: attention : pointer targets in passing argument 2 of «sys_read" differ in signedness
/usr/src/linux-2.6.10/init/do_mounts_rd.c: In function «flush_window":
/usr/src/linux-2.6.10/init/do_mounts_rd.c:373: attention : pointer targets in passing argument 2 of «sys_write" differ in signedness
  CC      init/do_mounts_initrd.o
In file included from include2/asm/mpspec.h:5,
                 from include2/asm/smp.h:18,
                 from /usr/src/linux-2.6.10/include/linux/smp.h:17,
                 from /usr/src/linux-2.6.10/include/linux/topology.h:33,
                 from /usr/src/linux-2.6.10/include/linux/mmzone.h:372,
                 from /usr/src/linux-2.6.10/include/linux/gfp.h:4,
                 from /usr/src/linux-2.6.10/include/linux/slab.h:15,
                 from /usr/src/linux-2.6.10/include/linux/percpu.h:4,
                 from /usr/src/linux-2.6.10/include/linux/rcupdate.h:41,
                 from /usr/src/linux-2.6.10/include/linux/dcache.h:10,
                 from /usr/src/linux-2.6.10/include/linux/fs.h:16,
                 from /usr/src/linux-2.6.10/init/do_mounts_initrd.c:4:
include2/asm/mpspec_def.h:78: attention : «packed" attribute ignored for field of type «unsigned char[6]"
  LD      init/mounts.o
  CC      init/initramfs.o
In file included from include2/asm/mpspec.h:5,
                 from include2/asm/smp.h:18,
                 from /usr/src/linux-2.6.10/include/linux/smp.h:17,
                 from /usr/src/linux-2.6.10/include/linux/topology.h:33,
                 from /usr/src/linux-2.6.10/include/linux/mmzone.h:372,
                 from /usr/src/linux-2.6.10/include/linux/gfp.h:4,
                 from /usr/src/linux-2.6.10/include/linux/slab.h:15,
                 from /usr/src/linux-2.6.10/include/linux/percpu.h:4,
                 from /usr/src/linux-2.6.10/include/linux/rcupdate.h:41,
                 from /usr/src/linux-2.6.10/include/linux/dcache.h:10,
                 from /usr/src/linux-2.6.10/include/linux/fs.h:16,
                 from /usr/src/linux-2.6.10/init/initramfs.c:2:
include2/asm/mpspec_def.h:78: attention : «packed" attribute ignored for field of type «unsigned char[6]"
/usr/src/linux-2.6.10/init/initramfs.c: In function «flush_window":
/usr/src/linux-2.6.10/init/initramfs.c:402: attention : pointer targets in passing argument 1 of «flush_buffer" differ in signedness
/usr/src/linux-2.6.10/init/initramfs.c: In function «unpack_to_rootfs":
/usr/src/linux-2.6.10/init/initramfs.c:443: attention : pointer targets in assignment differ in signedness
  LD      init/built-in.o
  HOSTCC  usr/gen_init_cpio
  CHK     usr/initramfs_list
  UPD     usr/initramfs_list
  CPIO    usr/initramfs_data.cpio
  GZIP    usr/initramfs_data.cpio.gz
  AS      usr/initramfs_data.o
  LD      usr/built-in.o
  CC      arch/i386/kernel/process.o
In file included from include2/asm/mpspec.h:5,
                 from include2/asm/smp.h:18,
                 from /usr/src/linux-2.6.10/include/linux/smp.h:17,
                 from /usr/src/linux-2.6.10/include/linux/sched.h:23,
                 from /usr/src/linux-2.6.10/arch/i386/kernel/process.c:17:
include2/asm/mpspec_def.h:78: attention : «packed" attribute ignored for field of type «unsigned char[6]"
/usr/src/linux-2.6.10/arch/i386/kernel/process.c: In function «show_regs":
/usr/src/linux-2.6.10/arch/i386/kernel/process.c:259: attention : pointer targets in passing argument 2 of «show_trace" differ in signedness
{standard input}: Assembler messages:
{standard input}:1393: Error: suffix or operands invalid for `mov'
{standard input}:1395: Error: suffix or operands invalid for `mov'
{standard input}:1743: Error: suffix or operands invalid for `mov'
{standard input}:1745: Error: suffix or operands invalid for `mov'
{standard input}:1855: Error: suffix or operands invalid for `mov'
{standard input}:1856: Error: suffix or operands invalid for `mov'
{standard input}:2197: Error: suffix or operands invalid for `mov'
{standard input}:2210: Error: suffix or operands invalid for `mov'
make[2]: *** [arch/i386/kernel/process.o] Erreur 1



So I googled a little bit and   found this link :
[http://www.linuxquestions.org/questions/linux-from-scratch-13/problem-while-make-kernel-343910/](http://www.linuxquestions.org/questions/linux-from-scratch-13/problem-while-make-kernel-343910/)

where someone gives the following advices :
inux# wget [www.kernel.org/pub/linux/devel/binutils/linux-2.6-seg-5.patch](www.kernel.org/pub/linux/devel/binutils/linux-2.6-seg-5.patch)
root:/usr/src/linux# patch -Np1 -i linux-2.6-seg-5.patch

But that doesn't work from the directory where I downloaded linux-2.6-seg-5.patch
So I went to /usr/src and made linux point 
 to linux-2.6.10 , and from /usr/src I typed :
root@lachez-moi:/usr/src# patch -Np1 -i linux-2.6-seg-5.patch
patch: **** Can't open patch file linux-2.6-seg-5.patch : No such file or directory
root@lachez-moi:/usr/src# patch -Np1 -i ~cedric/telechargements/linux-2.6-seg-5.patch
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- linux/arch/i386/kernel/process.c.seg       2005-03-27 13:07:14.000000000 -0800
|+++ linux/arch/i386/kernel/process.c   2005-03-28 10:28:47.000000000 -0800
--------------------------
File to patch: 


 I checked that linux/arch/i386/kernel/process.c
 exists, 
 Have you got an idea ?

---

### Post by cedric_libre on 2008-09-08
up !

---

