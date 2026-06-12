---
title: "Mobility Radeon 9200"
date: 2006-06-25
forum: Hardware &amp; Laptops
---

### Post by Corey on 2006-06-25
Anyone else using a laptop with a mobility radeon 9200? If so can you please tell me how you got it to work in dapper? Mine work beautifully in breezy but now I can't get it to work at all. Xorg yields nothing but a black screen with the ati, radeon, or fglrx driver. The only driver that works in Vesa but I can't get vesa to run at 1200x800 so I have ugly black bars on the sides of my screen. Please help!!!

---

### Post by Kosmonaut on 2006-06-26
Have you tried to reconfigure your X-Server? If no, then try this:

> sudo dpkg-reconfigure xserver-xorg


---

### Post by Corey on 2006-06-27
Yes i tried that. It autodetected that I should use the ATI driver but I still just get a black screen from xorg.

---

### Post by Kosmonaut on 2006-06-27
Ok! Next step ;-)
 What does "/var/log/Xorg.0.log" and "etc/X11/xorg.conf" say?

---

### Post by doog on 2006-06-28
The ATI driver is broken with regard to the Mobility chips( Express 200M known ) and require you to disable onboard memory( called Sideport ) in the BIOS and setup 128MB of shared memory( called UMA ).  Try that and see if your blank screen goes away. If it does, PLEASE go to ATI.com and tell them you'd like them to fix the driver.

[https://support.ati.com/ics/support/KBAnswer.asp?questionID=1714](https://support.ati.com/ics/support/KBAnswer.asp?questionID=1714)

Once you report back, I'll tell you how to get back your 128MB of onboard memory for 2D-only support.

---

### Post by Corey on 2006-07-27
Thanks for the tip, but unfortunetly this PC has the worst bios ever. The most "advanced" setting is wheter to show a vaio animation at startup and what level the speakers should be set at. There is no way for me to edit graphics settings in this bios. The good news is I've discovered a very strange solution by screwing around with my xorg.conf and various modules while running in rescue mode. For some reason the ati driver works as it should just as long as the fglrx module has been loaded. I set my xorg.conf to use the ati driver but I added fglrx to my /etc/modules file so that it gets started at boot. Now I can run at my full native resolution but still no 3D accel. I can certainly live with that (for now). Very very strange solution though, i dunno why it works but it does. Hope this helps others with this problem. And I can only pray that AMD will treat us better in the future than ATI has in the past!!!

---

### Post by Okami on 2006-07-28
Sounds a little like the problem I had, but I have an radeon 320m. 
For me Xorg freeze with direct rendering enabled, I had to disable direct rendering or use vesa as drivers. The solution was to use a custom DSDT. 
It may not be a solution for you but... you never know =)

---

### Post by Corey on 2007-03-09
Whats a custom DSDT? I've got a usable set up right now, but I cannot get Direct Rendering working.

---

### Post by nova972 on 2007-08-28
I have a very similar problem, can someone please help me , in relatively simple directions...

Im running an old sony vaio with a radeon mobility 9200 card, the resolution Im aiming for is 1280x800, the only driver that seems to work is VESA.

Ive been using Sudo dpkg-reconfigure xserver-xorg to play around and try whatever drivers are available, the ATI driver wont load at all.

Ideas???

thanx

btw Im running Fiesty 7.04

---

