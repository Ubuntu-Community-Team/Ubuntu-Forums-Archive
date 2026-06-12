---
title: "Survey: degraded notebook performance under Linux (NC10, 1000HE, Wind U100)"
date: 2009-05-16
forum: Hardware
---

### Post by AlexandreS on 2009-05-16
I'm currently looking for a notebook, and the contenders so far are the Samsung NC10, Asus Eee PC 1000HE and perhaps the msi Wind U100.

*[rant] Looks like for the first time since 2000, I'll have no choice but to pay the WinTax. I'm sad that I could not complete the decade without paying it again, specially to buy in a segment which started with a strong Linux presence [/rant]*

My question to the users of these notebooks is the following: since I plan to only use Linux on the notebook, I would like to know what kind of degradation in performance can I expect. For instance, the 1000HE strong suit is an extra long battery life, but I have read in forums that using Linux will shave 2 hours of battery life. If so, the long battery argument does not fly for me anymore, as I WILL be using Linux on my notebook.

Just to be clear about this, I'm aware that there is plenty of info on how to run Linux on these machines ([1,]("http://ubuntuforums.org/showthread.php?t=361236")[2]("https://wiki.ubuntu.com/LaptopTestingTeam")). But what I want is to know what kind of performance are you achieving **right now** with your model, and **how** did you managed it (distributions, patches, etc). Also, I would like to know what kind of functions could not be made to work so far, or have a degraded performance. Specially important to me are battery life, the ability to do voip, and the possibility to do presentations through the VGA port. But of course any problems and sources of irritation are of interest to me (suspend mode, hibernation, etc).

Hopefully, this thread will also be useful to others to exchange information on how to improve their notebook performance.

---

### Post by enchantedsky on 2009-05-16
Here is my experience with Ubuntu Linux 9.04 on Asus Eee 1000HE:

1) CPU throttling DOES work. When you're running a program, the CPU jumps up to 1.6 GHz......but when you idle, it drops to 1.0 GHz. Perhaps it could be lower though, which may account for using up more battery power. (especially if there is a lower underclocked CPU speed in Windows XP)

2) The screen brightness controls don't really work well. Yes it works when you press Fn + Function key which controls brightness, but Ubuntu seems to have a mind of its own with brightness. It dims the screen when you're idling and doing nothing, but when you move the mouse cursor, it over brightens as if the laptop is plugged in. There is no way to control this auto-brightness feature in Ubuntu. Windows XP, on the other hand, ultimately lets users permanently set a brightness level, and sticks to it, whether the laptop is plugged in, or on battery power. Also, the screen shuts off COMPLETELY in XP after a few minutes of idling, probably reinforcing a better battery life under Windows XP than in Linux 

3) Hibernation and suspend work in Ubuntu Linux on 1000HE, but it's slow as hell. Windows XP's resume from hibernation is a ton faster, and I don't know why. Linux is supposed to theoretically faster, and I was using the new Ext4 partition which contribute to a higher speed. Shutting down and booting from scratch in Linux on 1000HE is actually faster.

4) Not really related to battery life, but Flash performance is worse in Linux than Windows XP. This is NOT Linux's fault, but Adobe not creating a proper Linux version that is bug free. It also drains battery life easily, but that's true on the Windows version as well

5) When I updated the BIOS in 1000HE to the latest version, wireless internet STOPPED working in Ubuntu Linux 9.04. I don't know why, and I'm still trying to figure out why it stopped working. When I booted up Windows, it was working. In Linux, it sees routers, but infinitely attempts to connect, but cannot make a connection. That is to anyone's router (my home, my neighbors, friend's house, etc) so I know it is not the router's fault. Apparently, the BIOS updates do NOT take into account that some users use Linux......they perhaps only check for compatibility under Windows XP and make sure nothing breaks solely for that operating system. Which leads to #6...

6) The Asus Eee PC BIOS updating does NOT function under Linux! So you have to run Windows at some point if you want to update the BIOS. Updating it IS important, because for instance, the latest BIOS version optimizes video performance by increasing framerate and making videos look less jittery. If there is a command line way of updating the BIOS with Linux, it is not really well supported by Asus, and you could screw up your computer. Hence, using Asus' official BIOS updating for Windows XP.

So that's my experience with 1000HE and Linux :)

---

### Post by Rhubarb on 2009-05-16
> **enchantedsky said:**
> 6) The Asus Eee PC BIOS updating does NOT function under Linux! So you have to run Windows at some point if you want to update the BIOS. Updating it IS important, because for instance, the latest BIOS version optimizes video performance by increasing framerate and making videos look less jittery. If there is a command line way of updating the BIOS with Linux, it is not really well supported by Asus, and you could screw up your computer. Hence, using Asus' official BIOS updating for Windows XP.

