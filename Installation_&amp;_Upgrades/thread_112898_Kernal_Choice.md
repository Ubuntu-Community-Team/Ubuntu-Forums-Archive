---
title: "Kernal Choice?"
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by ronlondre on 2006-01-05
I'm installing Breezy Badger on an older Gateway computer with a Pentium III CPU, 256mb RAM, and ~13.5 GB of HD space. I've come to a part of the installation which reads the following:
The list shows the available kernels. Please choose one of them inorder to make the system bootable from the hard drive.
Kernal to install:;
- linux-386
- linux-image-386
- linux-image-2.6.12-9-386



Which of the above kernels should I choose?

---

### Post by earobinson on 2006-01-05
[http://www.ubuntuforums.org/showthread.php?t=85917&highlight=kernel](http://www.ubuntuforums.org/showthread.php?t=85917&highlight=kernel)

---

### Post by AlexMorin on 2006-02-21
That page does not tell you which one to use when installing from CD.

To a newbie like myself, it's not a slamdunk :
- linux-386
- linux-image-386
- linux-image-2.6.12-9-386

What is the difference? I've been searching these forums left and right ("kernel", "breezy install kernel", "which kernel to use"), to no avail. I get hundreds of results, but none that help me out.
Sorry if this post bugs you, but I spent a good 30 minutes searching for an answer.

---

### Post by Killgore on 2006-02-22
I believe that i picked
- linux-image-2.6.12-9-386

Im pretty sure that you cant really go wrong with that one.

---

### Post by az on 2006-02-22
This is why you should never use the expert install.  

You shouldn't even be asked this question.

The correct package is linux-386, which will install the correct linux-image as well as the corresponding linux-restricted-modules.

Once you are online, install the linux-686 package, since that is an optimised kernel for a pentium.  On a pentium three, you should see a nice improvement in speed.

---

### Post by AlexMorin on 2006-02-22
Thank you very much!

---

