---
title: "TX4310 Sata controller Driver"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by vtoal on 2007-05-02
Hi!

I saw several posts regarding this driver, I am trying the do the install/compilation according the Promise's instructions but for a beginner like me - THEY SUCK - I could use some help:

Step 1: yah, np
Step 2: yepper - no issue either
Step 3: here my first error:
*****************************************************
victor@thome03:/usr/src/linux$ sudo make mrproper
scripts/Makefile.clean:17: /usr/src/linux-headers-2.6.15-28-server/drivers/infiniband/ulp/srp/Makefile: No such file or directory
make[3]: *** No rule to make target `/usr/src/linux-headers-2.6.15-28-server/drivers/infiniband/ulp/srp/Makefile'.  Stop.
make[2]: *** [drivers/infiniband/ulp/srp] Error 2
make[1]: *** [drivers/infiniband] Error 2
make: *** [_clean_drivers] Error 2
*****************************************************
after this of course non eof the subsequent things work. 

I am using Dapper 2.6.15-28-server - any idea out there what todo? I can't get beyond this one today

Victor
 
=============================
/**********************************************************************************
*   PROMISE FastTrak TX4310/579/779 Series Linux Driver Installation Guide
*
*   PROMISE Linux support team <support@promise.com.tw>   2006/03/30
***********************************************************************************/
	
How to make driver  for FastTrak & load it?

1.) Please ensure cc, the source compiler , version is above 3 by issuing Linux command :
    	# gcc -v
     If you do not install the compiler, you will not be able to built Promise driver. 
    
2.) Please ensure linux kernel source directory is "/usr/src/linux". 
	For SuSE EL9 platform, it always release its kernel source in /usr/src/linux-2.6.7-97.
		Please make a link to the appropriate directory, for example:
			# ln -s /usr/src/linux-2.6.7-97 /usr/src/linux
			
	For RHEL4 platform, it always release its kernel source in /usr/src/kernels/2.6.9-5.EL.??? which ??? means various kernel images.

3.) Setup Kernel Compile Environment
	For SuSE EL9, SuSE 10:
    		# cd /usr/src/linux/
   		# make mrproper
   		# cp arch/$(ARCH)/defconfig.??? .config
   		# Execute 'make' for a while about 5 sec. and then stop its execution. (Avoid below  make menuconfig fail...)
    		# Execute 'make menuconfig' & exit with configuration save.
    		# Execute 'make' for a while about 10 sec. and then stop its execution.
    		
    	For RHEL4:
    		DO NOTHING.
    
    	[1].  $(ARCH) means architecture, which is i386 or x86_64.
    	[2]. ??? is options to make choose, default, smp and bigmem, depend on your booting image.
    	 
4.) Check /lib/modules/$(UTS_RELEASE)/build directy was linked properly to /usr/src/linux. 
     UTS_RELEASE is the current version of your booting image. You can get it by issuing Linux command :
    	 #uname -r

5.) Goto directory where the PROMISE driver source was located.

5.) Issue Linux command to make FastTrak driver: ftsata2.o
	#make clean
    	#make or #make all

6.) Load PROMISE driver
	# modprobe -a sd_mod
	# insmod ftsata2.ko or # insmod ftsata2.o
	
7.) You can copy this module to /lib/modules/$(UTS_VERSION)/kernel/drivers/scsi/ for automatic load when boot system.
    
Note:
	1. Promise partial source can be adapted on kernel 2.4 & 2.6. 
	2. Different OS may has different kernel source location, please  do some modifications of above steps to fit their requirements.

---

