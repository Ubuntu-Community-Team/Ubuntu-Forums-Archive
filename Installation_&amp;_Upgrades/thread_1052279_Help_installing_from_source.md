---
title: "Help installing from source"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by RMSe17 on 2009-01-27
I am using Ubuntu 8.10 32 bit server with the added desktop packages for GUI.  I am trying to install open-iscsi-2.0-870.2  (open-iscsi-2.0-870.2.tar.gz).  I extracted that into a folder on the desktop.

I also did apt-get build-essential.

I was reading the README file provided with the open-iscsi package, and it said that Debian users need to download kernel headers.  Am I correct in assuming that this applies to Ubuntu as well?  How do I download my kernel headers?  

I am guessing that I am missing them, and maybe something else? since when I run "sudo make" in the open-iscsi-2.0-870.2 directory, I get all kinds of warnings and errors.  

Do I need to get "sudo make" to work without errors before I run "make install"?  (Is that the order of things?  I have no idea).  

I tried to find a guide on how to install and compile things in Ubuntu docs, but could not find a howto.

Please help :)




Just in case this tells you something, here is what happens when I run sudo make

```

~/Desktop/open-iscsi-2.0-870.2$ sudo make
make -C utils/fwparam_ibft
make[1]: Entering directory `/home/at-adm-wsg-alexoum/Desktop/open-iscsi-2.0-870.2/utils/fwparam_ibft'
cc -O2 -g -fPIC -Wall -Wstrict-prototypes -I../../include   -c -o fwparam_ibft.o fwparam_ibft.c
cc -O2 -g -fPIC -Wall -Wstrict-prototypes -I../../include   -c -o fw_entry.o fw_entry.c
cc -O2 -g -fPIC -Wall -Wstrict-prototypes -I../../include   -c -o prom_lex.o prom_lex.c
<stdout>: In function ‘yylex’:
prom_lex.l:91: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
prom_lex.l: At top level:
<stdout>:1622: warning: ‘yyunput’ defined but not used
<stdout>:1665: warning: ‘input’ defined but not used
cc -O2 -g -fPIC -Wall -Wstrict-prototypes -I../../include   -c -o prom_parse.tab.o prom_parse.tab.c
cc -O2 -g -fPIC -Wall -Wstrict-prototypes -I../../include   -c -o fwparam_ppc.o fwparam_ppc.c
fwparam_ppc.c: In function ‘loop_devs’:
fwparam_ppc.c:352: warning: passing argument 4 of ‘qsort’ from incompatible pointer type
In function ‘strncat’,
    inlined from ‘fwparam_ppc’ at fwparam_ppc.c:439:
