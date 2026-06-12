---
title: "Where does my extra RAM go?"
date: 2008-12-05
forum: Hardware
---

### Post by residualbit on 2008-12-05
So this may be a dumb question, but I know 32 bit only supports up to 3 gigs. I have four installed. Does that extra gig do anything?

---

### Post by Existentialist on 2008-12-05
Most 32 bit OS's will support a maximum of 4gb of RAM.  Due to physical address space being allocated to other devices such as video cards, a 32 bit OS will show some amount less that 4gb.  Usually this is anywhere from 3.25-3.75gb of addressable RAM when using most 32 bit OS's.

---

### Post by ByteJuggler on 2008-12-05
> **nkirk1 said:**
> So this may be a dumb question, but I know 32 bit only supports up to 3 gigs. I have four installed. Does that extra gig do anything?

No, it's wasted.  Inaccessible due to the address space being used by other devices in the system (e.g. video card etc.)  That's partly why you need 64-bit operating system (although even on a 64-bit system you're not always guaranteed to have all 4GB available, though your chances are certainly much better and the likely loss if any much smaller.  See [here]("http://www.codinghorror.com/blog/archives/000811.html") for more.)

---

### Post by EV500B on 2008-12-05
> **nkirk1 said:**
> So this may be a dumb question, but I know 32 bit only supports up to 3 gigs. I have four installed. Does that extra gig do anything?
Your extra gig is almost "useless" as it does not increase your pc's performance.
The maximum RAM an linux os can support depends on its kernel. There's a way that your os support the 4gb; you must modify and patch your current kernel using the information in this link
 :arrow:[http://www.linux.com/feature/119287](http://www.linux.com/feature/119287)
There's also kernels that have been already modified in Debian but i don't know if that option is available in Ubuntu or the Os you're using.

PS: The number of RAM it supports can be changed but not its 
"memory managing" as it will only allow a maximum of 3.something Gb to one process or application.

---

### Post by psusi on 2008-12-05
Modern 32 bit operating systems running on at least a Pentium Pro processor can use up to 64 gigs of physical ram using paging address extensions.  It's just that no single process can use more than about 3 gigs of virtual memory.

In short, the 4 gigs of ram you have are being used just fine, unless your motherboard wastes some of it because it is hidden behind memory mapped IO, such as your video card's memory, rather than remap parts of it above the 4 gb physical address mark.

---

### Post by residualbit on 2008-12-05
Thanks for the input.I've been using ubuntu for a few years now and I was just wondering.

I guess my question now is why does it only show that I have 3 gigs of ram? should it show 3.99 or something? I have two 2gig modules.

---

### Post by psusi on 2008-12-05
What do you mean by "it"?

---

### Post by residualbit on 2008-12-06
pretty much anywhere in ubuntu that displays system information, but specifically the system info applet.

---

### Post by residualbit on 2008-12-06
I also remembered that when I had a dual boot with vista (don't ask why), vista originally showed 3 gigs and then after sp1 came out, it(system properties) showed 4.

If I pull up the bios before ubuntu starts, it shows 4096mb installed. 

My video card, which is an on board nvidia geforce go 7150m, was using 64mb and so i bumped it up to 128mb.

So i'm still unclear as to if the extra is being used for system process or something. Either way, it is not displaying more than 3 gigs in ubuntu. And looking at the previous posts it seems that there is some disagreement on the subject.

---

### Post by binbash on 2008-12-06
[http://ph.ubuntuforums.com/showthread.php?t=853678](http://ph.ubuntuforums.com/showthread.php?t=853678)

---

### Post by ByteJuggler on 2008-12-06
> **nkirk1 said:**
> I also remembered that when I had a dual boot with vista (don't ask why), vista originally showed 3 gigs and then after sp1 came out, it(system properties) showed 4.

If I pull up the bios before ubuntu starts, it shows 4096mb installed. 

My video card, which is an on board nvidia geforce go 7150m, was using 64mb and so i bumped it up to 128mb.

So i'm still unclear as to if the extra is being used for system process or something. Either way, it is not displaying more than 3 gigs in ubuntu. And looking at the previous posts it seems that there is some disagreement on the subject.

Windows Vista SP1 was changed from reporting *usable* memory to reporting *installed* memory.  It doesn't mean that they've fixed it so that you can access/use all 4GB of RAM on 32-bit Windows Vista and it's giving you the illusion of having 4GB usable when in fact that's not the case.

Your extra RAM will **not **be used unless
a) you run a special 32-bit kernel with support for PAE and your BIOS remaps either the memory hole above 4GB or remaps the extra ram above 4GB so there's not a conflict between the adress space in your system being used for devices like video cards, and actual physical RAM.

or 

b) you run a 64-bit kernel, again where your motherboard is capable of remapping the device address map usage out of the way of the physical RAM's address space usage.

See [here]("http://techfiles.de/dmelanchthon/files/memory_hole.pdf") for more.

---

