---
title: "Acer Aspire 1420P touchscreen not working"
date: 2010-06-10
forum: Hardware
---

### Post by mqo on 2010-06-10
Hi, im new to linux, and ubuntu. Ive got acer aspire 1420p convertible laptop. After installation everything works fine, only problem seems to be that touch screen doesnt work at all. When i touch the screen mouse will click applications in upper left corner. 
Ive read many many many guides how to configure touchscreen, but nothing seems to be working. Touch screen is resistive multitouch MosArt (according to [http://lii-enac.fr/en/projects/shareit/multitouch-devices.html](http://lii-enac.fr/en/projects/shareit/multitouch-devices.html) it's the same one as on ASUS T91M)
I would appreciate any help how to fix this issue, but think of me as a newbie in linux world>) thanks

---

### Post by mqo on 2010-06-11
so there's no solution to make touchscreen working? or should i wait for 10.10 ? or just stick with win7 >.<

---

### Post by bobdawsonvenice on 2010-06-11
I too had this problem, but a wonderful post (with video) allowed me to fix the problem myself.  Here is the link:

[http://www.threadabort.com/archive/2009/11/21/acer-aspire-1420p-touch-screen-problem-dead-zones-pdc.aspx](http://www.threadabort.com/archive/2009/11/21/acer-aspire-1420p-touch-screen-problem-dead-zones-pdc.aspx)

Good luck!

---

### Post by mqo on 2010-06-12
but i have no hardware problem with touchscreen, it's working great under windows 7, ive got problems installing some drivers into ubuntu to make it work. but anyway thanks

---

### Post by arobase40 on 2010-09-02
I think this touchscreen is not supported as multi-touch, but as a single-touch panel...

You may need to download xf86-input-evdev 2.4 or above version of the driver, compile and install it.

But prior to this you need to download the dependencies :

sudo apt-get install build-essential
sudo apt-get install autoconf
sudo apt-get install libtool
sudo apt-get install x11proto-core-dev
sudo apt-get install x11proto-xext-dev
sudo apt-get install libxi-dev
sudo apt-get install xserver-xorg-dev
sudo apt-get install xutils-dev


./autogen.sh --prefix=/usr

sudo make install

Reboot and it just work.. Hopefully... ;)

---

### Post by noek on 2010-10-18
Hi! Same problem for me (klick on the Acer Aspire 1420p screen brings the mouse pointer to the upper left corner and does the click there). 

However, I followed the same discussion in some other forum, and it seems that a patch about that just made it into the currently developed Linux Kernel **2.6.36-rc7**
([http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=e1f092102f65e424be40c318a0fab7bb6e34194f](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=e1f092102f65e424be40c318a0fab7bb6e34194f)) 

So as soon as 2.6.36 comes out, which should not take too long any more, I guess, the screen should run with some package li[FONT=Verdana]ke x-ser[/FONT]ver-xorg-input-evtouch or similar. I'll try it then. 

However, my question is now (not really very experienced!): At what time will I get the new Kernel for my system (running 10.10 Maverick Meercat)? Will it a) come with the regular update, or only, if I b) upgrade to a later (yet to come) version of Ubuntu?

Thanks,
Noek

---

### Post by noek on 2010-11-06
Now it works, using Kernel 2.6.36. As I understood from this thread
[http://ubuntuforums.org/showthread.php?t=1604192&highlight=kernel](http://ubuntuforums.org/showthread.php?t=1604192&highlight=kernel)
the Kernel in 10.10 will most likely never be changed to 2.6.36. Therefore, I installed the new kernel manually - I used the deb-Package, see this thread:
[http://ubuntuforums.org/showthread.php?t=1603401&highlight=kernel](http://ubuntuforums.org/showthread.php?t=1603401&highlight=kernel)
Works fine (including the touchscreen), but as I understand it, this kernel will not be automatically updated, since it does not originally belong to the 10.10 system. Well, I can live with that ;-)

---

