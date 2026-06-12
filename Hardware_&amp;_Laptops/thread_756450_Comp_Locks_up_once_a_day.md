---
title: "Comp Locks up once a day"
date: 2008-04-15
forum: Hardware &amp; Laptops
---

### Post by gyzer on 2008-04-15
For several months now the machine I use to surf the web and such has had an odd problem of locking up. It only locks up the first time its been turned on that day, and with in about 10-20min of the OS being up. It usually locks up when it does something like I'm trying to open up a program or open up a file, or if I'm multitasking. The strange thing is though, after that initial lock up, I restart and the computer runs fine and never locks up again until I shut it off.

I know the simple solution would be just to leave it on all night, but this computer is in my bedroom and I really don't want to have it on when I'm not using it in one way or another.

The strange thing with this problem is that now it has stuck around since I installed Ubuntu 8.04 which I did just the other day for the first time ever. Before this problem was in XP.

So now I know that its not the operating system I'd like to get some suggestions from people on what it might be.

I have run memory testing programs to check my RAM and thats fine, and I've run diagnostics on both my hard drives and they also come up fine.

Here are my system specs:

512MB RAM
1.4Ghz Athalon XP, currently running at 1.1Ghz (I've been runing it at that for years)
80GB Deskstar IBM Hard drive (Also I've had for like 5 years and have never had a problem)
200GB Seagate Hard Drive 
GeForceTi 4200, drivers currently not installed
ECS K7S5A mother board (yes, it is a pile of garbage, worst Mobo I've ever purchased) but its worked for over 5 years now with only the USB bus acting up.

Any thoughts or suggestions would be appreciated. I'd like to try and avoid installing another mobo, but if thats what it takes I can do it.

---

### Post by gyzer on 2008-04-16
Was this the wrong forum to post this in?

Are there any diagnostic programs in Ubuntu that I can use to help narrow down what the problem is?

---

### Post by VeN0mizer on 2008-04-16
Do you have any restricted drivers enabled? I know my laptop would randomly lock up and it took me days to discover it was the crappy broadcom wifi drivers (bcm43xx cutter) that was the culprit. I removed those and used ndiswrapper and have been lockup free for months.

EDIT: Oh it happened in winblowz too...sounds like a time for trial and error (Joy!) If you can consistently get it to lock up after 10 mins every time, start removing components one at a time until one makes a difference...if none makes a difference, what about the CPU temp? video card temp? chipset temp? Are all the fans working ok?

For me, most lockup problems are ram or hard drive issues more than anything. It seemed to me with a lot of my windows customers with old computers, when the computer would randomly lock up, it was due to windows trying to access the swap file and something HD related failed, whether windows read a bad sector or what have you...chkdsk NEVER reported ANY errors on the drives, yet replacing them fixed the problem...PROBABLY WONT WORK FOR YOU though, just throwing it out there

Also...does it lock up when in the BIOS config?

---

### Post by gyzer on 2008-04-16
The only restricted driver I have installed is my Nvidia drivers, but this happend before I even had that installed. 

I am running ndiswrapper so I can have my D-Link DWA-130 USB Wireless draft N Network Adapter working. That worked just fine.

In the past I did have problems with one of the DIMM slots on the motherboard. The problem with it was that during bootup right when XP would be loading the computer would restart. This would happen several times in a row sometimes, and other times it would just happen once or not at all for as long as weeks at time. I thought that there was a problem with my RAM, but I moved it to another DIMM slot and that worked just fine. I guess it is possible that its the hard drive, or possibly there are some bad areas in the memory.

The computer does not lock up in BIOS. 

The only problem with doing trial and error is that the problem just happens once a day. When I get home tonight I'll turn it on, after however long it takes it'll lock up, I'll restart it and then it'll work just fine for the rest of the night. So if I were to do trial and error, it would take me probably a week to really test out all of the components on the computer.

Should I unmount my file system and run a fschk?

Thank you for your sugestions

---

### Post by 1875 on 2008-04-16
Have you noticed any change in fan activety prior to your freeze ? Take the side off and check none of your fans are stalling on start up.

---

### Post by gyzer on 2008-04-16
No I haven't checked to see if any fans are stalling on startup. Is there a good fan and cpu temprature program for Ubuntu that you'd recomend?

---

### Post by VeN0mizer on 2008-04-16
KTemperature is one, but it can be a pain in the rear to get it configured. Try google for configuring options. As far as it not locking up in BIOS...I would suggest trying to install ubuntu on another hard drive and slip it in on your next "one-a-day" boots ;) That way we can determine if maybe swap file access on a bad drive is to blame....just a shot in the wind, and we can eliminate it as a problem...OR...try the live cd to see if it freezes with it, that will save you the headache of eliminating the hard drive by using another ;) :guitar:

EDIT: So yes, I would try the live CD approach first, and if there are no freezes there, install ubuntu on a spare HD and see what happens :P I'm not sure how to do what windows calls a "surface scan" in linux, but for me, windows never found any errors on for sure BAD drives when I ran it on them, not sure if the results will vary for you in linux...and if there are no freezes both running off of the live CD and the spare HD, then that pretty much seals the deal I think :P good luck! ;)

---

### Post by VeN0mizer on 2008-04-17
*BUMP*

Any new activity?

---

### Post by gyzer on 2008-04-17
I ran the LiveCD last night and no problems. That made me start thinking about my usb bus, which I can't use my usb network adapter with the LiveCD cause I have to use ndiswrapper and restart the system for it to recognize it.

So I started up off the hard drive with the usb network adapter disconected and did some large file transfers between my hard drives. No lock up. After that I connected the usb network adapter and still no problem. 

From my current and past problems with the USB bus on this motherboard I'm going to say thats the problem. I've already purchased a USB 2.0 PCI card to by pass this issue. I bought it originally cause I only have two USB ports that work correctly on this computer.

I'm going to install the card this weekend so we'll see how things go after that.

Thanks for the help

---

### Post by VeN0mizer on 2008-04-19
Great! I hope things work out for you, PLEASE keep us updated as I always like chasing down these kinds of issues even if I'm way off on the solution :) It's great to know what things caused lockups for future references, etc...PM me if you would rather do that ;)

Thanks ;)

---

### Post by gyzer on 2008-04-20
So far so good.

I'll give another update in a few days.

---

### Post by VeN0mizer on 2008-04-20
I wonder if the onboard USB controller can be disabled via BIOS or jumpers when you install the new controller? Thanks for the updates :)

---

### Post by gyzer on 2008-04-21
That is a great idea. Sadly I don't know if that will help seeing as no devices are installed in it now.

Sadly though my comp froze earlier for the first time in several days. I was doing alot, had 3 workspaces with stuff going on, downloading and installing an update and I had my visual effects set to "extra". I've now brought them down to normal and I've of course noticed a huge performance increase. I've also brought up my CPU from 1.1Ghz to 1.8Ghz. I've had it at 1.1Ghz for a long time for a reason I can't even remember, so that might be helping things out too.

Well lets home at least one of those fixes will work.

---

