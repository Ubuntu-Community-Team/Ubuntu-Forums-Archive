---
title: "How to Improve Responsiveness / Latency"
date: 2008-09-05
forum: General Help
---

### Post by sml on 2008-09-05
I am running Ubuntu 8.04 and would like to reduce the latency as much as possible with general usage .... such as opening applications, switching between windows, opening photos, scrolling the Gnome menus etc.

I moved from a 1.8Ghz processor to a 4.1Ghz processor and this made no difference.

I have DDR2 667 RAM with an Intel P35 motherboard (I have plenty of RAM so I am only using about 10% RAM usage most of the time).

How can I improve the latency?

---

### Post by sml on 2008-09-05
I have been running a new c2r distro (ie 'copy2ram' or 'toram') which are fantastic and operate in an instant (eg Puppy & Slax) but I thought there might be some tricks to improve Ubuntu.

Another idea was the low latency kernel patch which Con worked on until he left and went onto new projects. Unfortunately this was stopped around 2.6.21.

---

### Post by sml on 2008-09-07
Any ideas guys?

---

### Post by kerry_s on 2008-09-07
trim it down to what you can stand, for example turning on low resource mode for metacity, install leafpad to use for simple text editor, ditch the background/wallpaper, etc... i have 1gig ram but i still trim things as if i had less, the less stuff running the faster everything else is. you should try and use suspend to disk to, it put's everything back as it was so it feels fast as if you never shutdown.

---

### Post by sml on 2008-10-07
Are there any other ideas? We can safely say that it is not my hardware. I am now running 8.10 Beta and Fedora 10 Beta. Gnome & KDE & other lightweight WMs. The lighter WMs are better but I am sure that Gnome and KDE can be better.

If Winblows can be more responsive than Gnome & KDE then we have serious problems!

---

### Post by Calmatory on 2008-10-07
What do you mean not being responsive? The Firefox takes two seconds to load? Switching a tab takes 50 ms too long? Want to alt+tab to another window in 0,23 seconds instead of 0,3 seconds?

Honestly, you should be put using Kubuntu on a 416 MHz Celeron machine with 256 MB of RAM and Riva TNT 2 Ultra for two months. Teaches a lesson. :) Oh, and been there and done that. ;)

What I am saying is that there is a limit. Even if you had twice or trice the CPU power, halved memory latency and quadruped memory bandwidth, had an IMC integrated to the CPU(like Athlon64's, X2's and Phenoms have!) there would still be the delay, which is caused by the software due to the way it works.

But if you still want to go faster, Ubuntu might not be the right distro. At least not with KDE/Gnome. Look at ArchLinux or even Gentoo.

And Windows being faster than Ubuntu? Shouldn't be a surprise that Windows XP indeed is faster, more lightweight than even Xubuntu(well, both were clean installations though). Seen this with the 416 MHz machine. :) Vista... Do I really need to comment? :D

---

### Post by sml on 2008-10-07
I was hoping that linux desktops could be improved such that the responsiveness is better than XP.

A distro like Ubuntu with a 4Ghz CPU with plenty of RAM would perform with a similar performance & responsiveness to a toram/copy2ram/c2r distro like Slax, Puppy, and the numerous other c2r live distros.

I think there is lots of room for improvement here - even with Gnome and KDE.

Yep ... used Arch full-time for 3 or 4 years. Fantastic distro. I just found Mr.Pacman too tempting ... a slight tweak to /etc/pacman.conf and before I knew it I was uploading a full system of unstable or testing packages. Always lots of fun when I got a little bored with the system :)

---

### Post by sdennie on 2008-10-07
The big win for responsiveness comes when most of your common applications and files are in cache and so the disk doesn't need to be used.  If a CPU upgrade didn't make things faster it's possible that the disk is the bottleneck (it usually is).  One thing you could try would be to use preload which tries to learn what applications you use most and keep them in the cache so they can be instantly accessed.  To install it:

```

sudo apt-get install preload

```

Then you can check out the config file /etc/preload.conf (it's well documented).  If I'm not mistaken, it takes preload a while to calibrate itself but it should help the system responsiveness once it's configured itself.

Other than that, I actually find compiz to be more responsive than metacity on my machine.  You can install compizconfig-settings-manager and turn off all the eye candy (specifically animations) and just use it as a basic window manager.

---

### Post by sml on 2008-10-08
Thanks vor. Will give it a shot :)

---

### Post by KeyserSoze93 on 2008-10-08
Also, try a lightweight window manager, such as fluxbox...

---

### Post by SeanHodges on 2008-10-08
Both Gnome and KDE4 are more responsive on my system than Windows XP (clean installation with AVG firewall installed and latest service pack). Cold boot to desktop, general opening and operation of applications are all noticeably faster in Ubuntu. KDE appears to be slightly quicker, but I haven't timed them so can't confirm this. I haven't purchased Vista so can't make the comparison there.

So there must be something causing your system to be less responsive. Are you using any poorly supported hardware, like a wireless card with a restricted driver?

---

### Post by mixmaster on 2008-10-08
Be sure to turn off all the desktop bling (wobbly windows, desktop compositing, shadows, 3d cubes etc).

I find Xubuntu to be more responsive than XP on several machines with differing hardware configs.

---

### Post by mikjp on 2008-10-09
Use a desktop distribution, not a server distribution :)

Gnome adds some unnecessary delays to opening menus etc., remove them. See [http://lifehacker.com/software/linux-tip/speed-up-gnome-menu-269934.php](http://lifehacker.com/software/linux-tip/speed-up-gnome-menu-269934.php)

---

### Post by cariboo on 2008-10-09
Instead of comparing your performance between a 7 year OS like windows and an up-to-date distribution like Ubuntu, Compare Vista to Ubuntu, then you get a better comparison.

Jim

---

