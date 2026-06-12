---
title: "Patching the kernel?"
date: 2008-10-18
forum: General Help
---

### Post by Ernir on 2008-10-18
I think it is in order to begin with a description of why I want to do this...

My wireless card (realtek, rtl8101e) on my laptop is not working. Apparently I was not the only one with this problem, so after a bit of searching I found this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256331/comments/9](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256331/comments/9)
The latest kernel patch supports this! Whoo! \o/

The problem is... how do I do that? Know that this computer has nothing on it but a brand new Kubuntu install and no way to directly reach the internet.

I downloaded the top file from [http://www.kernel.org/](http://www.kernel.org/) , and have transferred it to my laptop. Now I have a file called patch-2.6.27.1 on my desktop, and no idea how to apply it. I did not manage to wrap my head around the tutorials I could find, sorry. =(

Can you help me make this work? =)

~Ernir

---

### Post by cicatrix1 on 2008-10-18
Compiling a kernel is a fairly long process.  What you have downloaded is a patch file, which is used to modify source code.  Which means you'll have to download the kernel source, apply the patch, then compile the kernel.  It's quite the undertaking, really.  I would read some HOWTO's regarding kernel compiling if you really need to go through with it :)

---

### Post by Ernir on 2008-10-18
Oooff. Did not think I was in *this* deep over my head. xD

I guess it is back to the tutorials, then.


Unless someone has a better way to make this card work? :(

---

### Post by Ernir on 2008-10-18
One idea I just had - does the intrepid beta that is currently out have the latest kernel version? I can not find any place that says so explicitly. =)

---

### Post by Absorbed on 2008-10-18
Master Kernel provides easy to follow steps to compile the latest kernel: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

I did it successfully, but it takes three hours to compile on my 2.8ghz cpu.

Edit: Oh, to apply the patch you go into the /usr/src/linux-2.6.27 folder (assuming that's where you extracted the source to) and then type "patch -p1 < /path/to/patch-la-de-da"

---

### Post by GuitarRocker2562 on 2008-10-18
> **Ernir said:**
> One idea I just had - does the intrepid beta that is currently out have the latest kernel version? I can not find any place that says so explicitly. =)

Yep, and it's pretty stable. But remember, it is in development, and something CAN go wrong, so if you absolutely need you computer to "just work" then I wouldn't suggest upgrading. That being said, at this point the only upgrades to it are for bugs, so it is less likely to die on you.

---

### Post by Ernir on 2008-10-18
Whoo! That even leaves me with *options*. =)

Thanks, both of you. =D

---

