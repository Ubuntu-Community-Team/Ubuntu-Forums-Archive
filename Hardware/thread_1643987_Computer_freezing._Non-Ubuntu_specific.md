---
title: "Computer freezing. Non-Ubuntu specific"
date: 2010-12-12
forum: Hardware
---

### Post by jllangston on 2010-12-12
Greetings,

So, I have a dual boot machine: xp and linux. What I've noticed is that my computer freezes somewhat randomly in Linux. Not just a program, but everything, it all stops: the mouse won't move, I can't Ctl-Alt shift to another login, eventually, after a few keystrokes even the num-lock key doesn't change the light on my keyboard.

I typically leave the computer on. It doesn't seem to be related to this as sometimes the computer froze within ~20-30 min after restarting.

At first, i thought that it was firefox as the computer froze when clicking on some link. Unfortunately, when the computer restarts i can click on the link again and it'll work. So, i first thought that i'd try chrome as forums were saying that firefox sometimes causes problems, but the same behavior happens in chrome, too...

More searching led me to disable and remove flash and most things adobe. Still the computer freezes.

I have searched the system logs but don't really see anything... but then again, not exactly sure what i should be looking for.

I have eliminated the possibility that the computer is running too hot as sometimes the freezing occurs after semi-heavy use. I installed the hardware sensor package, but it is not showing really hot temps, about ~124F for the MB (it's label).

Also, the freezing is not Ubuntu specific; same thing occurs in PCLinuxOS. Nor is it browser specific. It occurs while using a program called LabView, also when the screen saver was using random screensavers (an animated one i'm guessing was the culprit). I have since turned screen savers off.

What's frustrating about it is that most of the time, nothing REALLY serious happens as a result of me having to restart the machine, but sometimes I lose things: took me awhile to get the sound back after one such restart. As an annoying aside, the computer never freezes under Windoze...

About the only thing i'm guessing is something related to JAVA (browser, labview, screensaver??)or cpulimit (i've seen that in the logs), but i'm reaching here...

Computer specifics:
desktop model running ubuntu 10.10
ati radeon graphics card
amd athlon xp 2400
nvidia nforce2 ac97 sound built in
1000 MB RAM


I apologize for the length of this post and am grateful for any assistance.

---

### Post by MauserM98 on 2010-12-12
I am for the moment a Fedora user. After the upgrade from fedora 13 to 14 several things happened witch has rarely happened previously.
In Fedora 13 my PC's did not once crash or freeze. But under Fedora 14 it has been a unstable havoc.

I've tried many solutions to enhance stability and some do help. I guess it is also working in Ubuntu.
I will tell you some of the thing I have done but first I will tell what I think is the main reason for the trouble : The KERNEL!!!!!

So that was my 5 cents.
Temporary relieve :
1. Shut off compiz. (Do you really need wobbly windows?)
2. Use 32 bit flash instead of 64 bit flash.
3. Don't let open office quickstart start automatically.

I know there is users in here who use several distros so please come with feedback.
Even though we like different distros we all share the same kernel.

---

### Post by matt_symes on 2010-12-12
Hi

Hmmm. Have a read of this thread.

[http://ubuntuforums.org/showthread.php?t=1478787&page=154](http://ubuntuforums.org/showthread.php?t=1478787&page=154)

Seems its happening to a number of distros. I use a number of different distros including Ubuntu 10.04, 10.10 and fedora 14 and i just don't get the freezes. Too many people have been though.

@[jllangston]("http://ubuntuforums.org/member.php?u=253379") What distro are you using?

Kind regards

---

### Post by MauserM98 on 2010-12-12
> **matt_symes said:**
> Hi

u=253379"]jllangston[/URL] What distro are you using?

Kind regards

I use Fedora 14 x86_64 version with gnome gui.
I use this on a Intel core 2 duo PC with 2 gigs RAM. I also use the kmod nvidia driver for my Nvidia 9500 GT card.

I have a laptop (Acer aspire 5920 G) with the same system and it has never frozen once)

The first computer mentioned was working flawlessly with fedora 13 during 6 months until I upgraded it.
It might be a RAM failure but I don't think so. To many experience the same as I do.

---

### Post by jllangston on 2010-12-12
@Matt: I'm using Ubuntu 10.10.

Thanks for that link to the other thread... I have some reading to do now!

@all: Thanks for the replies, I'll post feedback as i can generate it!

---

### Post by MauserM98 on 2010-12-22
I tried to solve my problems with freezing with a Ubuntu 10.10 install. It managed to freeze 10 minutes after everything was installed.
So I went back to Fedora again 14. And now it works.
So what was wrong in my case.
I upgraded my system from F13 to F14 with a preupgrade command. It is not a recommended way of doing it. So a fresh install was my cure.
Ubuntu 10.10 looked nice but was not particularly fond of my hardware. It could not even read an IDE disk I had my backupfiles on (EXT4). It also started with an error message saying : HDA intel no codecs available. (Whatever that means).

So what did I learn?
1. Fresh install is the way to go in Fedora.
2. Ubuntu looks really nice.
3. Compiz is crap. (And not necessary)

---

### Post by totosmoto on 2010-12-27
Hello, 
I have the same problem the computer is freeing totally and only power off is working. It happens when i download something. First i was thinking, that it was because of the torent client, but when i started the update manager it froze again, so i think it happens when i download something. It is strange because i do not proerience this kind of problem in windows. I use Ubuntu 10.10 and my laptop is acer 3100, the kernel is 2.6.34

---

### Post by GuiGuy on 2010-12-27
All of this sounds similar to the problem I was having with my Toshiba NB200 after I upgraded to Ubuntu 10.10. [Details and solution here]("http://ubuntuforums.org/showthread.php?t=1653942").

---

### Post by totosmoto on 2010-12-28
Hello, again! Thanks for your answer! I have checked the BIOS, but it seems my BIOS is very poor. Here are ics from what i have in the BIOS. 
[http://dox.bg/files/dw?a=eaa0e7f856](http://dox.bg/files/dw?a=eaa0e7f856)
[http://dox.bg/files/dw?a=1397990bd6](http://dox.bg/files/dw?a=1397990bd6)
[http://dox.bg/files/dw?a=fce25d3aa2](http://dox.bg/files/dw?a=fce25d3aa2)
[http://dox.bg/files/dw?a=29386e358e](http://dox.bg/files/dw?a=29386e358e)
[http://dox.bg/files/dw?a=9e684de8a2](http://dox.bg/files/dw?a=9e684de8a2)
What do you suggest in this case?
Meanwhile i've succeeded to download the latest core and i will what will happen after installing it.

---

### Post by totosmoto on 2010-12-28
Nothing different with the new core, still it is freezing. Hope someone can help me about this!

---

