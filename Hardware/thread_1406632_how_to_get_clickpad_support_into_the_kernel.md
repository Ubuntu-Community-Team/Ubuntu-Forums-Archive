---
title: "how to get clickpad support into the kernel?"
date: 2010-02-14
forum: Hardware
---

### Post by akos.maroy on 2010-02-14
I wonder what it would take to get Synaptic ClickPad support (Mac style single-click clickpad with simulated buttons) into the Ubuntu kernel?

a patch has already been written to make it work, see here: [http://www.spinics.net/lists/linux-input/msg06333.html](http://www.spinics.net/lists/linux-input/msg06333.html)

I can patch the stock kernel sources manually as needed, but that's always manual work. what is the best way to make this go into the ubuntu kernel package?

---

### Post by ngrilly on 2010-03-20
Here is some explanations about how to apply this patch and compile a new kernel:

[http://georgia.ubuntuforums.org/showthread.php?t=1388164&highlight=clickpad&page=2](http://georgia.ubuntuforums.org/showthread.php?t=1388164&highlight=clickpad&page=2)

---

### Post by akos.maroy on 2010-03-20
> **ngrilly said:**
> Here is some explanations about how to apply this patch and compile a new kernel:

[http://georgia.ubuntuforums.org/showthread.php?t=1388164&highlight=clickpad&page=2](http://georgia.ubuntuforums.org/showthread.php?t=1388164&highlight=clickpad&page=2)

well, I know how to apply it myself. my question is: what does one have to do to get it into the kernel source, so that you don't have to compile your own kernel all the time, but just use the official one..

---

### Post by nemilar on 2010-03-28
I'd like to bump this post.

These clickpads are becoming more and more popular (the new HP Mini series uses them) and it would be nice if we could get it put into Ubuntu mainstream.  

I dual boot my netbook and I am kind of stuck using windows most of the time, because even with some of the workarounds, it is a pain not to have the clickpad functioning in Linux.

Does anyone know how to go about getting this done?

---

### Post by akos.maroy on 2010-03-29
> **nemilar said:**
> I'd like to bump this post.

These clickpads are becoming more and more popular (the new HP Mini series uses them) and it would be nice if we could get it put into Ubuntu mainstream.  

I dual boot my netbook and I am kind of stuck using windows most of the time, because even with some of the workarounds, it is a pain not to have the clickpad functioning in Linux.

Does anyone know how to go about getting this done?

you mean bumping, or getting the clickpad working?

for the latter, see the patch here: [http://www.spinics.net/lists/linux-input/msg06333.html](http://www.spinics.net/lists/linux-input/msg06333.html)

---

### Post by CrippledCanary on 2010-04-07
How about telling that you are affected by 
[Bug 516329]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/516329")

Hopefully if enough people need it, it will be incorporated into the lucid kernel.

---

### Post by akos.maroy on 2010-04-08
> **CrippledCanary said:**
> How about telling that you are affected by 
[Bug 516329]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/516329")

Hopefully if enough people need it, it will be incorporated into the lucid kernel.

good idea - just did, let's hope it works..

---

