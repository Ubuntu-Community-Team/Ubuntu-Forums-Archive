---
title: "How to: Hardy freeze-ups with nVidia cards"
date: 2008-08-16
forum: General Help
---

### Post by zieglerj on 2008-08-16
I'm running a AMD 64 bit Athlon 2Ghtz, 4 gb ddr2 ram, with wireless data card modem and a nVidia e-Geforce 6200 dual display.
Before this my system was completely freezing two - three times a day even if I only had a couple of windows open.
I followed this how to: [http://ubuntuforums.org/showthread.php?t=797270](http://ubuntuforums.org/showthread.php?t=797270)
substituting :
sudo init 3
sudo sh NVIDIA*

where it says to type:

sudo sh NVID[tab]

and haven't had a single freeze up all day while running multiple windows on four different desktops with extra compiz effects and widgets. Not only have I not had a freeze-up, my system has been running smoother than it has since I installed my video card.

I figure I'd post this since there seem to be a lot of problems reported with nvidia related freezes in hardy. 

If you're out there Xiong Chiamiov, Thanks! I owe you big time.

---

### Post by zieglerj on 2008-08-17
I spoke too soon. While the driver I downloaded from Nvidia does work great, Hardy froze up just after I finished writing the above post. 
Now I am in the process of trying using the rt kernel as was sugested by another poster.

---

### Post by zieglerj on 2008-08-18
24 hours, no freezes.

---

### Post by zieglerj on 2008-08-19
Ok, I've made it weeks now with heavy usage and no freezes. I'm going to consider this a pretty effective way of getting around hardy's lock-ups if you have a nvidia card. 

Download the latest nvidia driver from here: 
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

then move it into your home folder. 
Now type in terminal:

sudo aptitude install linux-image-rt linux-restricted-modules-rt
sudo apt-get remove --purge nvidia*
sudo apt-get install linux-headers-$(uname -r) libc-dev build-essential

Now copy down the next commands because we are about to drop to the command prompt interface then type:

sudo /etc/init.d/gdm stop

hold alt+F1
enter in your username and password then type:

sudo init 3
sudo sh NVIDIA*

this should open the installer program for the nvidia drivers. Follow the instructions it gives you and at the end let it reconfigure your xorg.conf. 
Once completed type:

sudo /etc/init.d/gdm start

If you are using a dual display card and are used to having your "nvidia X server settings" program under system>administration> I should tell you that it's not gone but setting up the drivers this way moves it to applications>system tools>
I hope this works for many of you, I know it has vastly improved the performance of my machine. Even if you're not having freezes I would recomend these drivers.

---

### Post by oxman on 2008-08-28
Still smooth sailing after a week?

---

### Post by davenxt on 2008-08-28
You have done a good question, it’s really interesting. If you get any good reply, so please let me know. So I’ll also get some good idea. 
Thanks for your future help.

---

### Post by zieglerj on 2008-08-28
yes, smooth sailing. I'm back to being a very satisfied Ubuntu-er

---

### Post by oxman on 2008-08-28
Thanks for the reply. I have heard that the new kernel fixed the problem for some.

---

