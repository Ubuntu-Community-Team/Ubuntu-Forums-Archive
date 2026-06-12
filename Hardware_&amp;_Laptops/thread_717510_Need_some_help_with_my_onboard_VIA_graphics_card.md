---
title: "Need some help with my onboard VIA graphics card"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by HomeImprovement on 2008-03-07
hi all!

i'm quite new to linux, ubuntu and the mainboard i'm using in the box where i'm trying to get it working.

the mainboard is a VIA EPIA-CN13000G, C7/1300Mhz Mini-ITX with onboard graphics (amongst other onboard stuff).

by default it seems ubuntu (gutsy gibbon 7.10) installs a vesa generic graphics driver, which means i am unable to use advanced graphics stuff, and just get the most basic (no 3d or desktop effects for instance).

the problem isn't so much as to install the driver, but to get the system to acutually use the driver. first of all i'm not even sure how to change the driver. as far as i have noticed there's nothing different in the driver list in "screens and grapchics" after installing the openchrome driver for openchrome.org and also the open unichrome driver from viaarena. there doesn't seem to be any new options for me to use after installation.

and either way - my system won't let me change the driver. by default it uses the vesa generic graphics card driver, i change it i.e. to the s3 driver from the list, press ok and cross my fingers.

after a second of black/blank screen the dialog disappears and the system returns to its former state. when i go back to "screens and graphics" it tells med it's using the vesa generic driver.

i have thought of manually editing xorg.conf but i am not sure what information to add, like the name of the driver etc.

i have honestly over several days tried and tried every possible solution i have thought of after searching the net. i'm feeling the solution is close, i just can't find it.

i'm really stuck, and need the help from this community. the sad thing is that the graphic problems i'm experiencing is the only thing that is holding me back from running a full fledged linux media centre in my living room (no ms or windiows).

any thoughts? anyone

thanks so much in advance 

HomeImprovement

---

### Post by overdrank on 2008-03-07
> **HomeImprovement said:**
> hi all!

i'm quite new to linux, ubuntu and the mainboard i'm using in the box where i'm trying to get it working.

the mainboard is a VIA EPIA-CN13000G, C7/1300Mhz Mini-ITX with onboard graphics (amongst other onboard stuff).

by default it seems ubuntu (gutsy gibbon 7.10) installs a vesa generic graphics driver, which means i am unable to use advanced graphics stuff, and just get the most basic (no 3d or desktop effects for instance).

the problem isn't so much as to install the driver, but to get the system to acutually use the driver. first of all i'm not even sure how to change the driver. as far as i have noticed there's nothing different in the driver list in "screens and grapchics" after installing the openchrome driver for openchrome.org and also the open unichrome driver from viaarena. there doesn't seem to be any new options for me to use after installation.

and either way - my system won't let me change the driver. by default it uses the vesa generic graphics card driver, i change it i.e. to the s3 driver from the list, press ok and cross my fingers.

after a second of black/blank screen the dialog disappears and the system returns to its former state. when i go back to "screens and graphics" it tells med it's using the vesa generic driver.

i have thought of manually editing xorg.conf but i am not sure what information to add, like the name of the driver etc.

i have honestly over several days tried and tried every possible solution i have thought of after searching the net. i'm feeling the solution is close, i just can't find it.

i'm really stuck, and need the help from this community. the sad thing is that the graphic problems i'm experiencing is the only thing that is holding me back from running a full fledged linux media centre in my living room (no ms or windiows).

any thoughts? anyone

thanks so much in advance 

HomeImprovement

Hi and please do not make multiple threads on the same issue
[http://ubuntuforums.org/showthread.php?t=716710](http://ubuntuforums.org/showthread.php?t=716710)
Have you looked here
[https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)

---

