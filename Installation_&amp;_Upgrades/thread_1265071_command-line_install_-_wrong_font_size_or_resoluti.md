---
title: "command-line install - wrong font size or resolution"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by clevertomato on 2009-09-12
I'm experienced with PCs but a linux beginner. I have a week's experience with Ubuntu 9.04. I heard about Lubuntu and thought of my old Pentium II, then learned it'll be a while before Lubuntu is released. For fun, I decided to install a base command-line Ubuntu using the alternate iso. I have spent all of a couple days with this. Upon booting after the install, the font used is huge. This results in only part of the screen being visible on the old Gateway LCD panel. I can only see several lines above what I type, so I'm running blind. I've no idea why it's doing this. I searched and searched. I've tried editing the Grub entry upon boot, adding "vga=792" and other combinations, but that results in worse... colored blocks (like a strange game of tetris) on the LCD instead of words. What is going on and how can I fix this. It's not critical, but now it's just a matter of principle for me to figure this out. Otherwise, I'll have to admit defeat and resolve never to be able to install Ubuntu (command-line) on this PC. Incidentally, I have successfully installed the full Ubuntu 9.04 but it was PAINFULLY slow of course. I wanted to do a base command-line install and then load lxde (if I can figure out how to do that and load similar apps as Lubuntu), but I can't even get past this crazy problem so I can take a stab at the rest of my adventure. I certainly don't have a chance if I can't see what I'm typing into the command line!

---

### Post by clevertomato on 2009-09-13
Nobody has responded to my query... I'm not sure what to make of that. Maybe nobody will care, but just in case someone knows how to fix this or maybe this will help someone else out there... I at least identified the source of the problem. I removed the nVidia Riva 128 AGP display card and put in a different one (borrowed Asus V7100), flipped the on switch, and voila--I could see all my command-line screen on the LCD as it should be with a normal-sized font. I have no idea why the Riva 128 makes the command-line font huge (resulting in the line where the user types being off the visible screen area), and I still would like to know if anyone out there knows a fix for this, but at least I've narrowed down the source of the problem.

---

### Post by giuseb on 2009-09-15
I am experiencing the same problem, having installed the Ubuntu server 9.04 on an old Gateway Pentium II. Thanks for the tip on the video adapter, will try to replace it like you did. Sorry I cannot offer any meaningful insight on the matter...

Cheers,
Giuseppe

---

### Post by clevertomato on 2009-09-16
I'd be interested if swapping display adapters works for you, too. It's nice to think that maybe I could help someone out even though I'm a linux infant.  :)

---

