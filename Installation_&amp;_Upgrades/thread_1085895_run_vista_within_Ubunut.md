---
title: "run vista within Ubunut?"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by telmore007 on 2009-03-03
I downloaded the program Virtual Box. I have my computer it can boot up in vista or ubuntu. How do I get that program to work to load vista with ubuntu? 

I watched some videos and it saying it loads though iso or cd. Is that the only way you can view vista in ubuntu? Not if you have it to dual boot?

Thanks

---

### Post by blueridgedog on 2009-03-03
VirtualBox allows you to install guest operating systems that run virtually.  You can install Vista as a guest OS with VirtualBox.  You will need to create a new virtual machine, then mount your Vista disk as a CD for the virtual machine and start it.  It should boot off of the disk and start the install. Remember that Vista has a minimum of 512 MB RAM and 15 GB HD.

For more info on creating a new virtual machine, see:

[http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html](http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html)

Good luck and don't be afraid to experiment.

---

### Post by Mark Phelps on 2009-03-04
Are you really asking, since your post implies that you already have a dual-boot machine, how to access your existing Vista installation from inside a virtual machine inside Ubuntu?

I've done some reading about that because I have the same situation, and what I read indicated that, while it's possible to do that, it basically breaks Vista activation, in that, every time you launch Vista after that, you have to reactivate it -- even if you boot into Vista directly.

Since I'm running an OEM version of Vista (i.e., can only be activated once), that's enough to keep me from trying this.

So, if you get this working, please let us know if the activation problem appears for you.  Maybe that has been fixed by now.

Thanks.

---

### Post by kvarley on 2009-03-04
Yeah dual-booting will work if you do it right.

Vbox allows virtual machines to be created as said before, however...

Why would you want Vista? XP maybe, but Vista!?

---

