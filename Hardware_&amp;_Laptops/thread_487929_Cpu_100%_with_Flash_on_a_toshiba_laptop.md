---
title: "Cpu 100% with Flash on a toshiba laptop"
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by Kishandr on 2007-06-29
Hi there,
I have noticed a problem my cpu runs at 100% when i am watching flash let me be specific its WATCHING A FLASH VIDEO and not Running a flash video......The difference in if i minize the browser the cpu returns to normal even if the flash video  is running ......
Now the specifications:
Ubuntu Fesity
Cpu:Mobile intel pentium 4 --2.4 ghz
memory-487.3mb
Now the flash package is Flash-nonfree   9,0,31,0 installed in synpatic manager....
Its a toshiba laptop a40 series 
No desktop-effects on ...even with the desktop effects its the same out put....

The browser same effects with firefox and epiphany both latest editions....

No cpu surge when watching a movie file in totem or any other player(mplayer and Xine)....

Please help me to resolve this problem
Any other specifications u need please let me know .....

---

### Post by Metacarpal on 2007-06-29
Sounds like it could be a video configuration issue.  What video card do you have, and which driver are you using?

---

### Post by Kishandr on 2007-06-29
Intel Corporation

82852/855GM Integrated Graphics Device

Donnot know about the drivers how to find it out

---

### Post by Metacarpal on 2007-06-29
The fast and easy way would be to go to your System menu > Administration > Hardware Information (or possibly System > Preferences > Hardware Information, depending on your version of Ubuntu).

Find the entry on the left column that shows your graphics card.  Click that to highlight it.  Then in the right side, click on the Advanced tab.  There should be an entry that says, "info.linux.driver"

---

### Post by Kishandr on 2007-06-30
Thanks for the answering my queary....the value is agpgart-intel if that helps you to i would be glad and apprecitate your effort please let me know if u need any other information....The thing i noticed is that flash... when paused or when i minize or if i shift the tab in browser the cpu falls to low level as soon as swith to the flash witht the video there is surge in cpu .......to 100%..please advice is it a bug or it is just with my system

---

