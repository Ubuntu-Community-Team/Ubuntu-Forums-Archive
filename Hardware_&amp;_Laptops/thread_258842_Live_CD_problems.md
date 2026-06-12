---
title: "Live CD problems"
date: 2006-09-16
forum: Hardware &amp; Laptops
---

### Post by johanPO on 2006-09-16
Hello,

I have treated myself to a new PC. The old one is now at 4-5 years old, so I thought is was time. My plan was to connect the old hd and use the Live DC to partition the new drive and then copy all the files and then it should to my understanding work. 

So I build the PC and then I put in the Live CD, and boot... After the standard questions, the X server does not want to co-operate. So I have to edit /etc/X11/xorg.conf and change ATI to VESA to get a GUI. startx and we are up and running. Now to my surpise, my new SATA drive is not detected... 
after trying lots of things, I give up and put in the UBUNTU installation CD and reboot. To my surpise the drive is detected and the graphics gard detected and it is working. Only problem is that everything from the old PC is missing... 

Now my question is, why is my drive not detected by the Live CD when the older Ubuntu installation cd does? Both are Dapper. Second question is, does it now make sense to copy the old installation? I guess I will try it, but somehow I have a bad feeling about copying something onto a running OS. 

Any help is appreciated
Johan

---

