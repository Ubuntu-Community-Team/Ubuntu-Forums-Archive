---
title: "more GRUB"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by ipburbank on 2009-06-14
Hey, another grub question. I followed this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

but I get:

Grub loadingstage1.5

[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ] 

when I boot. I know this has been asked elsewhere, but all the help is specific to that person. If I could get this working it would be great!

~thanks in advance, Istvan.

---

### Post by merlinus on 2009-06-14
Hi.  Can you detail everything that you did?  For example, did you boot from the live cd?  Exactly what commands did you enter in the terminal?

Also, post results of:

```

sudo fdisk -l

```

---

### Post by ipburbank on 2009-06-14
I actually found the problem just 2 minutes ago: my bios was set to IDE for my drives, not ahci - all better now!

~thanks anyway, Istvan.

---

