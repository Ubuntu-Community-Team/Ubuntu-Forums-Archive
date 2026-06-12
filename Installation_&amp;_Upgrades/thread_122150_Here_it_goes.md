---
title: "Here it goes"
date: 2006-01-26
forum: Installation &amp; Upgrades
---

### Post by WoodPost on 2006-01-26
I've posted a few times here before in my various stages of install and uninstall. I'm ready to find my happy place, so here what i got.
80gb IDE hard drive with XP - boot, system on it
250gb Sata as storage for Xp - no boot or system files on it
250gb Sata for Ubuntu.

I understand how to install Ubuntu onto the hard drive and configure grub and all. i want to know how i should go about taking advantage of my Hyper Threading Processor, I've read something about recompiling a kernel, but i don't know what that mean, so help would be nice, thank you. A link to another topic about it would be enough, I think i might be able to figure it out.

---

### Post by Sutekh on 2006-01-26
[QUOTE=WoodPost]I've posted a few times here before in my various stages of install and uninstall. I'm ready to find my happy place, so here what i got.
80gb IDE hard drive with XP - boot, system on it
250gb Sata as storage for Xp - no boot or system files on it
250gb Sata for Ubuntu.

I understand how to install Ubuntu onto the hard drive and configure grub and all. i want to know how i should go about taking advantage of my Hyper Threading Processor, I've read something about recompiling a kernel, but i don't know what that mean, so help would be nice, thank you. A link to another topic about it would be enough, I think i might be able to figure it out.[/QUOTE]
You would like a SMP kernel.  No need to compile it, Apt-Get/Synaptic has plenty.

Here's the link you want
[Ubuntu Forums - Picking the Kernel thats right for you]("http://www.ubuntuforums.org/showthread.php?t=85917")


[You probably want the 686-smp, for newer pentiums]
```

sudo apt-get install linux-686-smp
```

---

### Post by WoodPost on 2006-01-26
I have a Pentuim 3.0Ghz HT, so I think your right in thats the kernal i want to use. So i would install Ubuntu with the normal kernal then just download the new one?

---

### Post by Sutekh on 2006-01-26
Yup.  When you install Ubuntu, you won't have the choice of which kernel to install.  The basic i386 kernel is on the CD.  So once thats working then you can install the newer 686-smp one, to take advantage of HT.

---

### Post by WoodPost on 2006-01-26
Thank you. Another question, are there any open-source programs that take advantage of a dual core like Photoshop and Battle Field do? Forgive me if these are not the actual programs, I know there are some, I think those are it.

---

### Post by Sutekh on 2006-01-26
Don't know about Photohop, but I haven't heard of any games that take advantage of multi-threading CPUs yet.  I could be wrong...

---

