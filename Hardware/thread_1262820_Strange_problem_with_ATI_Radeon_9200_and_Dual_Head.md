---
title: "Strange problem with ATI Radeon 9200 and Dual Head"
date: 2009-09-10
forum: Hardware
---

### Post by strixx on 2009-09-10
Hi,
 
I have a strange problem. I just installed Ubuntu 9.04 on a computer with a ATI Radeon 9200 graphic interface with 128MB RAM. I have one monitor connected to the VGA connector and one to the DVI-I connector.
 
Everything looked like it was working. I checked off the "Mirror screen" in Screen resolution and I got my desktop to strech out to both screens.
 
But here is the problem: When I "use" the (about) 5 last pixels to the right on the second screen it messes up. It seems like that part of the screen doesn't update correctly. I can move the mouse in that area without any problems but as soon as I move a windows in that area or maximize a windows on the second screen it goes crazy.
 
I've searched the forum but found no answers, only a lot of threads about problems with getting the dual head to work at all.
 
I've tried a openSUSE live CD and there it worked fine.
 
Here is my xorg.conf:
```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection
 
Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Virtual    2048 768
    EndSubSection
EndSection
 
Section "Device"
    Identifier    "Configured Video Device"
EndSection
```
Does anyone know what to do?

---

### Post by strixx on 2009-09-22
I have now tested a little bit more, and found out that the problem only occurs when i have the screenresolution set to 1024x800 on both screens. If I reduce the resolution on only one screen then it works fine.
So as I understand it there must be a problem with the memory allocation in some way.

But I don't understand wy it works in openSUSE but not in Ubuntu. Could it be different driver or kernel? I will try to continue researching but I would really love some input.

---

### Post by strixx on 2009-10-18
Anyone?  :(

---

### Post by strixx on 2009-10-20
Found a way to make it work.

By turning Compiz off it works. But according to this "[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)" that should only apply to cards with 16Mb RAM or less, and mine has 128Mb.

Could there by a bug in the driver that unable it to locate all memory?

---

