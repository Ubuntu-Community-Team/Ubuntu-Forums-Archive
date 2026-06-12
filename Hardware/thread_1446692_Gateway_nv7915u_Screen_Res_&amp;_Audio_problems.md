---
title: "Gateway nv7915u: Screen Res &amp; Audio problems"
date: 2010-04-04
forum: Hardware
---

### Post by whiskey.will on 2010-04-04
So I have just acquired a new laptop the [Gateway nv7915u]("http://www.gateway.com/systems/product/529668369.php") (or "desktop replacement" according to gateway, see:[http://ubuntuforums.org/showthread.php?t=1437137&highlight=nv7915u](http://ubuntuforums.org/showthread.php?t=1437137&highlight=nv7915u)) and wiped Windows 7 to begin tweeking my Ubuntu to match my previous machine, but there are a few issues I wasn't experiencing before: 

[1.] there's no sound ([http://ubuntuforums.org/showthread.php?t=1427902&highlight=nv7915u](http://ubuntuforums.org/showthread.php?t=1427902&highlight=nv7915u)) and I haven't even figured out where to begin with this. If you have any ideas they would definitely help as the main reasons I own a computer are for Music & Banking... 

[2.] the native screen resolution is 1600x900 and I am unable to achieve this. The highest I can get through the system>preferences>display menu is 1024x768.  I have been trying the Xrandr command in terminal but I can't exactly figure it out (a step-by-step would be extremely helpful here), here are the current settings and I would like to achieve 1600x900...

will@Wills-GateWay:~$ xrandr
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
will@Wills-GateWay:~$ 

I hope someone has already figured this out, I'm sure the Ubuntu Folk we'll know of something to do...

---

### Post by whiskey.will on 2010-04-04
Thanks to MCWHO, my [2.] problem has been resolved with much ease.  For future user's that encounter this same issue follow [these simple directions]("http://www.linwik.com/wiki/using+the+intel+arrandale+intel+graphics+media+accelerator+hd+with+ubuntu+9.10"), I would say read over them once just for your benefit before proceeding and you'll be as good as gold...

---

### Post by 2much2soon on 2010-04-09
so is upgrading the kernel working well for you?
 
I have the same machine as you but am having display issues, as in no display on the Ubuntu partitions of a dual boot with Win7 setup.
 
Everything worked fine after the initial install, but then I started monkeying around with the mode/modeline settings in my xorg.conf file to get the 1600x900 display. 
 
Now, I get a blank screen after selecting either of the Ubuntu options from the Grub boot menu.
 
I can't even get to a terminal/command prompt anywhere except for the Grub shell, which doesn't offer enough capability to over write the modified (and apparently now faulty) xorg.conf file with the backup I made before starting...

---

### Post by whiskey.will on 2010-04-13
> **2much2soon said:**
> so is upgrading the kernel working well for you?
 
I have the same machine as you but am having display issues, as in no display on the Ubuntu partitions of a dual boot with Win7 setup.
 
Everything worked fine after the initial install, but then I started monkeying around with the mode/modeline settings in my xorg.conf file to get the 1600x900 display. 
 
Now, I get a blank screen after selecting either of the Ubuntu options from the Grub boot menu.
 
I can't even get to a terminal/command prompt anywhere except for the Grub shell, which doesn't offer enough capability to over write the modified (and apparently now faulty) xorg.conf file with the backup I made before starting...

The new kernel is working perfectly with the RESOLUTION not the AUDIO though, if you have any updates on that please post them...   All I did was follow the directions I posted and it worked fine, I didn't do any tweeking though...

---

