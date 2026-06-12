---
title: "I need this computer, but it has an ATI card!!!"
date: 2009-07-31
forum: Hardware
---

### Post by Topher88 on 2009-07-31
I am looking to buy [this laptop]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834157020"), but it has an ATI Mobility Radeon HD 4650 graphics card, and I have heard that ATI and Ubuntu don't play well.  I recently started [this thread]("http://ubuntuforums.org/showthread.php?t=1228155") comparing this laptop with a similar Intel based laptop, but I later realized that the Intel laptop didn't have the IEEE port that I would need for video editing.  If I purchase the ATI laptop, will I be shooting myself in the foot if I would like to also run Ubuntu?

---

### Post by thetick1 on 2009-07-31
Well it really depends on which ATI chipset and which driver.  

For example I have an old Thinkpad A22m with an ATI Rage 128 M3.  Ubuntu picked the ati driver instead of the r128 and my screen was completely messed up (parts of screen missing ,others were repeated).  I was very luck my LCD was not damaged. 

So I tried a few other distros and Puppy Linux which is good for old hardware setup Xorg perfect at 1400x1050 display.  So I just copied the Xorg.config file to my Xorg Ubuntu directory and my ati M3 video works great with Ubuntu.  I have to switch to 1280x1024 with the dri driver for 3D, but that is limitation on the video memory not a broken driver.

---

### Post by PatrickVogeli on 2009-07-31
I'd say you'd better go with intel. Right now, Intel processords outperform AMD, and this is specially true in laptops, where AMD is now way behind.

Also, using linux, you'll probably have better luck with some fully intel based notebook (chipset, graphics and wireless) than with amd, which usually use broadcom, atheros or, even worse, realtek wifi chipset, which can be tricky to set up or directly impossible.

So, just look a bit more and don't hurry in buying a laptop, take time.

---

