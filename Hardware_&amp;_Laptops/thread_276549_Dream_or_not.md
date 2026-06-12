---
title: "Dream or not?"
date: 2006-10-13
forum: Hardware &amp; Laptops
---

### Post by hblaw on 2006-10-13
Drivers - Linux seems to make drivers and Kernels too close together, and every Kernel wants to include all drivers for hardwares? Correct?

Why not a 'core' Kernel with drivers that can be installed by 'apt-get', and the core and driver modules can be seperately developed/updated/maintained? (Affected by windows, whose core seems not to be updated so often like linux, any idea?)

Is this the case currently or Linux is doing entirely different things and aims to put hardware support in its core for other reasons?

HB

---

### Post by diepruis on 2006-10-13
This is unlikely to happen because Linux & the Windows kernel are entirely different. Linux is a monolithic kernel, but Windows uses a microkernel. AFAIK Linus Thorvalds is opposed to making Linux a microkernel, so in a nuthshell, yes you're dreaming ;)

---

### Post by hblaw on 2006-10-13
OK. OK. I really don't know what you are saying indeed. But I understand from your description that it is in the root of Linux that it cannot support hardware as easy as Windows?

---

### Post by diepruis on 2006-10-13
No.

The only thing that is keeping Linux from being as compatible as Windows is that Windows has more support, both from end-users and from hardware manufacturers.

The kernel and how it / drivers are implemented does not affect compatibility.

---

### Post by hblaw on 2006-10-13
I mean, if a driver module has to be recompiled for every update of kernel, how can hardware manufacturer implement drivers for linux even if they are willing to do so?

---

### Post by diepruis on 2006-10-13
They release the source code, then we can recompile them ourselves. Of course, most companies are unwilling to do this, which is one of the factors contributing to the problem with Linux compatibility. Besides, the actual compilation is not the problem (it doen't take that long) it's actually the many different kernels that presents a problem.

Companies can also release binary drivers like ATi does with their drivers, though I am unsure how that works. Some compromise of this form might be the answer.

I think I understand what you mean now. But, still, to have one common kernel to interface with the drivers will require a complete rewrite of Linux. That's what Windows, and other microkernels, does.

---

### Post by galileon on 2006-10-13
the ATI (or NVIDIA for that matter) need a kernel module to be present, and this kernel module itself is opensource, so it is compiled by the ubuntu team for eg, in linux-restricted-modules...

then the driver you actually download from ati or nvidia is simply the binary bit which sticks on the module already compiled in the kernel...

---

### Post by diepruis on 2006-10-13
That's kinda clever. Thanks for the explanation.

---

### Post by hblaw on 2006-10-14
Yes. That sounds solve the problem. So the 'module' you mentioned is a layer between Linux core and the binary dirver? However the core changes, the module provides a uniform interface for the driver, so that the hardware company can publish divers in CDs with their products which will not be affected by the development of Linux core. Right?

This sounds great and I guess the next step will be to provide a generic interface for the same type of hardware - i.e. the interfact for graphic cards are same for any kind of graphic card, so that it will be easier for hardware Co to write driver. ? Any thoughts? Or it has already been implemented in some form?

---

### Post by galileon on 2006-10-14
i dont know much about this, but when you run the nvidia installer on a custom compiled kernel, it first tries its own compiled modules, then complains it doesnt know the kernel, tries to download a "precompiled kernel interface", fails, then asks to compile one for your own kernel...

but if you use the drivers from ubuntu repositories, the restricted-modules has the kernel interface in it, and nvidia-glx is the binary driver...its all actually very user friendly in installation, only selecting stuff in synaptic - the snag is to activate it, which doesnt occur by default

thats when people start to dig in the /etc/X11/xorg.conf file to set driver to "nvidia" instead of "nv", the opensource driver.

actually, 

sudo dpkg-reconfigure xserver-xorg -fgnome 

gives a nice graphical configuration tool which worked everytime i tried it... even on some exotic resolution on a friend's computer (1440x900, whic kinda painful to configure manually in xorg.conf)...

---

### Post by diepruis on 2006-10-14
Now if we can only get all games to run on Linux...

---

### Post by hblaw on 2006-10-14
I don't think that's good enough for hardware company. I think they should be able to ship their driver CD with the hardware. I doubt this is the reason for not been able to get enough support from hardware Co.

If they can ship binary driver once and with no need to modify them just because Linux kernel has upgraded from 2.16.10 to 2.16.12, or from 2.16 to 2.18, etc, I guess they will be willing to compile a driver for linux users - why not? They have source code for windows, I should not be difficult for another platform (I assume), and most hardware ships with Mac drivers as well.

?

---

### Post by hblaw on 2006-10-14
My idea is, the OS platform is open source - this is OK. But we should know that hardware companies has valid reason to maintain confidential their tech specs and their technologies. We can leave the driver work to them, or to some interested third party providers. - We may not pay for Linux, but we pay for hardware. :)

But I would think maybe we can provide some generic driver in open source form. ... I'm really not a tech guy but I study law. I know how a company would think when they shall disclose something - especially high-tech companies.

