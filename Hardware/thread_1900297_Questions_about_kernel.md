---
title: "Questions about kernel"
date: 2011-12-26
forum: Hardware
---

### Post by JCoop on 2011-12-26
I own a Lenovo V570 laptop and recently switched the kernel to version 3.1.5. The reason for the switch is that this kernel is supposed to correct the freeze up after suspend/hibernation and it is supposed to be optimized for the intel hardware (graphics, networking, power, etc.) I am running Ubuntu 11.10. After switching, my wifi stopped working (wired connection works fine) and after looking on my system I discovered that the iwlagn driver module is now missing. I actually have a few questions related to this that I am hoping someone can answer. Before I get into that though, the most recent kernel I ran that worked without error was 3.1.3. My laptop uses an Intel i5 processor and the Intel hd 3000 graphics (one of the reasons I updated the kernel)and an intel centrino 6150 wireless N card. I updated the kernel off the Ubuntu ppa Kernel site using the headers and image for the precise OS. Everything else in the kernel appears to be working fine and reverting back to a previous kernel enables the driver and wifi. So my questions are:

1) Is there a way to re-install the iwlagn module manually?

2) Is there anyway to have the 3.1.5 kernel update like the mainline kernel did or will I need to manually apply updates and patches? Why is the 3.1.5 kernel not really advertised for people running hardware similar to mine (I came across it when researching intel graphics drivers)?

3)There are a lot of possible kernels. I have searched for an answer, but I haven't been able to find an explanation about why there are so many. Is each new kernel in the ppa an updated or improved version of the previous version number? Why are the mainline kernel restricted to version 3.0 thus far? Also, why does the OS name change after kernel 3.1.4 (from Oneiric to Precise)? Are the kernels optimized for Ubuntu 11 vs Ubuntu 12?

4) From what I have read, kernel 3.1.* is the series I need to be in to maximize the performance of my hardware. Also, 3.1.5 is supposed to be the one to have if using the 3.1 series of kernels? Does anyone know if this is correct? 

Finally, could someone explain to me why they keep such a backlog of previous kernels if each successive kernel is supposed to be more efficient. Thank you in advance for any information you can provide. Also, I am very interested in finding out how I can get involved in the Ubuntu kernel development process, so any information that is available on that would be great as well. Thanks again for your time.

---

### Post by JCoop on 2011-12-28
Well, this post sat for a long time with no attempts to answer any of my questions so I thought I would post what I found out and mark the thread closed. Maybe this will help someone else. Also, these answers are just the best that I could deduce. They may not be 100% correct.

1- The module can be installed manually, but it is difficult. This would probably not fix the broken status of the currently installed driver anyway.

2- Since the kernel is not technically listed as a stable build, any patches or updates would need to be installed manually. You could write a script that would be able to handle it probably.

3- I am still not sure why there are so many versions of each kernel, especially when some of those kernels are considered experimental. What I did find was the current 3.0 kernel is the currently accepted kernel for Ubuntu 11.10. The 3.1 kernel seems to be optimized for people using Intel HD graphics and also has a few power saving features. More info on this can be found at Phoronix. The 3.2 kernel merges the 3.1 changes and a few more and will be released officially with Ubuntu 12. There is already work on a 3.3 kernel that may include specific features for Ivy Bridge. 

4- Kernel 3.1 is optimized for Intel HD graphics, but it isn't necessary to have the 3.1.5 version. The successive version increases just incorporate various tweaks or bug fixes. For whatever reason, after 3.1.4 the iwlagn driver is broken. 

I hope this helps someone else who may have similar questions. These answers are just the result of hours of reading and making what appeared to be logical connections. If any of the information looks incorrect please make note of it.

---

### Post by alfonso78 on 2012-01-08
Hi,

I'm really not an expert on kernel, but it seems I'll need to play with it to fix my box.

Where do you find new kernels?

I have looked here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

and it seems 3.1.4 is the latest kernel released for 11.10 Oneiric.

The more recent versions are for Precise, which is Ubuntu 12.04 that will be released end of April 2012.

Is maybe the reason why you had problems?

cheers,

---

### Post by Lekensteyn on 2012-01-22
You usually want to avoid Ubuntu's mainline builds as they do not work well with out-of-tree modules (nvidia/fglrx drivers for example, those cannot be unloaded).

After that, there are two remaining options: use the kernel from Precise or build it yourself (PPAs are a third option, but the quality is unknown)

Using the Precise kernel seems the easiest one, it has currently has the 3.2 kernel. TO build a kernel yourself, see [http://askubuntu.com/q/89542/6969](http://askubuntu.com/q/89542/6969) or [http://askubuntu.com/a/95119/6969](http://askubuntu.com/a/95119/6969)

---

### Post by alfonso78 on 2012-01-22
> **Lekensteyn said:**
> TO build a kernel yourself

Hi Lekensteyn,

Finally I did build my own kernel. It's much easier than I thought...

more or less I followed this with some changes (the patches I needed to apply):
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

```
sudo apt-get install git-core kernel-package fakeroot build-essential libncurses5-dev

mkdir $HOME/kernel
cd $HOME/kernel
```

```
git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git

```

or an other git, depends on your needs. This is the mainline tree... afaik

```

cd linux

cp /boot/config-`uname -r` .config

```
note: since I installed other kernels from PPAs in the meanwhile, I explicitly copied the original kernel from Ubuntu 11.10:

```
cp /boot/config-3.0.0-12-generic-pae .config

```

Then download and apply patches (if you need to):

```
wget http://paste.debian.net/download/AAA
wget http://paste.debian.net/download/BBB
wget http://paste.debian.net/download/CCC

$ git am AAA BBB CCC
Applying: 
Applying: 
Applying: 

```

and continue:

```
yes '' | make oldconfig

make-kpkg clean

CONCURRENCY_LEVEL=`getconf _NPROCESSORS_ONLN` fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

```
if you need to test more kernels I suggest you change
--append-to-version= to something that tells you which one you are compiling

e.g.

```
CONCURRENCY_LEVEL=`getconf _NPROCESSORS_ONLN` fakeroot make-kpkg --initrd **[COLOR="Red"]--append-to-version=-someText[/COLOR]** kernel_image kernel_headers

```

this took about 40 mins for me

```
cd ..

sudo dpkg -i linux*.deb

```
In my case it run directly the new kernel but to make sure I
edited /etc/default/grub (don't forget update-grub after editing)

```
# I want to see the menu!
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3

```

```
update-grub
reboot
```

when you rebooted, you can see if you are actually running the new kernel with:

```
uname -a
```

somewhere in the output you should find **[COLOR="Red"]-someText[/COLOR]**

---

