---
title: "Can't install LAN driver"
date: 2009-01-15
forum: Hardware
---

### Post by oygle on 2009-01-15
I'm trying to get a LAN driver installed for an ASUS mobo (inboard lan), and initially had some prblems with the [Bash script syntax error]("http://ubuntuforums.org/showthread.php?t=1039144") , and someone kindly advised what to do there, and can get the script to run.

The script is still returning

> Check kernel header files (not found) [ failed ]
Kernel header not found. Please install the linux header files
development package or crate a symbolic link from the
/usr/src/KERNEL_VERSION directory to linux
Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux

Installation of sk98lin driver module failed.

and although the lan seems to work 'out of the box', I'd prefer to have the corect driver installed, because the lan card is causing the computer not to power off (I disable the lan in bios and the computer powers off just fine, I enable it, no power off at shutdown, so somewhere a driver is not being unloaded properly, or not installed properly, etc), and also the lan doesn't come up (no light on hub/switch) without me having to manually bring it up.

What symlink do I need, and do I need to d/load Linux source ?

I have this

> $ ls -al /usr/src
total 44
drwxrwsr-x 11 root src 4096 2008-12-19 22:48 .
drwxr-xr-x 13 root root 4096 2008-12-19 22:59 ..
drwxr-xr-x 20 root root 4096 2008-09-23 03:48 linux-headers-2.6.24-19
drwxr-xr-x 6 root root 4096 2008-09-23 03:48 linux-headers-2.6.24-19-generic
drwxr-xr-x 20 root root 4096 2008-11-26 16:10 linux-headers-2.6.24-21
drwxr-xr-x 6 root root 4096 2008-11-26 16:10 linux-headers-2.6.24-21-generic
drwxr-xr-x 20 root root 4096 2008-12-04 19:49 linux-headers-2.6.24-22
drwxr-xr-x 6 root root 4096 2008-12-04 19:50 linux-headers-2.6.24-22-generic
drwxr-xr-x 22 root root 4096 2008-12-19 22:48 linux-headers-2.6.27-9
drwxr-xr-x 7 root root 4096 2008-12-19 22:48 linux-headers-2.6.27-9-generic
drwxr-xr-x 2 root root 4096 2008-12-19 22:48 nvidia-173.14.12
$ 

Oygle

---

### Post by oygle on 2009-01-15
Some instructions from [http://champagnes.blog111.fc2.com/blog-date-200805.html](http://champagnes.blog111.fc2.com/blog-date-200805.html)

```

sudo bash
cd /usr/src/
ln -s linux-headers-2.6.27-9-generic linux
cd /pathwherescriptis/
./install.sh

```

it displayed an error, a 'fail' on compiling the kernel. Looking at the tail end of the install log

> 
--
+++ Compile the driver
+++ ====================================
make: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
+++ Compiler error
--------


I have gcc installed. Do I need the 'build-essentials' package as well ?

This seems to be the section of code where it failed

```
	fname="Compile the driver"
	echo -n $fname
	message_status 3 "working"
	make $MAKE_CPU_FLAG >> $logfile 2>&1


	if [ ! -f $drv_name.o ]; then
		echo -en "\015"
		echo -n $fname
		message_status 2 "failed"

		make_dep
		fname="Compile the driver"
		echo -n $fname
		message_status 3 "working"
		make $MAKE_CPU_FLAG >> $logfile 2>&1
	fi


	if [ -f $drv_name.o ]; then
		cp $drv_name.o ../
		echo -en "\015"
		echo -n $fname
		message_status 1 "done"
	else
		echo -en "\015"
		echo -n $fname
		message_status 0 "error"
 		echo
		echo "An error has occurred during the compile proces which prevented "; \
		echo "the installation from completing.                              "; \
		echo "Take a look at the log file install.log for more informations.  "; \
		echo "+++ Compiler error" >> $logfile 2>&1
		echo $inst_failed
		cleanup
		clean
		exit 1
	fi
```

Oygle

---

