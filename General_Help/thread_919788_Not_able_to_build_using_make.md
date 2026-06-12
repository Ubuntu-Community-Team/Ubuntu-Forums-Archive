---
title: "Not able to build using make"
date: 2008-09-14
forum: General Help
---

### Post by akshata on 2008-09-14
Hi,
I have witten the following C program test.c for kernel 2.6 

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

### Post by mahuyar on 2008-09-14
You'll have a better chance of getting the answer quickly in the programming forum.  It's [here]("http://ubuntuforums.org/forumdisplay.php?f=39").

---

### Post by trekkie690 on 2008-10-18
dont you have to put in the make file that your using gcc
like 
CC = gcc
     $(CC) $(whatever thing is) -0.....

---

### Post by snova on 2008-10-18
No. The kernel build system handles that. Module-level Makefiles just append to particular variables and communicate them back to the top level Makefile, which then builds them appropriately.

---

### Post by mkrahmeh on 2008-10-18
> **akshata said:**
> Hi,
and the coressponding Makefile as

obj&#8722;m += hello&#8722;1.o
all:
make &#8722;C /lib/modules/$(shell uname &#8722;r)/build M=$(PWD) modules
clean:
make &#8722;C /lib/modules/$(shell uname &#8722;r)/build M=$(PWD) clean



don't know if this is the effect of the copy-paste of the script, but i think that the rules (make -C ...etc) have to be preceded with a tab space..right ?

---

