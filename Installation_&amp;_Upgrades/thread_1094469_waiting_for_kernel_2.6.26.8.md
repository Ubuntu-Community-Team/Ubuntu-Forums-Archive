---
title: "waiting for kernel 2.6.26.8"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by mpolito1969 on 2009-03-12
Does anybody know when the update will be released?

I've been fighting against the bug describe here

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789)

and it seems the new kernel release will fix it.

Ciao,
Max

---

### Post by davec64 on 2009-03-12
Do you mean 2.6.28?

The latest stable release is 2.6.28.7

Have a look here:

[http://www.kernel.org/]("http://www.kernel.org/")

Although it hasn't got through to the repositories yet you could compile it yourself.

All the best

---

### Post by Neo_The_User on 2009-03-12
Have you tried compiling the snapshots? Thats what I usually do (except I clone the git repos by hand)

[http://kernel.org/pub/linux/kernel/v2.6/snapshots/patch-2.6.29-rc7-git5.bz2](http://kernel.org/pub/linux/kernel/v2.6/snapshots/patch-2.6.29-rc7-git5.bz2)
[http://kernel.org/pub/linux/kernel/v2.6/testing/patch-2.6.29-rc7.bz2](http://kernel.org/pub/linux/kernel/v2.6/testing/patch-2.6.29-rc7.bz2)
[http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.28.tar.bz2](http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.28.tar.bz2)

I listed them the opposite way. sorry.

---

### Post by TheLions on 2009-03-12
you can get it from jaunty (whic is in alpha/unstable state)

using repository or from here:

[http://packages.ubuntu.com/jaunty/linux](http://packages.ubuntu.com/jaunty/linux)

but this will possibly bork your ubuntu system...

---

### Post by mpolito1969 on 2009-03-12
> **davec64 said:**
> Do you mean 2.6.28?

You're right, I meant 2.6.28

> **davec64 said:**
> 
Although it hasn't got through to the repositories yet you could compile it yourself.

All the best

It's more or less 5 years since I last built a kernel from scratch, and I was on a Gentoo system. I  almost sure I'll make a big mess.

I'd rather using that nice feature of modern Linux distributions: I click somewhere and the system does the job for me :D

Is there a way to know when I'll find this new kernel version in the update manager?

Ciao,
Max

---

### Post by avtolle on 2009-03-12
My best guess is that the kernel you are seeking will not be showing up in update manager for 8.04 or 8.10. It seems to me that once a release occurs, there's not a kernel update of the type you are seeking. So, you may upgrade to Jaunty when it is released in April; or, compile the kernel yourself if you don't want to do that upgrade.

To clarify: Hardy is still using 2.6.26.x; Intrepid 2.6.27.x; I'd be very surprised to see 2.6.28.x appear in any repositories for either release, even the backports repo, given what I've observed in the 3 or so years I've been using Ubuntu.

---

### Post by mpolito1969 on 2009-03-12
> **avtolle said:**
> My best guess is that the kernel you are seeking will not be showing up in update manager for 8.04 or 8.10. It seems to me that once a release occurs, there's not a kernel update of the type you are seeking. So, you may upgrade to Jaunty when it is released in April; or, compile the kernel yourself if you don't want to do that upgrade.

To clarify: Hardy is still using 2.6.26.x; Intrepid 2.6.27.x; I'd be very surprised to see 2.6.28.x appear in any repositories for either release, even the backports repo, given what I've observed in the 3 or so years I've been using Ubuntu.

Well... that's some bad news.

I will probably have to brush up my knowledge about kernel builds.

Ciao,
Max

---

### Post by mpolito1969 on 2009-03-14
> **avtolle said:**
> 
To clarify: Hardy is still using 2.6.26.x; Intrepid 2.6.27.x; I'd be very surprised to see 2.6.28.x appear in any repositories for either release, even the backports repo, given what I've observed in the 3 or so years I've been using Ubuntu.

This is quite a disappointment.

We are not talking about a problem experienced on a outlandish hardware, something like a bug that you see when connecting a 5 1/4 inch hard drive to a firewire interface through some sort of home made adapter.

I can't connect a Nokia 3600 Slide phone and the bug report contains a lot of other phones/USB hard disks that can't be connected.

I thought Ubuntu was a Linux distributions targeted to "normal" users (I mean to people that not necessarily are Linux guru) and the only thing I can do to solve this problem is compiling a new driver (with all the uncertainties that come with such a solution)?

OK, I could also wait some weeks, without connecting my phone to the PC, for the new Ubuntu release, which is clearly not a better solution.

I didn't mean to be argumentative, I just wanted to explain why I feel so disappointed.

Ciao,
Max

---

### Post by martrn on 2009-03-14
> **mpolito1969 said:**
> We are not talking about a problem experienced on a outlandish hardware, something like a bug that you see when connecting a 5 1/4 inch hard drive to a firewire interface through some sort of home made adapter.

I suppose you could connect a home made adapter to a 5 1/4 inch drive to a gnu/linux or ubuntu computer system if you wanted to.  You might be have to recomile your kernel but hey you could probably do it if you wanted to.

> **mpolito1969 said:**
> I can't connect a Nokia 3600 Slide phone and the bug report contains a lot of other phones/USB hard disks that can't be connected.

The 3.2 megapixel camera was released how long ago ?  Did not nokia provide you with any drivers or kernel modules for use with your linux distribution ?  It takes a while for people to write kernel modules and changes in the kernel mean that stuff gets added all the time.  It take a while for newer stuff particularly 'gadgets' to be added.

> **mpolito1969 said:**
> I thought Ubuntu was a Linux distributions targeted to "normal" users (I mean to people that not necessarily are Linux guru) and the only thing I can do to solve this problem is compiling a new driver (with all the uncertainties that come with such a solution)?

Sounds like a reason to compare linux to windowze.
Ubuntu != Windows {really it isn't}
Read the philosophy behind ubuntu, and behined GNU software and behind Linux and try to understand what it is about.

> **mpolito1969 said:**
> OK, I could also wait some weeks, without connecting my phone to the PC, for the new Ubuntu release, which is clearly not a better solution.I didn't mean to be argumentative, I just wanted to explain why I feel so disappointed.Max

I suggest you try a different forum to explore your feelings, maybe one that specialises in feeling somehow if you are interested in exploreing them.

---

### Post by mpolito1969 on 2009-03-18
Just in case someone else with the same problem comes here: I solved the problem booting with the old kernel, the one from Ubuntu 8.04. I noticed in the system boot screen that old kernels were still there and I tried.

It seems to me 8.10 is stable with the old kernel also. Anyway, if it gets unstable I can boot with the old kernel, exchange files with the phone and then reboot with the right one.

Ciao,
Max

---

### Post by markbuntu on 2009-03-18
A lot of hardware support is backported to older distros with kernel updates but it is very dependent on developer interest and wether or not the older kernels can support such a thing without too much trouble. There is a great how to in the tutorials section about building your own kernel.

---

