---
title: "MA521 on Ubuntu 4.10 Help"
date: 2005-01-06
forum: Hardware &amp; Laptops
---

### Post by Enzo386 on 2005-01-06
Hey, i posted this in another thread also but nobody has replied, and i figured this would be the place to post it as it is laptop based. 

I purchased a driverloader license, and have been using Libranet linux for the past 3 months perfectly with my wireless card and driverloader to load my windows drivers. Now i want to switch to ubuntu, but when i try to install driverloader on ubuntu, it says i need the kernel source installed. I know i could get that through apt, but i don't have internet in order to get it. Please help! Is there a way i could download it on the PC i'm on now and burn it to a CD and install it using apt from the CD or something like that?

---

### Post by Enzo386 on 2005-01-07
Alright i downloaded the  Linux-Source package for Ubuntu 4.10 and i'm going to un-tar it in /usr/src 

I need to know how to recompile the kernel from there. On Libranet i had to recompile to get driverloader working, so i'm guessing i need to recompile on ubuntu. 
How do i recompile?

---

### Post by Enzo386 on 2005-01-07
Alright, i installed GCC from the CD using apt-get install gcc and i got driverloader working. I used the kernel headers from the repository that i downloaded on this pc, burned it to a CD, and installed it on my laptop. Now i'm on the driverloader web configuration screen, i've uploaded the windows driver it needs, but it says it can't detect my device, but the power light is on on my device and it reads it in the HAL device manager that comes with ubuntu.

Ideas anyone?

---

### Post by mythagel on 2005-02-01
I'm currently using my MA521 on Ubuntu warty (4.10) with ndiswrapper ([http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)) which i've found to be fantastic, excepting the fact that signal strength is not reported, which really isn't an issue at all.

apt-get install ndiswrapper

then follow the instructions starting from "2. Install your Windows driver" at [http://ndiswrapper.sourceforge.net/phpwiki/index.php/Installation](http://ndiswrapper.sourceforge.net/phpwiki/index.php/Installation)

Another option i believe is wlan-ng, which i have not tried personally yet, but which is supposed to support the Prisim chips in this card.

-Nick

---

### Post by benkorkor on 2005-02-02
Thank you for the instructions on getting my ma521 to work. Again, thanks.

---

