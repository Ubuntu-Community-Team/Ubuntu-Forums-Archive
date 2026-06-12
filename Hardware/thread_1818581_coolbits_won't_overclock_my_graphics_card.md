---
title: "coolbits won't overclock my graphics card"
date: 2011-08-05
forum: Hardware
---

### Post by Neutrosider on 2011-08-05
I have a Geforce 8500 GT, and i usually overclocked it in windows, so i tryied to overclock it in ubuntu too.

i googled and found out how to activate coolbits for the nvidia settings. that worked fine, also changing the Memory clock worked for me, but i can't really change the GPU Clock.

when i try to increase the gpu clock, it always jumps back to 459 (thats my default gpu clock)

the strange thing is, reducing the gpu clock works, but increasing it afterwards is not working. for example if i decrease it to 450, it works, but i then can't go back to 459 or anything above 450.

my default clocks are 459MHz for the GPU and 400 MHz for the Memory, and i used to overclock it to 640 MHz for the GPU and 430 MHz for the Memory in windows.

---

### Post by Neutrosider on 2011-08-06
*PUSH*

I now tryed nvclock too, but nvclock has the exact same problems as coolbits does.
I read that nvclock only really works with som older graphic cards. Does someone knows a way how to overclock the GeForce 8500GT ?? it's quite important for me ^^

---

### Post by Neutrosider on 2011-08-06
ok, i could solve the problem. i used XP to dump the graphic card bios, edited it using NiBiTor and reflashed the bios using nvflash. i couldnt overclock in ubuntu, but now ubuntu thinks the overclocked values are the default values :)

---

