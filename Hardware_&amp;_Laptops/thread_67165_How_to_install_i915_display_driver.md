---
title: "How to install i915 display driver??"
date: 2005-09-19
forum: Hardware &amp; Laptops
---

### Post by mail2sona938 on 2005-09-19
Ive done exactly wat zacman has recommended in 
[http://ubuntuforums.org/showthread.php?p=359403&posted=1#post359403](http://ubuntuforums.org/showthread.php?p=359403&posted=1#post359403)

and I dont get GUI on restarting. What should I do? I hav switched back to vesa driver. Now Im usind 686 kernel. Pls help

---

### Post by mlomker on 2005-09-19
Did you try that because a **sudo dpkg-reconfigure xserver-xorg** and selecting the i915 driver didn't work?

I don't have that video card, but you'll need to provide a lot more details if you're looking for help.

---

### Post by mail2sona938 on 2005-09-20
Thanks a lot...Ive done it....I got it when I did dpkg-reconfigure xserver-xorg . Now Im getting 830FPS. Is there any way of getting any more..Anyway Im quite happy.

---

### Post by mlomker on 2005-09-20
> . Is there any way of getting any more..Anyway Im quite happy.

I doubt it.  You can get triple that with a modern ATI or Nvidia card but that's an inexpensive one.

---

### Post by caporaso on 2005-09-20
[QUOTE=mlomker]Did you try that because a **sudo dpkg-reconfigure xserver-xorg** and selecting the i915 driver didn't work?

I don't have that video card, but you'll need to provide a lot more details if you're looking for help.[/QUOTE]
 Hi:
Has anyone been able to get the i915 chipset working at 1920x1200 resolution? I've been working at it for a while with no luck, and I was just wondering if anyone had any ideas...  I am able to use the <b>sudo dpkg-reconfigure xserver-xorg</b> command, and configure up to 1600x1200 (which is stretched horizontally).  I have a Dell Inspiron 6000 with WUXGA panel.

Thanks for any help/ideas.

Greg

---

### Post by mlomker on 2005-09-21
[QUOTE=caporaso]Hi:
Has anyone been able to get the i915 chipset working at 1920x1200 resolution? [/QUOTE]

Have you looked in your /var/log/Xorg.0.log after trying it?  My guess is that it won't work because the controller won't have enough memory.

---

### Post by caporaso on 2005-09-21
Hi again:
I just checked that log file at found the following line which seems of interest:

(II) I810(0): Not using mode "1920x1200" (no mode of this name)

Above this is a list of the available modes, and 1920x1200 is not listed among them.  I could post the whole file if that would help, but it's pretty big so I didn't want to do it if its not necessary.

I'm at a loss for what to do to fix this, but any help would be greatly apprecitated.

Thanks!
Greg

---

### Post by mlomker on 2005-09-21
> I'm at a loss for what to do to fix this, but any help would be greatly apprecitated.


You probably can't.  The video cards built into motherboards do not have enough memory for such a high resolution.  I think you need to buy a card.

---

### Post by caporaso on 2005-09-21
[QUOTE=mlomker]You probably can't.  The video cards built into motherboards do not have enough memory for such a high resolution.  I think you need to buy a card.[/QUOTE]
 I am sure that the hardware is capable of that resolution (I had it working with Win XP) and have heard that others have had luck, I just haven't got it working for myself yet. Thanks for your help!

--Greg

---

### Post by mlomker on 2005-09-21
[QUOTE=caporaso]I am sure that the hardware is capable of that resolution (I had it working with Win XP) and have heard that others have had luck, I just haven't got it working for myself yet. [/QUOTE]

In that case the linux driver doesn't support it.  I did some cursory searches but didn't find any alternative drivers.  That particular driver comes with the kernel.  Have you tried upgrading your kernel to a new version?  I think 2.6.11 is in the repos for Hoary.

---

### Post by mlomker on 2005-09-22
I ran across some 3D drivers for Intel cards today, including the i915.  I don't know how to install these since I don't have one of these cards, but [look here.](http://dri.freedesktop.org/wiki/Intel)

---

