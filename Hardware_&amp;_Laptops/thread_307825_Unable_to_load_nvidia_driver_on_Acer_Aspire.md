---
title: "Unable to load nvidia driver on Acer Aspire"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by alion on 2006-11-27
I installed Ubuntu Edgy on my Acer Aspire 9300 laptop(Turion64, x2)

#uname -a
Linux 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/LInux

It looks like nvidia-kernel-common package is pre-installed.So I installed nvidia-glx package.

And finally:
```
#sudo nvidia-glx-config enable
I get the error:
"Error: unable to load nvidia kernel driver!Be sure to have installed the nvidia driver for your running kernel"
```

Should I install nvidia-glx-dev and compile a driver manually?
Is there more simple way to save a time?

---

### Post by Jimmey on 2006-11-27
Did you install the restricted kernel modules?

> sudo apt-get install linux-restricted-modules-$(uname -r)

---

### Post by alion on 2006-11-27
Yes, I believe they were installed automatically...

---

### Post by Jimmey on 2006-11-27
Do you have more than one kernel?

If there's more than one kernel in Grub's menu.lst, try booting another one.

---

### Post by alion on 2006-11-27
Yes, I tried to do so - the same error...
It looks like I need to try to compile nvidia manually...Are there any instructions?

---

### Post by cutlerite on 2006-11-28
I am having the same problem!  I am getting:

unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.

---

### Post by cutlerite on 2006-11-28
nevermind.  this works:

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy")
:)

---

### Post by alion on 2006-11-29
on 32-bit version of Ubuntu it doesn't work however. But on 64-bit one it works like a charm :D . Thanks a lot!

---

### Post by Suzan on 2006-11-29
Do you updated from Dapper to Edgy?

Because in Edgy the default kernel for 32bit installations is the generic-kernel.

Please install the generic-kernel:
linux-image-2.6.17-10-generic
AND the fitting restricted-modules:
linux-restricted-modules-2.6.17-10-generic

Start your system with that kernel and install the package nvidia-glx an do a

sudo nvidia-glx-config enable

in the terminal and restart your x-server.

---

### Post by alion on 2006-11-30
Thanks, Suzan, but in my case it was the lack of appropriate driver in ubuntu's repository, I dowloaded it from NVIDIA site and compiled manually

---

