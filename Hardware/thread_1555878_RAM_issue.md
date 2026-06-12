---
title: "RAM issue"
date: 2010-08-18
forum: Hardware
---

### Post by Speckta on 2010-08-18
Hi. I recently purchased a second stick of 1GB RAM (400Mhz) from Corsair (the same exact stats as the 1GB of RAM currently in my desktop).

I installed the RAM and the computer powered on.

However, when I run ```
free -om
```This is the result I get:

```
             total       used       free     shared    buffers     cached
Mem:           607        472        134          0         71        176
Swap:         1608          0       1608

```Which doesn't sound like 2GB worth of RAM to me.

I was wondering if there was anything I had to do for Ubuntu 10.04 LTS to recognize the RAM.

---

### Post by Fafler on 2010-08-18
Not normally. You could try installing memtest86+. Select it from the boot menu (you might have to press ESC to get to it). It will show info about the modules you have installed.

---

### Post by jimbop99 on 2010-08-18
Also check your BIOS to see if it is showing up there.

---

### Post by Speckta on 2010-08-21
I'm preparing some pictures to show you what's going on.
I installed memtest86+, and the "show memory configuration" option indicates that there are, indeed, two sticks of 1024MB with 400 Mhz speed.
However, it only tests 624MB. (and usually with 200-333Mhz of speed, so not full speed).
After running the memtest for 66+ hours (don't judge! I was gone all week-end), I did find some errors in the test.
The boot screen only shows 624MB.
I have a built-in video card which takes ~128M of RAM for framebuffer in the BIOS.
I -cannot- find an option in the BIOS to try and manually set the RAM settings.

I'm afraid this may mean a problem with the motherboard.
Let me know what you think. I'll post pictures of this stuff soon.

---

### Post by Speckta on 2010-08-21
Sorry for the double post, but here are the pics:

[IMG]http://i664.photobucket.com/albums/vv10/Speckta/1GB400Mhz.jpg[/IMG]

[IMG]http://i664.photobucket.com/albums/vv10/Speckta/Chipset.jpg[/IMG]

[IMG]http://i664.photobucket.com/albums/vv10/Speckta/Mem86-errors.jpg[/IMG]

---

