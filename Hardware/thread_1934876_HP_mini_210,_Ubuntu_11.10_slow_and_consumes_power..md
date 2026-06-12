---
title: "HP mini 210, Ubuntu 11.10 slow and consumes power."
date: 2012-03-03
forum: Hardware
---

### Post by daathi on 2012-03-03
Hi,

I upgraded my 11.04 to 11.10 when it was published, everything seemed fine and I was very happy. Then the laptop got quite sluggish, especially internet browsers. Speedtest.net says (for 10/2 cable modem) 9,7/1.89 so the connection speed is not the issue here. It's more like FF and Chrome takes a while to start and to find any page. Sometimes it's painfully slow to get to any www page, especially those with lots of images and stuff. Ubuntu itself seems to run most of the time at adequate speeds, menus open almost normally and so on, although boot time has grown a lot, however the overall experience is slower that 11.04. Then I thought that a SSD might help a bit as my friend upgraded his Mini and said many good things. On the contrary, the problem did get a tad worse and now the battery runs empty in use and stand-by mode much faster. I tried the workaround for [power issues]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html") and some pwm software too (Jupiter), didn't notice significant improvements. Switching to 2D or lowering swappiness does not help either. Does anyone have _any_ ideas?


Edit: some typos and stuff, I was forced to go to grocery store in the middle of writing this... :(

---

### Post by designdolphin on 2012-03-03
I have a HP Mini 110-3700 with a 6 cell battery. From what I read the 210 has a more powerful processor, which may use more power. This is what I have done to improve performance and battery life, YMMV and use at your own risk:

[LIST]
[*]Installed the 64 bit version of Ubuntu 11.10 instead of the 32 bit.
[*]Uninstalled Unity, Compiz, and Zeitgeist (Compiz and Zeitgeist run as a process as thus using power), and installed gnome-shell
[*]Installed laptop-mode-tools (Read the documentation. Have a look at the different modules and configurations. )
[*]In laptop-mode-tools modules set the cpufreq to conservative in battery modus.
[*]Changed the theme to Awaita (there were some reports of the Human theme consuming extra cpu cycles, not sure, but testing this against the current Ubuntu theme, to test if there is any difference.) There may be themes that improve performance more. Still looking for those.
[*]Uninstalled any programs and/ or daemons that run services, that you are not using, or system does not need. (I left cron, acron, and atd).
[*]Turned down the screen as low as can go, while still being able to read normally. 
[*]Uninstalled Flash (or don't watch video in your browser while on battery, unless you want a considerable shorter battery time duration is my experience.) 
[*]Run an ad or Javascript blocker such as NoScript in Firefox to minimize use of Javascript. 
[*]There are some Firefox memory and disk cache optimizations out there. Doing a search on this can increase the performance. 
[*]Installed PowerTop and take a look at the readouts there. Also visit the lesswats.org website for information.
[*]If you're not using IPv6, and only IPv4 you can elect to turn this off in Ubuntu and Firefox. It can also speed up your browsing, according to some sources, as for example Firefox is trying to lookup IPv6 connection as well. 
[/LIST]

There is also a lot of articles on powersaving for linux on the net.  Definitely worth a read.  Doing a search on things such as 'improving battery life linux' will get you results.

Currently I get about 8+ hours of battery life, depending upon usage. (With 12.04 this should be even better, as Ubuntu and the kernel have improved power savings.) :)

You can hold of using laptop-mode-tools and wait for 12.04 if you want to stick to the basic way. 12.04 contains some powersaving things as well. 

Hope it helps.

---

### Post by LinuxFan999 on 2012-03-03
> **daathi said:**
> Hi,
 
I upgraded my 11.04 to 11.10 when it was published, everything seemed fine and I was very happy. Then the laptop got quite sluggish, especially internet browsers. Speedtest.net says (for 10/2 cable modem) 9,7/1.89 so the connection speed is not the issue here. It's more like FF and Chrome takes a while to start and to find any page. Sometimes it's painfully slow to get to any www page, especially those with lots of images and stuff. Ubuntu itself seems to run most of the time at adequate speeds, menus open almost normally and so on, although boot time has grown a lot, however the overall experience is slower that 11.04. Then I thought that a SSD might help a bit as my friend upgraded his Mini and said many good things. On the contrary, the problem did get a tad worse and now the battery runs empty in use and stand-by mode much faster. I tried the workaround for [power issues]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html") and some pwm software too (Jupiter), didn't notice significant improvements. Switching to 2D or lowering swappiness does not help either. Does anyone have _any_ ideas?
 
 
Edit: some typos and stuff, I was forced to go to grocery store in the middle of writing this... :(
How much RAM does your netbook have?
I would recommend having at least 2 Gigabytes of RAM when running Ubuntu 11.10. If you have only 1 Gigabyte, you should either upgrade to 2 Gigabytes of RAM, or try Xubuntu or Lubuntu instead.

---

### Post by designdolphin on 2012-03-06
How much slower does it run? There is a difference between performance between Gnome 2 and Unity on some netbooks, is my experience. Even then though a clean Ubuntu 11.10 install shouldn't run all too slow on a netbook with these specifications. 11.10 comes in around 400mb use on a clean install on my netbook, which has 1 gig (and although I find that amount of memory use a tad much, compared to say Xubuntu or other linux distros) it still moves along zippely, and runs most apps fine (o.k. you shouldn't try to run anything like, extreme renderings, on Blender, but that is a given). 

Maybe something went wrong with the upgrade process? It might be that you need do to a clean install. In my experience upgrade can be a tricky process. Or maybe it is Unity that is given the performance lag? As it comes in quite hefty, with Compiz for example. Do you notice a difference in performance between Unity and Unity 2d? 

Are there any errors in your logs, that could be the cause of this? 

Hopefully other people can help you as well.

---

### Post by daathi on 2012-03-07
Hi guys! Thank you all for replying :)


I've got 2 gigs memory, actually now that you said, this situation resembles the time before adding more memory. I'm running 32 bit Ubuntu, as 64 bit OS is not supported by CPU...AFAIK. I tried Gnome Shell and actually liked it better, but it kept crashing every day and wasn't considerably faster, so...back to Unity. Difference between 2D and 3D Unity is not big, but there is some. IPV6 has been disabled and I tried Jupiter for saving battery, but all it did was slow down more (it lowers CPU clock speed when not on AC). I'll try laptop mode tools.


It's possible that something went wrong with upgrade. Maybe I'll try reinstall also. Although this has happened in two separate installs on two separate disks. As for the log files, I don't really understand them, but I did see one thing mentioned in few places: *ERROR* invalid framebuffer id. This actually could have something to do with this, more graphics, more lag. Usually in form of web sites, but some how I think GPU could have something to do with this.

Well isn't this odd....by the time I finished writing this I noticed that something has changed...The laptop is actually faster!!  I just went and tried few heavy-ish websites at the same time and they worked far better than in ages. Not good good, but still. Hmm...I did receive few updates very recently and booted today. Well, I have to see if this lasts :lolflag: 
Thank you guys for helping! If you know what that framebuffer error is, please do tell.


Edit: Heh, I reboot the Mini again and boot-up is now lightning fast! Only thing that got worse, is that my Grub is now missing :D Just a purple screen instead of Grub menu...

---

