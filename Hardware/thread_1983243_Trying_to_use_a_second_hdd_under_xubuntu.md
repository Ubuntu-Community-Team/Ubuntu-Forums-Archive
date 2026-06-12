---
title: "Trying to use a second hdd under xubuntu"
date: 2012-05-19
forum: Hardware
---

### Post by mace200200 on 2012-05-19
Basically I have my main HDD with xubuntu 11.04 installed, then I have my second HDD with windows installed.
            I want to use the second HDD to dual boot windows on (which I've done), and i want to be able to use the files from Windows 7 in xubuntu (I want to be able to install programs in windows, then run them in xubuntu with wine for the most part). Since I've never run two hard drives together under Linux or Windows I don't know what to do. From what i understand, or rather think i understand, I first need to mount the second HDD (the one with the windows 7 install), then set it up to auto mount each time i boot into Linux before i can set it to use files installed in Win7.

How do i make it so that the second drive will auto mount, and then take files that I've installed into Win7 and run/use them in xubuntu?
And also my main drive with the xubuntu install is very small, my second one is large, which is why i want to run programs from the second hard drive, while running xubuntu which is on the fist one.

Please help me or tell me where to start, I really wish i knew how to run Linux better but I do not and need to learn.

---

### Post by ahallubuntu on 2012-05-20
You can't quite do what you hope to do.  If you want to run programs in Wine, you need to install them separately in Wine.  The programs you have installed separately in Windows 7 cannot simply be executed from Wine.  Installing a program in Windows or Wine means adding entries to that installation's registry and other things.  Wine has an entirely separate registry, etc.

You can certainly mount your Windows 7 hard drive in Xubuntu and access files from it, but you won't be able to run the installed software directly.

Further, you may find that many Windows programs run poorly or not at all in Wine - at least, that's been my experience.  Another option for you might be to create a virtual machine in Xubuntu with, say, Virtualbox (free from Oracle) and install an entirely separate Windows installation inside of that - that will allow you to install and run almost any Windows software you want (much more reliably than Wine), but you still have to install everything separately.

Unfortunately, Virtualbox requires extra disk space and more RAM.  You may not have the resources to install it on your small Xubuntu hard drive.

---

### Post by mace200200 on 2012-05-20
> **ahallubuntu said:**
> You can't quite do what you hope to do.  If you want to run programs in Wine, you need to install them separately in Wine.  The programs you have installed separately in Windows 7 cannot simply be executed from Wine.  Installing a program in Windows or Wine means adding entries to that installation's registry and other things.  Wine has an entirely separate registry, etc.

You can certainly mount your Windows 7 hard drive in Xubuntu and access files from it, but you won't be able to run the installed software directly.

Further, you may find that many Windows programs run poorly or not at all in Wine - at least, that's been my experience.  Another option for you might be to create a virtual machine in Xubuntu with, say, Virtualbox (free from Oracle) and install an entirely separate Windows installation inside of that - that will allow you to install and run almost any Windows software you want (much more reliably than Wine), but you still have to install everything separately.

Unfortunately, Virtualbox requires extra disk space and more RAM.  You may not have the resources to install it on your small Xubuntu hard drive.


Yea i actually just found out that dual booting wouldn't work like I thought it would I'm so sad now :(
I've been playing games under linux with wine for a while Starcraft II works very very well, the only problem I have with playing games on linux is that sometimes I can't get them to install which is why i wanted to run windows to install games in then run under linux. 
It's not that bad though since all i have is a 32bit win7 disc, I'm gonna borrow a 64bit disc from my friend because i discorved that the key will work for either platform. Then i can use windows for most of my games, but still have linux for.....everything else.

---

