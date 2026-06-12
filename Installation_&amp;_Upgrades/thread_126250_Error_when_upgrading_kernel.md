---
title: "Error when upgrading kernel"
date: 2006-02-06
forum: Installation &amp; Upgrades
---

### Post by christhemonkey on 2006-02-06
Im trying to get a kernel with full preemption enabled using [this guide]("http://www.ubuntustudio.com/wiki/index.php/Breezy:Vanilla_Kernel_With_Realtime_Preemption")
But after i have compiled and installed, when i restart, it spews out a load of stuff about the usage of modprobe and insmod, then says:
```
ALERT! /dev/hda1 does not exist. Dropping to a shell!
```

My hard drive is ext2fs which i have enabled as built-in to the kernel (as opposed to a module) and it still doesnt work!

Many thanks in advance for your help!

---

### Post by ::DoGG:: on 2006-02-06
It would be helpfull id You could post the messages about modprobe (insmod ?) ypou mentioned, probably something is messed up in the kernel with modules for block devices and filesystem support, did You make "make modules" and "make modules install" after creating kernel image ??
Send the console messages and i will try to help You as much i can.

---

### Post by tseliot on 2006-02-06
Did you build the support for ext2fs in the kernel? If you built it as a module it won't work.

This means that you have to recompile the kernel.
When you use menuconfig do this:
[QUOTE=]Get to "File Systems".

Select your filesystem (ext3, reiserfs, etc.) with the cursor.( ext3 is the filesystem used by Ubuntu by default, so if you chose automatic partitioning when you installed Ubuntu Hoary then "ext3" is definitely your filesystem)

Then press the spacebar on the desired filesystem (a "*" will appear beside it). (Make sure there's a "*" beside it instead of a "M". In this way the support for you filesystem will be built directly in the kernel instead of being built as a module and you will not get a "kernel panic")

For example:
select "ext3 journalling filesystem support" and press the spacebar (a "*" will appear beside it).

Press the right arrow and select exit.[/QUOTE]

---

### Post by christhemonkey on 2006-02-06
OK, the errors it gives are (well most of them, were kind of alot, so just selected highlights!)

```
insmod: error inserting '/lib/modules/2.6.15.2-rt-50studio/kernel/drivers/video/console/bitblit.ko : -l Unkown symbol in module
(says the same thing for a couple of other modules like cursor.ko)
modprobe: invalid option -- b
Usage: modprobe [-v] [-dir_name] etc.....
```

In the howto it never mentioned make modules install, you can read what i did [here]("http://www.ubuntustudio.com/wiki/index.php/Breezy:Vanilla_Kernel_With_Realtime_Preemption")
It does say something about ```
make-kpkg --modules_image 
```though...

---

### Post by LordBug on 2006-02-06
"Unknown symbols" is, from what I've seen, typically caused by skipping the "make modules_install" part of the kernel compile.

---

### Post by christhemonkey on 2006-02-07
ok cheers i'll try doing that then!
Do i need to be in the /usr/src/linux directory?

---

### Post by christhemonkey on 2006-02-07
ok, that didnt work, thanks anyway though! I am going to try following the guide [that someone has posted]("http://www.ubuntuforums.org/showthread.php?t=85064&highlight=kernel+compiling") and taking in advice your advice. Any help still appreciated!

---

### Post by wrtrdood on 2006-02-07
Double-check the /boot/grub/menu.lst entry for the new kernel.  It sounds like the root value is wrong.

Given what you've said about the modules, it would appear that the package build was not complete or that the kernel was not installed correctly.

Another good reference is:
 [http://www.ubuntuforums.org/showthread.php?=84174l](http://www.ubuntuforums.org/showthread.php?=84174l)

---

### Post by christhemonkey on 2006-02-07
Thats a broken link :(
What should the root value be?
I think mine is something like 3,0?

---

### Post by christhemonkey on 2006-02-08
Bump? Anyone?

---

