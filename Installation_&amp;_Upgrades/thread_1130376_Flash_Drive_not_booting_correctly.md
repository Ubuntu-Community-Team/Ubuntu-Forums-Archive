---
title: "Flash Drive not booting correctly"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by Guillaumeb on 2009-04-19
hello,

After installing ubuntu on my netbook i wanted to install it on my second laptop

The laptop is running Windows Vista. I want to create a dual boot with 9.04

I created a USB flash drive with Unetbootin, had the laptop boot on the USB but then I am having the problem shown in the pic below:

[IMG]http://yahoovibes.com/failstoboot.jpg[/IMG]

Do you guys could tell me what to do to make it work? It happened to me on my netbook yesterday and I had to give the idea of installing 9.04 and install UNR.

I would like to test 9.04 before installing it and see what works. Also i want to install the OS from the live environment, as i'd be more comfortable. Thing is, how to make it work ?

Thank you very much

---

### Post by sobrien on 2009-04-19
At the "initramfs" prompt, type exit; it will give you another initramfs prompt to which you type exit again.  Do this a total of four times, and then Ubuntu 9.04 "Jaunty" will pop right up.  It works great, and I like a lot of the changes, BUT, the USB stick does NOT remember any changes that you make.  

I hope that this can be fixed; there are times when having my handy USB flash drive with Ubuntu on it is quite helpful.

---

### Post by Guillaumeb on 2009-04-20
This won't work unfortunately...

---

### Post by Guillaumeb on 2009-04-20
Just so you know today's build corrected the problem with an ISO file that was 699 Mo instead of 4,2 Go yesterday...WTF ?

---

### Post by tamas305 on 2009-04-20
I tried to boot Ubuntu from my USB on my friends computer, an old gateway, and when I went to the boot menu and selected to boot from external USB drive. It just did not do anything, it booted from the internal hard drive (Windows).

Sorry I'm not able to supply more information about his computer.
-tamas

---

