---
title: "/sbin/init:428:cannot open dev/console PANIC"
date: 2006-03-19
forum: Hardware &amp; Laptops
---

### Post by Pustulo on 2006-03-19
HI All,

Up until 3 days ago, I was happily running Hoary on my nforce2 mobo and AMD2600+ CPU.  Then I spent up and bought me a new CPU and mobo.

Now I'm on an Asus SLI-Premium (nforce4 SLI) and an AMD64x2 4400+.

When booting into Hoary, I get:

pivot_root: No such file or directory
/sbin/init:428:cannot open dev/console
Kernel Panic

HELP!!

I've had a similar problem before (error 429), although that was just that the root device was wrong after moving my Ubuntu to a SATA disk.  This time around, it appears to me that disk devices look okay, but I can't really be sure.

I've tried using mkinitrd from a rescue boot (install CD), however it seems to always be looking for an i386 kernel, and I only have k7's installed.  Any idea how to get around this?  I have exhausted myself on migrating this thing over the last 3 days.

Thanks.

---

### Post by Pustulo on 2006-03-20
Okay, solution found.  Sort of.

- Performed a 'rescue' boot from installation CD.
From F2 console:
- mount -o bind /proc /target/proc
- mount -o bind /dev /target/dev

Now it just so happened that I needed a kernel upgrade, so in F1 console:
- apt-get update
- apt-get upgrade

New kernel installed, all good.  I'm not sure what specifically fixed it, but there you have it.

Now to get an X display on this new video card!

---

