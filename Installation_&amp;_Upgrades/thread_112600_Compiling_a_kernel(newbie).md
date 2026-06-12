---
title: "Compiling a kernel(newbie)"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by ashrack on 2006-01-04
Could some1 explain to me what is the difference between the following commands for compiling a kernel and which one is better and why... Since am trying to understand all of the commands:

```
sudo make-kpkg clean

sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
```
This method is used in this HOWTO:
[http://ubuntuforums.org/showthread.php?t=85064](http://ubuntuforums.org/showthread.php?t=85064)

and

```
make bzImage install modules modules_install
```
from this HOWTO:
[http://ubuntuforums.org/showthread.php?t=75443&highlight=suspend2](http://ubuntuforums.org/showthread.php?t=75443&highlight=suspend2)

And also what does 'make-kpkg clean'  and 'make oldconfig' do?

IS there a method to use if I were to fuxar a newly created kernel so I would easily be able to change some settings in 'make xconfig' and then recompile it faster since I would only be changing one value?

edit:
changed menuconfig into oldconfig
made a typo B4

---

### Post by az on 2006-01-04
[QUOTE=ashrack]Could some1 explain to me what is the difference between the following commands for compiling a kernel and which one is better and why... Since am trying to understand all of the commands:

```
sudo make-kpkg clean

sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
```[/QUOTE]

Use kernel-package (make-kpkg) to compile the kernel and call it 2.6.12-custom and then put it inside a debian package so that I can install and remove it easily and safely.  Make a headers package like that, too.  (You need headers to build modules (drivers) if you do not have the full linux-source lying around (300megs of disk space)

[QUOTE=ashrack]
```
make bzImage install modules modules_install
```
from this HOWTO:
[http://ubuntuforums.org/showthread.php?t=75443&highlight=suspend2](http://ubuntuforums.org/showthread.php?t=75443&highlight=suspend2)
[/QUOTE]

Compile the kernel and install the modules.  You would need to remove everything by hand.

[QUOTE=ashrack]
And also what does 'make-kpkg clean' 
[/QUOTE]

If you compile some stuff, there are object files still there.  If you change some settings and want to recompile, using prebuild object files with a different configuration will bork.  Clean up the object files from a previous build.

[QUOTE=ashrack]
 and 'make menuconfig' do?
[/QUOTE]

Show me a menu of my kernel options so that I can play with them.  You need libncurses5-dev to do this.  I use menuconfig and not some fancy-smancy qt or gtk interface.  However, I can count on one hand the time I have compiled a kernel (maybe one and a half hands).  Usually, you compile it for nothing - the stock kernel has everything you need.  It's good clean fun, though.

[QUOTE=ashrack]
IS there a method to use if I were to fuxar a newly created kernel so I would easily be able to change some settings in 'make xconfig' and then recompile it faster since I would only be changing one value?[/QUOTE]

No.

---

### Post by ashrack on 2006-01-05
typed 'make menuconfig' instead of 'make oldconfig'

What is the point of running 'make oldconfig'? Since I can just choose in 'make xconfig'  which kernel config file to load???

So it's better ti use 'make kpkg' command then 'make bzimage' , right?
And why does in the guide says that recompiling a kernel if U made a mistake will make it faster:
> Most common failing is not getting all of the IDE drivers (and ext3 filesystem) compiled into the kernel during make menuconfig. If these are left out, the system will give a "Big Fat Error" on boot, or a "Kernel Panic". If you have to adjust any of these, the re-compile goes much faster, because it only has to compile the changes (step 14).
taken from:
[http://ubuntuforums.org/printthread.php?t=75443&pp=40](http://ubuntuforums.org/printthread.php?t=75443&pp=40)

---

### Post by ashrack on 2006-01-07
bump

---

### Post by ashrack on 2006-01-12
What is the point of using '--initrd'
I read the 'man' pages, but still don't know what the benefit is?

---

### Post by az on 2006-01-12
[QUOTE=ashrack]What is the point of using '--initrd'
I read the 'man' pages, but still don't know what the benefit is?[/QUOTE]


The debian package that make-kpkg will spit out will run a script to build an initrd for your new kernel.

An initrd (init Ram Disk) will detect hardware and load drivers for them on demand.  If you include all of those modules as kernel options, you do not need an initrd.  If you change your hardware, though, you need to rebuild your kernel or it will not boot.

Some filesystems (like LVM, I think) need to have an initrd set them up before you boot.

"typed 'make menuconfig' instead of 'make oldconfig'

What is the point of running 'make oldconfig'? Since I can just choose in 'make xconfig' which kernel config file to load???"

I think when you go from one version to another, make oldconfig will look to see if there are new options for you to configure instead of going through all of them by hand.



"So it's better ti use 'make kpkg' command then 'make bzimage' , right?"

It is more elegant.

"And why does in the guide says that recompiling a kernel if U made a mistake will make it faster:"

If you don't change anything it will work, since the kernel will only build what it had not previously build - it will not clean out the compiled object files.  If you change stuff, you will have to clean your object files and it will take the same amount of time as the first time.

---

### Post by ashrack on 2006-01-12
Tanx M8.
Thus far have learned a great deal about kernel compiling and have also compiled lots of working kernels by now.

But the following thing is still bugging me:
I use REISERFS and under REISERFS option in MENUCONFIG I've set * from the default M(module)
But now when I boot the kernel I get an error message:
```
FATAL:Module REISERFS NOT FOUND
```
BUt the systems works perfectly well than.
Why is that?

---

### Post by az on 2006-01-12
[QUOTE=ashrack]Tanx M8.
Thus far have learned a great deal about kernel compiling and have also compiled lots of working kernels by now.

But the following thing is still bugging me:
I use REISERFS and under REISERFS option in MENUCONFIG I've set * from the default M(module)
But now when I boot the kernel I get an error message:
```
FATAL:Module REISERFS NOT FOUND
```
BUt the systems works perfectly well than.
Why is that?[/QUOTE]

I would guess that the initrd is trying to load the reiserfs module, but it is not there.  Both the resons for it not being there and for it still working is that you compiled it into the kernel.

I guess the scripts which detect the need for the module and try to load it do not look to see if it is already compiled statically in the kernel.

---

### Post by ashrack on 2006-01-14
anyway to change this script behaviour?

---

