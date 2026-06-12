---
title: "wubi, grub prompt no boot after restart..."
date: 2008-09-14
forum: General Help
---

### Post by geminias on 2008-09-14
I installed wubi, rebooted the machine, chose Ubuntu in the boot menu, and then a grub prompt initialzed itself and waited for me to type random things.  When I used the "find" command the program froze.  Does anyone know what is wrong / how to fix?

danke

---

### Post by Becker54 on 2008-09-15
> **geminias said:**
> I installed wubi, rebooted the machine, chose Ubuntu in the boot menu, and then a grub prompt initialzed itself and waited for me to type random things.  When I used the "find" command the program froze.  Does anyone know what is wrong / how to fix?

danke

all i get is that Grub prompt. tried kernel, but it says kernel must be loaded. Tried what few things were in menu but none do anything.

---

### Post by ago on 2008-09-15
press insert rapidly at boot after selecting ubuntu, and report any message you see.

---

### Post by voodoobettie on 2009-06-20
I had the same problem, after choosing Ubuntu from the Windows boot loader and I got dropped into grub. I installed Ubuntu (via wubi) on a secondary hard drive (it gave me the option, after all, and I have tons of room on my secondary hard drive). 

As suggested above, I tried pressing insert several times after selecting Ubuntu but I couldn't really see the messages onscreen because it loaded too fast but I think I caught a glimpse of an error that said "start cmain_failure" - but that's all I got. (If I manage to see the error properly I'll report back.)

I'm going to play around to boot from grub but I thought I'd give a heads up that the newbie-friendly wubi installs sometimes still need a bit more know-how than joe average would likely have, even though I love the idea of them and I want them to work so we can get everyone to switch to linux! :)

---

### Post by aiiee on 2009-12-11
also got dropped to sh:grub prompt an a wubi machine.  This had been working fine for *weeks* then suddenly I cannot access.   How to fix this please?  How to make it stop happening?

---

### Post by maethor on 2009-12-14
I'm getting the exact same problem (ie, it goes into grub's shell) after updating.

---

### Post by Zymoan on 2010-03-26
I am also having this issue on 2 PCs. Its obviously a common issue. Is there anybody out there who can help.

---

### Post by MandeaSaracu on 2010-05-13
Try copying wubildr.mbr and wubildr to every partition you have.

---

### Post by wmalik on 2010-11-23
I am facing the same issue. It was working fine for last 1 month but suddenly I cant access Ubuntu now because whenever I try to boot Ubuntu it sends me to the grub prompt.

---