It is indeed very much possible to update the BIOS on eee pcs, just read it here:-
[http://www.blakeanthonyjohnson.com/?p=170](http://www.blakeanthonyjohnson.com/?p=170)
You'll need a usb flash drive, and a little poking around in the terminal, but that's it.
I've used this method of updating the BIOS on my eee pc twice - though I did use gparted to create the partition, but used the terminal to mount it.

> **enchantedsky said:**
> 2) The screen brightness controls don't really work well. Yes it works when you press Fn + Function key which controls brightness, but Ubuntu seems to have a mind of its own with brightness. It dims the screen when you're idling and doing nothing, but when you move the mouse cursor, it over brightens as if the laptop is plugged in. There is no way to control this auto-brightness feature in Ubuntu. Windows XP, on the other hand, ultimately lets users permanently set a brightness level, and sticks to it, whether the laptop is plugged in, or on battery power. Also, the screen shuts off COMPLETELY in XP after a few minutes of idling, probably reinforcing a better battery life under Windows XP than in Linux
This is very easy to fix, just go to System --> Preferences --> Power Management, and configure it up there.


I've got an Eee PC S101 - I removed windows (I couldn't get a refund of win xp - I tried) and installed Ubuntu 9.04:-
[http://www.asus.com.au/products.aspx?l1=24&l2=164&l3=0&l4=0&model=2595&modelmenu=1](http://www.asus.com.au/products.aspx?l1=24&l2=164&l3=0&l4=0&model=2595&modelmenu=1)
The website quotes a battery usage of 5.4 hours, which quite frankly would be near impossible to reach even when running windows.
I can run my eeepc s101 with at least 3 hours usage, with the CPU running flat out, and screen brightness all the way up.

CPU frequency scaling works automatically, so when it's running idly, or running light applications, it runs at 900MHz.
It's able to (by default) automatically scale up to 1.6GHz when needed.
It is also possible to choose what speed you want the CPU to run at, however I find it is unnecessary to do so.

The following are the minor problems I have with it when running Ubuntu 9.04:-

1) Wireless N doesn't work for encrypted access points easily - This can be made to work, but it's quite tricky to do at the moment - this should be a lot easy in probably by the next release of Ubuntu 9.10

2) Playing some flash videos can be quite horrible. - This is mainly to do with a fault of adobe.  Using gnash or extracting the swf video file and playing locally works very nicely.

3) Ever since upgrading to the latest BIOS, I can't disable on-board wireless networking.
* Update, there seems to be a new version of the BIOS out for this, so this may indeed be incorrect now.

4) Hibernation doesn't work, but Suspending works flawlessly.
- I think I recall Hibernation working in Ubuntu 8.10, so it's just a little bug that probably could be fixed with a little tinkering.

5) Plugging in an external monitor doesn't work easily.
It'll display your login screen nicely, but as soon as you login nothing is displayed on the external monitor.  I've tried briefly to get it working - but with no success.
I'm sure if I devoted a little more time I could get this working.

6) The overclock button doesn't work, this is no big deal really, as I can manually choose what frequency to run at (or let it automatically scale).  I am unable to overclock it to 1.8GHz (I haven't tried doing this, if I had more time I could probably get this working).


Everything else works really really well.
Compiz works nicely.
The webcam is detected fine and works flawlessly with cheese.
The Microphone is detected and works nicely.
Using Ubuntu 9.04 with ext4 makes it run insanely fast.
The (16GB) SSD hard drive in the S101s is much quicker than other solid state drives for netbooks, so all in all it runs really quick.

My only major gripe would be that Asus advertises on the web site that you can get Gnu/Linux with it, but if you go to any supplier they say that the don't have / can't get the model with Gnu/Linux.
- They only stock the Win XP models.  - Sounds like Microsoft are up to their old Monopolistic tricks again.
I'd also tried over a duration of 2 months trying to get a refund of the Windows tax off Asus.  I was unsuccessful in my efforts to do this.
Ironically Microsoft were the most helpful party to contact regarding this - but the EULA (of which I'd declined) states that the manufacturer is able to give the refund.
Asus had changed their story about not being able to give me a refund to me on several occasions.  The only story that they ended up using the last few times was that windows is bundled with the netbook, and can't be unbundled.  I can return Windows for a refund, but that would also involve returning the eee pc as well.
I gave up trying to pursue them about this after 2 months.
Every time I contacted them I'd quote the relevant section of the EULA to them, which seemed to make them pause and try to concoct a different excuse that they could use.  Perhaps the threat of legal action could make them change their minds.

Sorry for my ramble back then.
I am very happy with my eee PC, it works really nicely with Ubuntu.

---

### Post by AlexandreS on 2009-05-17
Thanks for you extensive feed back!

> **enchantedsky said:**
> When I updated the BIOS in 1000HE to the latest version, wireless internet STOPPED working in Ubuntu Linux 9.04. 

That's pretty nasty! If further updates solve that issue, would you mind updating this thread? This "feature" kills the point of using Linux on the 1000HE...

---

### Post by AlexandreS on 2009-05-17
> **Rhubarb said:**
> It is indeed very much possible to update the BIOS on eee pcs, just read it here:-
> Using gnash or extracting the swf video file and playing locally works very nicely.Thanks for the tips!

> Ever since upgrading to the latest BIOS, I can't disable on-board wireless networking.Looks like BIOS upgrades are a hurdle for Linux. I hope I can get a firmware version that works reasonably well, and keep it as a backup.

> 5) Plugging in an external monitor doesn't work easily.
It'll display your login screen nicely, but as soon as you login nothing is displayed on Hope it can be fixed, as I would use the notebook for meetings and presentations. But on the other hand I'm not too worried, I can't imagine having the VGA port not working.

> Sorry for my ramble back then.
Not at all, I'm just as frustrated as you are ;)

---

