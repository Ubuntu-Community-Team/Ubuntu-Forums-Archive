---
title: "problem with p4-clockmod (no such device)"
date: 2006-11-01
forum: Hardware &amp; Laptops
---

### Post by pipolas on 2006-11-01
Hello,
I have a celeron M and I want to use p4-clockmod because my computer is too hot.
I do

    > sudo modprobe p4-clockmod

but I have

    > pipolas@pipolas-laptop:~$ sudo modprobe p4-clockmod
    Password:
    FATAL: Error inserting p4_clockmod (/lib/modules/2.6.18.1/kernel/arch/i386/kernel/cpu/cpufreq/p4-clockmod.ko): No such device
    pipolas@pipolas-laptop:~$
I use the kernel 2.6.18.1, and i have activate p4-clockmod at the compilation
In /lib/modules/2.6.18.1/kernel/arch/i386/kernel/cpu/cpufreq, I have "p4-clockmod.ko.

I have the same problem with the kernel 2.6.17(edgy eft kernel)

What can I do for resolve this problem.
thanks a lot and sorry for my bad english (i am french)
pipolas

---

### Post by patrickfromspain on 2006-11-01
maybe your celeron M doesn't support that at all??

I have a Celeron M 370 (1,5GHz) and it works very well with p4-clockmod :S

---

### Post by pipolas on 2006-11-02
Thank you.

I have doing a lot of test and, i'm sure that my computer support that.

I don't know what to do and my computer is hot and make a lot of noise

Thank you
pipolas

---

### Post by pipolas on 2006-11-02
Up??

---

### Post by patrickfromspain on 2006-11-02
I really can't say much... maybe you could cry ubuntu 6.06 and see if there it works..

By the way, what celeron M have you?

---

### Post by pipolas on 2006-11-02
ok, I will test ubuntu dapper.

I have a celeron M 310 (1.2 ghz)

---

