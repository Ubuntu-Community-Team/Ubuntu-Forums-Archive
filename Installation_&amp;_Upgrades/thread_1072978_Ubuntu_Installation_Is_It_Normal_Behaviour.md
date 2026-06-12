---
title: "Ubuntu Installation: Is It Normal Behaviour"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by Rafay on 2009-02-17
Hi to all!

i have downloaded a copy of Ubuntu Desktop 8.10 and have mounted it on the VirtualBox..
when i start the machine.. i gives selection for language and setup type.. 
i chose "install" and then it starts loading and the Ubuntu Logo appears..
but when the Ubuntu logo disappears or assumingly the Installation needs to begin.. i just see a "_" sign on the black screen and i have tried it a couple of times and have waited for 10 minuted or so to see if something happens..

I need to know that is it normal behaviour for Ubuntu installation?
_________________________________________________________
I have 1Gb Ram and allocated 420mb to Ubuntu ...
I am using the iso image file and have not burned it to CD..
I have run the "check CD for errors" and it showed that 1 error was found on a file..
I have started downloading another copy of Ubuntu as well  :(

---

### Post by roachk71 on 2009-02-17
It appears that your VM memory allocation is set too high for a machine with 1GB (less if your graphics card shares memory with the system.) This tends to conflict with the system cache (since most OSes tend to occupy most of the free RAM with this cache.)

If your computer has 1GB installed, it's best to be a bit frugal with your VM's memory allocation; say 192 to 256MB for testing, and up to 384 for more demanding usage patterns.

Your best bet, though (and if your machine can be expanded that far,) is to install 2 to 4GB of memory so that a more desirable amount can be allocated to the guest OS.

My own computer has only 1GB installed, with 128MB allocated to graphics, so I'm staying away from virtualization for now...

EDIT:

Another possibility...Not assuming you haven't done so, but have you preformatted an uncompressed virtual drive of at least 16GB in size?

---

### Post by Rafay on 2009-02-18
i got a fresh copy of Ubuntu 8.4 and i works like a charm now
Maybe the error was correct and it maybe because i downloaded the file with a few pauses

as for memory... thanks i have a laptop and i nearly had forgotten that i could expand the memory.. will do very soon

now just trying to get a hold of Ubuntu and will see if it is upto my need..

Thanks:)

---

