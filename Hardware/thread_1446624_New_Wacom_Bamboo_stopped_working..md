---
title: "New Wacom Bamboo stopped working."
date: 2010-04-04
forum: Hardware
---

### Post by Rany Albeg on 2010-04-04
Hello , 

A while ago i compiled the new driver , and my tablet - new wacom bamboo pen CTL-460 - was working fine.

It suddenly stopped working.
I see that wacom.ko is located in all the directories with a kernel-version-name under /lib/modules

```
rany@rany-laptop:/lib/modules$ uname -r
2.6.31-20-generic
rany@rany-laptop:/lib/modules$ find -name "wacom.ko"
./2.6.31-16-generic/kernel/drivers/input/tablet/wacom.ko
./2.6.31-20-generic/kernel/drivers/input/tablet/wacom.ko
./2.6.28-16-generic/kernel/drivers/input/tablet/wacom.ko
./2.6.31-14-generic/kernel/drivers/input/tablet/wacom.ko
./2.6.31-19-generic/kernel/drivers/input/tablet/wacom.ko
rany@rany-laptop:/lib/modules$
```

Also tried to 'sudo depmod -a' in order to probe all the modules and create list of module dependencies.

This might be useful :

```
rany@rany-laptop:/lib/modules$ cd $(uname -r)
rany@rany-laptop:/lib/modules/2.6.31-20-generic$ cat modules.dep|grep wacom
kernel/drivers/input/tablet/wacom.ko:
kernel/drivers/input/touchscreen/wacom_w8001.ko:
kernel/drivers/hid/hid-wacom.ko:
rany@rany-laptop:/lib/modules/2.6.31-20-generic$
```

I appreciate your help.
Have a nice day.

---

### Post by Rany Albeg on 2010-04-07
*bump*

---

### Post by Ayuthia on 2010-04-10
Have you tried recompiling the driver?  Each time there is a kernel update, you have to rebuild it.  The wacom.ko that you might be seeing is the one that came with Ubuntu's kernel update.

---

### Post by Rany Albeg on 2010-04-14
Hi Ayuthia , 

I didn't recompile the driver.
In face I'm having trouble uninstalling it.
Can you help with that?

Thanks in advance , 
rany.

---

### Post by Favux on 2010-04-14
Hi Rany,

Ayuthia's right, the wacom.ko you're seeing in the new kernel directory may be the old default one that doesn't support your P & T.  If you have the wacom.ko from your first compile (what version was that?) you could try copying it into the new kernel directory and reboot and see if that works.  Otherwise you'll probably have to recompile.  You shouldn't have to uninstall the current driver, just compile over it.

---

### Post by Rany Albeg on 2010-04-24
Tablet is working fine now.
Recompiled the driver.

Thank you.

---

### Post by Favux on 2010-04-24
Good deal Rany!  Back in business.

---

