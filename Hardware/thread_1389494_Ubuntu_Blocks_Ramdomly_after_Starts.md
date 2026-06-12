---
title: "Ubuntu Blocks Ramdomly after Starts"
date: 2010-01-24
forum: Hardware
---

### Post by ferminnajar on 2010-01-24
Hi,
I have a laptop Toshiba Satellite with 4 gb of RAM an a ATI Radeon video card. I installed the Ubuntu 9.10, and also i installed the ati drivers.

The problem i have is that sometimes Ubuntu starts, and sometimes dont.
When start my computer, i have to turn it off and turn it on 4 of 6 times and then, Ubuntu starts. 
Before start, i get blocked in a blank ( black ) screen after the logo appears.

I tried to use this but doesnt work:

[B]sudo dpkg-reconfigure -phigh xserver-xorg

[/B]Any ideas ?

---

### Post by ferminnajar on 2010-02-07
Is there somebody who can help ? 
I will show you a private message that i received, i wont write his user name for respect:


" Hi, I write you directly because some people in here don't like me pointing out that Ubuntu 9.10 has some annoying bugs regarding switching on and off. I tried 9.10 for a week and decided that it was basically not worth the sweat.

If the machine runs well with a 9.04 live CD, I woud recommend doing a clean install of this version. Fully supported and much more stable.

[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

Best regards"

Thats why i dont uninstall Windows yet.

---

### Post by llawwehttam on 2010-02-07
Ubuntu 9.10 was a bit of a guinea pig release......... or maybe lab rat translates better for others. Anyway there are a lot of new things in it such as the new type of GDM, grub2 and various other bits and bobs. 

Linux has never really been good with ATI cards. ATI have not made their drivers well for linux and the free ones are not very good whereas Nvidia's linux drivers work very well. I have seen a lot of problems with ATI cards and drivers in various linux distros.

Ubuntu 10.04 Lucid Lynx LTS will be much more stable and should be a much better release all round. The only reason I am using 9.10 is because I don't mind bug fixing.

---

### Post by 23dornot23d on 2010-02-07
Do you get as far as the boot menu ..... 

if not grub2 possibly .... 

what errors do you see if any ?

does ctrl + alt + f8 ...... work at the black screen or is it locked up at this point ....

does it run from the live CD ok ....

---

### Post by acornbrain on 2010-02-16
23dornot23d, 
 
I am having a similar problem:
 
[http://ubuntuforums.org/showthread.php?t=1407927](http://ubuntuforums.org/showthread.php?t=1407927)
 
Boots fine from Live CD, but black screen only on regular boot. No Ubuntu startup noise, just black screen. I think Ubuntu boots and logs me in automaticaly, because the hard drive lights are working, and the light on my wireless adapter is working as if it is connected, and I can restart by ctrl-alt-del, just no picture whatsoever. In fact, monitor will go to power save mode after a few minutes from lack of signal.
 
Any help would be greatly appreciated!
 
I can use the Live CD fine, and my filesystem and all my stuff is there, as if it is a mounted volume.
 
THANKS!
 
-brian

---

