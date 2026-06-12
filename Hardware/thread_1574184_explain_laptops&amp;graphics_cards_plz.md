---
title: "explain laptops&amp;graphics cards plz"
date: 2010-09-13
forum: Hardware
---

### Post by flyingsliverfin on 2010-09-13
as far as ive picked up, desktops have a motherboard, on which u stick a video card, which has a gpu on it. and from incomplete info ive picked up and pieced together from other random places, a laptop has a motherboard, without a video card, but the gpu sticks on the motherboard.
i dont think ive got everything right here...

---

### Post by mastablasta on 2010-09-14
you got it half right. 
 
Most notebooks have so called integrated graphics cards that use computers RAM (such as INTEL GMA). Some however have dedicated graphics cards, similar to the ones found on desktops. the ones with dedicated cards are usually more expencive. but also perform better (e.g. Alienware computers)
 
Lately another type is appearing with notebooks that have graphics card integrated into CPU. I am not quite sure why this is good, but i think it has to do something with powersaving and also to save on space (everything becomes smaller that way and can maybe be used on phone or similar small device).

---

### Post by flyingsliverfin on 2010-09-14
so i guess that last one is what comes new with the intel ix cores?
what kind of ram does that intigrated in the cpu graphics card take?
and how can they integrate a whole graphics card into the cpu? ive looked into my desktop and the graphics card is about  1/5 of the size of the whole motherboard.

---

### Post by cascade9 on 2010-09-14
A motherboard can have intergrated graphics or a standalone GPU. Doesnt matter if its a desktop or a laptop. 

Most laptops have intergrated graphics, because its cheaper. Sometimes they have GPUs soldered onto the motherboard (you can get this with desktops as well, its just very rare) and some laptops even have a 'video slot' (like a desktop PCIe slot but it can only be used for video cards, not for other hardware like RAID controllers, sound cards, etc). 

The intel "GPU on the CPU" idea is more about intel saving money, and expanding the domination they have over video chips than anything else (yes, ATI and nVidia are the biggest makers of video card GPUs, but intel has more market share than either of them) 

Only the i3 and i5 have the GPU on the CPU, i7s dont. Intel has assumed (rightly IMO) that anyone who can afford an i7, laptop or desktop, can afford a decent GPU. 

If you used the GPU on the i3/i5 chips, it uses the main system RAM. iX has to use DDR3 AFAIK, so it will be using DDR3. 

BTW, the size of your video card will be (mostly) used by RAM chips, etc. The actual GPU isnt that big, and the i3/i5 GPU will be a lot smaller than most GPUs (as it is laking a lot of the power of ATI/nVidia GPUs)

---

### Post by flyingsliverfin on 2010-09-14
> **cascade9 said:**
> 
as it is taking a lot of the power of ATI/nVidia GPUs
what do you mean, that they use more almost the same amount of power as in current or that it has the same performance as the ati/nvidia gpu's

the integrated graphics cards or the i3/5's are enough to watch hd movies and play basic games though right? or does the seperate gddr3 ram make that much of a difference?

---

### Post by cascade9 on 2010-09-15
"Lacking", not "taking". Intels video chips have always been gutless. 

The i3/i5 GPU should play basic games, and most of them should have the CPU power to decode HD, even if the GPU doesnt help (I have no idea on how well VAAPI is working with intel these days, let alone the new i3/i5). 

Honestly, for games and HD, you would be bettter of with an nVidia GPU and an AMD CPU, or even a Core2Duo.

---

### Post by flyingsliverfin on 2010-09-15
r the gpu's and cpu's in laptops exchangeable? (just wondering)

---

### Post by cascade9 on 2010-09-16
> **flyingsliverfin said:**
> r the gpu's and cpu's in laptops exchangeable? (just wondering)

Depends. 

You cant change an AMD CPU to Intel CPU with any modern system, laptop or desktop. You may be able to change one AMD or Intel CPU for another of the same type and family, eg, you might be able to change an Intel Core2Duole CPU for another Core2Duo. It wotn always worj because of different power abd FSB requirements, and BIOS support.  

Its never posible to change from Core2Duo to i3/i5/i7. 

As for the GPU in laptops....very rarely are they changeable. Very few laptops have the MXM slot that you need to change GPU in a laptop,and even if you do get a laptop with an MXM slot, teh GPU replaccements are very expensive. 

If you want to play around with changing hardware like that, get a desktop- its easier, faster, cheaper with far more options that laptops.

---

