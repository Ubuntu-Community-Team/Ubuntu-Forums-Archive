---
title: "Resolution Problem"
date: 2008-08-12
forum: Hardware
---

### Post by Lufkin on 2008-08-12
Hi,

Okay, it's something wierd. I installed Ubuntu 8.04 like two days ago, everything was fine, resolution of 1028x780 like always. But this morning, "woops", the resolution changed to 800x600, I do not how.

I removed the nVidia "restricted" driver and reinstalled it, and now, I can't have more than 640x480 !!! What's the problem ?!

I have a GeForce 5600 video card.

Thanks.

---

### Post by tuxxy on 2008-08-12
Are you tryin to change the res through nvidia-settings?

Search through synaptic for nvidia driver see which one is installed, either nvidia-glx or nvidia-glx-new, remove the driver you installed, now try and enable the driver again through hardware drivers

---

### Post by Lufkin on 2008-08-12
I did it and nothing changed. Both nVidia-settings and "Screen resolution" have only 640x480 and 320x420 ...

It's nvidia-glx-new version 169.12+2.6.24.13-19.45 that is installed.

---

### Post by Lufkin on 2008-08-12
Okay, i found something here :

[http://ubuntuforums.org/showthread.php?t=832943](http://ubuntuforums.org/showthread.php?t=832943)

But I'm not sure that "forcing" the system to put the resolution we want is something good. Or not ? Anyways, thanks for your help. :)

---

### Post by Bellissi Moron on 2008-08-13
I've just had exactly the same problem with a Nvidia 7200 card and 15" LCD Monitor and only solved it by doing the following:

a) Open up computer
b) Remove Graphics Card
c) Replace Graphics Card
d) Re-start computer.

On start-up you will see a message saying your resolution is too low and would you kike to change it ... oh, yes PLEASE!! ... there are two drop-down dialogues one for resolution and the other for the monitor. I was able to select the correct reso and monitor-type from those. When the computer continues to boot-up it will still be in the low resolution. Re-boot your computer. Your next horrifying sight will the username box which appears to be in an even lower resolution than before ... can't quite figure that one out ... anyway, don't panic ... enter your user and password and, hey presto, you're back in business with the correct reso size for your monitor!

So that's it ... simply reset your graphics card ... I wish I'd thought of that at the beginning and saved myself a load of unnecessary hassle!

BM

---

