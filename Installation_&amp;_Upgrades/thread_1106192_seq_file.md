---
title: "seq_file"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by overflow_ on 2009-03-25
Hello!
I need to write a program that uses the virtual directory /proc.
So I use the seq_file interface, but the compiler cannot find seq_file. I have found it in the source code of any version of kernel Linux in kernel.org, but I don't have it in my directories, even if I have compiled my current kernel (2.6.27-7) from there.

Do I have to install any package?
Is there and other interface and probably the seq_file interface is not still supported?
Any tips?

---

### Post by Anthon on 2009-03-25
sudo apt-get install linux-headers-generic
and after that
ls /usr/src/linux-headers*/include/linux/seq_file.h
to include you probably need to specify the directory as an option to gcc ( -I /usr/src/linux-headers-<YOURKERNELVERSION>/include )
and use 
  #include <linux/seq_file.h>
in your program

---

