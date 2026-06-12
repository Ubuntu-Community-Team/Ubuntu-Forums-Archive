---
title: "Ubuntu, and Kubuntu hang on load"
date: 2008-11-30
forum: General Help
---

### Post by spy_1134 on 2008-11-30
I'm not sure whether this is a hardware problem or not but whenever I log in on Ubuntu 8.10 the thing froze. This happened on Kubuntu as well. It wasn't a disc problem (reburned multiple times with multiple discs) This happened with all 3 ways i tried to upgrade: Synaptic, cd via direct download, and cd by bittorrent. Was this just a release bug? :confused:

---

### Post by cmnorton on 2008-12-01
I'm confused. Was this installation successful and now you cannot log in without hanging? Or, do the installs hang?

---

### Post by spy_1134 on 2008-12-02
> **cmnorton said:**
> I'm confused. Was this installation successful and now you cannot log in without hanging? Or, do the installs hang?

I can get to my login screen etc. But when I enter username then password the thing stops. As far as I know the installation was successful since this even happened on the live cd. :(

---

### Post by cmnorton on 2008-12-02
Try CTRL+ALT+F1 and logging in text mode. Does that stop?

If you can log in then, check your logs and the output of dmesg.
Start with /var/log/syslog (using tail -10 15 or 20 /var/log/syslog) and then /var/log/messages.

---

### Post by spy_1134 on 2008-12-05
I was able to get a terminal so it's only the visual interface that's bugged. I'll be back with the results ( I have to reburn the cd ](*,))

---

### Post by spy_1134 on 2009-03-23
Sorry I haven't posted in a while. I had given up on this issue but I'm giving it another go since I love Ubuntu. :)

I just burned a Kubuntu 8.10 livecd and ran it without installing, I can install it if I need to since Gentoo didn't seem to work either...

Here's what I know about my hardware...
2.4 GHz Intel Celeron with 1gb of ram

I ran the command "tail -10 /var/log/syslog" and the following line caught my eye:

"Mar 23 08:03:36 ubuntu kdm[6632]: Failed to start X server. Starting failsafe X server"

Any additional help would be appreciated :D

EDIT: Out of curiosity I looked deeper through the log file and found this:
Mar 23 08:03:33 ubuntu kdm[6632]: X server start up timeout, terminating
Mar 23 08:03:33 ubuntu kdm[6632]: X server died during startup

I'm baffled since I don't know much about the X server :/

---

### Post by spy_1134 on 2009-03-26
*Bump*

---

### Post by zolek78 on 2009-03-26
Im having something similar to your problem as well but im using kubuntu for a while now and it happened after i updated something on adept. I doubt there is something to do with the video card, reinstall might get it to work? I'll try it now

---

### Post by spy_1134 on 2009-04-03
I have reinstalled it several times and it didn't affect the problem whatsoever. :???: I would really love to get Ubuntu up and running again. :mad:

---

### Post by spy_1134 on 2009-04-07
*bump* :(

---

### Post by spy_1134 on 2009-04-12
Here's some more info on the problem, I found that the problem's origin was Debian (I tried installing it and got the same result).

I keep getting a message something along the lines of:

Fatal Error:
lockup

Please help, I really love Debian and Ubuntu and don't want to switch to something like Fedora, which is really slow on my computer. :mad:

BTW I'm not a complete noob so if the fix involves editing config files then there won't be any problems :p

---

### Post by spy_1134 on 2009-04-13
*bump*

Come on... Does anyone know how to fix this?

I either want it fixed or I need a new Linux distro.

Help with either one would be appreciated :p


For the Linux distro:
Has to be updated regularly, or be a very secure system. Has to have the driver rt61pci enabled by default or come with a compiler so I can build it myself.
And it has to be really fast.

My machine is a Dell Dimension 2400 with a 2.3 GHz proccessor and 1GB of RAM, graphics card is stock. (Which is probably why the X Server locks up...)


All help is appreciated,

Chris

---

### Post by Thura on 2009-04-13
Sounds like a hardware prob, Why not file a bug in lauchpad ? There you can get answers from developers ... Here, most are normal users ...

---

### Post by Brixton on 2009-04-13
I am having the exact same problem as Spy.

I have tried Ubuntu/Xubunut 8.10 multiple times, in multiple drives.

I can never run the live cd, as it never boots, it locks up right after hearing the start up sounds.

I am attempting this on a Dell 2400 with 2.66ghz, 1gb RAM, integrated intel graphics (Intel 8245G/GL/GE/PE/GV Graphics Controller.

I'm pretty sure it has something to do graphically as well. Only after installing, since the live cd fails, does it run in only safe graphics mode. I also can not install in windows as it always gives an error at 99% install claiming the disk can not be read from.

The disk itself is fine, it loads perfectly in other computers. I have also tried other burns and the alternate installer.

I am new to this system so I'm not sure if missed something obvious.

---

### Post by cmnorton on 2009-04-13
I would write up all details of this, including anything you can get out of your logs -- not the entire content of the logs but a few lines that look pertinent -- and post that at up at Ubuntu Launchpad.

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

As to the Ubuntu live CD not launching, that sounds like a bad CD (bad image on the CD).

---

### Post by spy_1134 on 2009-04-13
The CD wasn't bad. What I meant by it didn't load is that the X server failed to start.

I have been trying Debian but got the same error, I fired up my computer today and for some weird reason it started working. :confused:

Since Debian started working I'm going to retry the Ubuntu install.

---

### Post by spy_1134 on 2009-04-19
I found the solution to the problem:

Apparently there is a driver bug for dell dimension 2400's default graphics controller, so it crashes when it tries to load compiz special effects
More Info: [http://ubuntuforums.org/showthread.php?t=1100012](http://ubuntuforums.org/showthread.php?t=1100012)

SOLUTION:
The solution listed in the above post link said to remove compiz, and compiz-core
I haven't tried this solution because I really want compiz on my system, so the solution for me is either to stick to 8.04 LTS or wait for 9.04 release (Which Comes In A Few Days!!!)

Thanks for all the help guys :D,
Chris


   - EDIT -
I have tried the solution and it works!
to remove compiz, log in to the terminal by pressing ctrl+alt+F1 and then enter the command: sudo apt-get remove compiz*

The command will remove anything that has to do with compiz, which causes the problems.
Again, Thanks for all of the help :P This forum is a big help

---

