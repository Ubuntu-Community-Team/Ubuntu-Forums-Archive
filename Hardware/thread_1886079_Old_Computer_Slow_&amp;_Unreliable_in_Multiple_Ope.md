---
title: "Old Computer Slow &amp; Unreliable in Multiple Operating Systems"
date: 2011-11-24
forum: Hardware
---

### Post by thomas144 on 2011-11-24
Hi, everyone!
I'm not sure if this is a relevant question or if I'm putting this in the right place, but I'm having odd symptoms with a PC (It's a Dell Dimension 8200 from circa 2001). It has 256 MB of RAM, a Pentium IV processor, and a 40GB hard drive. When it ran Windows XP, it was gradually becoming slower and slower. It took about five minutes to boot, and when I logged on, the computer was very unresponsive. For example, it took several seconds for the Start menu to appear after clicking on it. Also, switching windows was unresponsive in the same manner, and programs seemed to take much longer than they should to load. In general, it was unreliable and slow. Applications would occasionally freeze up and had to be closed by killing their processes with Task Manager.
    When I tested it with Xubuntu, the CD drive used to boot from the CD was very temperamental. I had to repeatedly attempt to boot the CD until it finally recognized there was a CD in the drive. The strange thing about Xubuntu was that it was slow in the same way, and quite unstable. It took a few seconds for the Applications menu to pop up, switching windows was slow, and plugging in a flash drive caused the computer to freeze, the monitor go black and enter sleep mode, and the login screen to load. Trying to log back in causes the cycle to repeat again. Also, when I opened a window, it would put a grayish border around the window and have trouble in general with drawing the desktop background. The confusing thing is that a lot of these problems would happen even while the computer was using no swap space.
    I know this is a very long-winded post, but I've spent a lot of time thinking about and Googling problems but I have no clue as to why the computer would be experiencing similar issues in Xubuntu and Windows XP. I'm thinking that it could be a lack of RAM, but these problems happen in Xubuntu even without any sort of swap space. What's going on?
P.S. My plan was to turn this machine into a dual-boot Windows/Lightweight Ubuntu version computer.

---

### Post by snowpine on 2011-11-24
Have you considered simply upgrading your hardware? Tomorrow is Black Friday (if you live in the US) plus there are always great deals on Craigslist and Freecycle. :)

Here is a list of Ubuntu-certified hardware: [http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/)

---

### Post by thomas144 on 2011-11-24
Thanks for the suggestion, but I don't really need this PC to be very fast; I just want something usable. I have a laptop that runs Ubuntu very fast, and that's what I'm typing on.

---

### Post by thomas144 on 2011-11-24
I was wondering what the problem was. Do you think that it's just old and slow, or is something failing?

---

### Post by snowpine on 2011-11-24
Did you actually install Xubuntu or just try it from the Live CD?

Pentium 4 is OK but 256mb ram is borderline in 2011. Plus it sounds like your CD drive is failing. :)

Why not give Puppy Linux a try? That's just about the fasted Linux distro that's still reasonable user-friendly.

---

### Post by MG&amp;TL on 2011-11-24
Try Lubuntu: [lubuntu.net]("lubuntu.net")

Extremely fast on my pentium IV.

---

### Post by thomas144 on 2011-11-24
> Pentium 4 is OK but 256mb ram is borderline in 2011
I was thinking that, too. Maybe after Thanksgiving I can get more RAM (and a new CD drive). I know a good computer store nearby. For some reason, I didn't think of Lubuntu. I don't need anything really user-friendly, and I'm quite comfortable working with the command line. I was thinking that I could install a command-line only Ubuntu and install X and IceWM, but Lubuntu is another thing to consider, and I can burn a live CD of that. I'll probably go and download a torrent of Lubuntu sometime today.

---

### Post by dandnsmith on 2011-11-24
Sounds like you need to do things first:
- install a new, working CD device
- do a thorough clean out/re-install of XP

