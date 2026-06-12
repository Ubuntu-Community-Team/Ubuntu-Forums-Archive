---
title: "Does anything need enabled in the kernel for klogd"
date: 2008-08-31
forum: General Help
---

### Post by Syco54645 on 2008-08-31
Does anything need enabled in the kernel for klogd to work?   I made a new kernel from scratch and klogd is hanging on boot.  When running it from /etc/init.d/klogd it errors saying it cannot create a file in /var/run because it already exists.  In the generic ubuntu kernel it works fine.

Any help would be greatly appreciated.

-Syco54645

---

### Post by Rocket2DMn on 2008-08-31
You can check if it is running
```
ps aux | grep klogd
```
Should be /sbin/klogd I think (that's what it shows for me).

---

### Post by Syco54645 on 2008-09-01
it is not running.
the exact error is "mkfifo: cannot create fifo '/var/run/klogd/kmsg' file exists"

---

### Post by Rocket2DMn on 2008-09-01
OK, what kernel are you running?  Have you updated your system recently?  To check kernel version, post the output of
```
uname -a
```
When you say you made a new kernel from scratch, I assume you mean you compiled your own from the source at kernel.org?  It's possible you forgot something.  Here is the Master Kernel Thread if you are interested - [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by Syco54645 on 2008-09-01
Linux rickjames 2.6.24.3-aaov.1one #1 SMP PREEMPT Mon Sep 1 02:42:25 EDT 2008 i686 GNU/Linux

Like I said, this is my own kernel compile.
Here is the story in full.  I bought an Acer Aspire One Netbook and decided to replace the default Linpus Lite install with Ubuntu (actually working one the oneLinux team for this).  I decided to compile a custom kernel using the .config file from the Linpus kernel sources.  The kernel in linpus was 2.6.23.x so I used make oldconfig to get it up to the version of the sources that I was using.  In Linpus, klogd is not running, so I am assuming that it is a kernel config that is causing my issues.  I can either disable klogd or get it working, I would rather get it working.  I cannot find anything on google related to my problem and noone in #ubuntu seems to have any ideas either.

So now that you know the full story, maybe it will be easier to diagnose.

-Syco54645

---

### Post by Rocket2DMn on 2008-09-01
I think you would have to recompile the kernel with the option to use klogd.  Were you presented with the option to enable it, or did it just skip over it becaues it had previously been specified as disabled?  You may need to use make menuconfig so you can navigate around a bit to check the options you want, or you may consider just compiling the kernel entirely from scratch.
I don't know enough about configuring the kernel to try and get klogd to run otherwise (maybe it's possible to recompile only that portion, and/or use it as a module?).

---

### Post by Syco54645 on 2008-09-01
i did do a make menuconfig and could not find it.  i also looked in make xconfig and used the search with no luck.

---

### Post by Rocket2DMn on 2008-09-01
Can you please post the output of
```
ls -l /var/run/klogd/kmsg
lsmod | grep klogd
sudo modprobe -r klogd
sudo modprobe klogd
lsmod | grep klogd
```

---

### Post by Syco54645 on 2008-09-02
This is what i get, not too interesting i'm afraid.

```
frank@rickjames:~$ ls -l /var/run/klogd/kmsg
ls: cannot access /var/run/klogd/kmsg: No such file or directory
frank@rickjames:~$ lsmod | grep klogd
frank@rickjames:~$ sudo modprobe -r klogd
FATAL: Module klogd not found.
frank@rickjames:~$ sudo modprobe klogd
FATAL: Module klogd not found.
frank@rickjames:~$ lsmod | grep klogd

```

An interesting thing happened.  I stopped klogd when booted in the generic kernel (using bum) and restarted it and booted into my custom kernel and klogd no longer hangs at startup (but then again, it is not running now it appears), but I would still like to get to the bottom of this so that debugging is easier).

---

### Post by Rocket2DMn on 2008-09-02
I would have to say that if you used the options from another linux install which didn't have klogd running, then you are going to have to recompile the kernel with klogd enabled.  Maybe there is an easier way, but I don't know of it.  I will ask around the Beginners Team to see if anybody else knows more.  Good luck.

---

### Post by Syco54645 on 2008-09-02
> **Rocket2DMn said:**
> I would have to say that if you used the options from another linux install which didn't have klogd running, then you are going to have to recompile the kernel with klogd enabled.  Maybe there is an easier way, but I don't know of it.  I will ask around the Beginners Team to see if anybody else knows more.  Good luck.

I realize that it was disabled, but I cannot find it in make menuconfig anywhere.  Do you know how to enable it in the kernel?  I do not have a problem compiling the kernel again, I have done it so much recently.

---

### Post by Rocket2DMn on 2008-09-02
I linked you to the Master Kernel Thread earlier, here it is again - [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
That has detailed instructions on how to build a kernel from the source at kernel.org.  I'm not sure if you will want to skip step 8, or to do it then try to go back and re-enable necessary options.

---

### Post by ajmorris on 2008-09-02
hi there,
The user-space syslog call is provided by a function in the kernel called 'sys_syslog' which is needed for klogd. The kernel syslog call is called 'printk', try looking in your source for something along those lines... I'm not sitting at a linux box at the moment, so if you cannot find this, or someone else doesnt come along... ill have a poke around my source tonight when i get home... Although... i was under the impression that the sys_syslog function was enabled in the vanilla source that comes from kernel.org by default, and only wont be there if you disable it explicitly. 
 
AJ

---

### Post by Syco54645 on 2008-09-02
> **ajmorris said:**
> hi there,
The user-space syslog call is provided by a function in the kernel called 'sys_syslog' which is needed for klogd. The kernel syslog call is called 'printk', try looking in your source for something along those lines... I'm not sitting at a linux box at the moment, so if you cannot find this, or someone else doesnt come along... ill have a poke around my source tonight when i get home... Although... i was under the impression that the sys_syslog function was enabled in the vanilla source that comes from kernel.org by default, and only wont be there if you disable it explicitly. 
 
AJ

I am building using the ubuntu sources though.  not sure what is going on there.  I would think that it would be enabled by default.

---

### Post by ajmorris on 2008-09-04
ill keep looking in greater detail, but all i can find in my source at the moment is; 
Kernel Hacking --> Kernel Debugging

I don't know if that will help the problem at all...

---

### Post by Syco54645 on 2008-09-04
> **ajmorris said:**
> ill keep looking in greater detail, but all i can find in my source at the moment is; 
Kernel Hacking --> Kernel Debugging

I don't know if that will help the problem at all...

I turned that on and it did not help.  There is very little documentation on the web for klogd as well.

---

### Post by ajmorris on 2008-09-05
what architecture are you using?

---

### Post by Syco54645 on 2008-09-20
> **ajmorris said:**
> what architecture are you using?

sorry it has been a while since i replied.  i am using x86 architecture.

---

