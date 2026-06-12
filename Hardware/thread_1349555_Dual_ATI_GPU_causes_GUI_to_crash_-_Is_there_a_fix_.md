---
title: "Dual ATI GPU causes GUI to crash - Is there a fix to this?"
date: 2009-12-08
forum: Hardware
---

### Post by spydeyrch on 2009-12-08
I love playing arounud with linux and it's distros, primarily ubuntu and it's derivitives. I have noticed something that is a real pain!! I have a dual boot system: Win7 x64 and Ubuntu 9.10 x64. I love to play games on my win7 partition but love to be productive in on my ubuntu partition. The issue comes from the fact aht I have two ATI GPUs in a crossfire setup to play the newer games at higher resolutions. Once I switch back over to ubuntu, if I have both cards in the machine still, than no mater what I try, the GUI for ubuntu WILL NOT LOAD!!! I am stuck starting in the terminal. It isn't even like the GUI starts and I can see my desktop and then BAM!! I get booted out and sent to the terminal. Nope. I start the machine, ubuntu does its loading progress bar thing and then straight to the terminal. I have searched around and haven't seen anyone else have this same issue but I might have missed something.
 
Anyone have any ideas? I hate having to power down my win7 partition, pull out my second GPU, and then start my ubuntu partition JUST to use ubuntu. It is a pain in the neck. It wouldn't be that big of a deal if I didn't game on my win7 system. I play games like Crysis, Far Cry 2, Assassins Creed, etc. Games that will not work in wine or crossover, sorry, I have tried.
 
Is there a solution to this issue?
 
Thanks for your help guys!
 
-Spydey :P
 
P.S. Here are my specs:
 
AMD Phenom 9950 oc'd 3.2Ghz
Asus M3A79-T Deluxe Mobo
2 x ATI HD3870 in CrossfireX (for Win7)
4 gigs DDR2 PC8500 1066 Mhz
Win7 x64 & Ubuntu 9.10 x64

---

### Post by spydeyrch on 2009-12-11
*bump..... bump....bumpity....bump....bump*
 
Anyone? Has anyone else experienced this with a dual GPU setup?
 
Any input would be greatly appreciated. Thank you a ton! :-)
 
-Spydey
 
 
:popcorn:

---

### Post by markbuntu on 2009-12-11
From the terminal try

sudo aticonfig --list-adapters

to check if the driver sees both cards. 

sudo aticonfig --adapter=all --initial -f

then reboot to initialize both cards.

aticonfig --help

for a list of aticonfig commands and explanations of what they do which you will need to set up crossfire.

---

### Post by spydeyrch on 2009-12-11
Thanks a ton markbuntu! :D  I will give it a try when I get home from work. thanks for your help!
 
-Spydey

---

