---
title: "Cannot compile driver for Promise Fasttrak TX4200"
date: 2009-09-16
forum: Hardware
---

### Post by KhurramF on 2009-09-16
I have a jaunty system and have added a Promise Technologies Fasttrak TX4200 (soft)raid controller to it. Promise Technologies does not provide a driver for Ubuntu (only for RH and Suse), but it does provide a source for compiling it. The readme for the archive is as follows

> 1.) Please make sure you have linux kernel source code at ("/usr/src/linux"),
    and gcc version is 3.x by issuing Linux command :
    # gcc -v

2.) Set Kernel Compiling Environment on Linux System
    # cd /usr/src/linux/, if no linux exist, make a symbolic link to proper linux source directory.
    # make mrproper
    # Please note and make sure the release version string in "/usr/src/linux/Makefile" is match with the kenel version string you want to build with, else the build or the insert will be NOT properly.
    # "make config" or "make menuconfig" or "make xconfig"
	To set kernel config items as you wish as below,
	Processor type and features/Processor family
	Processor type and features/High Memory Support
	Processor type and features/Symmetric multi-processing support
    # make dep clean

3.) Goto directory where PROMISE driver codes is located and edit Makefile.

4.) Choose right parameters in Makefile, default parameter is GENERIC.
#$(CC) $(GENERIC) -c $*.c 
	$(CC) $(SuSE) -c $*.c 
#$(CC) $(TURBO) -c $*.c 
#$(CC) $(MDK) -c $*.c 
     ex:	GENERIC	 for most common case
		SuSE	 for SuSE linux common case
		TURBO	 for Turbo linux common case
		MDK      for Mandrake linux common case
 
    Or modify it for suitable your system, each item only one can be used.

5.) Issue Linux command to make FastTrak(UP/SMP) driver: ftsata2.o

    	#make or #make all

    If Dual Processor system

	#make smp

I followed the instructions 1 to 2. Then I tried to run "make" but it gave the following error:

> Makefile:57: *** Linux kernel source not configured - missing config.h.  Stop.

I have checked the /usr/src/linux folder for config.h files and have found the following:

./include/config/x86/find/smp/config.h
./include/config/i2o/config.h
./net/tipc/config.h
./fs/dlm/config.h

I think the first line should be the config.h file it is looking for. I have tried to run both "make" and "make smp", but the error message is the same.

Can someone please tell me how to fix this?

Thanks,
Khurram.

---

### Post by IcarusR on 2009-09-17
First off I'm not an expert at compiling kernels.

Did you run all the commands as it says ```
# "make config" or "make menuconfig" or "make xconfig"
```
I believe these create the kernel config that it says is missing

Did you do #4 editing the Makefile ?? ie make sure only #$(CC) $(GENERIC) -c $*.c  is uncommented

Might be worth reading up on Kernel recompiling.

Just my thoughts.

---

### Post by KhurramF on 2009-09-18
> **IcarusR said:**
> First off I'm not an expert at compiling kernels.

Did you run all the commands as it says ```
# "make config" or "make menuconfig" or "make xconfig"
```
I believe these create the kernel config that it says is missing

Did you do #4 editing the Makefile ?? ie make sure only #$(CC) $(GENERIC) -c $*.c  is uncommented

Might be worth reading up on Kernel recompiling.

Just my thoughts.
Thanks for your reply. I ran "make menuconfig" and then saved my changes (not that there were any). I am compiling the generic version, so the other options (in the Makefile) are commented out.

---

### Post by IcarusR on 2009-09-19
Have you searched through the kernel config to see if this is already built into the kernel ? It may just need selecting. A lot of Promise cards are supported.
I assume you have tried it to see if it 'just works'.

Fraid I can not help you with the original error.

---

