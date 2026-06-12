---
title: "[SOLVED] Ubuntu Eee 8.0.4 CPU over clocking"
date: 2008-07-15
forum: Hardware
---

### Post by tinny on 2008-07-15
Hi

I have installed / configured [Ubuntu Eee]("http://www.ubuntu-eee.com/index.php5?title=Main_Page"). It appears that the CPU over clocking functionality is not setup by default with this Eee Ubuntu install.

cat /proc/cpuinfo always reports "cpu MHz		: 630.097"

I had a look at the change log / bug list and there is no mention of CPU over clocking.

[http://www.ubuntu-eee.com/index.php5?title=Changelog#Ubuntu_Eee_8.04](http://www.ubuntu-eee.com/index.php5?title=Changelog#Ubuntu_Eee_8.04)

I have setup CPU over clocking before (a past standard Ubuntu install) but was very disappointed that the functionality broke after a kernal header update.

Has anyone set this up reliably?

---

### Post by tinny on 2008-07-18
bump

I know there are very smart people out there! Please help :)

---

### Post by Dark_Stang on 2008-07-18
To be honest, I wouldn't recommend it. That being said, there isn't a way to overclock it in the bios?

---

### Post by tinny on 2008-07-18
> 
To be honest, I wouldn't recommend it.


This over clocking is common place on alternative Linux installs on the eee PC.

Here is the technique that I have followed in the past. 

[http://wiki.eeeuser.com/howto:overclockfsb]("http://wiki.eeeuser.com/howto:overclockfsb")

The problem is that this is a compiled kernel module and will stop working once the kernel headers are updated (I think this is what kills it)

BTW: My eee PC runs WAY better with this over clocking and doesn't get too hot etc...

---

### Post by Dark_Stang on 2008-07-18
So compile it then lock the current kernel and kernel header versions in synaptic so they never update...?

---

### Post by tinny on 2008-07-18
> **Dark_Stang said:**
> So compile it then lock the current kernel and kernel header versions in synaptic so they never update...?

Really??? How do I do that?

Will this conflict with any future Ubuntu updates?

---

### Post by warp99 on 2008-07-18
You don't have to lock the kernel version. Just recompile the module and install, it takes less than a minute. Instructions on how to compile the module are included with the source code. Just be sure to run 'make clean' before you run 'make' when recompiling against any new kernel that you upgraded.

After you compile the module in order for it to load on start-up you need to do two thing. First add the module to your modules list by issuing the following:

```
echo "eee" |sudo tee -a /etc/modules
```

then copy the eee.ko module you just built to the new kernel library:

```
sudo cp eee.ko /lib/modules/$(uname -r)/misc
```

---

### Post by tinny on 2008-07-18
> **warp99 said:**
> You don't have to lock the kernel version. Just recompile the module and install, it takes less than a minute. Instructions on how to compile the module are included with the source code. Just be sure to run 'make clean' before you run 'make' when recompiling against any new kernel that you upgraded.

After you compile the module in order for it to load on start-up you need to do two thing. First add the module to your modules list by issuing the following:

```
echo "eee" |sudo tee -a /etc/modules
```

then copy the eee.ko module you just built to the new kernel library:

```
sudo cp eee.ko /lib/modules/$(uname -r)/misc
```

You also need to add "eee" to /etc/modules right?

Yeah this is what I have done in the past, it just a little annoying.

Before reinstalling the kernel module I have to remove the existing one right? (had problems with this before)

```

modprobe -r eee

```

Correct?

---

### Post by warp99 on 2008-07-18
> **tinny said:**
> You also need to add "eee" to /etc/modules right?

If you've already done this you don't have to do this again. That's what the 'echo "eee" |sudo tee -a /etc/modules' command was for. So you can skip that one.

> Before reinstalling the kernel module I have to remove the existing one right?

No because you're building the new module against the new kernel so the module for the new kernel doesn't exist. Just make sure to copy the module into the new kernel library. You can set up a script to do this every time you upgrade the kernel. 

If you don't want to compile the module I've attached it to this post for the most recent kernel version (2.6.24-19-generic).

---

### Post by tinny on 2008-07-19
Cool thanks warp99!

---

