---
title: "Install disk works, will not boot after restart"
date: 2012-12-28
forum: Hardware
---

### Post by kuro114 on 2012-12-28
Hello,
So I just recently built my first computer (yay!) however I am having some difficulties. I was able to mount Ubuntu onto a DVD, and then turned my computer on and successfully installed it, however after the install and the restart Ubuntu will not launch. All I get past the flash screen is a black screen with a blinking cursor. I tried playing around in BIOS with the boot order (I put my HDD first) and it still will not launch the OS. Its weird because in the BIOS it recognizes that the HDD is there. When I put my DVD  back in I can get to the try ubuntu now part, and if I go back into install and see what the partitions look like it seems like my HDD is being used. So I dont know what to do now...I am stumped. Could someone please help me?
Mahalo!

---

### Post by ibjsb4 on 2012-12-28
Ctrl + Alt + F1

If that gets you to console then enter

```
startx
```

If you get a "x is already started" message, try

Ctrl + Alt + F7

Get a GUI?

What make/model of video card do you have?

---

