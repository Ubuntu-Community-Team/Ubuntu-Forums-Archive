---
title: "More RAM on 32 bit"
date: 2010-07-29
forum: Hardware
---

### Post by physic.dude on 2010-07-29
I use Ubuntu in 32 bit but I have 4GB or RAM and Ubuntu uses all of it, so I was wondering if i install more ram will my PC support 8GB?

---

### Post by MasterGamerJK on 2010-07-29
With a 32 bit OS your not going to get optimal performance out of anything over 4GB (even with a 3rd party program), you will have to use a 64 bit OS. As far as if your board will support it. Consult your mother boards documentation or google the boards name.

---

### Post by physic.dude on 2010-07-29
Well, is there a easy way to switch to 64 bit? All my hardware supports 64 bit, but I'm not sure if software such as Wine will be supported.

---

### Post by iponeverything on 2010-07-29
You can utilize RAM over 4 Gigs and stay 32 bit by installing the PAE kernel.

Do a google search on:

PAE vs 64 bit

For the pros, cons and benchmarks for PAE vs 64 bit.

Benchmarks:

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
===

The easiest way to upgrade to 64bit is backup /home do a clean install then restore /home after recreating the accounts.

---

### Post by physic.dude on 2010-07-29
> **iponeverything said:**
> You can utilize RAM over 4 Gigs and stay 32 bit by installing the PAE kernel.

Do a google search on:

PAE vs 64 bit

For the pros, cons and benchmarks for PAE vs 64 bit.

===

The easiest way to upgrade to 64bit is backup /home do a clean install then restore /home after recreating the accounts.


Well I did a quick Google search and found this.

"In Linux, any distro on the 2.6 version and up of the kernel has PAE  included native and most often enabled by default, so it’s another thing  you don’t have to worry about."

From here:
[http://pacoup.com/2009/05/27/pae-vs-64-bit-what-manufacturers-dont-want-you-to-know/ ]("http://pacoup.com/2009/05/27/pae-vs-64-bit-what-manufacturers-dont-want-you-to-know/")

So, I can install more RAM now without any hassle?

---

### Post by hudsonl on 2010-07-29
> **physic.dude said:**
> I use Ubuntu in 32 bit but I have 4GB or RAM and Ubuntu uses all of it, so I was wondering if i install more ram will my PC support 8GB?


Not to be dismayed ... Linux will reserve available memory for buffered cache and free it up, as needed.  Recently used pages are kept in memory (buffered cache) and freed as needed.  It **may look** like all your memory is being used .... but you might be fine.  As long as your not swapping ... you really don't need to consider adding more RAM.

Basically ... it may look like Ubuntu is using all the 4GB ... but you may not really need any more.

If you do a free -m ... see how much is free on buffered cache.  One one of my machines I have 4GB plus run a virtual machine (windows with 2 GB) allocated to it.  You can see from the picture that it looks like all the memory is being used, but 1285 MB is free in buffered cache.  No swapping (vmstat)

[IMG]http://hudsolve.com/images/memory.jpeg[/IMG]


Here's a look at the top processes ... you can see that VirtualBox is taking 2GB
 
[IMG]http://hudsolve.com/images/top.jpeg[/IMG]

**Anyway ... I would take a real close look (or second look) and decide if you really need it.**

Good luck.

---

### Post by howefield on 2010-07-29
> **physic.dude said:**
> Well, is there a easy way to switch to 64 bit? 

No, your choice is install a PAE kernel within your existing setup or clean install 64 bit.

> All my hardware supports 64 bit, but I'm not sure if software such as Wine will be supported.

Most of your software will be fine, where there isn't a 64 bit version, you can install the 32 bit version. There is an issue with flash as the 64 bit version has been removed from the Adobe website due to a security issue, you'd need to install 32 bit with nspluginwrapper.

---

### Post by physic.dude on 2010-07-29
I do frequently max out my 4GB of RAM a lot to the point where everything starts to lag.
If I install 4 more Gigabytes (8GB total) will Ubuntu utilize any of new stuff?

Edit: Another reason why I need more RAM is because the only way for me to use my adobe products is with Virtual Box and I would like to bump that from 2GB to 4GB in itself.

---

### Post by iponeverything on 2010-07-29
> So, I can install more RAM now without any hassle?

run this to see if your already using the pae kernel:

```
uname -a 
```

If you are not, it is easily installed through synaptic.

---

### Post by physic.dude on 2010-07-29
Thanks\\:D/

---

### Post by Yellow Pasque on 2010-07-29
If you're doing intensive virtualization, you might just want to install 64-bit anyway (virtualization is one of those things that can get a significant boost from 64-bit). If you have a separate /home partition, you can re-use it and retain a lot of your settings and customization. If you don't have a separate /home partition, it might be a good time to back up your home folder, install 64-bit Ubuntu with a separate /home partition, and restore your home folder ;)

---

### Post by iponeverything on 2010-07-29
> **Temüjin said:**
> If you're doing intensive virtualization, you might just want to install 64-bit anyway (virtualization is one of those things that can get a significant boost from 64-bit). If you have a separate /home partition, you can re-use it and retain a lot of your settings and customization. If you don't have a separate /home partition, it might be a good time to back up your home folder, install 64-bit Ubuntu with a separate /home partition, and restore your home folder ;)

I Agree - 
Ubuntu 64bit is mature IMO and in some areas will give a big performance increase according to some of the benchmarks I have seen.

---

### Post by physic.dude on 2010-07-30
Ok, I just got 2 more sticks of ram, (8 GB total) it all works fine, but is it possible to get more then 2.5 GB of ram on Virtual Box?

---

### Post by Yellow Pasque on 2010-07-30
> **physic.dude said:**
> but is it possible to get more then 2.5 GB of ram on Virtual Box?
...
> VirtualBox restricts the amount of guest RAM to 2560 MB on 32-bit Linux and Solaris hosts due to address-space limitations. These restrictions do not apply to 64-bit hosts.

---

