---
title: "Dell (intel) Video Drivers"
date: 2006-06-10
forum: Hardware &amp; Laptops
---

### Post by DiamondX on 2006-06-10
I have a Dell Inspirion E1505 (very similar to 6400), with the "Integrated Intel® Media Accelerator 950 Graphics" video card. I am currently using the Vesa drivers, but are there any that will work for this card that are better?

P.S. Is this the right place to ask? I couldnt decide between "Laptop HW Support" and "Video Card Support."

---

### Post by jer2eydevil88 on 2006-06-10
I am not sure if this is relevant to that card but have you tried this documentation?
[http://www.intel.com/support/graphics/sb/CS-010512.htm](http://www.intel.com/support/graphics/sb/CS-010512.htm)

---

### Post by SavageBeginner on 2006-06-10
Have you tried the i810 driver?

---

### Post by DiamondX on 2006-06-10
The Intel site doesnt have anything about the "Integrated Intel® Media Accelerator 950 Graphics". The closest thing to it is the 945. I just emailed them.

Edit: I think the 945 is the chipset of the 950, or something (I dont know that much about hardware). Im downloading the graphics drivers for the 945 chipset. On the page for the 950, the driver link goes to the 945. Im getting kinda confused...

---

### Post by DiamondX on 2006-06-10
[QUOTE=SavageBeginner]Have you tried the i810 driver?[/QUOTE]
How would I do that? By changing the xorg.conf file from "vesa" to "i810"? Ill try. Is there any way to know what drivers I have on my computer? I tried "i945", but I dont think I even have a driver called "i945".

---

### Post by SavageBeginner on 2006-06-10
[QUOTE=DiamondX]How would I do that? By changing the xorg.conf file from "vesa" to "i810"? Ill try. Is there any way to know what drivers I have on my computer? I tried "i945", but I dont think I even have a driver called "i945".[/QUOTE]Yea, that should work.  The i810 driver is installed by default so it should be on your system.  I think the i810 driver is for cards from the i810 and higher.

Has this worked for you?

---

### Post by vr6stress on 2006-06-10
use the 915resolution - i run an acer with a 950 chipset and i'm now able to get 1280x800 res on my 15.4 screen because of that fix...

some reason my xorg.conf was right with the resolutions, but 1280x800 was never an option...

followed the directions and got the patch installed and now everything is super peachy!

---

### Post by DiamondX on 2006-06-11
Sorry about not replying earlier. I was installing WoW, ran out of space, and screwed up the FS by mounting a new partition on /home... Atleast I wont do that again(it deleted everything in /home, including my main account & settings & files)! I just reinstalled Ubuntu with the new livecd/install cd. I just changed the xorg.conf to i810. I will restart in a little while, and tell you how it went.

---

### Post by SavageBeginner on 2006-06-11
[QUOTE=DiamondX]Sorry about not replying earlier. I was installing WoW, ran out of space, and screwed up the FS by mounting a new partition on /home... Atleast I wont do that again(it deleted everything in /home, including my main account & settings & files)! I just reinstalled Ubuntu with the new livecd/install cd. I just changed the xorg.conf to i810. I will restart in a little while, and tell you how it went.[/QUOTE]
Great, hope it works for you. :)

---

### Post by jjcv on 2006-06-12
You have the same card as the 6400.  I used the instructions below to get mine working.

[http://klepas.org/2006/04/09/ubuntu-on-the-inspiron-6400/](http://klepas.org/2006/04/09/ubuntu-on-the-inspiron-6400/)

---

### Post by DiamondX on 2006-06-12
It works. Thanks for the link, jjcv, but I had just done that. I am using the i810 drivers, and 915resolution. I am pretty sure it works great, but I have no real way of testing it. Is there a benchmark program for linux?

---

### Post by SavageBeginner on 2006-06-12
Here's some things you can do:

To see if you have direct rendering enabled.
```
glxinfo | grep "direct rendering"
```
To test 3D graphics.
```
glxgears -printfps
```

---

### Post by DiamondX on 2006-06-12
Works! I get ~1600 FPS, and direct rendering is working! Thanks everyone.:D :D

---

