---
title: "Can linux simulate 3d acceleration?"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by garrowolf on 2008-02-18
I don't have 3d hardware acceleration on my video card. It was the first laptop that Dell offered Linux on and it didn't have much in the way of bells and whistles. I have a dual core processor with 2 gigs of RAM so I am wondering if there is any way to simulate the 3d acceleration with RAM like a swap file or something.

thanx

---

### Post by viciouslime on 2008-02-18
3D acceleration is handled by a GPU, and whilst graphics cards do usually have their own RAM (though low-end ones sometimes just use system RAM), it is the GPU that provides the actual acceleration. These chips are capable of performing common graphics-related calculations far more efficiently than a CPU. However, with a core2duo processor, many older games will run fine using software emulation, but the results you're seeing now are basically going to be the best you're going to get.

---

### Post by garrowolf on 2008-02-18
yes but the question is can it simulate it? So far it chokes when it trys to find it for some games. Can it at least make the program think that it has the acceleration and simulate it?

---

### Post by chavanak on 2008-02-18
I dont think that is possible though am not completely sure!!! Even if you try and get it done, it doesn't guarantee you performance!!

---

### Post by hardyn on 2008-02-18
if your notebook is that new, it will have SOME form of 3d acceleration, even if it is an i950 integrated chipset.  The question is more about getting the drivers straight.

I don't have a machine with intel integrated graphics, so im not of much use, but im sure you can find directions on this forum to  set the driver up correctly.

What exactly are you trying to do in the way of 3d?

---

### Post by jespdj on 2008-02-18
It depends on the video driver; if you don't have a good graphics card that has hardware-accelerated 3D graphics, then the video driver could render the 3D graphics in software. It will however be much slower than when you have a good graphics card, most likely it will be so slow that games will not really be playable.

---

