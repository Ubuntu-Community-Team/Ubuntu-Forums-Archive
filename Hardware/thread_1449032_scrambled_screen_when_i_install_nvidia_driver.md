---
title: "scrambled screen when i install nvidia driver"
date: 2010-04-07
forum: Hardware
---

### Post by yacine911 on 2010-04-07
hello every one 
first i want to thank you for your help and support
 
 i'v been using ubuntu sins one year now ''for study purpose"" but recently i get a big problem 
 
Whenever I try to install Ubuntu 9.10  I get a success installation and all function very well 

but when i try to install nvidia driver ""i'v tried all the version (173,175,190,and last 195)" my Screen become completely scrambled like a graphic error.

i can see the loading Bar with the Ubuntu Logo after that is just the scrambeld sceen I can enter my username / pw (by just typing and hitting enter) and the desktop loads but I cannot really make out anything because the graphics is just scrambled .  

i tried to reinstall Ubuntu many times i always get the same problem when i try to install invidia driver 

can somme one help me with that plesae 

i have hp pavillon DV6000 core 2 duo 2Go ram and NVIDIA GeForce 8400M GS


ps; i'm using window 7 in the same laptop and and it work perfectly

---

### Post by yacine911 on 2010-04-07
bump

---

### Post by yacine911 on 2010-04-08
can somebody help me please

---

### Post by yacine911 on 2010-05-05
first i will start with this  ""i'm very disappointed'', after a long time of waiting for Somme one to help me i just give up. so i decide to work with my other pc till the release of ubuntu 10.04 .

so a few days ago i downloaded ubuntu 10.04, burn it and i'v tried to install it, first i'v get the black screen problem but i did fix that then the rest of the installation went very well no problem at all 

after a few minute of suspense ''downloading and installing nvidia driver"" i get the same problem the scrambeled screen agin  aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa please somme one help me


PS;sory for my poor english;

---

### Post by yacine911 on 2010-05-05
up

---

### Post by philliprobert on 2010-05-09
Hi yaccine,
I am using 10.04 64 bit on a very similar laptop, a hp pavillion dv6000 with the nvidia 8400m gs card. I just did a normal install, with no issues whatsover, and then enabled the graphics card under hardware drivers, again with no problems. Is there anything from my config that would help you troubleshoot?

---

### Post by yggdrasil255 on 2010-05-11
Yeah, I just downloaded the 10.04 64 bit and burned it.  Seems to have burned alright.  I want to upgrade because I've just end of life'ed Ibex (a great OS.. I will miss the ibex) 

Tried to install Lucid and got a scrambled screen.  

HP Pavilion dv6000

Hopefully there is a fix in the works soon?  I'm anxious to try it out!

---

### Post by yggdrasil255 on 2010-05-12
OKAY!

I don't have a complete solution here, but maybe someone else can direct us where to finish solving this problem (currently running 10.04 of HP Pavilion dv6000)

So I used the 64 bit install disk.  When the first boot screen appeared, I hit a button and got to the screen where I was presented with choices for starting (memtest, try first, etc).  Usually it was after this screen where the trouble began.  

This time I hit F6 to look at the boot options.  I fiddled with some of the boot options and noticed that it worked.  Eventually, after two reboots or so I narrowed it down to the "nomodeset" option.  This will allow the screen to be viewable (not perfect, however).  I was able to complete the isntall at least, and test that other systems worked.  

The problem is, I have no idea what this actually DOES in grub.  So once my system was installed, it still did this, and still *does* during bootup and shutdown (I muddled through the scrambled screen and managed to put the proprietary Nvidia drivers on).

So that's that.  Maybe someone here can tell you exactly how to modify grub to make it boot like this and work perfectly.  If I find out exactly how to make it work, I will let this thread know.  Good luck!

---

