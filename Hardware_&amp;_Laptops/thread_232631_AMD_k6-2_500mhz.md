---
title: "AMD k6-2 500mhz"
date: 2006-08-09
forum: Hardware &amp; Laptops
---

### Post by cantormath on 2006-08-09
Does anyone have recommendations for a AMD k6-2 processor, specifically a kernel recommendation?  If you can think of anything else, none kernel related, please post them as well.  I have never delt with this processor before.
  
Here are is the hardware
[lspci]("http://cantormath.com/lspciAMD.txt")
[lshw]("http://cantormath.com/lshwAMD.txt")

---

### Post by bscbrit on 2006-08-09
I don't think that you will have any particular problems with the kernel, but I wouldn't want to spend too much time using a full Gnome or KDE install.  It will be slow.  I'm sure that there are others who will tell me that they use the same CPU for their daily grind etc, but I still think its too slow for regular usage.

You will almost certainly find that your modem won't work immediately - or at least that was my experience.

You are below the recommend minimum RAM for running Ubuntu, but again YMMV.

---

### Post by Titus A Duxass on 2006-08-09
Use Xubuntu and you'll have no problems with your hardware. I wouldn't worry about the kernel selection, just use the CD.

---

### Post by cantormath on 2006-08-09
wow, does gnome suck on this machine, lol.  you definitely called that.
WOW.  Im in the process of installing xubuntu.

It seems that the boot and the shutdown are really kinda slow, like slower then a pentinum 400mhz with windows 2000.  Any ideas?

---

### Post by bscbrit on 2006-08-09
Yes - I did think that Gnome would be slow!

You can improve matters, after you have installed xubuntu, by removing unwanted daemons, services and other spurious bits of software that are loaded during the boot.  They don't take much CPU time but they still have to be installed so that they can go to sleep and do nothing!  If you don't need them, get rid of them.

Comparing with a Windows 2K boot is pretty meaningless other than being a comparison of expectations.  I have no idea how much or how little each of your OS is trying to handle so it is unrealistic to compare.

Alternatively, think of how much CPU time you will save by not having to run an antivirus program under linux!  You only boot and shutdown infrequently - it is actual productive time that is a more useful yardstick.

Incidentally, have you tried timing the boot and logon in seconds?  It might be a useful clue as to what is going wrong but, equally, it might not be quite as excessive as you believe it to be.  There might be several reasons for this.  If you use another, more modern, computer than subconciously you are comparing the boot and logon times between 2 very different systems.  Secondly, if you are waiting for a computer to start up then 60 seconds can seem a long time but it isn't very long in real terms.  Press the on switch and go and make yourself a coffee.  The computer will be waiting for you by the time that you get back.

I know that you provided a subjective comparison between 2 different systems running on the same computer but, as I have already indicated, I cannot evaluate what each system is trying to do. For example, my Ubuntu is running with ext3 journalling filesystems.  That means that at both boot and shutdown there is an adminstrative overhead to be taken into account.  The plus side is that there is much less chance that I will lose my data.  Windows doesn't replicate this and therefore will save time during boot and shutdown.  Do you want speed in preference to security or is are a few 10s of seconds more a small price to pay for not losing data?

---

### Post by Modki on 2006-08-09
AMD K6 @ 333Mhz with 96MB of RAM runs Xubuntu as fast as it ran the OS it came with (Windows 98 SE) and a fair bit more stable. The XFCE is just like GNOME from what I can tell (visually) but is a marked improvement in the speed department.

---

### Post by awong on 2006-08-13
ram may be the problem, I am running ubuntu with a k6-2 550 with 256 megs of ram and it feels faster imo browsing online than on windows 98.  I think the ram though will make a big difference.  I may be upgrading to 512 on mine though.

---

