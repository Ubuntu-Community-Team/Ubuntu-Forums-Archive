---
title: "Missing memory/RAM."
date: 2016-01-09
forum: Hardware
---

### Post by jeani on 2016-01-09
Hi,

I brought  new computer the other day and I have been plagued with instability since I first got it up and running, mainly allot of bad boots (having to reboot manually a few times to get into any OS), but the biggest problem is that my RAM seem to be missing 8gb out of 16gb, I have tried changing them around in the two slots, and it worked for one boot, as in Ubuntu it said I had 16gb, but then when I tried booting into Windows it again said 8gb, and in Ubuntu now it also again says 8gb. 

My setup:

-Ubuntu 15.10 x64 / Windows pro 8 x64
-Gigabyte GA-F2A88XN-WIFI, Socket-FM2+ (updated the Bios to the latest version)
-HyperX Fury DDR3 1866MHz 16GB Black (Two 8gb sticks)
-AMD Athlon X4 860k Black Ed. Socket-FM2+
-MSI GeForce GT 740 2GB PhysX CUDA

I could see the full 16gb in Bios the whole time, but only one time in Ubuntu so far.

Anyone know what I need to do to get the full 16gb working in Ubuntu and also hopefully Windows?

---

### Post by kurt18947 on 2016-01-09
I think I'd run memtestX86 for a few hours to be sure you don't have a bad RAM stick or bad MoBo RAM socket. Memtest is found on *buntu live CD/USB.

---

### Post by jeani on 2016-01-09
> **kurt18947 said:**
> I think I'd run memtestX86 for a few hours to be sure you don't have a bad RAM stick or bad MoBo RAM socket. Memtest is found on *buntu live CD/USB.


Forgot to mention that I have already done that, no errors.

---

### Post by jeani on 2016-01-09
I am also currently test running two 2x 2gb cossair RAM from my old computer and they are working fine so far. Will try all possible combinations with old RAM and new.

---

### Post by jeani on 2016-01-09
I just checked Bios with the original 16gb installed after testing various combinations, now it only lists 8262mb and not 16gb as it did before..will try to change them around and see if the numbers in bios change again.

---

### Post by jeani on 2016-01-09
Ive noticed that if I reboot holding the power button in I get 16gb when it reboots, but if I press the reset button I only get 8gb...I also think my Nvidia drivers are a problem, but not sure if it is related to the Ram issue?

---

### Post by kurt18947 on 2016-01-09
I'm just guessing here - no expertise beyond having fooled with this stuff a few years. What happens if you just install one stick at a time and reboot?

---

### Post by jeani on 2016-01-10
> **kurt18947 said:**
> I'm just guessing here - no expertise beyond having fooled with this stuff a few years. What happens if you just install one stick at a time and reboot?

It boots up just like a regular boot, I tried both sticks in each slot and the same out come, no difference. 

This morning it took many boots for me to get into Ubuntu, and when I do get in I get an error message. I found that the best way to get into the default Ubuntu desktop is to log into Cinnamon or Gnome desktop first, then wait a few minutes and log into the default desktop, which works then, as if I go straight into the default desktop it usually crashes(freeze up) within a few seconds..

---

### Post by jeani on 2016-01-10
Think I will try to install 14.04 instead, as now even my Logitech mouse is having issues, have to use a secondary mouse...

---

### Post by jeani on 2016-01-10
Using 14.04 now, it is much more stable, even when I have 16gb active, however it is not working 100%, I struggle when trying to install Nvidia drivers as an example, it is as if the computer forgets that I have pressed "apply" and just goes back to the default X server, I tried installing Nvidia drivers a few times but I cant get it to finish...Maybe I should ask the shop to replace the ram I brought, but what if it is the motherboard?

---

### Post by kurt18947 on 2016-01-10
> **jeani said:**
> Using 14.04 now, it is much more stable, even when I have 16gb active, however it is not working 100%, I struggle when trying to install Nvidia drivers as an example, it is as if the computer forgets that I have pressed "apply" and just goes back to the default X server, I tried installing Nvidia drivers a few times but I cant get it to finish...Maybe I should ask the shop to replace the ram I brought, but what if it is the motherboard?

I'm not a pro, just a hobbyist who's made the occasional expensive mistake. If you were to go back to the shop, your best case would be that Windows doesn't see 16 GB. of RAM. Depending on your shop, they could use an argument (though I'd hope not) along the lines  of "This motherboard isn't rated to work with anything but Windows. Running an unsupported operating system voids your warranty." If only Windows were installed when you go to the shop, that argument need never come up. As long as Windows continues to see 8 GB. RAM when there's really 16 GB. I'd think you have an excellent case that there's a hardware failure of some sort.

One thought I just had. Did you consult the motherboard book manual installing the DRAM? It may matter which slots are filled in what sequence. IME that's a function of dual channel memory vs. single channel but just something to check.

---

