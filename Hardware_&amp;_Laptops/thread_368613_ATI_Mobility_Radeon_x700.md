---
title: "ATI Mobility Radeon x700"
date: 2007-02-23
forum: Hardware &amp; Laptops
---

### Post by MueasA on 2007-02-23
Hello everybody,

   I have little problem here (I hope that :) ), I have Toshiba Satellite M70 with ATI Mobility Radeon x700, after booting from the CD, the process went OK, and when it's time to showup the desktop all I get is black screen with the starting sounds, that's all... no messages no errors. But, when trying and boot from the graphics safe mode, the desktop came up and every thing is fine!!!

Any input would be appreciated, I wish to convert to Linux, but it will be impossible without your help.

Thanks

---

### Post by !bilay on 2007-02-27
Have you solved this issue?  I have the same computer and the same problem.  Found some relevant info, I will try tonight to get it working.

[URL="https://wiki.ubuntu.com/EdgyKnownIssues/59618"]
https://wiki.ubuntu.com/EdgyKnownIssues/59618[/URL]
[URL="http://www.ubuntuforums.org/showthread.php?t=354041&highlight=blank+screen"]
http://www.ubuntuforums.org/showthread.php?t=354041&highlight=blank+screen[/URL]
[URL="http://www.ubuntuforums.org/showthread.php?t=353596&highlight=radeon+x700"]
http://www.ubuntuforums.org/showthread.php?t=353596&highlight=radeon+x700[/URL]

---

### Post by herpez on 2007-02-28
its easy. when the screen gets black, do ctrl alt f2, then go root (sudo), go edit /etc/X11/xorg.conf and in the section Device, change driver to vesa.
Then save, do ctrl alt f7 and then do ctrl alt backspace to startx, and it goes fine
To install, i recommend the alternative version ;)

---

### Post by !bilay on 2007-03-01
Yep, it's easy.  This was the best walkthrough for a n00b:

[https://wiki.ubuntu.com/EdgyKnownIssues/59618]("https://wiki.ubuntu.com/EdgyKnownIssues/59618")

---

### Post by MueasA on 2007-03-02
I will try that tonight, I was trying to solve this problem for the past few days.

The links are promising, should be easy....

Thanks guys for the replys, I really want to switch to Linux

---

### Post by !bilay on 2007-03-02
Also, I finally got Beryl working on the x700 after multiple tries.  This guide was perfect:

[http://ubuntuforums.org/showthread.php?t=291464&highlight=beryl+ATI+x700]("http://ubuntuforums.org/showthread.php?t=291464&highlight=beryl+ATI+x700")

---

### Post by MueasA on 2007-03-03
The steps are great and easy. I managed to get the GUI. but another problem came up!!!

When I click on the install icon, and getting into the normal steps to complete the installation, It stops (or taking very long time) to resize the HDD, I don't know if this a normal thing,  

what if I used Partition magic and resized the HDD, then install ubuntu? (I tried that but I got lost and couldn't complete the installation). 

Any input please.... Thanks

---

### Post by MueasA on 2007-03-03
I couldn't Install it!!!    I can only boot from live CD, once it's partitioning time and choosed the 1st option to resize my only partition,  and hit forward,  wait for 1 minute .....  5 minutes ...... 15 minutes !!!!!!!!! the Back button colored again and selective, and nothing happened,  hit forward again, tek tok tek tok tek :-k !!!!! again 15 minutes or so...  nothing happened  ](*,) 

Please help

---

### Post by MueasA on 2007-03-04
Now what? This is really frustrating...  I installed ubuntu 6.1 following the links above and this one [COLOR="Sienna"][https://wiki.ubuntu.com/EdgyKnownIssues/59618]("https://wiki.ubuntu.com/EdgyKnownIssues/59618")[/COLOR] to do the partitioning.

Everything went fine until the next reboot, it freeze on splash screen and I had to hard reset the computer. The only way to boot is through recovery mode. 

if check this link [https://wiki.ubuntu.com/EdgyKnownIssues/59618]("https://wiki.ubuntu.com/EdgyKnownIssues/59618") you will find at the end of the page [COLOR="Sienna"]After installation [/COLOR]head-line, and yes I have break=bottom at that line, but when I delete that phrase I can't save the file!!!.

Please help here, this is really frustrating

---

### Post by MueasA on 2007-03-04
Sorry the link for partitioning tutorial is [http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")  I got confused

---

### Post by MueasA on 2007-03-05
Here what I did........

I installed ubuntu 6.06 over 6.1.  

-Inserted ubuntu 6.06 and booted the graphical safe mode.
-Edit partitions manually or whatever, and installed it over 6.1, reformatted booth Ext3 HDD and swap. 

-Its time now to restart the box.
-Booted to login/password screen and everything is fine!!!!

That entire headache to get around the ATI and change it to vesa!!!!!!!!!!

There must be something wrong in the first place, but I can’t figure out.

Anybody has any idea about that????

I'm sure this will help other people onboard.

---

