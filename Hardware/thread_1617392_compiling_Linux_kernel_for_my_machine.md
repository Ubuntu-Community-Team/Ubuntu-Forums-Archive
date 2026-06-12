---
title: "compiling Linux kernel for my machine"
date: 2010-11-09
forum: Hardware
---

### Post by pepsifx357 on 2010-11-09
I've got an Intel D945GCLF2D motherboard with an Intel Atom 330 processor.  I'm wanting to tweak the system out and compile a linux kernel just for it.  I've been studying the specs for the motherboard and processor so I would know what to activate and what to leave out.  I've compiled three kernels for different computers of mine and unfortunately, one way or another, I always get a kernel panic.

Are there any pointers and or advice any of you could give me so that I could finally be successful in compiling a kernel specific to this machine?

thanks

---

### Post by pepsifx357 on 2010-11-09
bump?

---

### Post by pepsifx357 on 2010-11-09
I've started with round one on this machine.  It has taken 4 hours so far and still not finished yet.

I went through the make gconfig this time instead of the ncurses one, thinking that it would make it easier...Nope.  If I have to do it again, I'll use make menuconfig.

There are so many options in the kernel, I didn't know enough about most of them to know whether or not to turn them off.

I tried my best to remove the one that I KNEW I wouldn't need.  But I really wish there was a more specific version of "How to compile a kernel" for people wanting to know what some of those options are.

---

### Post by pepsifx357 on 2010-11-09
So after about 4 hours and 30 minutes I canceled the compilation and tried it again, this time I went back to the make menuconfig and got rid of EVERYTHING accept the modules I needed for the motherboard and other various things that I though I might need.

2 hours later, still going.

I'm not sure if its just the Atom processor, but you'd think after removing EVERYTHING from the kernel options it would take less time to compile.

I'll try again tomorrow.

---

### Post by Ayuthia on 2010-11-09
What steps are you using to compile the kernel?  I know when I when through it using [this version]("https://help.ubuntu.com/community/Kernel/Compile"), it took over three hours to complete on my laptop.  I am not for sure what it is doing different from the standard version (which takes under an hour to compile).

---

### Post by pepsifx357 on 2010-11-10
My complete steps are:

1. Download the kernel from kernel.org (In this case it was 2.6.36)

2. Download the needed files (Build-essential fakeroot gcc ect)

3. Uncompress

4. sim link to /usr/src/linux

5. Make menuconfig (I got rid of everything except the drivers needed for my specific motherboard.  I used lspci to find what drivers I needed. There are a lot of options I know nothing about. Which is the biggest problem.)

6. make-kpkg clean

7. make-kpkg --initrd --rootcmd fakeroot --append-to-version $(date +%s) kernel_Image

8. sudo dpkg -i 

Number 7 is probably where some of my problems are coming from.  I'm actually going by the steps in "A Practical Guide to Ubuntu Linux" Third Edition.

I'm not exactly sure that the commands behind --append-to-version are correct.

After I let it compile overnight, I installed and got another kernel panic.  It's the same one I always get.  Something about cannot mount VSF something?  I think it has to do with the hard drive not mounting.

---

### Post by IcarusR on 2010-11-10
Have you tried using the original Ubuntu install kernel config file & remove or change the obvious stuff ?

```
bash:/usr/src/linux$ cp /boot/config-2.4.18.030320 .config
bash:/usr/src/linux$ make oldconfig
```

> There are a lot of options I know nothing about.

Try googling anything you don't understand.

If you get kernel panic look for the last thing that was loaded or done for the culprit. 
If can not see on the screen then boot with good kernel & check the log files for the failed boot.

This may also help...

> Since the 2.6.32 kernel, a new feature allows you to update the configuration to only compile modules that are actually used in your system:

make localmodconfig

from here

[https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way]("https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way")

Compiling kernel has always taken ages on the few occasions I have done it.

---

### Post by pepsifx357 on 2010-11-10
> **IcarusR said:**
> 

This may also help...



from here

[https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way]("https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way")

Compiling kernel has always taken ages on the few occasions I have done it.

So instead of using make menuconfig, I would use make localmodconfig?

---

