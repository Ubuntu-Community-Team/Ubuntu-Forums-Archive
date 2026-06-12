---
title: "Optimizing boot time on my laptop"
date: 2008-11-15
forum: General Help
---

### Post by lotharz0r on 2008-11-15
Hi.
I have recently made the switch to ubuntu from Gentoo.
I have been using Gentoo for about 5 years, and I love it, but I decided to try Ubuntu because it's easy to use and because I wont have to compile apps if I want to install something.

I installed Kubuntu, but I am not that found of KDE, so I installed XFCE which I like very much. I like it fast and simple, i used fluxbox on my gentoo installation.

Overall Ubuntu seems like a good OS, good HW support and very easy to use, but maybe a little complicated to optimize and customize.

The performance of the fully booted system is good enough.
I only use the terminal, firefox and sometimes Thunar and rdesktop, but what annoys me is the slow boot.

**Questions:**
[LIST]
[*]What can I do to reduce the system boot time? Is there any apps I can use to disable stuff I dont need, or some configuration I can do to make it faster? I have disabled stuff like bluetooth and kdm, but it was not of much help.

[*]In gentoo I used to make my own kernels, but it was way to much work to get it to work imho. Is there any tools I can use to make my own kernel with only support for the drivers I need to make it faster?
[/LIST]

---

### Post by Peter09 on 2008-11-15
If you disable the splash option (nosplash) in the grub menu at startup. (hit esc at the grub prompt, select the 2nd line and type E to edit it) You can see the boot sequence, it may give you an idea as to where it is slow.

---

### Post by swoody on 2008-11-15
I've always been interested in optimizing my laptop as well. Either bootup time, battery life (now 8hrs), or just making things work smoother. I've accumulated quite a few bookmarks along the way, so I'm hoping these will help you out on your quest :)

