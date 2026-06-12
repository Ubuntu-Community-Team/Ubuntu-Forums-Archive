---
title: "PepperPad3 keypad - driver needed"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by Pypasaur on 2007-06-03
Installed Ubuntu Feisty on the PepperPad3 ( [http://www.pepper.com/](http://www.pepper.com/) ).

The PepperPad3's nonstandard split keyboard requires a special driver. 
Fortunately, this driver is opensource -- it has been compiled on Fedora Core 4, but I don't know if it will compile under other systems.

Fortunatley, Pepper has opened up the source code (attached below) under the GPL.

pad3_kypd.c

How can the driver be compiled for Ubuntu ?

I'd love to continue using Ubuntu on my PepperPad3.
Thanks in Advance!

---

### Post by teaker1s on 2007-06-03
you need to compile it

[https://help.ubuntu.com/community/teaker1s?highlight=%28teaker1%29#head-7122eba654269ea93933b2ca057919c42ec2cd6d]("https://help.ubuntu.com/community/teaker1s?highlight=%28teaker1%29#head-7122eba654269ea93933b2ca057919c42ec2cd6d")

welcome to the forums

---

### Post by Pypasaur on 2007-06-03
> **teaker1s said:**
> you need to compile it

[https://help.ubuntu.com/community/teaker1s?highlight=%28teaker1%29#head-7122eba654269ea93933b2ca057919c42ec2cd6d]("https://help.ubuntu.com/community/teaker1s?highlight=%28teaker1%29#head-7122eba654269ea93933b2ca057919c42ec2cd6d")

welcome to the forums

Thanks! I followed the guide but hit a speedbump at the part about ./configure

I forgot to mention that this driver is a kernel module (it compiles to a .ko file)
Does that make it more complicated ?

The driver source file ( pad3_kypd.c ) resides within the PepperLinux kernel source tree in /drivers/input/keyboard/

It's supposed to compile into a .ko file:

pad3_kypd.c     >>>  pad3_kypd.ko 

In PepperLinux (kernel 2.6.12) , the finished module resides in:

/lib/modules/2.6.12-geode/kernel/drivers/input/keyboard/pad3_kypd.ko 

It  comes with a Kconfig file, too -- what's that for ?

Please bear with me, I am a complete newbie, and have no experience compiling kernel modules. 

What's the next step to get this kernel module compiled and plugged into the Ubuntu Kernel ?

Thanks in advance!

---

### Post by teaker1s on 2007-06-04
I'm not sure of the direct answer as I've used "module-assistant" and repositories and I'm using debian at the moment, But if your prepared to try something

```
sudo apt-get install module-assistant
``` (easy way to install kernel modules)

```
gksudo nautilus
``` (guessing that module assistant gets it's source from **usr/src/linux** so the tarball will need to be there I think

```
sudo module-assistant
```

If this doesn't work as you need then I would ask a mod to change your thread title to "Kernel module installation help"

---

### Post by Pypasaur on 2007-06-04
> **teaker1s said:**
> 
If this doesn't work as you need then I would ask a mod to change your thread title to "Kernel module installation help"

Thanks alot!
Module-assistant shows many modules, but unfortunately it won't show the keypad driver source file I'd like to compile.

I'm totally lost on what to do next.
Please help..
Thanks in advance...

---

### Post by teaker1s on 2007-06-04
If someone can suggest where module-assistant gets it's source from-you could possibly place the source in the appropriate folder.
I think you should ask a mod to change the title to kernel module installation required-it will get you more help hopefully:popcorn:

---

### Post by Pypasaur on 2007-06-04
> **teaker1s said:**
> If someone can suggest where module-assistant gets it's source from-you could possibly place the source in the appropriate folder.
I think you should ask a mod to change the title to kernel module installation required-it will get you more help hopefully:popcorn:


Thanks!
I have created a new thread that states the problem more clearly:

[http://ubuntuforums.org/showthread.php?t=464584](http://ubuntuforums.org/showthread.php?t=464584)

Thanks

---

