---
title: "Fixing Gutsy Hibernate/Suspend (Blinking Cursor) HOWTO"
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by catfishk on 2007-11-23
i see a lot of posts for people wanting to fix their issue with the blinking cursor during Hibernate/Suspend.  machines using Ubuntu Gutsy's kernel and ATI cards (fglrx) can compile the SLAB allocator back into the kernel, and this fixes the issue, as it was changed to SLUB in Gutsy (makes a lot of sense, huh?).  i successfully suspend/hibernate using uswsusp and tux on ice, now that i compiled my own kernel, with fglrx version 8.42.3 from ati's website.  and yes, it works great with AIGLX and Compiz-Fusion!

 here is a nifty HOWTO (thanks Sean!) i found to help you do this.  it is EASY too!  enjoy!

 [http://blog.vaxius.net/?p=19](http://blog.vaxius.net/?p=19)

 i am not sure if this fixes Nvidia's driver issue that seems to do the same blinking cursor thing?

---

### Post by ravenon on 2007-11-24
I have applied the method given on the blog post (kernel compile) on a 64bit Turion with Radeon Express 200 chipset and X700 graphics card. A key idea in that blog was to link the firmware after building the kernel. In previous attempts at kernel compiling, I always lost my wireless (its listed hardware is an iwp3945, but I believe it uses the iwp2200 driver). Pat on the back to the person who 's blog it is. Machine suspend to ram or disk, wireless works like a charm, and I am running the ATI/AMD 7.11/8.4333 driver.

---

