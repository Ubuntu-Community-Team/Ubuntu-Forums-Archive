---
title: "automount usb drive broken with compiled kernel"
date: 2006-10-14
forum: Hardware &amp; Laptops
---

### Post by andb on 2006-10-14
I have a kernel which I have compiled myself. I can mount usb memorykeys fine with sudo mount /dev/sda1 /mountpoint, however, Id like them to automount as they do with the plain vanila ubuntu kernel. Id appreciate any help in this direction, have I missed a kernel option or a module I need to compile to support this?

---

### Post by David Corrales on 2006-10-29
I'm having the same problem :( 2.6.18 with ck1 patch.

---

### Post by zgornel on 2006-10-29
If you plan to recompile a vanilla kernel with/without ck patch, there is a good tutorial here: [http://ubuntuforums.org/showthread.php?t=217657](http://ubuntuforums.org/showthread.php?t=217657) .
The important thing is to use the .config file that was used for the ubuntu kernel. Personally, I compile only ubuntu kernel from the source packages in the repository.

---

### Post by zasf on 2006-10-29
> **David Corrales said:**
> I'm having the same problem :( 2.6.18 with ck1 patch.

I compile my own kernel since 2.6.16 and I still have the very same problem with 2.6.18.1, I'm very interested in some solution

---

### Post by David Corrales on 2006-10-29
I found the following thread with the exact cause for the problem:
[http://www.ubuntuforums.org/showthread.php?p=1681392](http://www.ubuntuforums.org/showthread.php?p=1681392)

---

### Post by zasf on 2006-10-31
> **zasf said:**
> I compile my own kernel since 2.6.16 and I still have the very same problem with 2.6.18.1, I'm very interested in some solution

hum, now it works, see my config, it might help

---

