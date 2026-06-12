---
title: "Support for dual core, 64bit processors?"
date: 2006-07-13
forum: Hardware &amp; Laptops
---

### Post by johann_p on 2006-07-13
I am planning to buy a new computer and I wonder what support for "newer" processors and chipsets I can expect. I have heard for instance, that the default installation of Dapper does not support both cores of dual core processors. Is that true? What do you expect to happen on one of the upcoming  Intel core2 processors?

What is the status of 64 bit support? I heard there are problems in Ubunte (e.g. Firefox plugins not working etc.).

It does not make much sense to buy computing power that is not used by the OS, so I would like to make sure in advance that Ubuntu supports this.

---

### Post by krazykirk on 2006-07-13
Isn't there a 64 Bit edition of Dapper? (If it's 64 bit..?) And also, by default Ubuntu doesn't use both cores, but you can get a version of the kernel (686) so it would use both kernels. I have a Hyperthreading processors, so i use the 686 kernel so can utilise both kernels.

---

### Post by johann_p on 2006-07-13
> **krazykirk said:**
> Isn't there a 64 Bit edition of Dapper? (If it's 64 bit..?) And also, by default Ubuntu doesn't use both cores, but you can get a version of the kernel (686) so it would use both kernels. I have a Hyperthreading processors, so i use the 686 kernel so can utilise both kernels.

Well Ubuntu is supposed to be the user-friendly Linux and I would rather not mess around with installing kernels etc. myself. I wonder why they do not just set up the system to use both cores from the start? As far as I know, other distros like Suse or Fedora do that. 

Regarding the 64 bit version my concern are things I heard about mixtures of 64 and 32 bit software that are not compatible and causing problems (e.g. a 64 bit Firefox not able to run the 32 bit Java plugin).

---

### Post by 3rdalbum on 2006-07-13
Installing the SMP kernel is easy, so it's not really much "messing around". I heard that some programs are incompatible with the SMP kernel, and that's why it's not installed by default.

Right now, support for 32-bit programs on 64-bit is not great. But really, unless you want to use more than 4 gigabytes of RAM, or you're doing intensive scientific work, you don't need a 64-bit operating system.

---

### Post by tseliot on 2006-07-13
> **johann_p said:**
> I have heard for instance, that the default installation of Dapper does not support both cores of dual core processors. Is that true? What do you expect to happen on one of the upcoming  Intel core2 processors?
That's true. You need to install a kernel (from Ubuntu's repositories) which has SMP enabled. It's deadly easy.

> **johann_p said:**
> What is the status of 64 bit support? I heard there are problems in Ubunte (e.g. Firefox plugins not working etc.).
Use Ubuntu 32bit, ii will make your life easier.

> **johann_p said:**
> It does not make much sense to buy computing power that is not used by the OS, so I would like to make sure in advance that Ubuntu supports this.
If you use an SMP kenrel you can enjoy your dual core CPU.

Using a 64bit OS should perform better if you need to use your computer as a server, handling databases, etc. A desktop user can't tell the difference (I use an AMD64 processor)

---

### Post by johann_p on 2006-07-13
> **3rdalbum said:**
> Installing the SMP kernel is easy, so it's not really much "messing around". I heard that some programs are incompatible with the SMP kernel, and that's why it's not installed by default.
Well, programs not being compatible sounds even less encouraging.

> 
Right now, support for 32-bit programs on 64-bit is not great. But really, unless you want to use more than 4 gigabytes of RAM, or you're doing intensive scientific work, you don't need a 64-bit operating system. I am exactly planning to upgrade my computer because I need lots of ram and am doing scientific work (otherwise I would just keep my old box :) )

When I read a recent comparison of Fedora, Suse and Ubuntu in a (printed) computer magazine mentioning these shortcomings just for Ubuntu but not the others, I got worried and wanted to confirm what they said here. 

Seems that given the requirements for my future hardware I am probably better off with Suse right now (I just switched to Ubuntu from Suse quite recently because after testing it on my old computer I grew to like it, especially the better and much faster.pre pet  package management)

---

### Post by hizaguchi on 2006-07-24
I'm running 64 bit Dapper on my laptop with a Turion X2.  The big problems for me so far are that the synaptics driver is acting funny with the 64 bit install (not a problem with 32 bit live CD) and my processor is running at half speed.  The touchpad is annoying on its own, but the half speed processor kinda eliminates the benefit of using the 64 bit OS.

---

### Post by herrdoktor330 on 2006-07-24
I have a question:

If you compile your own kernel for an athlon64 x2, what is the safe processor family option when you compile? Would you just use the 686 with SMP?

---

