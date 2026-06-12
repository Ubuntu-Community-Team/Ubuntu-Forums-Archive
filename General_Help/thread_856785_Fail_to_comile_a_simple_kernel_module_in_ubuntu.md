---
title: "Fail to comile a simple kernel module in ubuntu"
date: 2008-07-11
forum: General Help
---

### Post by Kunsheng Chen on 2008-07-11
I refer to resource online and try to compile a hello world module, the module file is hello-1.c and is under folder /home/kchen3 as below:

#include<linux/module.h>
#include<linux/kernel.h>

int init_module(void)
{
    printk(KERN_INFO "Hello world 1.\n");
   
 
    return 0;
}

void cleanup_module(void)
{
    printk(KERN_INFO "Goodbye world 1\n");
}

Also I have a Makefile in the same folder as following:

obj-m += hello-1.o

all:
	make -C /home/kchen3 M=$(PWD) modules

clean:
	make -C /home/kchen3 M=$(PWD) clean

Everything should be good to go yet when I run 'make' under the folder, error comes out:

make -C /home/kchen3 M=/home/kchen3 modules
make[1]: Entering directory `/home/kchen3'
make[1]: No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/home/kchen3'
make: [all] Error 2


I am a newbie but never thought to be stuck right after few steps.  I am using ubuntu 8.04 and the kernel source version is 2.6.25.  Any idea is appreciated. 

Kun

---

