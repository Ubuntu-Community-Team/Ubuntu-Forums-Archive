---
title: "UVCVideo Error on boot"
date: 2010-09-22
forum: Hardware
---

### Post by canadacam39 on 2010-09-22
I think this is the correct place to post this....
I have playing around with Linux for about 3 months now, but have only recently fully installed it. I have a Sony VAIO VGN-FZ21S, and it plays pretty good with Ubuntu 10.04.
But to the point, my computer seems to hang at BIOS/GRUB. It just shows that little flashing __, hangs for a second, and then keeps going for about 30 seconds. After that, it says UVCVIDEO: FAILED TO INITIALIZE with some numbers, twice underneath each other, and shows the Ubuntu boot screen. 
I did a bit of Googling, and found that it was a webcam driver, and to check that the webcam works, I installed Cheese. Cheese couldn't find the built-in MotionEye camera, but had no trouble with my external Microsoft HD webcam. I tried with Skype, too - same result. 
My question is, can I remove the __ prompt, and the error message, to speed up boot time? It doesn't matter if it renders my webcams useless, I can use my desktop for Skype.

Thanks in advance,
Cameron

---

### Post by svega85 on 2010-10-17
this fixed my webcam, but not the error during boot [http://diogomelo.net/drupal/blog/10/webcam-problem-dell-inspiron](http://diogomelo.net/drupal/blog/10/webcam-problem-dell-inspiron)

---

### Post by Quackers on 2010-10-17
canadacam39 what is th webcam involved? I used to get the same messages during boot. The way I got rid of it was to load the driver and firmware for my built in webcam (Sony VCC6 with a R5u87x chipset). If you have the same camera you can get what you need here
[https://launchpad.net/~r5u87x-loader/+archive/ppa](https://launchpad.net/~r5u87x-loader/+archive/ppa)

---

### Post by canadacam39 on 2010-10-17
svega85, thanks for the link, have tried and the webcam now works, but only once; using it, then turning it off, if you want to use it again a reboot is required. But as said, there are still boot messages.

Quackers, have tried the link, and it works! I have a Vaio VGN-FZ21S and I tried the VGP-VCC8 and it worked! Messages during boot now only appear while coming out of hibernate, but I can live with that.

Thanks everyone! (A very quick thread :))
-canadacam39

---

