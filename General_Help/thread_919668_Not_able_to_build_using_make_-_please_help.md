---
title: "Not able to build using make - please help"
date: 2008-09-14
forum: General Help
---

### Post by akshata on 2008-09-14
Hi,
    I have witten the following C program test.c

#include <linux/module.h> 
#include <linux/kernel.h> 
int init_module(void)
{
printk(KERN_INFO "Hello world 1.\n");
return 0;
}
void cleanup_module(void)
{
printk(KERN_INFO "Goodbye world 1.\n");
}


and the coressponding Makefile as

obj&#8722;m += hello&#8722;1.o
all:
make &#8722;C /lib/modules/$(shell uname &#8722;r)/build M=$(PWD) modules
clean:
make &#8722;C /lib/modules/$(shell uname &#8722;r)/build M=$(PWD) clean


When i run a make command in the same directory i get the following output
make: Nothing to be done for 'all'


The test.ko file is not getting created. Please can anyone tell me what the problem is and how to rectify it?

Thanks,
Akshata

---

