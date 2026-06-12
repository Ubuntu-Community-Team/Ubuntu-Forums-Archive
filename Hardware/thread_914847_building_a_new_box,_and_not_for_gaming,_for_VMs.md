---
title: "building a new box, and not for gaming, for VMs"
date: 2008-09-09
forum: Hardware
---

### Post by dynacrylic on 2008-09-09
I'm intending on getting rid of my four older PCs and go with one box and run VMs off it. 

I would like at least 4gb ram, if not more, and the main OS will be ubuntu 8.04 (of which I don't plan on upgrading, just updating)

There are some library-geared (as in the place where you borrow books) open source applications I plan on running on it, so the box is not specifically intended for gaming. I should also add that this is for home testing purposes, not production.

I'm wondering what kind of boxes/configs others are using specifically for VMs?

---

### Post by in-dust-rial on 2008-09-09
well im sorry that i am the first to answer because my experience is down to only a VMware BSD and a VirtualBox windows guest on hardy.

i like your idea, but its not totally clear to me.
how many guests do you want to run on the system?
how big would a guest'process', running a test, be on the host-system?

i tried to goolge how linux SMP affects performance on virtual machines.
(quadcore better then dualcore? i would guess so)
and if you decide for a cpu and a budget... you max approximate a maximum of ram and  look what motherboard would fit to em... in respect to the bus speeds! 
and THEN dont forget the HD... i guess the HD will have many requests... so maybe several HDs are a good idea?

but i dont know about much you want to do, so please be explicit, so we can learn together ;D

good luck

---

### Post by in-dust-rial on 2008-09-09
[http://blogs.vmware.com/performance/2007/07/comparing-intel.html]("http://blogs.vmware.com/performance/2007/07/comparing-intel.html")
so here it is "something"
...if you are meassureing performance with tiles...
[comments help to find out if the information is reliable]

what tiles are is explained here or in the wmmark download section:
[http://www.vmware.com/vmtn/resources/573]("http://www.vmware.com/vmtn/resources/573")

but dont ask me how many ram is needed for this and what kind of bus :O
these testing machines had 32gig? well
i dont get it!

how many guests can there be on a host without problems?

---

### Post by dynacrylic on 2008-09-12
Yeah, I'm thinking there will only be two or there hosts running at a time, at it will not even be all the time even. There will probably be several hosts on it, just not running all at once.

thanks for the feedback :)

---

### Post by IntuitiveNipple on 2008-09-12
Depending on the *guest* operating systems you intend running, you might consider using KVM (the hardware-accelerated version of QEMU) or UML (user-mode-linux). Both of these will offer near-native speeds if the guest is the same architecture family.

A 64-bit host system that has hardware virtualisation support with 8GB RAM and a 64-bit SMP kernel (e.g. Hardy amd64) would be most suitable. That will ensure they guests aren't starved of resources.

With 3GB RAM my Vaio laptop can comfortably run three KVM x86 guests: one Windows and two Linux but if they were expected to do something other than development testing I'd want double the RAM.

---