/usr/include/bits/string3.h:153: warning: call to __builtin___strncat_chk might overflow destination buffer
make[1]: Leaving directory `/home/at-adm-wsg-alexoum/Desktop/open-iscsi-2.0-870.2/utils/fwparam_ibft'
make -C usr
cat: /lib/modules/2.6.27-9-server/build/Makefile: No such file or directory
cat: /lib/modules/2.6.27-9-server/build/Makefile: No such file or directory
make[1]: Entering directory `/home/at-adm-wsg-alexoum/Desktop/open-iscsi-2.0-870.2/usr'
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o util.o util.c
util.c: In function ‘daemon_init’:
util.c:38: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
util.c: In function ‘oom_adjust’:
util.c:46: warning: ignoring return value of ‘nice’, declared with attribute warn_unused_result
util.c:52: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
util.c:53: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o io.o io.c
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o auth.o auth.c
auth.c: In function ‘get_random_bytes’:
auth.c:198: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
auth.c:206: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
auth.c:214: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o login.o login.c
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o log.o log.c
log.c:334: warning: ‘__dump_char’ defined but not used
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o md5.o md5.c
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o sha1.o sha1.c
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o iface.o iface.c
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o idbm.o idbm.c
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o sysdeps.o sysdeps.c
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o sysfs.o sysfs.c
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o iscsi_sysfs.o iscsi_sysfs.c
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o netlink.o netlink.c
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o initiator.o initiator.c
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o scsi.o scsi.c
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o actor.o actor.c
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o mgmt_ipc.o mgmt_ipc.c
mgmt_ipc.c: In function ‘mgmt_ipc_write_rsp’:
mgmt_ipc.c:459: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o isns.o isns.c
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o transport.o transport.c
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o iscsid.o iscsid.c
iscsid.c: In function ‘main’:
iscsid.c:430: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
iscsid.c:436: warning: ignoring return value of ‘ftruncate’, declared with attribute warn_unused_result
iscsid.c:438: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE util.o io.o auth.o login.o log.o md5.o sha1.o iface.o idbm.o sysdeps.o sysfs.o iscsi_sysfs.o netlink.o initiator.o scsi.o actor.o mgmt_ipc.o isns.o transport.o iscsid.o -o iscsid
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o strings.o strings.c
strings.c: In function ‘enlarge_data’:
strings.c:83: warning: format ‘%lu’ expects type ‘long unsigned int’, but argument 3 has type ‘size_t’
strings.c:83: warning: format ‘%lu’ expects type ‘long unsigned int’, but argument 4 has type ‘size_t’
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o discovery.o discovery.c
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o iscsiadm.o iscsiadm.c
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE util.o io.o auth.o login.o log.o md5.o sha1.o iface.o idbm.o sysdeps.o sysfs.o iscsi_sysfs.o ../utils/fwparam_ibft/fw_entry.o ../utils/fwparam_ibft/fwparam_ibft.o ../utils/fwparam_ibft/fwparam_ppc.o ../utils/fwparam_ibft/prom_lex.o ../utils/fwparam_ibft/prom_parse.tab.o strings.o discovery.o iscsiadm.o -o iscsiadm
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o iscsistart.o iscsistart.c
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE   -c -o statics.o statics.c
cc -O2 -g -Wall -Wstrict-prototypes -I../include -DLinux -DNETLINK_ISCSI=8 -D_GNU_SOURCE -static netlink.o util.o io.o auth.o login.o log.o md5.o sha1.o iface.o idbm.o sysdeps.o sysfs.o iscsi_sysfs.o initiator.o scsi.o actor.o mgmt_ipc.o isns.o transport.o ../utils/fwparam_ibft/fw_entry.o ../utils/fwparam_ibft/fwparam_ibft.o ../utils/fwparam_ibft/fwparam_ppc.o ../utils/fwparam_ibft/prom_lex.o ../utils/fwparam_ibft/prom_parse.tab.o iscsistart.o statics.o -o iscsistart
login.o: In function `resolve_address':
/home/at-adm-wsg-alexoum/Desktop/open-iscsi-2.0-870.2/usr/login.c:168: warning: Using 'getaddrinfo' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
make[1]: Leaving directory `/home/at-adm-wsg-alexoum/Desktop/open-iscsi-2.0-870.2/usr'
make -C kernel
cat: /lib/modules/2.6.27-9-server/build/Makefile: No such file or directory
make[1]: Entering directory `/home/at-adm-wsg-alexoum/Desktop/open-iscsi-2.0-870.2/kernel'
make[1]: *** No rule to make target `linux_2_6_', needed by `kernel_check'.  Stop.
make[1]: Leaving directory `/home/at-adm-wsg-alexoum/Desktop/open-iscsi-2.0-870.2/kernel'
make: *** [all] Error 2

```

---

### Post by oldos2er on 2009-01-27
Is there some particular reason you're not installing open-iscsi from the repositories?

---

### Post by RMSe17 on 2009-01-27
I have the following problems with the repository version:

[http://ubuntuforums.org/showthread.php?t=1052193](http://ubuntuforums.org/showthread.php?t=1052193)

I read this thread

[http://ubuntuforums.org/showthread.php?t=957696&highlight=iscsi](http://ubuntuforums.org/showthread.php?t=957696&highlight=iscsi)

which suggested that installing the new version fixes my problem.

But I am having problems getting the new version to install because it is in the source code form, and something is not working.

---

### Post by oldos2er on 2009-01-27
Try running 'make' without sudo. If there is documentation with the source code ( a docs directory, or README or INSTALL files), you might want to read it.

---

### Post by RMSe17 on 2009-01-28
Ok, problem solved.  I was missing something called "kernel headers."  Since I had no idea which Kernel I had, and synaptic gave me lots of choices, I looked up a way to find out what kernel I had by typing
```
uname -r
```
Then I got the kernel headers for that kernel.

Running the make command no longer generated any errors, neither did the make install.

The new version of Open-ISCSI is installed, and is running without giving me the errors from Status :)

Thanks

---

