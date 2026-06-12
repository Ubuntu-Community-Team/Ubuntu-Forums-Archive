---
title: "Instaling DRI, I get this error: config_x86_CMPXCHG ..."
date: 2005-11-24
forum: Hardware &amp; Laptops
---

### Post by Ruso on 2005-11-24
....config_x86_CMPXCHG needs to be enabled in the kernel .

I am trying to enable 3D on my Rage Mobility video card, so I've followed the instructions of HOWTO, but I can not compile the DRI packages because of that error.

How can I enable  this ("config_x86_CMPXCHG") in the kernel??

---

### Post by ranf on 2005-11-24
[QUOTE=Ruso]....config_x86_CMPXCHG needs to be enabled in the kernel .

I am trying to enable 3D on my Rage Mobility video card, so I've followed the instructions of HOWTO, but I can not compile the DRI packages because of that error.

How can I enable  this ("config_x86_CMPXCHG") in the kernel??[/QUOTE]
I had this problem also. This config is set whenever a CPU other than 386 is chosen.
I've tricked the DRI compile by simply putting a standard Ubuntu 686 config in /usr/src/linux.
It then compiled and worked.

---

### Post by Ruso on 2005-11-24
Thank you for answering, but where can I find the standard Ubuntu 686 config ??

---

### Post by ranf on 2005-11-24
[QUOTE=Ruso]Thank you for answering, but where can I find the standard Ubuntu 686 config ??[/QUOTE]
What kernel(s) do you have installed?
The config... is in `/boot'.

---

### Post by Ruso on 2005-11-24
I have 2.6.12-9-386 kernel.

---

### Post by Ruso on 2005-11-24
I got rid of that problemm by installing the 2.6.12-9-686 kernel. So I installed DRI packages without anyproblems, but after entering the Xterminal the 'Direct rendering' is still NO.

**glxinfo | grep direct ** gives me this results:
```

direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```

Any way to enable the direct rendering? Or I can forget about this feature?

---

### Post by ranf on 2005-11-25
[QUOTE=Ruso]
I am trying to enable 3D on my Rage Mobility video card, so I've followed the instructions of HOWTO, but I can not compile the DRI packages because of that error.
[/QUOTE]
Which HOWTO are you talking about?

---

### Post by Ruso on 2005-11-25
I was following this [http://ubuntuforums.org/showthread.php?t=7200&highlight=Rage+Mobility](http://ubuntuforums.org/showthread.php?t=7200&highlight=Rage+Mobility) HOWTO.

---

### Post by ranf on 2005-11-26
[QUOTE=Ruso]I was following this [http://ubuntuforums.org/showthread.php?t=7200&highlight=Rage+Mobility](http://ubuntuforums.org/showthread.php?t=7200&highlight=Rage+Mobility) HOWTO.[/QUOTE]
This HowTo is written for Warty (4.10). I followed the same HowTo on Hoary (5.04). It worked there.
I assume you have the current version Breezy (5.10).
Because the DRI install.sh compiles a kernel module you need a gcc version that matches the one the kernel was compiled with:
```
sudo apt-get gcc-3.4
# and before running install.sh
export CC=/usr/bin/gcc-3.4

```

---

### Post by ranf on 2005-11-28
[QUOTE=Ruso]
Any way to enable the direct rendering? Or I can forget about this feature?[/QUOTE]
Hello

I've got it going again.
Mainly by following this Howto (with adaptions for mach64):
[http://ubuntuforums.org/showthread.php?t=75393](http://ubuntuforums.org/showthread.php?t=75393)

Don't get the latest files from 
[http://dri.freedesktop.org/snapshots](http://dri.freedesktop.org/snapshots)

but the last from June/July here:
[http://dri.freedesktop.org/snapshots/archive](http://dri.freedesktop.org/snapshots/archive)

---

