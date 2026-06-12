---
title: "Installing nvidia drivers causes 'Low Graphics Mode' on startup"
date: 2008-11-13
forum: General Help
---

### Post by rayofash on 2008-11-13
I have a GeForce FX 5200, I'm running Ubuntu 8.04, and I've installed all the patches. In /etc/default/linux-restricted-modules-common I've added "nv nvidia nvidia_new". When I install the nvidia drivers from the Hardware Drivers menu and enable it, after reseting either the X server or Ubuntu it causes it to boot up in Low Graphics Mode and completely rewrite the xorg.conf file. When I use nvidia-settings it says it's not using the nvidia drivers.

After I remove the drivers and restart, I can go back to 1024x768, but (of course) without the Compiz graphical features.

Before this started happening I had everything working, I installed the nvidia drivers from nVidia directly and had Compiz and Emerald running fine and everything was beautiful. At the time I didn't have anything written in the /etc/default/linux-restricted-modules-common file. After restarting this started happening.

I found another thread from back when 8.04 was first released, the guy had the same graphics card as me. The way he fixed it was by doing a fresh install and leaving out 4 of the updates, I don't want to do this though.

---

### Post by SleepingProphet on 2008-11-13
I'm not 100% sure what the problem is, but I fought a lot of battles with my ATI drivers and my HDTV before I finally found a combination of drivers + installation method + xorg.conf that worked properly for me, so I have learned some tricks :)

1-Rather than doing a full reboot, when you make changes to xorg.conf and want to see if the X server is still going to work right, you can hit CTRL+ALT+Backspace to kill and restart the X server. Be warned, when you do this it also kills all programs you have running, including your current desktop environment, causing you to have to log back in. Even so, I found it's much much faster for me than rebooting.

2-When you are presented with that lame "Low Graphics Mode" warning at the beginning of the session after you install the drivers, the options you choose are crucial. The menus are nested, so you can choose the view the log and then go back out. I highly reccomend trying the other options before you resort to booting into Low Graphics Mode. I found that X is fairly picky about how xorg.conf is formatted, so if you hand-edit it (and you might have to), then you may make a simple typo. The error messages will usually give you an idea of why stuff failed. In the same menu you can also "reconfigure X" which lets you go into xorg.conf and change stuff. If you have made a simple typo this stuff will let you save your xorg.conf and get stuff working without tedious reboots

3-if X gives you weird errors and you have no idea what you mean, have it backup the log and then boot into Low Graphics Mode and look at those logs. Why bother if you don't know what they mean? Simple: throw those errors into Google, or post them on here and then you can get a lead on why stuff isn't working.

4-Once you hit a happy point with your Linux install where stuff is working, back up your system. I was sort of astonished to learn you can simply run a terminal command and it'll dump everything from your current system into a compressed archive without any additional software. No crazy drive ghosting needs to be done, nor any special software loaded. I spent a couple days getting my system "just so" and even after loading a full out 8.10 Ubuntu system + KDE 3.5 + a bunch of other stuff, my system backup was like 2GB! I seriously wish I knew this from the first time I hit that "Oh yes, everything works!" point, cuz I seriously have reinstalled various distros of Linux like 10 times in the past month.

I hope these tips help you get the stuff figured out and generally have a bit of an easier time.

---

### Post by rayofash on 2008-11-13
Found the other guys thread, he was having the same problem:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=4414172](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=4414172)

---

### Post by SleepingProphet on 2008-11-13
have you considered trying 8.10? I know on the ATI side of the fence, that actually did make a difference because apparently 8.10 has a new version of X and some things are different. Found that the older drivers would NOT work on 8.10 and the newer drivers wouldn't work on 8.04. I only mention this cuz everyone in that thread is posting from a couple months ago, whereas 8.10 only just came out a couple weeks ago.

Also how are you installing the drivers? AFAIK there are 3 methods (in order of annoyance level)
1-Let Ubuntu do it for you. This is a component called Jockey, which should automagically detect that you've got "restricted drivers" available and then pop up a message telling you so. You click it, tell it its OK, give it your password and reboot. Done.

2-Use EnvyNG. This is available via Apt-Get and is really easy to use, basically the same as above except its downloading the "latest" drivers from nVidia as opposed to using the Ubuntu repositories.

3-run the installer .RUN file manually and do your configs of xorg.conf manually.

---

### Post by Mortosa on 2008-11-13
I have a different video card then you, mines a 9600 GT. For me I would download the Nvidia drivers from Nvidia, ctl+alt=F2 and install the drivers and everything would be fine. But as soon as I rebooted I got a "Low graphics mode"  irritated the daylights outta me. So here is what I did.

[http://ubuntuforums.org/showthread.php?t=805444](http://ubuntuforums.org/showthread.php?t=805444)

I hope this helps

---

### Post by rayofash on 2008-11-13
I tried all those things, it's in my first post. The only thing I haven't tried is earlier drivers, I'll test some out after work.

---

### Post by rayofash on 2008-11-13
Okay, now the drivers don't even show up in the Hardware Drivers thing so I can't remove it.

Dagnabit.

Edit: Oh, Envy fixed everything, goody!

---

