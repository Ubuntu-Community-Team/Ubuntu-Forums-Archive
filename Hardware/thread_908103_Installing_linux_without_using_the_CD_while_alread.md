---
title: "Installing linux without using the CD while already booded"
date: 2008-09-02
forum: Hardware
---

### Post by Herbonator on 2008-09-02
I have an interesting problem. I have an acer laptop that I am trying to get up and running that has a faulty DVD drive it seems (although it may be a motherboard issue, I havent been able to diagnose it very well).

I can sometimes use a live CD to get into most distros (Knoppix, Mandriva, Ubuntu, etc) but when I try to install and it needs to read the CD a lot it causes the machine to freeze up with read errors from the CD.

Can anyone suggest a work around for this? Is there a way to install a distro entirely from the HDD or internet without needing the CD once it is already booted? Please note that the laptop is unable to boot from USB so installing from a memory stick isnt an option.

Thank you for your help.

---

### Post by Jose Catre-Vandis on 2008-09-02
This thread will help you out:

[http://ubuntuforums.org/showthread.php?t=666267](http://ubuntuforums.org/showthread.php?t=666267)

---

### Post by Herbonator on 2008-09-02
> **Jose Catre-Vandis said:**
> This thread will help you out:

[http://ubuntuforums.org/showthread.php?t=666267](http://ubuntuforums.org/showthread.php?t=666267)

Thankyou, that may do the trick.

For the record I am unable to get into the comp at all via the CD now. It has deteriorated it seems.

---

### Post by IntuitiveNipple on 2008-09-02
You could install everything to a chroot (change-root) mounted partition using debootstrap - same way we build virtual machine images without using the ubiquity installer.

I wrote an [article and script to do this](http://tjworld.net/wiki/Linux/Ubuntu/BuildChroot) a few weeks ago. It'd need a couple of minor modifications but the process is the same.

---

### Post by Herbonator on 2008-09-02
It looks like the problem is the motherboard after all (or perhaps both the HDD and CD) as I can't get QTParted to load without freezing the comp.

Anyone have any good projects for a laptop without a decent motherboard? It's got a nice screen and I'm a photographer, is there a way to make a photo frame out of it?

---

### Post by IntuitiveNipple on 2008-09-02
It could be fault memory modules. Are they accessible? Can you get hold of more of the same module to do a swap-test?

---

### Post by Herbonator on 2008-09-03
> **IntuitiveNipple said:**
> It could be fault memory modules. Are they accessible? Can you get hold of more of the same module to do a swap-test?

I just checked both modules and the test reported that they are fine. 

Im now getting the pxe-e61 media test failure error message now too so I can be sure that the HDD is dodgy.

The CD drive may just be dodgy and it may not be a motherboard issue as it works sometimes for some CDs... Not sure whether it's worth buying another HDD for it to test. Any suggestions?

---

