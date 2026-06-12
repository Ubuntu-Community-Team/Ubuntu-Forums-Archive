---
title: "[SOLVED] coretemp on kernel 2.6.22"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by crhumber on 2007-08-09
I recently compiled kernel 2.6.22 on my machine, which is supposed to include the coretemp package for reading temperatures of multi core processors.  However, when I type "sudo modprobe coretemp" I get "Module coretemp not found".  This module is supposed to be included in kernel 2.6.22 and I see the file coretemp.c in my /usr/src/linux-2.6.22/drivers/hwmon/ directory.  Is there anything I can do other than try to recompile the whole kernel?? thanks

---

### Post by 5-HT on 2007-08-10
Yup, coretemp's in mainline for 2.6.22. Did you check your .config? Apart from recompiling the whole kernel after making sure coretemp is selected, you could compile the module itself but would have to write a makefile (lots of how-tos are around).

---

### Post by crhumber on 2007-08-10
Thanks.  I checked my configuration and I did forget to include the coretemp module in my compilation.  I am now trying to compile the module itself.  I copied the coretemp.c file to a separate directory and made a Makefile like this:


obj-m    := coretemp.o

KDIR    := /lib/modules/2.6.22-custom2/build
PWD    := $(shell pwd)

default:
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

but when I type make I get the error:

# make
make: Nothing to be done for `default'.

According to the how to I was reading this error comes if you haven't compiled that kernel yet, but I have.  I can confirm by typing uname -r at the prompt and getting 2.6.22-custom2 out.  Any ideas?

---

### Post by 5-HT on 2007-08-10
Not too sure what's going on, but here are a few things that might help:
> **crhumber said:**
> 
    $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules
Does this line start with a tab?
Is /lib/modules/2.6.22-custom2/build pointing to the proper kernel source?
Did you do a make clean after compiling the kernel (might be the problem if so)? 
Issuing a 'make modules_prepare' in the top-level of the kernel source.

Another way of doing it: [http://kerneltrap.org/node/4203](http://kerneltrap.org/node/4203) (you'll need to make sure that coretemp is selected in your config prior to this)

---

### Post by crhumber on 2007-08-10
How do I know if /lib/modules/2.6.22-custom2/build is pointing to the correct directory?  I did not do a make clean after compiling the kernel.  Is that something that I can still do at this point?  If so, what is the command?  Sorry for all the questions...I'm still kind of a newbie!

---

### Post by 5-HT on 2007-08-10
About the build directory in /lib/modules/<kernel version>/: it's a symlink to your kernel build directory.
You can check that it's pointing to the right location (the directory in which you built the kernel) by issuing an 'ls -l /lib/modules/2.6.22-custom2/build'. If it's not pointing to the proper directory delete it, and create a proper symlink called 'build' pointing to the kernel build directory.

About make clean: nope, it's nothing you'd want to do as it migt have removed some required files in your build directory (the command is 'make clean' from the build directory).

Newb eh? Well you managed to roll your own kernel! That's something! The easiest thing may be to just to rebuild the whole kernel; I personally can't stand mucking around with makefiles and would take the rebuild route myself.
cheers,

---

### Post by crhumber on 2007-08-10
Thanks!  I actually got it to work using the link you provided.  Everything works great now.  thanks for the help!

---

