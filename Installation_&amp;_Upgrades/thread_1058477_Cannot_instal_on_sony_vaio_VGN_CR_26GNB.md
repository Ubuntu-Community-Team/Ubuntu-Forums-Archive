---
title: "Cannot instal on sony vaio VGN CR 26GN/B"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by drrakrinair on 2009-02-02
Hi, I tried installing Ubuntu on my sony vaio VGN CR 26GN/B.  Once rebooted it gives installation proceeding window, once 100% it gives me a blank screen with a blinking cursor.  I waited for an hour nothing happened. The keyboard does not enter anything.  I had to hard reboot.  Again when trying to start ubuntu it takes a long time, gives me an error loading hardware drivers fail. Takes a long time to create swap.  Asks me to type user name and password then i get only the $ prompt. Please help

---

### Post by Will4 on 2009-02-02
which edition did you install? 8.04 or 8.10?

---

### Post by drrakrinair on 2009-02-02
8.10

---

### Post by drrakrinair on 2009-02-02
> **Will4 said:**
> which edition did you install? 8.04 or 8.10?

I am using ubuntu 8.10

---

### Post by Will4 on 2009-02-02
i guess we both have the same VAIO-problems. 
I know someone a little bit more advanced would tell you a different story but if you don't have Intel video chipset, at the end would be easier to install 8.04. i did and had no problem at all, everyone gave a diferent way to  solve a different coming problem all the time with 8.10
once in 8.04 no problem at all...just try, if you are one of those after the new things, 8.10 would be temptation but if old-fashion keeping things that work, try 8.04

---

### Post by drrakrinair on 2009-02-02
Thank you for the post.  I do not have ubuntu 8.4 I got 8.10 yesterday shipped to me. My video chipset in ATI Radeon.  Does that make any difference?  When i tried it the first time running from the CD it worked fine, no crash.  Once installed it gave me the shock of my life. I am totally lost and clueless on what to type on a $ prompt.

---

### Post by Will4 on 2009-02-02
you should need to install the new xorg (video driver) for ATI i guess. it comes with 8.10 but then after that you get a net problem and until now, 8.04 have not given me any. 
you can download it from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
just try and update it....well...
code:
> sudo -s
gedit /etc/apt/sources.list

once it opens... sellect all (Ctrl+A) and delete and paste this....

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free 

enjoy it!!!

---

### Post by drrakrinair on 2009-02-02
> **Will4 said:**
> you should need to install the new xorg (video driver) for ATI i guess. it comes with 8.10 but then after that you get a net problem and until now, 8.04 have not given me any. 
you can download it from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
just try and update it....well...
code:


once it opens... sellect all (Ctrl+A) and delete and paste this....

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free 

enjoy it!!!

Sorry for being a pain, I cannot login to Ubuntu, so is it good if i download on to windows and then try to install from windows or do I have to get into Ubuntu someway or the other?

---

### Post by drrakrinair on 2009-02-03
Any body home??

---

