---
title: "8GB RAM seen as 2GB RAM"
date: 2011-09-11
forum: Hardware
---

### Post by cosmicgr on 2011-09-11
Hello
I have a HP dv7 new laptop with 64bit i7 processor and 8GB RAM. I have installed Ubuntu 10.10 (32bits). It sees only 2GB RAM when I check it from the command *free -m*.
How can I enable my ubuntu to use the full 8GB RAM?

---

### Post by PhilGil on 2011-09-12
> **cosmicgr said:**
> Hello
How can I enable my ubuntu to use the full 8GB RAM?
Short answer is to install the 64 bit version of Ubuntu.

Long answer is that 32 bit operating systems will only recognize a maximum of 4GB of RAM, including your video RAM.

There is a 32-bit Linux kernel available that will recognize more than 4GB of RAM (it's called "bigmem" in Debian, not sure if there's a supported equivalent in Ubuntu). It's more of a kludge for older servers with a lot of system RAM, though.

---

### Post by walt.smith1960 on 2011-09-12
Installing a 64 bit kernel is the best answer.  If you don't want to do that you can install the PAE kernel. it's a surprise that the PAE kernel didn't install in any system with 4 GB RAM or more. In Synaptic type "pae" in the search box.  You should find what you need. Wikipedia has a write-up on what PAE is, how it works and its limitations.

---

### Post by Jagoly on 2011-09-12
if you haven't got too much data on ubuntu, reinstalling the 64bit version of 10.04 or 11.04 would be the best choice. Otherwise you can try those other kernels.

---

### Post by coffeecat on 2011-09-12
@cosmicgr, welcome to the forum! 

Even with the 32-bit version and the generic kernel (not the PAE one) your system should be seeing about 3.2GB of RAM, not 2GB. Check the BIOS to make sure all the 8GB is being seen by the BIOS.

---

### Post by .... on 2011-09-12
Since you just installed Ubuntu, reinstall and use the 64-bit version. Seriously. The only thing you want to avoid is the version of Flash found in Ubuntu64's repo. Use this instead: [https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)

---

### Post by walt.smith1960 on 2011-09-12
> **.... said:**
> Since you just installed Ubuntu, reinstall and use the 64-bit version. Seriously. The only thing you want to avoid is the version of Flash found in Ubuntu64's repo. Use this instead: [https://launchpad.net/~sevenmachines/+archive/flash]("https://launchpad.net/%7Esevenmachines/+archive/flash")

Or use our own LovingLinux' Firefox extension Flash-Aid. I've used it with good effect. You do need SUDO permission to run it.

---

### Post by cosmicgr on 2011-09-16
Thank you all of you!
I had to use some programs which run on 32bit only, so I could not install 64bit ubuntu. I'm already running 64bit Fedora for 64bit applications. This 32bit was for testing only.
I have successfully installed the PAE kernel. It is now recognizing full 8GB RAM. 
Thanks once again for all your support!

---