[http://resources.zdnet.co.uk/articles/features/0,1000002000,39454355,00.htm](http://resources.zdnet.co.uk/articles/features/0,1000002000,39454355,00.htm)
[http://its-about-amoena.blogspot.com/2007/12/how-to-make-ubuntu-to-start-faster.html](http://its-about-amoena.blogspot.com/2007/12/how-to-make-ubuntu-to-start-faster.html)
[http://www.openfirmware.info/Welcome_to_OpenBIOS](http://www.openfirmware.info/Welcome_to_OpenBIOS)
[http://sayakb.blogspot.com/search/label/MakeFast](http://sayakb.blogspot.com/search/label/MakeFast)

I have a ton of different ones as well, so let me know if you'd like more info about extending your battery life or just making Ubuntu snappier! :D

---

### Post by lotharz0r on 2008-11-16
Thanks for the links. I'll look through them and see if there's anything that helps speeding up the system.


If I boot without splash and remove the quiet option I see that the system boot stops for several seconds after loading the USB mass storage driver.
If I only remove quiet, and still have splash it stops for several seconds with the message "Waiting for root filesystem".
Quite annoying.

---

### Post by _sAm_ on 2008-11-16
Do you have dual core?

---

### Post by lotharz0r on 2008-11-18
No, its got an 1,6GHz Celeron with 1,5 GB RAM.
I have tried disabling several of the services I dont use, disabling splash and I have set vm_swappiness=10

I have also edited /etc/init.d/rc and changed:
CONCURRENCY=none 
to
CONCURRENCY=shell


For some weird reason this resulted in almost 30 seconds slower boot.
Previously my system booted in 57 seconds, now it boots in 1:20.

My system is fully updated with the newest packages.

It still stops and does nothing while the message "waiting for root filesystem" appairs.

I tried changing from UUID to /dev/sdx in /etc/fstab and grubs menu.lst, but it made no difference.

---

### Post by oldos2er on 2008-11-18
CONCURRENCY=shell only works on dual (or more) core CPUs.

---

### Post by lotharz0r on 2008-11-18
Ok. I did change it back since it only increased my boot time.
Any idea why the boot stops for several seconds after loading the USB mass storage driver?

As mentioned it says "Waiting for root file system" when I've got splash on and quiet off.

---

### Post by ScottHW on 2008-11-18
> **lotharz0r said:**
> 
... I have disabled stuff like bluetooth and kdm, but it was not of much help.

I am also interested in both saving battery life, and increasing boot time.  Could you describe in a little more detail how you "disabled" that stuff?

I've seen this older thread with commands to stop Bluetooth once it's running, but that certainly doesn't do any good for boot times...
**Turn off bluetooth radio**
[http://ubuntuforums.org/showthread.php?t=120403](http://ubuntuforums.org/showthread.php?t=120403)

---

### Post by ScottHW on 2008-11-18
Oh, and last week I saw a link to this fascinating site:
**LPC: Booting Linux in five seconds**
[http://lwn.net/Articles/299483/](http://lwn.net/Articles/299483/)

The quote is brilliant,
"It's not about booting faster, it's about booting in 5 seconds"
 - Arjan van de Ven, Linux developer at Intel and author of PowerTOP

---

### Post by oldos2er on 2008-11-18
You can disable Bluetooth at System, Administration, Services.

---

### Post by ScottHW on 2008-11-18
> **oldos2er said:**
> You can disable Bluetooth at System, Administration, Services.

Alright, very helpful, thank you!

Now, how 'bout this; I normally don't want to use Bluetooth, so it's disabled. But, what if I do happen to want to use it?

Can I enable it and bring all the Services online without rebooting?

---

### Post by Marius Derekus on 2008-11-18
> **woody86 said:**
> I've always been interested in optimizing my laptop as well. Either bootup time, battery life (now 8hrs), or just making things work smoother. I've accumulated quite a few bookmarks along the way, so I'm hoping these will help you out on your quest :)

[http://resources.zdnet.co.uk/articles/features/0,1000002000,39454355,00.htm](http://resources.zdnet.co.uk/articles/features/0,1000002000,39454355,00.htm)
[http://its-about-amoena.blogspot.com/2007/12/how-to-make-ubuntu-to-start-faster.html](http://its-about-amoena.blogspot.com/2007/12/how-to-make-ubuntu-to-start-faster.html)
[http://www.openfirmware.info/Welcome_to_OpenBIOS](http://www.openfirmware.info/Welcome_to_OpenBIOS)
[http://sayakb.blogspot.com/search/label/MakeFast](http://sayakb.blogspot.com/search/label/MakeFast)

I have a ton of different ones as well, so let me know if you'd like more info about extending your battery life or just making Ubuntu snappier! :D

Please give info on extending your battery life! 8hr is amazing (mine is 2-3hr with display all the way down 1hr with display up). Maybe 8hr is a dream never to come true, but if i could at least extend longer then 2hr that would be great. Thanx.

---

### Post by esmurdo on 2008-11-20
> **woody86 said:**
> I've always been interested in optimizing my laptop as well. Either bootup time, battery life (now 8hrs), or just making things work smoother. I've accumulated quite a few bookmarks along the way, so I'm hoping these will help you out on your quest :)

I have a ton of different ones as well, so let me know if you'd like more info about extending your battery life or just making Ubuntu snappier! :D

I second that request!!!!!! 8 hours would be amazing!

---

### Post by swoody on 2008-11-20
By far the largest power-consumer on a laptop is the display. If you have a laptop that has a default brightness that's too bright, you can use gnome-power-manager to change the default so you can always keep your laptop display nice and dim. First, if you don't have it, you must install gnome-power-manager. You can do this through Synaptic, just look for... you guessed it - gnome-power-manager. After you install it you need to right click your menus and select "Edit Menus", look for a program called Configuration Editor and make it visible. Then when you open Configuration Editor, on the left hand side, click on apps>gnome-power-manager>backlight and change all the numerical settings to 0 (for 0% background brightness, you can set this higher if 0 is too dim to be comfortable, but remember, the higher you set the default,  the more power your screen is going to consume. Then if you're having problems with the backlight resetting whenever you open or close your lid go to apps>gnome-power-manager>buttons and change "lid_battery" to "nothing" this will make it so that whenever you're on battery and open/close your lid, that it will not do anything, and will therefore keep your screen brightness just as you left it. Try this out, and if you have any problems with it, just ask me. 

Here's some more info for you all to check out. Some of these things may not apply to all laptops as some will not allow CPU Scaling, Undervolting, etc. but check them out, and do what you can anyways:

CPU Scaling:
[http://www.arsgeek.com/2008/01/16/cpu-scaling-ubuntu-battery-life-and-you-how-to-scale-your-cpu/](http://www.arsgeek.com/2008/01/16/cpu-scaling-ubuntu-battery-life-and-you-how-to-scale-your-cpu/)

Undervolting your CPU:
[http://ubuntuforums.org/showthread.php?t=786402](http://ubuntuforums.org/showthread.php?t=786402)

Disabling Unneeded Services (a little old, but still works great!):
[http://ubuntuforums.org/showthread.php?t=89491&highlight=disabling+services](http://ubuntuforums.org/showthread.php?t=89491&highlight=disabling+services)

Take control of your backlight:
[http://www.berthon.eu/ice_and_fire/?p=84](http://www.berthon.eu/ice_and_fire/?p=84)

Using PowerTOP:
[http://ubuntu-tutorials.com/2008/06/19/extend-your-battery-life-with-powertop/](http://ubuntu-tutorials.com/2008/06/19/extend-your-battery-life-with-powertop/)

Using some programs to extend battery life:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_battery_life&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_battery_life&num=1)

Some other tips:
[http://www.totalnetsolutions.net/2007/08/13/how-to-increase-battery-life-in-ubuntu-or-debian-linux/](http://www.totalnetsolutions.net/2007/08/13/how-to-increase-battery-life-in-ubuntu-or-debian-linux/)

Yet more tips:
[http://sheehantu.wordpress.com/2007/06/21/saving-battery-life-in-ubuntu/](http://sheehantu.wordpress.com/2007/06/21/saving-battery-life-in-ubuntu/)


Also, keep in mind that for a laptop improving performance and attaining a longer battery life are USUALLY closely related. When your hard-disk spins up, your CPU is being overworked, or you're running multiple apps, it not only makes your computer feel slower, but it uses up more battery life. So most things you can find to help make your computer feel zippier will also help reduce your power consumption :)

If you have any questions or comments, please feel free to let me know. Thanks again guys, and hopefully this stuff will help you out at least a little bit :D

---

### Post by Coreo on 2008-11-26
Thanks for that post!!   :popcorn:

This whole "speeding up boot" idea is kinda interesting
Lately, it all seems to revolve around SSD's. Hard drive access times just can't compare, unfortunately.

The only speed that really matters to me is that my Media Centre boots up before my TV finishes warming up.    ;)

---

