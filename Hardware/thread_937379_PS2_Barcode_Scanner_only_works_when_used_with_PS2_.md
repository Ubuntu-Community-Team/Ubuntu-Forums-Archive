---
title: "PS/2 Barcode Scanner only works when used with PS/2 keyboard  (not true in Gentoo)"
date: 2008-10-03
forum: Hardware
---

### Post by FuriousGeorge on 2008-10-03
For some reason, in Kubuntu my Barcode Scanner will not start 'working' until I plug a standard ps/2 keyboard into the female ps/2 DIN that is found on the  cable of every ps/2 barcode scanner.

This is not the case in either Gentoo or Windows.

Does anyone know why this may be the case?

I'm fairly certain this has something to do with my kernel, as in Gentoo I built my kernel by hand, and it works, while an LTSP 'thin client' using am automagic 'genkernel' exhibits the same behavior as Kubuntu.

Thanks in advance,
Brian

---

### Post by nixscripter on 2008-10-04
Try _[compiling your own kernel]("https://help.ubuntu.com/8.04/installation-guide/i386/kernel-baking.html")_ with the Ubuntu default options, and then compare the configuration files.

---

### Post by FuriousGeorge on 2008-10-04
> **nixscripter said:**
> Try _[compiling your own kernel]("https://help.ubuntu.com/8.04/installation-guide/i386/kernel-baking.html")_ with the Ubuntu default options, and then compare the configuration files.

Sure, I'll give this a try, but did you mean to say 'Gentoo default options', since it works in gentoo,and not in kubuntu?  

I have no idea if it would work in Ubuntu, but I assume it uses the same kernel as Kubuntu...

Also, if the point is just comparing .configs I can do that already since I have the .config file for both kernels.

Thanks for the documentation, I didn't know how to compile a kernel the debian way.

By the way, both Gentoo and Kubuntu are using 2.6.24.  (kubuntu says its 2.6.24-19-1kununtu1, and gentoo says 2.6.24-generic9, or something)

The main difference between my custom Gentoo Kernel and the default Genkernel and Kubuntu kernels, which don't work, is that I tend to build everything into my custom kernel, whereas the others make lots of external modules.

---

### Post by nixscripter on 2008-10-04
I think Ubuntu and Kubuntu use the same kernel.

I meant default Ubuntu options. Run a diff and say "oh, this isn't my ubuntu kernel, I'll try this."

And speaking as someone who's done this recently, it's a lot of work, but I see no other alternative.

I hope those Ubuntu compile instructions help automate things (like genkernel would).

---

