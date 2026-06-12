---
title: "Shows Lesser amount of RAM"
date: 2009-04-11
forum: Hardware
---

### Post by dagarshali on 2009-04-11
Hi,
I recently added 4Gb of ram to my computer and when i check the system monitor, it says 3Gb of ram and not 4Gb. But, when I go to the bios and check, it shows 4Gb. Where did the other 1Gb go?

the result of uname -a is

> Linux Gundanna 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux

and the result of top is

> top - 17:56:57 up 6 min,  2 users,  load average: 0.09, 0.24, 0.13
Tasks: 120 total,   1 running, 119 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.9%us,  3.2%sy,  0.0%ni, 93.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3101868k total,   641344k used,  2460524k free,    17216k buffers
Swap:  3317380k total,        0k used,  3317380k free,   203704k cached



any help would be greatly appreciated..

cheers,
vishwa

---

### Post by ajmorris on 2009-04-12
hi there,
currently the default ubuntu 32bit linux kernel does not support the full 4gb RAM, depending on your system you will get 3.1 to 3.5gb instead. This may have been changed recently, im not sure, however, in the past, the only way to get access to the full 4gb RAM is by running the server kernel. To install it, run the following:
```
sudo apt-get install linux-server linux-headers-server
```
Alternatively, you could compile and configure your own kernel... (this is quite advanced)

Just to explain it, and as to why the server kernel supports the full amount of RAM...
A 32bit OS doesnt give you access to the full 4gb because some of your address space is reserved for system functions. The ubuntu server kernel has PAE support in it, however, the desktop kernel does not. Essentially, PAE is something in most newer CPUs, that allows IA-32 CPUs to address up to 64gb of physical memory. So if you are compiling your own kernel, you need to enable PAE in it. Another option with compiling your own kernel, is to take the .config file from the desktop kernel, and load that into the kernel source, and just enable PAE in that, so you are using the default ubuntu desktop kernel + PAE.
Be warned, if you have an nvidia graphics card, they can *sometimes* be a pain to install against the server kernel, as it has Xen Virtualization enabled.

Also, if your 32bit CPU does not support PAE, all of this would be for nothing... So to check if your CPU supports PAE, run the following:
```
egrep '(pae)' /proc/cpuinfo
```
If the output returns nothing, then your CPU does not support it, if it returns a whole list of cpu flags, double check that pae is in there, if so, that means your CPU supports PAE.

AJ

---

### Post by Zoowey on 2009-04-14
> **ajmorris said:**
> hi there,
currently the default ubuntu 32bit linux kernel does not support the full 4gb RAM, depending on your system you will get 3.1 to 3.5gb instead. This may have been changed recently, im not sure, however, in the past, the only way to get access to the full 4gb RAM is by running the server kernel. To install it, run the following:
```
sudo apt-get install linux-server linux-headers-server
```
Alternatively, you could compile and configure your own kernel... (this is quite advanced)

Just to explain it, and as to why the server kernel supports the full amount of RAM...
A 32bit OS doesnt give you access to the full 4gb because some of your address space is reserved for system functions. The ubuntu server kernel has PAE support in it, however, the desktop kernel does not. Essentially, PAE is something in most newer CPUs, that allows IA-32 CPUs to address up to 64gb of physical memory. So if you are compiling your own kernel, you need to enable PAE in it. Another option with compiling your own kernel, is to take the .config file from the desktop kernel, and load that into the kernel source, and just enable PAE in that, so you are using the default ubuntu desktop kernel + PAE.
Be warned, if you have an nvidia graphics card, they can *sometimes* be a pain to install against the server kernel, as it has Xen Virtualization enabled.

Also, if your 32bit CPU does not support PAE, all of this would be for nothing... So to check if your CPU supports PAE, run the following:
```
egrep '(pae)' /proc/cpuinfo
```
If the output returns nothing, then your CPU does not support it, if it returns a whole list of cpu flags, double check that pae is in there, if so, that means your CPU supports PAE.

AJ

Thanks a bunch! I have x64 compatible hardware on my system but I cheaped out on my motherboard which doesn't work well with x64 and have been looking for a way to install the 32-bit server kernel for such a long time and have tried but failed. But thanks to your post I finally have it working perfectly with even my ATI driver and it even detects 5.9GB of RAM when x64 saw 5.8GB. I can't say how thankful I am.

---

### Post by wicky_ts on 2009-04-14
I have the same problem and my machine has a nidia graphic card. what will be the best option. I havent done compiling my own kernal befoure.

---

### Post by Zoowey on 2009-04-14
> **wicky_ts said:**
> I have the same problem and my machine has a nidia graphic card. what will be the best option. I havent done compiling my own kernal befoure.

I didn't compile anything. I simply installed the Ubuntu server kernel and have been running it for about a good 30 minutes I think with absolutely no problems.

But first make sure you check that your CPU supports PAE by inputing the code provided by ajmorris in his post, if so then run the commend to install the server kernel.

If you want to compile the kernel then I'm not the person to ask. And if it doesn't work for you, you can simply use your desktop kernel, it'll still be available in the boot menu. But the server kernel has been working wonderfully for me so far.

---

### Post by ajmorris on 2009-04-14
> **wicky_ts said:**
> I have the same problem and my machine has a nidia graphic card. what will be the best option. I havent done compiling my own kernal befoure.

just give the server kernel a go :)
There have been issues with compiling nvidia drivers into the server kernel because of the enabled xen virtualization, but you wont necessarily get any issues, if you do, we can work around them :)

AJ

---

### Post by wicky_ts on 2009-04-15
Installed the server kernal. Everything is working fine except for the nvidia GeForce 9300 graphics card. Seems to be the system cant detect it. now I am running with low resolution. At the start up I get a message saying that resolution is low. When I select the configure option nvidia card is not there. 
I down load the driver from nvidia site. but not very clear how to install it.
Now ram is ok, but need help to increase the screen resolution.

---

### Post by ajmorris on 2009-04-16
> **wicky_ts said:**
> Installed the server kernal. Everything is working fine except for the nvidia GeForce 9300 graphics card. Seems to be the system cant detect it. now I am running with low resolution. At the start up I get a message saying that resolution is low. When I select the configure option nvidia card is not there. 
I down load the driver from nvidia site. but not very clear how to install it.
Now ram is ok, but need help to increase the screen resolution.

downloading the drivers from the nvidia site shouldnt really make a difference... what happens error message do you get when trying to re-install the already installed drivers from the repos? If you get no error messages, try rebooting after they are installed, to use the newly installed module for the server kernel.

AJ

---

### Post by wicky_ts on 2009-04-16
Hii Aj

I was able to solve my problem. just need to uninstall the driver and install it again using syanptic.

thanks

wicky

---

