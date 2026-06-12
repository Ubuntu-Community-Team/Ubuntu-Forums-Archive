---
title: "Problem installing modem driver"
date: 2005-07-12
forum: Hardware &amp; Laptops
---

### Post by stalflare on 2005-07-12
I have found the correct modem driver but it gives me a lot of troubles installing. I am a newbie to linux so probably this issue is due just to my total inexperience.

In the txt file for the driver this is what is written:

Installation
============

1. Unpack tar.gz package file:

	$ gzip -dc slmodem-2.9.X.tar.gz | tar xf -

2. 'cd' to package directory:

	$ cd slmodem-2.9.X

3. Review and edit 'Makefile' (if need):

   In many cases you will need to correct path to your local kernel
   source tree:

        KERNEL_DIR=/path/to/linux

   Default KERNEL_DIR is '/lib/modules/<kerne-version>/build'. Many Linux
   Distributions use directory '/usr/src/linux-<version>' also.

   Note: If you are using Linux kernel 2.4, only header files should be
         available for build in $(KERNEL_DIR)/include

   Another way to pass right value KERNEL_DIR is to use command line
   parameter while running 'make':

        $ make KERNEL_DIR=/path/to/linux ...

4. Run 'make' command to compile package:

	$ make

5. Install. As 'root' user run:

	# make install

   It will install:

   - application 'slmodemd' under '/usr/sbin' directory

   - hardware specific drivers (kernel modules) 'slamr' and 'slusb'
     under conventional kernel modules directory

   - character device nodes '/dev/slamr0-3' with major number 212
     (for pci modems) and '/dev/slusb0-3' with major number 213
     (for usb modems).

   - config modules for autoloading (by editing file '/etc/modules.conf')
     (only with 2.4 kernels)
=================================

I have tried running the command:

# make KERNEL_DIR=/lib/modules/2.6.10-5-386/kernel

I think that this is the directory where the kernel is... Anyways the command returns this error:

make -C modem all
make[1]: Entering directory `/home/lox/Desktop/slmodem-2.9.10.tar.gz_FILES/slmodem-2.9.10/modem'
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_main.o -c modem_main.c
make[1]: gcc: Command not found
make[1]: *** [modem_main.o] Error 127
make[1]: Leaving directory `/home/lox/Desktop/slmodem-2.9.10.tar.gz_FILES/slmodem-2.9.10/modem'
make: *** [modem] Error 2

From here I don't know what to do... I have tried to do #make install but it returns the same error, I am stuck...

Anyone can help?

Thanks a lot

---

### Post by az on 2005-07-12
Install build-essential and the linux-headers packages and you will be fine. 

Type uname -r to find out your kernel's version and install that version of linux-headers.

---

### Post by stalflare on 2005-07-12
Thanks a gain azz..

The install procedure still requires me to know the path to the kernel sources, I have tried to look for them but I haven't had a lot of luck.

Of two packages the first is the C compiler right? The header package what does it do?

Thanks again!

---

