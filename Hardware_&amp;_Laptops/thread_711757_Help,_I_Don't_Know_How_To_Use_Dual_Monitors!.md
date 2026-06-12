---
title: "Help, I Don't Know How To Use Dual Monitors!"
date: 2008-03-01
forum: Hardware &amp; Laptops
---

### Post by kira. on 2008-03-01
Hi everyone! I'm kinda new to Ubuntu, and I was wondering if I could get some help getting both my monitors working at the same time. By the way (if this helps at all) I run an NVidea GeForce8600 video card, and both my monitors are currently working fine on Windows.

Thanks alot!

---

### Post by sstusick on 2008-03-01
Well, there are plenty of threads on the forum regarding the use of dual monitors, try the search feature and see what you come up with. You're using an Nvidia card...that's a good sign that you'll get them dual monitors working ;)

---

### Post by kira. on 2008-03-01
thaaaaaaaaanks!

any tricks you might want to divulge, though?

---

### Post by kira. on 2008-03-01
because i've been looking at some threads, but I'm new, so I don't really understand much of what they're saying :(

---

### Post by sstusick on 2008-03-01
I haven't attempted dual monitors - yet. So I can't be of much help, but as I always do before asking on the forum is doing a search, and you'd be surprised at how many people have the same or similiar issues. Just about everything has been asked before, all you have to do is find that particular thread ;)

---

### Post by sstusick on 2008-03-01
> **kira. said:**
> because i've been looking at some threads, but I'm new, so I don't really understand much of what they're saying :(Well if we keep bumping this thread up, I am sure someone will come along and try to help you :)

---

### Post by kira. on 2008-03-01
hmmm, smart idea!

the thing is, all of the tutorials that I've found were people half-way through the process, while I've done nothing and have no idea of how to proceed
also, most people are running older video cards than me, and so have different configurations (does that make sense?)
anyways, what I'm just trying to say is that I'm at a loss as to where to start...

---

### Post by sstusick on 2008-03-01
Hmmm start here: [http://ubuntuforums.org/showthread.php?t=707159](http://ubuntuforums.org/showthread.php?t=707159)

ADDED: here's another - [http://ubuntuforums.org/showthread.php?t=580670&highlight=dual+monitors+8600](http://ubuntuforums.org/showthread.php?t=580670&highlight=dual+monitors+8600)

---

### Post by kira. on 2008-03-01
Actually, when I looked into my "screens and graphics" menu, it doesn't even show another monitor

---

### Post by baxterdog on 2008-03-01
I haven't had to do this in a while, but the previous poster is right. Look around. There was a thread I found a while ago that showed an addition to a config file for the video card where all that was needed was to add the address of the second monitor into it (and some more lines). Sorry I can't be of more help right now. All I remember is that it was actually quite easy.

---

### Post by kira. on 2008-03-01
Uh oh... i played with the gksudo nvidea settings, an now the image switched screens, and the resolution is out of whack, i cant even see half the screen..

---

### Post by jezebel on 2008-03-01
Hi

Ok...

When you did the gksudo nvidia settigns, did you get a whole let of settings to choose from?If not, get the drivers from Envy...

Avoid the Ubuntu built in options - I spent hours on that.

If you're mostly set up, make sure you don't have Compiz special graphics running - this messed me up. Go to System - Appearance - Preferences (and choose Visual effects - NONE).

Anyway if you're not mostly done, this sort of helped me with my Geforce 5200...

"So first, I had to install Envy, which "is an application...which automates the installation of both ATI and Nvidia's proprietary driver on Ubuntu" (Envy can be downloaded here). Anyway, even if you already have a driver which works under Gutsy (Ubuntu 7.10), you'd be better off using Envy and "upgrading" the driver that way. I spent too much time trying to configure the screens and graphics in Ubuntu, but my Nvidia driver at the time did not have any options for me to setup multiple monitors. After installing and running Envy, I then had more options in my Nvidia settings.

After installing Envy, I went to the Terminal and entered the command line:

gksudo nvidia-settings

This is important! Although you can launch the Nvidia settings dialog from Application - System Tools, you have no authority to alter the settings and nothing will be saved. Therefore, it must be done as "Super User" via the Terminal.

In the Nvidia settings dialog, I set up my monitors in the X Server Display Configuration. In there, I set Ubuntu to recognize two separate X-screens; I set the resolutions for each monitor; it's important to set one monitor's position as absolute (the default monitor) and the other as relative."

[IMG]http://bp0.blogger.com/_ROW6n9t-rrg/R646x3B5feI/AAAAAAAAAbA/Zf07taSlSRI/s1600-h/00021.jpg[/IMG]
J.

---

