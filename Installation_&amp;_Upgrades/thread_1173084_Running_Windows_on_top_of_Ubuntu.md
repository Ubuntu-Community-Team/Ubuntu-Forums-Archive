---
title: "Running Windows on top of Ubuntu?"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by Theory5 on 2009-05-29
I heard that there was a way to duel boot ubuntu and another operating system in a way that they both run at the same time. Is this true? How does this work and how can I do it?

---

### Post by eldragon on 2009-05-29
virtualbox

---

### Post by ELD on 2009-05-29
It is called virtualization, there are advantages and disadvantages to it.

---

### Post by Theory5 on 2009-05-29
I heard that ubuntu can do it itself, work as a base for another operating system.

---

### Post by ELD on 2009-05-29
> **Theory5 said:**
> I heard that ubuntu can do it itself, work as a base for another operating system.

Well as far as i know you heard wrong, ubuntu is an operating system built upon the linux kernel.

---

### Post by decoherence on 2009-05-29
> **Theory5 said:**
> I heard that ubuntu can do it itself, work as a base for another operating system.

Perhaps you're referring to KVM, which is included in the Linux kernel. There are many different options for doing virtualization on Ubuntu. VirtualBox is much easier to work with, at this stage, and is very easy to install on Ubuntu (just check Add/Remove... under the Applications menu)

I currently run Windows XP under Ubuntu using VirtualBox so that I can use the Windows version of GroupWise at work. Works great!

---

### Post by Theory5 on 2009-05-29
okay, so virtualization. what is that and how do I use it? What are its advantages and disadvatages?

---

### Post by Theory5 on 2009-05-29
> **decoherence said:**
> That is correct. VirtualBox is one such solution. Or perhaps you're referring to KVM, which is included in the Linux kernel. There are many different options for doing virtualization on Ubuntu.

I currently run Windows XP under Ubuntu using VirtualBox so that I can use the Windows version of GroupWise at work. Works great!

stop posting after I write a post! lol :p
KVM? How does that work?

---

### Post by Irishe on 2009-05-29
i recommend VirutalBox, Like ubuntu, it is Also free and can be found [[SIZE=3]here[/SIZE]]("http://www.virtualbox.org/wiki/Downloads")!
make sure to read about it first, it can make it much easier should you run into
problems.
 
Good Luck.

---

### Post by perixx on 2009-05-30
Hello!

If it's just down to running some not-too-demanding Windows desktop applications (preferably no top-notch games), you might try Wine, to run those apps directly under Linux (preferably if you have a Nvidia graphics card with latest binary drivers - due to bad OpenGL implementation in Ati's binary drivers):
[http://wiki.winehq.org/FAQ#head-72731b215bbd1ce36e3b84ac7ce114925ce16460](http://wiki.winehq.org/FAQ#head-72731b215bbd1ce36e3b84ac7ce114925ce16460)

Other from that, you might just do it the other way round and install Linux under Windows, with the WUBI-installer (a way of dual-booting on a single NTFS-partition):
[http://wubi-installer.org/](http://wubi-installer.org/)

Yet another possibility might be Cooperative Linux, which can run a native Linux kernel right within Windows, without virtual emulation (haven't tried this myself, though):
[http://www.colinux.org/](http://www.colinux.org/) 

greetings,


perixx


EDIT: KVM looks interesting!

---

