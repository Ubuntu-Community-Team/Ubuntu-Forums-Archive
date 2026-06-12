---
title: "Can't install anything!"
date: 2009-02-21
forum: Hardware
---

### Post by dbbolton on 2009-02-21
I have a ghastly difficult laptop (see [http://ubuntuforums.org/showthread.php?t=618665](http://ubuntuforums.org/showthread.php?t=618665) ), and now I can't install Ubuntu on it.

I just replaced the memory and hard drive. They were recognized in bios. I tried to boot several CDs, like Ubuntu 8.10, Debian lenny, Arch, Puppy Linux, OpenSUSE 11, as well as Windows XP and Windows 7. All of these CDs will start to boot fine but hang somewhere in the process. A couple of the Linux CDs froze right after showing this message:
```

io scheduler cfq registered
```

When I tried to boot the Debian and alternate Ubuntu CDS, it printed something like:
```
 (Number) Aperture beyond 4GB. Ignoring
```

Dam Small Linux 3.1 did get to the desktop in failsafe mode, and I can get to a non-x shell with Slackware.

Any suggestions?

---

### Post by cariboo on 2009-02-21
You can ignore this:

>  (Number) Aperture beyond 4GB. Ignoring

error, as it has to do with legacy agp support.

Jim

---

### Post by dbbolton on 2009-02-21
I was able to perform a frugal install with DSL, but now it freezes on boot after it says "Checking for USB..."

---

### Post by dbbolton on 2009-02-22
Ok, DSL will boot if I add the "nousb" option in GRUB.

Should I just get a new motherboard?

---

