---
title: "raid loadable kernel module help"
date: 2005-11-29
forum: Hardware &amp; Laptops
---

### Post by vb7prog on 2005-11-29
I could use some help. I have a raid card. In the readme it made me recompile the kernel and lots of crazy things. I ended up with this file ftsata2.o and I believe this is a kernel loadable module. The system doesn't seem to automatically load the module. when i do modprobe ftsata2.o it says file not found or similar to that. I can use insmod ftsata2.o fine, but again its being manually loaded. How can I get it to load automatically.

2nd is there a way to have fstab.conf processed again after booting, like running it manually because of changes? Because I can mount the ntfs drive fine once the driver is loaded but I want the disk to be readable by all users but using the mount cmd it becomes only readable to root.

PS here is the readme (if it helps )of the raid card drivers and I just don't understand why i had to recompile the kernel ...?

/**********************************************************************************
*   PROMISE FastTrak TX2200/TX2300/TX4200/TX4300/579/779 Series Linux Driver README
*
*   PROMISE Linux support team <support@promise.com.tw>   2005/02/14
***********************************************************************************/
	
How to make Driver Module (UP/SMP) of FastTrak , and load it?

1.) Please make sure you have linux kernel source code at ("/usr/src/linux"),
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

6.) Be sure to load scsi_mod.o before "insmod ftsata2.o".

7.) You can copy this module to /lib/modules/2.4.x/kernel/drivers/scsi/
    as current kernel's modules location.

8.) Issue "cat /proc/scsi/ftsata2/x" (x is a SCSI host number) to get the
    RAID array status.

---

### Post by vb7prog on 2005-11-29
ok i have a makeshift way that seems to work

I made a shell script in /etc/rc2.d/S08myscript


then in there i put

insmod ftsata2
mount -t ntfs -o uid=myuser,guid=users /dev/sda1 /mnt/sata


well hope this helps others then.

---

