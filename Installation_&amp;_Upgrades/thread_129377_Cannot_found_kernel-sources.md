---
title: "Cannot found kernel-sources"
date: 2006-02-13
forum: Installation &amp; Upgrades
---

### Post by wint on 2006-02-13
Hello.

I need to install eagle-usb-2.3.2 driver...
I type: ./configure and in the end of process i'll see:

error: kernel-sources cannot be found!

I had install linux-sources... but program not found them... I don't know why...
Plese help me somebody...:confused:

---

### Post by taurus on 2006-02-13
Do you have /usr/src/linux pointing to the version of the kernel that you are using?

---

### Post by wint on 2006-02-14
In my /usr/src i have only linux-source-2.6.12.tar.bz2 file and some other directories not concerning business... That should I do?

---

### Post by wint on 2006-02-14
Up!... It's realy important to me understand how to do it...

---

### Post by az on 2006-02-14
To compile a kernel modules, you need to use the headers for the kernel comfiguration that you compiled.  If you were to install linux-source, configure it and then install it, you would need that source (or rather, the ehaders from that source) to build your additional module.

That is not what you did, however.  You did not compile your kernel, you used the prebuilt ubuntu kernel.  The headers for that kernel are available on your install cd.  Use synaptic to install the linux-headers-386 (if you did not install another kernel) package.

You should not need to do anything else.  The linux-headers-2.6.12-9-386 directory will be used as your linux source directory.
It is the fault of the package you are trying to install which does not make it clear that you need to install either the linux-source or the headers for your running kernel....

---

### Post by wint on 2006-02-14
Thank you!:)

---

### Post by az on 2006-02-14
I filed a bug to change the description of the linux-source and linux-headers packages so that people will not have the same problems as you describe.


[https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/31431](https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/31431)

---

