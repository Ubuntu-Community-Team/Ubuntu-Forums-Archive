---
title: "Screen Brightness Problem on Lenovo Ideapad U460"
date: 2010-08-23
forum: Hardware
---

### Post by dgokhale on 2010-08-23
Hi..

I recently installed 64 bit 10.04 on my Ideapad U460. Most things seem to work fine but I am unable to control the screen brightness by using the Fn key and the Arrow keys (as it can be in Windows.)

The brightness can however be controlled using the Gnome Brightness applet.

I have tried googling the issue but have not found any solutions.

Does anyone know how to get the Fn key going??

Regards

D

---

### Post by treesurf on 2010-08-23
I am having the same problem with an Lenovo Y550.

---

### Post by dgokhale on 2010-08-24
I have reported this problem as a bug in launchpad ([Bug #623065]("https://bugs.launchpad.net/bugs/623065")).

It seems its an issue with the kernel not registering an event when those keys are pressed. I read that the issue is resolved in a 2.6.34 version of kernels that are yet to be released... Will try an install one and post an update

---

### Post by treesurf on 2010-08-26
Let us know if you have any success with any of the newer kernels.

---

### Post by dgokhale on 2010-08-27
I installed the [2.6.35-rc1-lucid kernel]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/") and that seems to solve the problem. I checked for the keymap and scan code and the FN+Up/Down keys do not register any scan code but the event is registered as an acpi_event.

Is there anything I can do to narrow down the problem to a specific program / module etc? 

Also can somebody check if what I have done resolves the problem on other Ideapad laptops?

---

### Post by treesurf on 2010-08-28
How do you go about installing that kernel?  Also, isn't there a backported version of the Maverick kernel that's available to install through a ppa?  Just wondering which route would be safer and/or better supported.

---

### Post by dgokhale on 2010-08-31
> **treesurf said:**
> How do you go about installing that kernel? 

Just follow the instructions given on [this page]("https://wiki.ubuntu.com/Kernel/MainlineBuilds") and you should be able to do it quite easily.


> **treesurf said:**
>  Also, isn't there a backported version of the Maverick kernel that's available to install through a ppa?  Just wondering which route would be safer and/or better supported.

Haven't really explored that. i tried the release candidate of Maverick through a live CD (it had 2.6.34 kernel version) but the brightness control didn't work in that either.

Maybe need to start moving backwards and find the first kernel that makes it work and then look for the exact problem. Priam facie it seems to me that its an ACPI issue. Though maybe I'm just plain wrong!

---

### Post by treesurf on 2010-09-01
Current backported kernel is 2.6.35.  I will try it later today.  Here is the PPA:

[http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu)


By the way, what is the difference between the "generic" and "generic-pae" kernel packages?

---

### Post by treesurf on 2010-09-01
Never mind, just did my own research to discover that PAE kernel is not necessary unless using over 4GB of RAM.  I'll give the generic kernel a try.

---

### Post by treesurf on 2010-09-01
I'm now running kernel 2.6.35-19 and can confirm that my brightness function keys do work again on a Lenovo Y550.

---

### Post by dgokhale on 2010-09-02
> **treesurf said:**
> I'm now running kernel 2.6.35-19 and can confirm that my brightness function keys do work again on a Lenovo Y550.

did you compile from source or got a deb package to install? and any idea on what has been patched such that it works?

---

### Post by treesurf on 2010-09-02
I installed a deb package from the maverick backport kernel PPA.  Unfortunately, I have now discovered that suspend does not seem to work properly with this kernel.

I have no idea what was patched so that the brightness keys now work.  I think the question really is what happened in the lucid kernel so that they DON'T work.  I had no problem with brightness keys prior to lucid.

---

### Post by treesurf on 2010-09-02
And now, strangely, suspend seems to be working again with no problem.

---

