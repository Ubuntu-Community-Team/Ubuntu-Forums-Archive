---
title: "Graphics / DRIVERS on Acer 3000 series"
date: 2009-10-29
forum: Hardware
---

### Post by mbrincat on 2009-10-29
Basically ive just installed 9.10 and my graphics look terrible... i'm new to Linux so please be patient with me :S

does anyone know how i can check to see what display driver is currently being used? 

i think its the display driver, the backgrounds look really strange and pictures just look like thier in 16bit colour... :S not good....  my graphics on the laptop are SIS 600 series, Laptop is a Acer Aspire 3003 WLMI but i cannot find a Linux driver it is apparently included with the linux installation... 

I'm also having a bit of trouble getting the wifi to work... :(

Any ideas / suggestions...? :p

---

### Post by L33tN1nj4 on 2009-10-29
At the top of the menu click System > Hardware Drivers 
This will detect if you have one installed if not find one you can use.

---

### Post by rob.gilbert on 2009-11-03
I've had same issue on Acer 5000 series. Graphics were working under 9.04 and then upgraded. Still working but wifi failed using upgrade feature. 

Under 9.04 I had to uncomment a line to allow module to load for sis graphics. That solved flicker and poor graphics. Trouble is if I made notes, can't find. I don't recall the steps in previous solution under 9.04.

Anyway, I've downloaded both x64 and i386 iso and burned cd. Beside having Grub error15/17, now resolved, back to poor graphics and no wifi. Attempting i386 install and hoping better result.

If not, and find solution, will post.

:Found Solution ( SIS760GX graphics chipset ):

Edit file named modules found in /etc adding line sisfb, save, exit and reboot

from terminal$ sudo gedit /etc/modules
key, sisfb

---

