---
title: "finding out what brand/type of ram i have"
date: 2005-12-01
forum: Hardware &amp; Laptops
---

### Post by renzokuken on 2005-12-01
i have 512mb of ram at the mo but want to upgrade to 1gig. i have a Asus A8V deluxe mobo so ideally i would like to buy another 512mb stick that is exaclty the same brand and type as my current one for dual channel purposes.

is there any way to find out what my current type of ram is (short of opening up my box and having a peek) >_<

also, whats the deal with linux and upgrading ram? does it automatically detect the upgrade or will i have to recompile/patch?

thanks

---

### Post by Dr. Nick on 2005-12-01
Not sure if brand name really matters for dual channel. I would just buy the same speed, which would probably pc3200. When your system boots it should tell you the ram speed, something along the lines of dram clock. I know that dual channel needs the same size/speed module, but I havent worried to much about the brand when ive done it. 

Unless your buying good memory like mushkin or ocz who make their own chips, or use only one provider, you cant really guarntee you will get the same memory chips. I bought 2 pny sticks seperately, one was a real good chip that would overclock a ton, the other was cheap and wouldnt budge past the default speed without crashing.

Linux adjust the memory for you, the only thing that wont be auto adjusted is the swap partition, but if your going to 1gig of memory you really dont need to worry about the swap as it will be used less, it shouldnt cause any problems.

EDIT
When you start your system look at the grub menu, may require you to hit "esc". Memtest may be on their , if you run it you may get some info on the installed memory aswell

---

