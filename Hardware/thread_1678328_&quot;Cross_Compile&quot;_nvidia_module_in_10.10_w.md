---
title: "&quot;Cross Compile&quot; nvidia module in 10.10 with gcc 4.5 for 10.04"
date: 2011-01-30
forum: Hardware
---

### Post by JackSchnippes on 2011-01-30
Hello Ubuntu community,


Wow, title sounds like I'm a mad man ;)

**Ultra-short description:**
How can I compile the nvidia module (to be able to use the Nvidia's blob), without having the card on the compiling system?

[B]Long description:
[/B]I use 10.04 Lucid and I'd like to use the kernel 2.6.37-12-lowlatency form the universe repository. Installation works fine except for the nvidia kernel module compilation via dkms. When I try to use install script from nvidia's homepage, it says that the kernel has been compiled using gcc-4.5 and I need the same version to compile the module.

So I've set up the build-essential environment inside a virtualbox with gcc 4.5. Of course the regular dkms compilation procedure for the nvidia module fails, since the virtualbox doesn't have an nvidia card ;)  

So the big question is, how can I compile the nvidia module inside the virtual machine for use in the host system?

Thank you for any help :)

EDIT
P.S.: Just a short mention WHY I want to use that kernel. I need the kernel for some audio recording and a need a recent kernel, since I need support formy M-Audio Fast Track Pro

---

