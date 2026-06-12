---
title: "Laptop display issues"
date: 2010-07-26
forum: Hardware
---

### Post by squiffer on 2010-07-26
Hi all, 

Using Ubuntu is my first relationship with a Linux operating system, and so far I am enjoying it! 

However, I seem to have a major concern with the display on the monitor on my laptop. I am using an EI Systems 4412 laptop, and on the first install of the latest Ubuntu, I was able to see everything on screen perfectly fine, but after a few hours the display has completely gone from the monitor and I am left with a blank screen. I have tried several restarts and on on start up, the BIOS messages appear perfectly fine, indicating the monitor still works, but as soon as Ubuntu being to run, all sings of visuals are gone.

 I connected my laptop to my TV  using a VGA cable and I can see everything perfectly fine, no problems at all, but I am still left with no output on the laptop monitor. 

After browsing around, I found that a re-install could work. I tried this with no luck at all. I have had no problems using Windows XP.

Anyone that has any suggestions will be greatly appreciated!

---

### Post by Tiberion on 2010-07-26
What is your video card on the laptop

---

### Post by squiffer on 2010-07-27
The only details I can find out about the graphics card on this laptop is that's it has an Intel Extreme 256-bit 2D/3D graphics accelerator, I can't seem to find out much more about it

---

### Post by Tiberion on 2010-07-27
Open terminal and run this, paste your results here on the forum
sudo lshw -C display

---