My experience suggests that at 256 MB RAM you'll be really struggling - Ive had problems running any of the modern releases of Linux, except those like Puppy, DSL, AntiX built for limited hardware.
Further, a failing CD drive can cause more trouble than you realise.
Also, XP is right at the bottom of it's range on 256MB RAM - it can work, but you have to keep the install cleaned, and you have to be careful what you try to run.

---

### Post by thomas144 on 2011-11-24
dandnsmith, you seem to be very insightful. I know that 256 MB of RAM is scraping the bottom of the barrel, so to speak. I'll try to get the RAM upgraded to something reasonable if I can, and get a new CD drive when I can find some time. You also said that a bad CD drive could be causing more trouble than I realize....and you might have a good point there. That could be my problem!
[RIGHT]Thanks for the help,
Thomas
[/RIGHT]

---

### Post by snowpine on 2011-11-24
Hi Thomas, first of all a new (to you) computer might be a better investment than a CD drive and RAM upgrade, I see lots of good stuff on Craigslist in the $0-300 range.

Second, you don't need to use the CD drive at all. If you have a spare USB thumb drive then you can create a "Live USB" which many users find is more reliable than CD technology. You mention you have a working Ubuntu install on another computer, I forget exactly but the app is called something like "USB Startup Creator."

---

### Post by mörgæs on 2011-11-24
> **snowpine said:**
> Hi Thomas, first of all a new (to you) computer might be a better investment than a CD drive and RAM upgrade, I see lots of good stuff on Craigslist in the $0-300 range.

Second, you don't need to use the CD drive at all. If you have a spare USB thumb drive then you can create a "Live USB" which many users find is more reliable than CD technology. You mention you have a working Ubuntu install on another computer, I forget exactly but the app is called something like "USB Startup Creator."

On new computers, yes, but it is not likely that such an old one can boot from USB.

---

### Post by snowpine on 2011-11-24
Every Pentium 4 I've used can boot from USB, I think Pentium 3 was the last chipset that did not have that capability.

Also the OP hasn't answered yet whether the slow Xubuntu was installed or Live CD. It is normal for a Live CD to be rather slow, especially on low RAM. If you haven't installed it yet then that would be recommendation to measure the actual performance.

Lubuntu (LXDE desktop) might be worth a try too. :)

---

### Post by mörgæs on 2011-11-25
Now we need to know! :-) 
Thomas144, can you boot from USB?

---

### Post by mastablasta on 2011-11-25
Firstly, USB boot can be achieved using PLOP boot manager that you put on a floppy drive or even on hard drive.
 
Secondly the issues mentioned seem to imply something wrong with graphics card driver or maybe they showed up only because propper install/configuration wasn't made. sometimes i have seen some graphics issues and even crashes with live system that were ironed out after install.
 
3rdly Lubuntu is a better (or should i say it is a lighter) choice but as i just found out it has a bug and graphics install doesn't work on 256MB ram (eventhough it should). it crashes. Using Mini.iso cd will work fine, probably alternateCD as well. Xubuntu should also work reasonably well (ram considering), the issue here could be with graphics card. 
 
and foruthly if you don't mind with a bit older porgrammes you could give Debian or a bit more user friendly Chrunchbang XFCE a try. I just installed in on 256 MB laptop (actually only 224 MB are available for OS) and at idle it takes about 80MB ram. most stuff worked out of the box just like in Ubuntu and so far the light applications (Chromium etc.) seem to run fast enough. I can still watch movies, youtube videos just fine. The processor i have is 1,2Ghz Athlon (so much weaker than yours i believe). i used the version based on debian stable as i don't really need the latetst and greatest on it but just for the whole thing to work. and the programmes are still newer than before on the preloaded winXP :-)

---

### Post by mörgæs on 2011-11-25
> **mastablasta said:**
> ... as i just found out it has a bug and graphics install doesn't work on 256MB ram (eventhough it should). it crashes. 

[https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/OneiricOcelot#Desktop_ISO_boot_to_a_terminal_prompt](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/OneiricOcelot#Desktop_ISO_boot_to_a_terminal_prompt)

---

