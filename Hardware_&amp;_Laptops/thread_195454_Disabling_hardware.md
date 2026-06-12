---
title: "Disabling hardware"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by lucis on 2006-06-12
I have two soundcards, one on the mobo and one as a PCI device. I prefer the PCI one. Having two, however, creates conflicts and confusion when trying to use audio applications. 

Is there a way to disable the mobo soundcard? I've looked everywhere but can't get a straight answer. Recompile the kernel? Edit my BIOS settings? Isn't there a way to do this within the OS? :( 

Thanks

---

### Post by pyromithrandir on 2006-06-12
I'd say to check your bios settings. If you can, disable the onboard one there.  That'll make your life the easiest because then linux will only have to keep track of the PCI card.

---

### Post by lucis on 2006-06-12
But why can't it be disabled within the OS? Windows can do that with no problem, come on...

---

### Post by pyromithrandir on 2006-06-12
Well, you could recompile your kernel without the drivers for the onboard soundcard. I just think disabling it in the bios is easier, because you'll only have to do that *once*, no matter how many different OSs you install.

Now, I don't know, there may be a way to do it with linux a different way, easier than recompiling the kernel.

And just because Windows can do it, do you really think that's the best way? I mean, come on...

---

### Post by lucis on 2006-06-13
[QUOTE=pyromithrandir]Well, you could recompile your kernel without the drivers for the onboard soundcard. I just think disabling it in the bios is easier, because you'll only have to do that *once*, no matter how many different OSs you install.

Now, I don't know, there may be a way to do it with linux a different way, easier than recompiling the kernel.

And just because Windows can do it, do you really think that's the best way? I mean, come on...[/QUOTE]

I don't know if Windows' particular method is the best, but wouldn't you agree having basic functionality found in Windows help Linux's place in mainstream use?

I realize that it can be disabled via the BIOS (which is the route I went, thank you for your suggestion) but most users aren't computer-savvy enough to do such a thing.

---

