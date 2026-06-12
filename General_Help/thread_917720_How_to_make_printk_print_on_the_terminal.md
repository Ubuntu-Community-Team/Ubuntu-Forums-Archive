---
title: "How to make printk print on the terminal"
date: 2008-09-12
forum: General Help
---

### Post by dayanandasaraswati on 2008-09-12
Hello friends, I recently started reading the book "Linux Kernel Module Programming Guide" where i found this small piece of code printing hello world. 

```
#include <linux/module.h>       /* Needed by all modules */
#include <linux/kernel.h>       /* Needed for KERN_INFO */
int init_module(void)
{
        printk(KERN_INFO "Hello world 1.\n");
        /*
         * A non 0 return means init_module failed; module can't be loaded.
         */
        return 0;
}
void cleanup_module(void)
{
        printk(KERN_INFO "Goodbye world 1.\n");
}

```

On compiling the code using "make" and on insmod-ing this code, I'm not getting the hello world printed on screen instead its printing only on the log file "/var/log/messages". But i want printk to print on my terminal. I'm using ubuntu(gnome). Please help me.

---

### Post by sdennie on 2008-09-12
I'm not sure if that's possible.  However, it's very straightforward to just have a separate terminal and run the following:

```

tail -f /var/log/kern.log

```

(Or /var/log/messages).  That will set that terminal to "follow" the log and print the messages to that terminal as they are appended to the file.

---

### Post by dayanandasaraswati on 2008-09-12
Thank you so much..Your help was of great use..Thanks a lot!!

---

