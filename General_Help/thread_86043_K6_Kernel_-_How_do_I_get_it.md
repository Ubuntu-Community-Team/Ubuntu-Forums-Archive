---
title: "K6 Kernel - How do I get it?"
date: 2005-11-04
forum: General Help
---

### Post by dominicb on 2005-11-04
I can't apt-get linux-k6.
This might be because I'm an idiot, I can't get to my machine right now so I can't try it again. I can apt-get linux-k7 but i'm not sure I want to run the k7 kernel on my k6-2 machine.

Anybody got any ideas?

---

### Post by Teroedni on 2005-11-04
As far as i know there ar not any K6 kernel.
I think k7 kernel is for k6 too.
You can choose between k7 and i386. Choose k7.
Never choose 686 . I did  that for a while, and i can promise that the machine dident like that to much;)

Your k6 have many similarity to K7 Like 3dnow

---

### Post by dominicb on 2005-11-04
[QUOTE=Teroedni]As far as i know there ar not any K6 kernel.
I think k7 kernel is for k6 too.
You can choose between k7 and i386. Choose k7.
Never choose 686 . I did  that for a while, and i can promise that the machine dident like that to much;)

Your k6 have many similarity to K7 Like 3dnow[/QUOTE]

Debian has a K6 kernel. I tried 686 but the machine won't even boot. The k6-2 has 3dNow, but I don't know if it has all of the instructions that a K7 has got, so even though I'm definitely going to try the K7, I'd like to try the K6 too.

---

### Post by Teroedni on 2005-11-04
Probably not all ,but many of the functions. I dont think you will get any difference between k7 and k6 .The thing your k6 cant run will probably not be enforced on it .
Th k7 kernel will only intiate the functions the k6 have. 

I am sorry but Ubuntu doesnt have an k6 kernel, so your stuck with the k7.
However if you try it and find out that the k7 isent working properly on your machine, it may be possible to compile a k6 verion on Ubuntu i guess:)

---

### Post by dominicb on 2005-11-04
I'll just have to give the K7 a go and see how it works.

---

### Post by Yagisan on 2005-11-04
[QUOTE=dominicb]I'll just have to give the K7 a go and see how it works.[/QUOTE] Don't do that!

K7 Kernels DO NOT work on K6. That is like saying an i686 kernel will work on a i486, it's just not going to happen.

I also have a K6/2 system, it uses the linux-image-2.6.12-9-386 kernel as that is the only ubuntu supplied breezy kernel that works on it.

---

### Post by dominicb on 2005-11-04
[QUOTE=Yagisan]Don't do that!

K7 Kernels DO NOT work on K6. That is like saying an i686 kernel will work on a i486, it's just not going to happen.

I also have a K6/2 system, it uses the linux-image-2.6.12-9-386 kernel as that is the only ubuntu supplied breezy kernel that works on it.[/QUOTE]

I couldn't see the K7 kernel working in a K6 myself. 

Can I use the Debian K6 kernel?

---

### Post by Teroedni on 2005-11-04
really?
:(
Its only i386 which  works?

---

### Post by Teroedni on 2005-11-04
[https://wiki.ubuntu.com/KernelHowto](https://wiki.ubuntu.com/KernelHowto)

a wiki for installing custom kernel.
If you compile the kernel for your machine it will be faster than any other type of kernel. So i would recommend tthat:)


as for the debian k6 
Yea i think it would work but not sure :(
Any others know if it is possible?


I am sorry for the k7 kernel recomendations, i was sure k7 was working for k6 but its seems i was very wrong:(

---

### Post by dominicb on 2005-11-04
I'll go through that wiki then, and compile myself a kernel.

---

### Post by Yagisan on 2005-11-04
As someone who used to do assembly level development on k6/2 I can tell you that you will not get a measureable increase in performance.

A K6/2 processor is basically a pentium mmx with 3dnow instructions. It architecturely predates the addition of conditional move instructions (the cause of biggest speed gains in i686, k7, k8 kernels etc) which can eliminate the need for slow branching. Now a pentium mmx is just that, a bog standard pentium, with mmx instructions. A pentium was basically two i486s (x pipe and y pipe) with an i387 math co-processor and and extra instruction built in (CMPXCHG8B), and an i486 was an i386 with two extra instructions (CMPXCHG, and BSWAP). Fundamentaly, when you look at it, it's just really a faster i386.

For kernel work do mmx and 3dnow help ? not really. In systems of that age you could use them to clear memory or bulk data movements, but in practice it was faster to do that using the i387.

I don't suggest the Debian kernel, but as long as it is the same version, it is unlikely to cause any harm, but don't uninstall the Ubuntu kernel in case it doesn't work out.

If I may ask, why do you need an optimised kernel ?

---

### Post by dominicb on 2005-11-04
The machine is dreadfully slow.

I'm using fluxbox instead of gnome, but it is still much slower than it ought to be. I actually think it's a hardware issue because it was running very slow under w98 before I installed ubuntu. But I'd like to try anything before going to the hardware because
a) I know next to nothing about it
b) hardware's not free

---

### Post by Qrk on 2005-11-04
Have you considered using the 2.4 kernel? I've personally found it to be better on old hardware. 
Ubuntu doesn't offer it, but I think Debian sarge defaults to it. You might have better luck. (Damn Small also uses 2.4)

---

### Post by Yagisan on 2005-11-09
[QUOTE=dominicb]The machine is dreadfully slow.[/quote]Tuning the software will give a minor boost at best. In my experience I got the best increase in percived preformance by 1)sticking in as much ram as I could (320MB), and 2) wacking in a faster videocard to replace the onboard card.

The prelink guide may also give a percived speed increase, as may turning on dma for the hard disks and cdrom if it is already on (some cdroms don't work properly with dma on, so it is most likely off)

---

