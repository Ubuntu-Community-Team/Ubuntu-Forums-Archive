---
title: "Fan always running at full speed, cpu governor - ondemand"
date: 2010-01-06
forum: Hardware
---

### Post by txacoli on 2010-01-06
Hello everybody, I have been searching the answer to my problem for a couple of days, and found no solution, so I decided to ask you guys for help.

I have hp compaq laptop, amd turion, 2 gig ram, 2.0 gHz, ati radeon x1200 and running Xubuntu 9.10.

I have the same problem in Ubuntu Jaunty and Karmic, my fan keeps running at full speed, despite having the cpu scaling governor set to ondemand. My cpu frequency is always at 800 MHz (the minimum). In windoze my fan runs at minimum speed, and also in Dreamlinux 3.5 based on Debian Lenny. I have no idea what to do, the fan is driving me mad. My cpu temp is always between 63 and 75 degrees C, which seems a lot for an idle computer. I thought my problem might be in the ati driver, could that be possible? Dreamlinux uses proprietary drivers and runs really cool & quiet, literally.

If you need any more specs, just ask. Thanks for all the suggestions, cheers!

---

### Post by mansonthomas on 2010-01-07
Hi,

 same issue on a sony VGN-SZ71E/B (core2duo T7250) where CPU FAN is running at full speed, cpu scaling governor is ondemand, cpu current speed : 800Mhz, sometime I see it going to full speed.

additionnal specs : [http://support.vaio.sony.eu/computing/vaio/specifications/index.aspx?l=en_US&m=VGN-SZ71E_B](http://support.vaio.sony.eu/computing/vaio/specifications/index.aspx?l=en_US&m=VGN-SZ71E_B)

Thomas

---

### Post by mansonthomas on 2010-01-07
Well, after some long time (much longer than vista), it slow down, but not still not as slow as in windows vista.

---

### Post by txacoli on 2010-01-09
Well I did some research regarding my radeon card and it turns out that it's not that well supported in karmic. I had to downgrade to intrepid, but I chose debian lenny instead. The video card is responsible for fan control, so until radeonhd 1.3 is out in a stable release, I have to stick to a 2.6.28 kernel. Maybe you should check your drivers, I can't think of anything else. Everything is running really good now I installed fglrx. Hope you can solve it, cheers!

---

### Post by derekmbarnes on 2010-01-09
> **txacoli said:**
> Well I did some research regarding my radeon card and it turns out that it's not that well supported in karmic. I had to downgrade to intrepid, but I chose debian lenny instead. The video card is responsible for fan control, so until radeonhd 1.3 is out in a stable release, I have to stick to a 2.6.28 kernel. Maybe you should check your drivers, I can't think of anything else. Everything is running really good now I installed fglrx. Hope you can solve it, cheers!

Hold up - what does Linux' graphic card support have to do with a CPU fan problem?  I have an ATI Radeon in my machine and the fan doesn't even turn on until the temperature hits 95 C. Could you help the rest of us out and provide a link to what you found?

---

### Post by Marvin666 on 2010-01-10
In most laptops, the graphics card and cpu share a fan.

---

### Post by mansonthomas on 2010-01-11
Hi,


  It makes sense, on windows 7 on the same machine I had the same issues, I update the nvidia drivers (not trivial btw : [http://blog.mansonthomas.com/2010/01/get-up-to-date-nvidia-graphical-drivers.html](http://blog.mansonthomas.com/2010/01/get-up-to-date-nvidia-graphical-drivers.html) ) and the fan run more slowly.

  I've also updated my nvidia drivers on ubuntu, and it seems to be better now.

Thomas.

---

### Post by GonzalitoUY on 2010-04-04
Thanks, thanks, thanks, I've tried everything for my Turion X2/Radeon x1270 laptop, and after reading this thread and installing radeonhd 1.3, now the fan acts as it should on Karmic.
Now let´s hope that all keeps the same (or better) on Lucyd when it comes out

---

### Post by Naaktgeboren on 2010-05-12
mansonthomas, you can fully control the fan on your Sony Vaio laptop with [vaiofand]("http://vaio-utils.org/fan/"), see [http://vaio-utils.org/fan/]("http://vaio-utils.org/fan/").

---

