---
title: "HOWTO:Device Driver"
date: 2008-07-28
forum: Hardware
---

### Post by riluve on 2008-07-28
I am both a driver and Ubuntu noobe.

I have "written" a rudimentary driver with the following basic structure: 
```

static int __init test_init(void)
{	printk("init\n.");
	return 0;}
static void __exit test_exit(void)
{	printk("exit\n.");}
module_init(test_init);
module_exit(test_exit);

```
I compiled it with the 2.6.26 kernel source as a module (test.ko), on an Ubuntu  8.04 machine.

However, when I try to install the module with ```
insmod test.ko
```, I get the following error:
```
 -1 Invalid module format
```

If I try ```
modprobe test
```then modprode can not find the module at all.

Any ideas where I am going wrong - or are the instructions I have not compatible with Ubuntu?

.

---

### Post by nick_h on 2008-07-29
You may be better posting this in [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39).

You should also read the following book - [Linux Device Drivers](http://lwn.net/Kernel/LDD3/).

---

