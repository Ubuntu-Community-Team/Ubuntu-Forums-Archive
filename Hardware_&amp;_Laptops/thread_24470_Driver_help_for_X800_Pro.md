---
title: "Driver help for X800 Pro?"
date: 2005-04-07
forum: Hardware &amp; Laptops
---

### Post by Archangel_X19 on 2005-04-07
Hey guys I wasn't sure how soon I'd find out but I wanted to see if someone could give me driver help with an ATI X800 pro.  I read the walkthrough on the ATI but I got so many errors and only got 700 FPS.  By the way MESA was still in control.  I tried it step by step and eventually it just failed my gui all together.  It wouldn't even copy the xorg.conf file over the new one.  Anyway, I was just hoping that someone with similar hardware could give me the best method of 3D acceleration with my card.  My specs are:

Dell XPS Gen 2, 3.0 ghz w/ Hyperthreading(enabled), 1024 MB PC3200 RAM, ATI X800 Pro, 2 maxtor 80 gb hard drives (IDE), Ubuntu Hoary, and cedega (really want to use it for CS: Source)

Any feedback would be awesome.  Thanks guys.  \\:D/

---

### Post by Archangel_X19 on 2005-04-08
I'm guessing no one has an x800 video card?

---

### Post by mikedfrwal on 2005-06-30
[QUOTE=Archangel_X19]I'm guessing no one has an x800 video card?[/QUOTE]
 i have the same problem with this card and nothing has been able to help

---

### Post by Curlydave on 2005-06-30
I have an x800pro. Just download the installer package for the newest drivers on the ATI website, run it, then change the driver in the device section of xorg.conf from "ati" to "fglrx". 

Keep in mind, you might have an x800 in Windows, but you might as well have a 9600 in Linux. :(

---

### Post by mikedfrwal on 2005-07-24
i found a solution

now when i downloaded the installer package i had to compile the module. it should be in 
/lib/modules/fglrx if you are using the latest drivers from the ati site. 


first you install the drivers using the installer from ati's site. then you in a terminal change to the module,s build_mod directory (Probably /lib/modules/fglrx/build_mod) 

then configure it (./configure) and change to the directory right above it and run the make install script 
```

sudo make_install.sh
```

then edit your xorg.conf file to use fglrx instead of ati. restart your system and it should work perfectly

and i would also like to point put that i never could get cs:source to work properly in cedega i would get crappy fonts and missing textures however this does not mean that you shuold not try if you have any questions or have any more luck feel free to come to [http://www.linux-reactor.com](http://www.linux-reactor.com) ask questions there or email me at [EMAIL=mikedfrwal@sourcerers.org]mikedfrwal@sourcerers.org[/EMAIL] 

good luck and happy gaming.

---