---

### Post by galileon on 2006-10-14
its already like that, as i said, the task of including the "kernel interface" is on the ubuntu kernel team, who have already included it in the stock kernel's restricted-modules, the hardware manufacturer only provides the binary closed source driver which runs thru the interface...

btw as a law student, could you enlighten us on the problem of mixing closed source binaries with the GPL kernel? i have seen loads of discussions on this, but no one seems to have a definite answer...:(

the gpl is at: [http://www.gnu.org/licenses/gpl2.html](http://www.gnu.org/licenses/gpl2.html)

cheers

---

### Post by Rui Pais on 2006-10-14
> **hblaw said:**
> Yes. That sounds solve the problem. So the 'module' you mentioned is a layer between Linux core and the binary dirver? However the core changes, the module provides a uniform interface for the driver, so that the hardware company can publish divers in CDs with their products which will not be affected by the development of Linux core. Right?
You are mixing terminology and fail some concepts...
modules is how drivers are called on Linux. People still say driver sometimes cause the are used to Windows. 

As an example nv and nvidia are both modules/drivers for the same hardware, but nv is open source (you can access code) and nvidia is a binary already compiled. 
You need to install any of them, as in Windows, in order to use it, the difference from nv is that you can compiled from source, if you get the kernel code. 

Either as compiled by you or get a binary from modules/drivers makers or your distro repos, modules are file with extension .ko that must be installed, meaning copied to /lib/modules/<kernel_number_version>/ and eventually some extra files to /usr/lib... 

And thats the difference from Windows. You got a module.ko for each kernel installed (but on Windows you don't have different microkernels around didn't you?;)) That as nothing to do with changes on kernel code (but with the fact that you can have several and different kernels installed at same time)


Edit:
> If they can ship binary driver once and with no need to modify them just because Linux kernel has upgraded from 2.16.10 to 2.16.12, or from 2.16 to 2.18, etc In fact, thinking a little, is exactly the contrary of you said. I have use the same nvidia driver in all kernels on Ubuntu as on Gentoo, and on Windows you usually need different drivers versions if you have different Window versions, cause they change accordingly.

---

### Post by diepruis on 2006-10-14
> **Rui Pais said:**
> In fact, thinking a little, is exactly the contrary of you said. I have use the same nvidia driver in all kernels on Ubuntu as on Gentoo, and on Windows you usually need different drivers versions if you have different Window versions, cause they change accordingly.

Fglrx requires you to recompile the kernel module everytime you install a new kernel. But other modules, e.g. for wireless cards, require you to recompile from source for each new kernel.

---

### Post by Rui Pais on 2006-10-14
> **diepruis said:**
> Fglrx requires you to recompile the kernel module everytime you install a new kernel. But other modules, e.g. for wireless cards, require you to recompile from source for each new kernel.

Binary property modules are just installed, code is not available for compiling. Eventually the installer runs ldconfig, to link to libs installed but thats not compiling the module. 

A lot of the kernel code are modules code so generically compiling a kernel is, in great part, compiling modules. Thats just an efficient and safer way of doing things. It's better then just take pre-compiled modules from a previous kernel or some site, and ensures that any fixes are applied and everything needed is made. 

Taking your example, if you didn't compile the wireless module for a new kernel and just copied an old *.ko to the correct path it will in most cases work. It's just thats not the better way of doing it. Maybe it sounds strange to have such a replication across kernels but it make it work safer. I tried a slocate sata_sis.ko, randomly chosen, and got six modules and six copies on kernel src. It could work probably if they was just one installed on same place and any kernel use that one, but then it was necessary much more caution with compatibilities, one broken modules would be broken for all kernels and so on... There should be many others advantages of doing things that way (using different drivers versions for different kernels, fixs or extras for some specific kernel versions, etc.)

---

### Post by diepruis on 2006-10-14
Oh. So what your saying is that, if develelopers are **very** careful, writing modules for the Linux kernel isn't such a chore at all?

---

### Post by Rui Pais on 2006-10-14
Sorry, don't understand your question :( 

(but definitely not talking about developers at all. Just the differences between Linux and windows deals with modules)

---

### Post by diepruis on 2006-10-14
Nevermind, it's not important :)

---

### Post by hblaw on 2006-10-15
So I understand from Rui Pais that proprietary drivers/modules actually can be shipped on CD with products. Installation of these modules requires copying to certain folder and run ldconfig etc to link the modules with the lib. Otherwise re-compiling and updating modules/drivers is just for safety reasons.

So that's great!

I think dipruis is saying the above - if the developers are careful, there is no need to recompile for safety reason. And drivers therefore can be shipped with products!

---

### Post by diepruis on 2006-10-15
Yeah, more or less.

What I can't figure out is why they don't ship Linux drivers with their products **even if** the driver is open source. Look at RT61 for example. The whole driver is open source and works pretty well, yet there is no Linux folder on the CD, no instruction on how to install for Linux.

Now, the community helped me, and I eventually got my card running. But how difficult would it have been to write a few sentences and add a few kilobytes to a CD? I could have saved 2 days (no joking).

---

