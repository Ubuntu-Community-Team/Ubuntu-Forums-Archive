---
title: "Jaunty Jackelope (v9.04) - boot/install problems"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by trhoresh on 2009-04-24
All,
 
I initially tried booting with the standard install file and reached the boot menu, but nothing happens when I attempt to install. In fact, nothing happens when I perform any of the options. I also tried the simple fix of removing the "quiet splash --" from the end of the command line and no change. I even resorted to attempting an install using Wubi and got nowhere. 
 
I then tried the AMD64 alternate installer and it shows nothing on the CD after writing the iso file (using InfraRecorder) and when I attempt to boot from the CD drive it simply boots windows from my HD
 
I also tried the i386 alternate installer just for kicks and got the same results as the AMD64 alt installer. 
 
Any insight/advice would be greatly appreciated. I would really like to get Ubuntu running, but the frustration at this point is getting old, to say the least.
 
System Specs: AMD64X2 2200MHz, MSI motherboard, lite-on CD/DVD-ROM (CD burner, DVD reader only), WD 200gig HD (about 170gig free), Nvidia 6900GT vid card, 2gig Patriot RAM. 
 
Thanks,
 
-Travis

---

### Post by Partyboi2 on 2009-04-24
Check that the md5sum matches before burning then try another program like [[COLOR=Blue]imgburn[/COLOR]]("http://www.imgburn.com/") to burn the iso to disk at x4 or less speed.

---

### Post by trhoresh on 2009-04-25
Partyboi,
 
Thanks for the input, I will give that a try. 
 
 
I forgot to mention in my original post, I am attempting to dual boot.
 
Also, from what I can gather, I should be using the main installer as it is for all x86 processors - what my AMD64X2 is, correct? I got a little confused when I came across the AMD64 alternate installer.

---

### Post by Partyboi2 on 2009-04-25
There is the ubuntu desktop live cd version which gives you the option to try ubuntu before installing and comes in 32bit and 64bit. You then have the ubuntu alternate cd which is a text base installer and comes in 32 bit and 64bit.

---

