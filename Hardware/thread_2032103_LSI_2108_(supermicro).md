---
title: "LSI 2108 (supermicro)"
date: 2012-07-23
forum: Hardware
---

### Post by CromagDK on 2012-07-23
I have this controller which is not seen or installed by ubuntu.
It seems i need to compile the drivers for it.
I just seem to run in to problems with it.
That is what i need help with; or if anyone else have a good idea for this to work :)
The source is from [ftp://ftp.supermicro.com/driver/SAS/LSI/2108/Driver/Linux/v06.12.1/v06.12.1.zip](ftp://ftp.supermicro.com/driver/SAS/LSI/2108/Driver/Linux/v06.12.1/v06.12.1.zip)

The controller does seem to want megaraid, just not the one that comes with ubuntu i guess.

Some different information:

ubuntu@ubuntu:~/lsi/megaraid_sas-v00.00.06.12$ ls
dkms.conf  Makefile  Makefile.standalone  megaraid_sas_base.c  megaraid_sas_fp.c  megaraid_sas_fusion.c  megaraid_sas_fusion.h  megaraid_sas.h  patches  redhat_driver_disk
ubuntu@ubuntu:~/lsi/megaraid_sas-v00.00.06.12$ 


ubuntu@ubuntu:~/lsi/megaraid_sas-v00.00.06.12$ sudo make -f Makefile.standalone 
make V=1 -I/lib/modules/3.2.0-23-generic/build/drivers/scsi -C /lib/modules/3.2.0-23-generic/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
rm -f include/config/kernel.release
echo "3.2.14$(/bin/bash /usr/src/linux-headers-3.2.0-23-generic/scripts/setlocalversion /usr/src/linux-headers-3.2.0-23-generic)" > include/config/kernel.release
make -f /usr/src/linux-headers-3.2.0-23-generic/scripts/Makefile.asm-generic \
	            obj=arch/x86/include/generated/asm
set -e; : '  CHK     include/linux/version.h'; mkdir -p include/linux/; 	(echo \#define LINUX_VERSION_CODE 197134; echo '#define KERNEL_VERSION(a,b,c) (((a) << 16) + ((b) << 8) + (c))';) < /usr/src/linux-headers-3.2.0-23-generic/Makefile > include/linux/version.h.tmp; if [ -r include/linux/version.h ] && cmp -s include/linux/version.h include/linux/version.h.tmp; then rm -f include/linux/version.h.tmp; else : '  UPD     include/linux/version.h'; mv -f include/linux/version.h.tmp include/linux/version.h; fi
set -e; : '  CHK     include/generated/utsrelease.h'; mkdir -p include/generated/; 	if [ `echo -n "3.2.14" | wc -c ` -gt 64 ]; then echo '"3.2.14" exceeds 64 characters' >&2; exit 1; fi; (echo \#define UTS_RELEASE \"3.2.14\";) < include/config/kernel.release > include/generated/utsrelease.h.tmp; if [ -r include/generated/utsrelease.h ] && cmp -s include/generated/utsrelease.h include/generated/utsrelease.h.tmp; then rm -f include/generated/utsrelease.h.tmp; else : '  UPD     include/generated/utsrelease.h'; mv -f include/generated/utsrelease.h.tmp include/generated/utsrelease.h; fi
mkdir -p .tmp_versions ; rm -f .tmp_versions/*
make -f scripts/Makefile.build obj=scripts/basic
(cat /dev/null; ) > scripts/basic/modules.order
rm -f .tmp_quiet_recordmcount
make -f scripts/Makefile.build obj=.
(cat /dev/null; ) > modules.order
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
make: *** [default] Error 2
ubuntu@ubuntu:~/lsi/megaraid_sas-v00.00.06.12$


ubuntu@ubuntu:~/lsi/megaraid_sas-v00.00.06.12$ find /usr/src -name "bounds.*" -ls
 22339    1 -rw-r--r--   1 root     root          270 Apr 11 00:38 /usr/src/linux-headers-3.2.0-23-generic/include/generated/bounds.h
 16353    5 -rw-r--r--   1 root     root         4405 Apr 11 00:38 /usr/src/linux-headers-3.2.0-23-generic/kernel/bounds.s
ubuntu@ubuntu:~/lsi/megaraid_sas-v00.00.06.12$ 



ubuntu@ubuntu:~/lsi/megaraid_sas-v00.00.06.12$ cat Makefile.standalone 
SRC :=	$(shell if test -d /usr/src/linux >/dev/null 2>&1;           \
		then echo /usr/src/linux;                            \
	elif test -d /usr/src/linux-2.6 >/dev/null 2>&1;             \
		then echo /usr/src/linux-2.6;                        \
	elif test -d /lib/modules/`uname -r`/build >/dev/null 2>&1;  \
		then echo /lib/modules/`uname -r`/build;             \
	elif test -d /lib/modules/`uname -r`/source >/dev/null 2>&1; \
		then echo /lib/modules/`uname -r`/source;            \
	fi)


	CPPFLAGS += -I$(SRC)/drivers/scsi

	obj-m  := megaraid_sas.o

	megaraid_sas-objs := megaraid_sas_base.o megaraid_sas_fusion.o megaraid_sas_fp.o

default: 
ifneq ($(SRC),)
	make V=1 $(CPPFLAGS) -C $(SRC) SUBDIRS=$(PWD) modules
else
	@echo
	@echo Build Failed, Kernel Source/Headers Not Found!
	@echo Please install the kernel devel package.
	@echo
endif
cat 
clean:
	rm -fr .megaraid* megaraid_sas.mod.* megaraid_sas.ko megaraid_sas.o megaraid_sas_base.o megaraid_sas_fp.o megaraid_sas_fusion.o .tmp_versions module* Module* *~
ubuntu@ubuntu:~/lsi/megaraid_sas-v00.00.06.12$ 

ubuntu@ubuntu:~/lsi/megaraid_sas-v00.00.06.12$ cat Makefile
obj-m			+= megaraid_sas.o
megaraid_sas-objs	:= megaraid_sas_base.o megaraid_sas_fusion.o megaraid_sas_fp.o

ubuntu@ubuntu:~/lsi/megaraid_sas-v00.00.06.12$

Thanks alot.
/Cromag

---

