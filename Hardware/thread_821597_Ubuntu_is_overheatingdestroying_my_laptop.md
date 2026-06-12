---
title: "Ubuntu is overheating/destroying my laptop"
date: 2008-06-07
forum: Hardware
---

### Post by vitorgatti on 2008-06-07
Hi,

I have a Dell Inspiron 6000
**Intel Centrino, 1.6Ghz, 512MB DDR400, DVD-RW, ATI Radeon X300 64MB**

I don't know if this is a Linux, Ubuntu or even my Laptop's problem, but I will explain what's happening:

[B]There are 3 tests:
FIRST:[/B]
- Ubuntu **8.04** installed, proprietary drivers working/or not
- System is kinda slow
- I run the command **glxgears**
- CPU Temp goes up to 89°C
- After 5 minutes glxgears running, the Laptop **shutdowns itself**

**SECOND:**
- Ubuntu **7.10** installed, proprietary drivers working/or not
- System is a little faster than 8.04
- I run the command **glxgears**
- CPU Temp goes up to 89°C
- After 5 minutes glxgears running, the Laptop **freezes** and no button works (only force-shutdown)

**THIRD:**
- Installed **Windows XP SP3**, all correct drivers from Dell
- System is a little faster than 7.10
- I run the benchmark program **3DMark03**
- I run this programs 2, 3 times (A LOT of HEAVY graphic tests are made, much more than the simple glxgears)
- CPU Temp goes up to 75°C
- Laptop works normally, does not freeze or shutdown

WHATTA HECK IS THAT? :(
Any help I'll be grateful

Thanks

---

### Post by vitorgatti on 2008-06-07
nobody?
this Ubuntu Forum is so damn crowded
a lot of threads simply never gonna have an answer, because there is not enough time to people that know the solution to share the information, because all the topics goes down really fast

this is the fourth thread that I start in this forum that nobody answer nothing

:(

---

### Post by sergiom99 on 2008-06-07
> **vitorgatti said:**
> nobody?
this Ubuntu Forum is so damn crowded
a lot of threads simply never gonna have an answer, because there is not enough time to people that know the solution to share the information, because all the topics goes down really fast

this is the fourth thread that I start in this forum that nobody answer nothing

:(
Thats' right.
Sorry dude, no much I can tell you.
Try searching the forums for laptop power management and the stickys in this forum.
G'luck!

---

### Post by Unix_Slayer on 2008-06-07
Try a laptop cooler. It might not be the heat doing it, but it might be a start. It can only help.

---

### Post by cygnine on 2008-06-07
vitorgatti, I have a Thinkpad T60 with the same problem: my cpu and gpu temps are consistently around 70C, and get up to 90C very quickly if I do something even mildly computationally taxing (e.g. playing a Youtube video). The *lowest* cpu temp I've seen is about 60C. Of course, Windows XP (dual boot) has no such problems with high temps or with spontaneously locking down the system. I don't know how to fix this as frankly nobody seems to have the authoritative answer. Here's what I've heard should work, but mysteriously doesn't work for me:

1.) Changing the cpufreq governor: this tells the cpu how hard to compute relative to what the user is asking for. I've got mine set to 'ondemand', which means that the cpu runs fast when the computer asks it to. Another setting is 'conservative', which seems like it should be better, but I still get really high temps with this. If you want to read up on how to scale your cpu frequency, I guess you can start with:
[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/]("http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/")
[http://www.howtoforge.com/cpu_frequency_scaling_ubuntu]("http://www.howtoforge.com/cpu_frequency_scaling_ubuntu")
Those are the only two reasonable sources I can find at the moment. In any case, this doesn't work for me, no matter what frequency scaling governor I use.

2.) Change the temperature `trip points' for events (e.g. turning on the fan, system critical shutdown, etc.). It seems you've been bitten by the critical shutdown. Well, for example, I've got a dual core, and my trip points read:

```
*****@*****:~$ cat /proc/acpi/thermal_zone/*/trip_points
critical (S5):           127 C
critical (S5):           99 C
passive:                 95 C: tc1=5 tc2=4 tsp=600 devices=CPU0 CPU1 
```

Which (I think) means that my system will shut down if my CPU0 reaches 127C (!!!!), or if my CPU1 reaches 99C. Finally, the fan only turns on if CPU1 reaches 95C. Now it's my (perhaps naive) opinion that these are pretty silly trip points. I want my fan to come on much earlier. Now, I'd like to change these trip points, as maybe if the fan comes on around 80C then I won't get system lockups at 99C. There are a bunch of threads that talk about this. Just a couple are:
[http://ubuntuforums.org/showthread.php?t=379729]("http://ubuntuforums.org/showthread.php?t=379729")
[http://ubuntuforums.org/showthread.php?t=551829]("http://ubuntuforums.org/showthread.php?t=551829")
And one that I've already posted this problem in:
[http://ubuntuforums.org/showthread.php?t=813274]("http://ubuntuforums.org/showthread.php?t=813274")

Now I'm sorry but the bottom line is that I don't know how to change the trip points. Apparently you can do so with the shell `echo' command (check the last thread link above), but it doesn't seem to work (Hardy 8.04) and I don't know why. I don't mean to add to your list of things that doesn't work, but maybe one of the two things above will do the trick for you. 

Frankly, I don't seem to be able to rationalize how this is *not* an Ubuntu/Debian/Linux problem (despite the fact that dozens of antiWindows-proLinux-defenders will no doubt insist that I'm doing something wrong). The bottom line is that I did a fresh Hardy 8.04 install some weeks ago, and basic operations potentially damage my hardware and essentially crash my boot in Ubuntu, and the *very same* basic operations work just peachy in Windows. 

Please let us know if you are able to fix anything.

---

### Post by Unix_Slayer on 2008-06-07
> **cygnine said:**
> Please let us know if you are able to fix anything.

What CPU does it have? Intel, or AMD?

---

### Post by cygnine on 2008-06-07
> **Unix_Slayer said:**
> What CPU does it have? Intel, or AMD?

My cpu is a dual core Intel.

---

### Post by Unix_Slayer on 2008-06-07
> **cygnine said:**
> My cpu is a dual core Intel.

It's probably one of those Mobile step up CPU's. This would prove the problems you are having when being taxed.

---

### Post by overdrank on 2008-06-07
> **vitorgatti said:**
> nobody?
this Ubuntu Forum is so damn crowded
a lot of threads simply never gonna have an answer, because there is not enough time to people that know the solution to share the information, because all the topics goes down really fast

this is the fourth thread that I start in this forum that nobody answer nothing

:(

HI and I believe that your thread not having received a answer is maybe no one has that model of laptop or that issue.  It seems that you have been trouble shooting your issue, but for me to help I have to either have that model of laptop or a similar issue on my systems. There for you will have to wait for a answer for more than 5hrs.

---

### Post by Unix_Slayer on 2008-06-08
> **overdrank said:**
> HI and I believe that your thread not having received a answer is maybe no one has that model of laptop or that issue.  It seems that you have been trouble shooting your issue, but for me to help I have to either have that model of laptop or a similar issue on my systems. There for you will have to wait for a answer for more than 5hrs.

I do believe he said it was a Thinkpad T60.

---

### Post by Unix_Slayer on 2008-06-08
> **cygnine said:**
> My cpu is a dual core Intel.

I would Google your system, and see if there are any other people complaining with your issues. Could be a bad CPU, or a memory problem.

---

### Post by Unix_Slayer on 2008-06-08
Take a look at this website, and do a search on the page itself for Thinkpad T60.  ===>[http://www.madman2k.net/]("http://www.madman2k.net/")

---

### Post by woodcarver on 2008-06-08
I agree, that does sound alot like a bad CPU. I'd check and see if all of the fans are operating, including the CPU fan. They run very hot to start with, in a laptop the heat is amplified.

---

### Post by ardvark71 on 2008-06-08
> **cygnine said:**
> 
Frankly, I don't seem to be able to rationalize how this is *not* an Ubuntu/Debian/Linux problem (despite the fact that dozens of antiWindows-proLinux-defenders will no doubt insist that I'm doing something wrong). The bottom line is that I did a fresh Hardy 8.04 install some weeks ago, and basic operations potentially damage my hardware and essentially crash my boot in Ubuntu, and the *very same* basic operations work just peachy in Windows. 


You've hit it right on the button. I've seen threads concerning this very problem here before and I've maintained that it was not strictly a hardware issue, considering temperatures stayed normal using XP.

This *is* a software issue somehow, some way, with Linux/Ubuntu. Otherwise, you would be seeing it with Windows as well.

Regardless of how many systems if affects or doesn't affect, a number of systems *are* affected and I heartily encourage the developers to look into it and come up with a solution. Perhaps this would be something to file a bug report on....

Best Regards...

---

### Post by cygnine on 2008-06-08
> **Unix_Slayer said:**
> I would Google your system, and see if there are any other people complaining with your issues. Could be a bad CPU, or a memory problem.

Could be, but then why aren't there any problems in Windows? If it's a hardware malfunction, then I should see problems in Windows as well, no?

I've tried Googling the issue, but I'm not really sure what to look for other than "T60 Ubuntu overheating" or some other such variant. I haven't been able to find any solutions. And there's something I want to try (that has to do with controlling how the software controls the hardware trip points), but I can't get it to work, and the howto solutions posted online (in several different locations) just don't work as advertised at all on my machine.

[QUOTE=Unix_Slayer]Take a look at this website, and do a search on the page itself for Thinkpad T60. ===>[http://www.madman2k.net/](http://www.madman2k.net/)[/QUOTE]

The post on that blog deals with a.) Wireless issues and b.) Graphics problems. I have neither. It is also the case that my GPU is hot, but my CPUs still ramp up temperature when I do entirely non-graphical computations as well. 

[QUOTE=woodcarver]I agree, that does sound alot like a bad CPU. I'd check and see if all of the fans are operating, including the CPU fan. They run very hot to start with, in a laptop the heat is amplified.[/QUOTE]
Again, if it were a hardware problem, then why does Windows seem to have no problems with it whatsoever? My CPU fan is working according to some sensors called 'ibm-acpi'; it's running around 3300rpm right now, with my cpu temps at 73C and 75C, respectively. I have Firefox and Thunderbird open, I have compiz running, and I'm just typing this response to you. Doesn't seem too taxing to me; certainly shouldn't be 70C. From previous experiments, turning compiz off seems to save me around 2C or 3C per cpu.

Sorry vitorgatti, I didn't mean to hijack your thread.

---

### Post by mivo on 2008-06-08
> **woodcarver said:**
> I agree, that does sound alot like a bad CPU.

It doesn't sound like a bad CPU since he is not experiencing the same problem in Windows.

---

### Post by Unix_Slayer on 2008-06-08
> **cygnine said:**
> Could be, but then why aren't there any problems in Windows? If it's a hardware malfunction, then I should see problems in Windows as well, no?

I've tried Googling the issue, but I'm not really sure what to look for other than "T60 Ubuntu overheating" or some other such variant. I haven't been able to find any solutions. And there's something I want to try (that has to do with controlling how the software controls the hardware trip points), but I can't get it to work, and the howto solutions posted online (in several different locations) just don't work as advertised at all on my machine.

Do research on your CPU on Google. See, ....if it was an AMD, I would say there might be integer problems. I've had AMD's overheat on me, but never Intel's.



> **cygnine said:**
> The post on that blog deals with a.) Wireless issues and b.) Graphics problems. I have neither. It is also the case that my GPU is hot, but my CPUs still ramp up temperature when I do entirely non-graphical computations as well.

Your right. I skimmed over too fast.

---

### Post by jrusso2 on 2008-06-08
Talk to these guys there is a Linux section and they know everything about T-60 down to the smallest parts

[http://forum.thinkpads.com/](http://forum.thinkpads.com/)

---

### Post by Watchtow3r on 2008-06-13
Don't say it's a bad CPU, that's total ********. I have an HP dv2000 (completely different) and I have the same problem. And a simple Google search reveals a bunch of other people with the exact same problem. Vitorgatti, the easiest way I found to bring down the temp. is to install the cpu frequency scaling monitor, then enable root priveledges with it so you can use it to change your cpu speed just by clicking on it. It's much easier than using the terminal and having to remember a command whenever you need to adjust the cpu speed. There's a short tutorial on how to do it here:

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=771258&page=4](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=771258&page=4)

This is a HUGE problem in Ubuntu. It's actually because of this reason that I would not recommend Ubuntu to anyone with a laptop. Something that erases your software is one thing, but something that could actually fry your hardware is MUCH MUCH worse.

If this isn't fixed by 8.10, I think I'm going to give up on Ubuntu.

---

### Post by AFarris01 on 2008-06-17
Ive got the very same problem with my laptop, a Toshiba Satellite P105-S9312.  I have it set up dual-booting XP, and ubuntu 8.04, and in addition to not being able to get sound up and running on there (it worked in 7.10) i also began experiencing this problem. I know its a fan control issue, because normally when im in windows, the fan is at a fairly audible level if im not using my cooling pad, and if i use the thing for a while, or start gaming on it, the fan speed ramps up considerably.  however, in ubuntu, the fan runs much more slowly, and does not ever ramp up even after extended use.  I first got clued into this problem when i was playing an interesting little game about a mexican cowboy killing aliens with a knife to get his abducted cow back (i dont remember the name, but its in the repos, and its great), when i started getting horrid tearing effects.  after this i touched the bottom of the laptop and nearly burned myself.  i checked the external temp with a thermal gauge, and it read 105F...not good.  its not really an issue when i use my cooling pad, but i rarely use the lappy anyway, but it is something id love to see fixed

---

### Post by durfff on 2008-06-19
I'm going to add to the count, in a slightly different but I believe related way...

I have an IBM T43, dual boot Ubuntu and XP SP2. Windows still has no problem, quiet fan and reasonable temperature (I've not checked temps in XP exactly but the laptop stays pretty cool), but I get onto Ubuntu (even after cold start), and the fan starts kicking in halfway through the Ubuntu splash and doesn't stop after that, with the laptop getting fairly hot underneath.

Now I'm not saying this is NOT hardware related (it some way it is for it only seems to be a laptop issue - desktop users with a similar problem?) but everything and everyone seem to point to something software-related!

At the moment I don't seem to have too much of a problem with temps, but the fan noise is starting to do my head in.

It could definitely do with getting some attention from developers - if windows can do it surely buntu can hack an even better version of automatic - and consistent - cpu scaling / fan control! It's one of them things that's still in the "google-it-terminal-to-****-and-after-a-week-it-finally-kinda-works"

damn, it doesn't

I've followed a few guides out there (some links earlier in this thread, if not I can relist them let me know) but no luck, my thinkpad fan is still always on, churning away that horrible grinding.

Let's hope this thread gets some attention!

---

### Post by mivo on 2008-06-19
I'll add, though, that my Dell 8500 laptop does not have this issue (well, not in Xubuntu anyway), so it does not affect all laptops. I have no doubt that it is software-related, though.

On my old desktop I had a similar problem with an ATI X700 and Linux. If I used the restricted drivers, the fan would always spin at 100%, and it was very loud and getting very hot. In Windows that happened only when I played heavily 3D games. That experience was one of the main reasons why I went with an Nvidia card when I got a new main desktop.

Actually, perhaps the problem here **is** the restricted ATI driver. Have you tried the open source one?

---

### Post by durfff on 2008-06-22
Thanks for the advice - I've just switched the driver to the open source (which seems to work just fine), but the fan noise is still here - even though the CPU temp has dropped from 58 to 47... Maybe the fan will stop spinning on a cold reboot... I'll give that a go later. But I'm now getting a bit worried that I'm somehow slightly damaging my laptop - I'm sure the fan won't get much life if it's spinning so high all the time!

So for now I'll have to go back to XP until I can find a proper solution... A shame, but then again I've got some Flash development to do...

---

### Post by emu on 2008-06-22
hi, I'm having the same problem with my thinkpad T43 - it's heating up to around 122F and the fan is always spinning.  it's getting so hot that even the touchpad feels warm.  I am not using the restricted ATI driver.  I hope this problem gets some attention - I'd hate for my laptop to burn out sooner than it has to.

---

### Post by medic8ted on 2008-06-22
Dell Latitude D510 dual boot XP and Hardy with same problem, cool or warm with XP and HOT with Ubuntu.  I'm not a gamer, so just FF and T-bird with Compiz heats it up so its hot to touch the bottom.  My temp sensors have never worked right even with Gutsy, so I have no idea how hot I'm even getting, but hot enough to make the graphics goofy and slow down page load times.

---

### Post by diamond7 on 2008-06-24
im running an acer aspire 5100 with hardy 8.04 "ultimate" distro.. i first throught it was a glitch of some sort because my laptop just randomly shut down, black screen... "running all boot scripts" and restarted.. then when it did the same thing.. and shut down.. and i turned it back on, and then it shut down again.. 3 times.. i notices my keyboard was extremly hot... i have scaled my cpu down to 2Ghz from 2.2.. i am also looking into different versions of linux to run besides ubuntu.. i am pretty new to linux as a whole and chose ubuntu so that things would be easier to learn.. but i dont want to blow up my laptop.. yet.. any suguestions anybody?

---

### Post by waapwoop1 on 2008-06-24
I have Ubuntu installed on my P4-m compaq laptop. I have an identical laptop with XP home running that my colleague uses who sits next to me. 

I have setup a lot of power saving features on mine and it still runs hotter. my HDD sits on 56 degrees C and cpu now sits at 45 degrees, however this is running at half power or 1.2Ghz. When i need to actually use the laptop, it runs at 2.2ghz, and the HDD gets to 67 degrees and the cpu goes to 70 degrees, i've seen it go to 90 before.

I had a look at the xp home machine, same spec, and its cooler running at 2.2ghz than mine is at 1.2ghz.

I previously had XP home on this machine with no noticeable heat, but switched to Ubuntu to see what it is like. I will keep Ubuntu, and i have had to buy a laptop heat tray thingy just in case i ruin my laptop.


I think with so many people complaining about this issue, there must be a problem. We can't all have bad cpus that seem to run fine under XP.

---

### Post by durfff on 2008-06-25
Well my situation now seems to veer away from this thread: my T43 just started making this fan-always-on-full-blast noise in windows too. Looks like it could be a hardware problem for me after all...

Weird thing though:my battery was getting old, so I got a new one thinking that maybe the power features were not working that well. But before I changed I looked in the BIOS and fiddled a bit with power settings. Now the lappy runs at about 47 but the fan seems to always be on, both in ubuntu and xp.

Weird.

---

### Post by Shanghai on 2008-06-25
I have the same on my Dell Inspiron XPS2. Seems to be the latest kernels above 2.24.16. I even had my laptop shutting down because of overheated GPU.
I'm now trying SUSE 11 (2.6.25.5) don't want to fry my Graphics card.
By the way it's been reported on other posts here in the forum as well so it seems to be a common problem have also seen posts in the linuxoutlaws forum.

---

### Post by mivo on 2008-06-25
> **Shanghai said:**
> I'm now trying SUSE 11 (2.6.25.5) don't want to fry my Graphics card.

Did this help the problem? My laptop's fine, but it would be good to isolate the possible cause.

---

### Post by Shanghai on 2008-06-26
Still running hot compared to Win XP 10-20C difference. It has not shut down on me yet though. I suspect the Kernel not the distro. Seems like Fab from the Linux Outlaws podcast thinks it's a problem with the newer Kernels he posted that on their forum. On 2.24.16 he's laptop is running cooler.
Would be nice to have it sorted out why should it run hotter than on XP?

---

### Post by jay019 on 2008-08-08
Its definately a problem with the newer versions of Ubuntu or the Kernel. I had no problems at all when using 7.04, after upgrading to 8.04 fan goes on at a higher temp and never switches off.

---

### Post by mobius357 on 2008-08-08
> **diamond7 said:**
> im running an acer aspire 5100 with hardy 8.04 "ultimate" distro.. i first throught it was a glitch of some sort because my laptop just randomly shut down, black screen... "running all boot scripts" and restarted.. then when it did the same thing.. and shut down.. and i turned it back on, and then it shut down again.. 3 times.. i notices my keyboard was extremly hot... i have scaled my cpu down to 2Ghz from 2.2.. i am also looking into different versions of linux to run besides ubuntu.. i am pretty new to linux as a whole and chose ubuntu so that things would be easier to learn.. but i dont want to blow up my laptop.. yet.. any suguestions anybody?

The fans on acers are SOFTWARE controlled. It's part of the acer "empowering software" My girlfriend had the same problem on hers. I'm afraid its Vista or nothing, the software won't even run on XP.

---

### Post by linux_tech on 2008-08-08
For overheating issues, beyond normal cleaning, a number of possible hw and sw solutions exist. Variables include make, model, cpu, os, bios, etc. On HW side, fan shrouds, new heatsinks, faster multi-spd fans, new firmware are possible solutions

 Regulating the speed of the fan is often a good way to keep the temp down, some of the fan software allows you to turn the fan on high or low spd, regulate what temperature it turns on, what temp it turns off, and includes a monitor to visually monitor the cpu temp.  Sometimes a simple bios update will help, other times a software util or daemon can help with the fan, if you think the fan is the cause. I've found a number of good programs for this.  

Overclocking can sometimes cause overheating, but many of the newer 
multi core cpus also tend to run hotter, for laptops this is more of an issue.

Lowering cpu voltage is another option if regulating the fan does not help.
Bios can sometimes have a way to adjust this, best to consult a service manual or check on this with support from manufacturer.
 
Modifying the kernal is another possibility. It seems some of the earlier Kernal versions had less issues with overheating.  If one has the time there are cpu settings that can be modified, additional kernal modules that can be installed  or the easiest way here is just to revert to an earlier version of the kernal.

Hopefully this will be improved with the next release. Maximizing efficiency and improving Kernal utilization of the many core cpus should be on the top of the list for developers. 

It would also help for the next release to either have some daemons that can be started or software that can be installed that will allow you to adjust fan speed as well as force it on at a certain temp and shut the fan off at a higher temp.  It would also be nice if the put a little cpu temp "gadget" that was part of the desktop for easy monitoring.

Using a good cooling pad with 3 or more fans built in, running on ac 
power can also help keep a laptop cool, especially if your using it 8 hours per day.

---

### Post by hackeye on 2008-08-08
Another addition to the long list of affected systems. I have an acer aspire 5920 with a core-2 duo proc running Hardy. I have it dual-booting with Vista.

I hardly do anything remotely resource-intensive on it - maybe a few browser tabs, jabber client, terminals with SSH sessions etc. When running ubuntu it gets so hot that i can't keep it on my lap for more than 15-20 minutes when running on battery power. Even the top of the thing where i rest my hands next to the touchpad while typing becomes incredibly hot. I've not had it shut down on me though. It seems to be slightly better on AC power.

I was wondering its a hardware issue, till i tried a similar usage with Vista, which has no heating problems whatsoever.

The strange thing is that a colleague of mine thas a Dell Inspiron (can't recall exact model, maybe 1525) which is also running Hardy without any heating problems.

I can just see questions on this post. Any answers? :-(

Ubuntu is otherwise a brilliant OS which can replace Windows in almost everything. But much as i hate it, i might have to go to Vista if ubuntu is gonna fry my 1 and only precious lappy!

- cheers,
hackeye

---

### Post by ibuclaw on 2008-08-08
[http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

Me and Vor are power saving mad when it comes to our laptops. (Vor is trying to get his to drop to 10W when idle).

There are lots of tricks from removing unused modules to setting all PCI buses to drop into idle mode quicker...
Another one is tmpfs'ing the firefox temp folder because it fsyncs() to the hard-drive everytime you browse a page causing no end of hard-drive activity...

There are some really good tips around. You just need to look for them.

Oh and think about what you are doing before you post on a dead thread...

Regards
Iain

---

### Post by hackeye on 2008-08-15
Thanks a lot for the tips. It should definitely guide me towards something useful.

> **tinivole said:**
> 
Oh and think about what you are doing before you post on a dead thread...


Well, i'm sorry, I'm a newbie to the ubuntu forums. But do you think i would have posted if i knew the thread was "dead"? Even now, a good few days after your reply, the page shows my post as well as 2-3 posts before mine all marked "6 days ago". Unless there's some other kind of timestamp which i'm overlooking, don't you think it's something for the forum admins to consider *why* it isn't obvious to a newbie that a thread is dead? And how exactly is "dead" quantified anyway?

- cheers

---

### Post by Barlennan on 2008-11-08
cygnine and ardvark71 are right - it's a software issue, and furthermore it's persisted in Ubuntu since at least Feisty.  My eMachines M2350 laptop shuts down once a day or so after reporting ridiculous temperatures like 159 C.  I don't think it's nearly that hot.  I reported it in [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/213818](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/213818)

[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/264069](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/264069) is probably even more relevant.

---

### Post by edgaruy1980 on 2008-11-09
I have a lenovo and I used to have Windows Vista Home premiun with aero and I did not have overheating but after switching to Ubuntu 804 and 810, I have the same problem, even couple times the Bios execute the critical shutdown for high temperature.
I tried to fixed adding the lib 686 and microcode.tpl and cpudyn, drivers for cpus, you could find them using Synaptic installer, just search cpu/processor.
They help a little, at least I'm not going critical :o
I hope they address this issue in the next realese because the 8.10 is just the same...

---

### Post by ranran on 2008-11-18
install i8kutils & gkrellm - regulates fan speeds just fine.

Also, for nvidia drives, they automatically push "performance" out of the video card (max mem/core speeds) compared to Windows which defaults to the lowest settings (and thus lower temperatures).  That can be changed in the Nvidia X server settings Powermizer settings.

---

### Post by kcleong on 2008-11-26
Adding to the long list, a HP Compaq NC8430 with a core2duo. The excessive heat is causing lock-ups. Most of the time at the end of the workday combined with cpu intensive tasks.

I'm experiencing this problem since the last two Ubuntu releases, prior and on Ubuntu 7.x I had less problems. When I'll find some spare time I'll try underclocking with PHC..

---

### Post by Barlennan on 2008-11-26
Try uninstalling powersaved and installing powernowd.  That stopped the random shutdowns on my k7 laptop, but did not make the CPU temperature reporting any more accurate.  The fan and CPU freq scaling are working more or less as they were before.

---

### Post by iponeverything on 2008-11-27
Here is a recently opened bug report on Launchpad. Everyone with this issue should add there comment to this bug report to help raise its profile and help the developers understand the scope of the problem.


[https://bugs.launchpad.net/ubuntu/+bug/296056](https://bugs.launchpad.net/ubuntu/+bug/296056)

---

### Post by rezaghp on 2008-12-11
I also have a little bit of heat under left palm rest of my Lenovo SL300 (T9400 2.5GHz) in Ubuntu. The heat is much less in Windows Vista.

---

### Post by kcleong on 2008-12-16
Another bug report related to overheating: 

[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/107937](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/107937)

---

### Post by dreamtrove on 2008-12-16
Newbie question
I have a similar problem. My Dell XPS M140 with SSD I just installed ubuntu 8.10 and now the fan runs all the time, which it didn't on windows xp. I need to either raise the fan trip point or lower the temperature by removing unnecessary background activity like TSRs etc. Powertop suggests the main CPU drain is coming from USB-related interrupts, nothing connected. Also, the trips appear to be on at 55 and off at 47. Any ideas?
Lemme know. Thanks.

---

### Post by kcleong on 2008-12-18
I believe that for a Dell laptop you can use a tool to control the fans. Try googling for it. You can change trip point like this: ```
echo "83:83:60:70:0" > /proc/acpi/thermal_zone/THRM/trip_points
``` (as root).

---

### Post by mplexus on 2008-12-19
I am also having thermal issues (overheating due to not scaling down for some seconds from max frequency to give cpu a chance to lower its temperature).

I have ACER 1524 (ubuntu 8.10)

I didn't do a thorough test but I tried setting options to thermal module.

Editted my /etc/modprobe.d/options and added the following line:

options thermal tzp=30 act=0 crt=0 psv=0
(tzp=30 means 3 seconds of polling)

( [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/22336/comments/264](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/22336/comments/264) )

Will see how it's going in the following days but for now it works fine: when cpu load reaches 99% it scales up to max frequency (on-demand governor) and when temp reaches 90 degrees it scales down one frequency for a few seconds - it is enough for temp to drop down to 70 degrees. Then, it scales up again to max freq to cope with heavy cpu load. Again, when temp reaches 90 degrees it scales down again for a few seconds and so on.

I tested with command yes | sha1sum and it actually DID NOT SHUT DOWN!

I hope my problem is fixed - we'll see...

---

### Post by kcleong on 2008-12-20
I solved the overheating by disassembling my laptop and cleaning out the dust...

---

### Post by m4u on 2009-01-06
My Laptop is an Acer Aspire 5720z (Ubuntu 8.10 64 bits) and the internal fan stops working during boot time causing overheating and shutting down. 

If I re-start the computer again, the fan remains stopping during boot.

I know a workaround for this problem: first I installed gkrellm and lm-sensors. Then, while monitoring the CPU temp, when it got to 75 degrees  Celsius I restarted the computer and the fan "magically" started during boot.

It seems that the CPU needs to get to 75 C for the kernel to recognize that it needs internal fan working.

It worked for me several times (no need to buy those external laptop fans).

---

### Post by m4u on 2009-01-19
Just to notice that after the boot (and the fan stars working), you can suspend the computer normally (the fan stops but then, when back from suspend, it starts again).

---

### Post by m4u on 2009-01-23
SOLVED! Just updated my bios to 1.42 (see [http://support.acer-euro.com/drivers/notebook/as_5720.html](http://support.acer-euro.com/drivers/notebook/as_5720.html))

Fans work, acpi now 'sees' the real temperature of the cpus.

---

### Post by richard.e.morton on 2009-06-08
Hi Everyone, I am still seeing this with Jaunty... 9.04 

I have a Lenovo Thinkpad T60. Whenever I run a mildly taxing operation; flash; javascript; video the system overheats and if I dont catch it soon enough (especially with videos) the system overheats and auto-shuts down.

Has anyone made progress with this?

Thanks

Richard

---

### Post by SynthesizersFTW on 2009-06-09
IBM ThinkPad t42p here, same as Richard, 9.04 causes rapid heat buildup to the point that it the CPU/GPU fan gave up the ghost (I just installed a new one from IBM Canada and I am just about ready to reinstall XP rather than risk blowing the whole thing up entirely).

The heating is noticeable after just a few minutes of doing some pretty routine things (like Update Manager!).  AFAIK the BIOS is the latest one available from IBM.

EDIT: I added the frequency scaling monitor to Gnome-panel - EGADS!  Pentium M 2.0GHz was cranked up to full 2.0GHz clock, all the time, by default!!!  This needs a *serious* launchpad entry if it is the root cause of the overheating in Jaunty.  I doubt sincerely that this is the intended behavior for laptops (especially with notoriously bad cooling to begin with).

---

### Post by ashwinhgtx on 2009-07-01
Why is this happening? Even my laptop is being fried by Ubuntu.
Intel Core Duo 1.66GHz, IBM R60.

---

### Post by RJARRRPCGP on 2009-07-01
> **vitorgatti said:**
> Hi,

I have a Dell Inspiron 6000
**Intel Centrino, 1.6Ghz, 512MB DDR400, DVD-RW, ATI Radeon X300 64MB**

I don't know if this is a Linux, Ubuntu or even my Laptop's problem, but I will explain what's happening:

[B]There are 3 tests:
FIRST:[/B]
- Ubuntu **8.04** installed, proprietary drivers working/or not
- System is kinda slow
- I run the command **glxgears**
- CPU Temp goes up to 89°C
- After 5 minutes glxgears running, the Laptop **shutdowns itself**

**SECOND:**
- Ubuntu **7.10** installed, proprietary drivers working/or not
- System is a little faster than 8.04
- I run the command **glxgears**
- CPU Temp goes up to 89°C
- After 5 minutes glxgears running, the Laptop **freezes** and no button works (only force-shutdown)

**THIRD:**
- Installed **Windows XP SP3**, all correct drivers from Dell
- System is a little faster than 7.10
- I run the benchmark program **3DMark03**
- I run this programs 2, 3 times (A LOT of HEAVY graphic tests are made, much more than the simple glxgears)
- CPU Temp goes up to 75°C
- Laptop works normally, does not freeze or shutdown

WHATTA HECK IS THAT? :(
Any help I'll be grateful

Thanks

The temps are still horrible when under XP.

Sounds like the heatsink and fan needs to be checked.

---

### Post by ianmillington on 2009-07-02
On my Dell Inspiron 630m the temp stays between 46 and 50. I have the power settings to "dynamic". I can see the CPU speed rise when an application is launched but then slow down when it's fully running. I am using KDE however. Is such a setting available in gnome?

---

### Post by kabloink on 2009-07-02
> **ianmillington said:**
> On my Dell Inspiron 630m the temp stays between 46 and 50. I have the power settings to "dynamic". I can see the CPU speed rise when an application is launched but then slow down when it's fully running. I am using KDE however. Is such a setting available in gnome?


Yes, in Gnome you add the cpu scaling frequency monitor to the panel. Which will allow you to set the cpu governor. The dynamic setting would be "ondemand".

---

### Post by letsflyakite on 2009-07-12
I had the same issue in my thinkpad T61, with Ubuntu 9.04 fresh install. The fan is horning non-stop while the part under my right hand palm just gets so hot it's physically uncomfortable to operate let alone enjoy anything "magic" about Ubuntu. This is my first Linux experience and it's not been good. As much as I wanted to step into the Linux world I didn't want my laptop to be burnt! 

Anyway I have removed Ubuntu completely out of hard drive and only runs it in VMWare now. Is there any one running other Distro of Linux, such as **Mandravia or openSUSE**, and I wonder if they will overheat the laptop too?

Any info will be gratefully received. If Mandravia or openSUSE does not overheat the laptop then I can consider to install Linux again on the hard drive.

Many thanks!

---

### Post by DeathByLinux on 2009-08-09
Like many other laptop users, I also suffer from this overheating issue. I am going to take a more philosophical approach to the matter. I think the problem lies in the software and hardware. I have come to this conclusion based on the fact that ATI, and other manufacturers, does not provide much support for linux based operating systems. I think if you look at the facts, it becomes clear as to why they would not "waste" time and resources on an operating system that has just over 4% of the market. 
When manufacturers like Intel, AMD, Dell, Acer, HP and ATI make their products, their main concern is to make sure that their product works well under a windows operating system. This is perfectly logical, if you are looking to make a profit. Due to this, I think that hardware that would normally work well in windows MAY not work well in Ubuntu. 
There, I have provided no real solution, but simply made the problem seem even more intimidating! My work here is done.

---

### Post by orawax on 2010-02-03
ThinkPad users may find help for some overheating / fan control issues from [_ThinkPad Fan Control_](http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control) software. ([_PPA for Karmic_](https://launchpad.net/~tp-fan/+archive/ppa))

---

### Post by madhat1 on 2011-01-28
I've got the same problem on my HP dv5000 laptop on both Ubuntu 10.10 and Windows 7.
Looking at ubuntu's syslog after a shutdown it states that CPU1 crossed its thermal trip point (99C).
Win7 doesnt say why its shutting down in the log, but i'm guessing its the same reason - temperature.
My laptop is 4 years old, the fan is not spinning as it used to and perhaps the thermal paste between the CPU and the heatsink needs refreshing...

I'll perform these maintenance steps and update.

---

### Post by Anoroc on 2011-02-04
> **madhat1 said:**
> I've got the same problem on my HP dv5000 laptop on both Ubuntu 10.10 and Windows 7.
Looking at ubuntu's syslog after a shutdown it states that CPU1 crossed its thermal trip point (99C).
Win7 doesnt say why its shutting down in the log, but i'm guessing its the same reason - temperature.
My laptop is 4 years old, the fan is not spinning as it used to and perhaps the thermal paste between the CPU and the heatsink needs refreshing...
 
I'll perform these maintenance steps and update.
 
You might want to take a vacuum to the fan to try and clean it up and maybe remove any dust bunnies hindering the air flow. Use an anti-static vacuum if you can. Also, use a toothpick or something thin and non-metallic to keep the fan from spinning while using the vacuum - don't want to overspin the fan. Using canned air can push stuff furhter inside, so that's why I recommend using a vacuum.
 
I don't know the dv5000 series, but if it has easy access to the fan via a cover then all the better. My friends Acer had easy access and I removed a quater sized dust ball that was blocking air flow. Myself, I have several pets and their hair wreaks havoc on my laptops - I can always tell when I need to do a cleaning because the fan runs harder when it's just sitting there.
 
--Anoroc

---

### Post by naptime on 2011-02-12
I have used Ubuntu for several years now and started noticing a lot of heat generated on my T42p laptop at least a year ago.  Recently the fan quit working and I replaced it.  After installing the new fan the laptop still generated a lot of heat.  I decided to measure the heat with cat /proc/acpi/ibm/thermal in a terminal and discovered my CPU ran consistently 85-90 deg C.  After reading a few threads on this problem I found that Mandriva runs cooler on Thinkpads.  I tested with some live CD versions and verified this.  I have now switched to PCLinuxOS (a Mandriva derivative).  My CPU temp now runs 55-60 deg C most of the time, with occasional excursions to 70 deg C.  

I suspect, but can't prove, that Ubuntu caused my fan to wear out prematurely.  Regardless, running 20 to 30 deg C cooler should definitely result in a longer life for my laptop.  I must say that I prefer Ubuntu in general, but will have to go with something else until I read of a fix I can use in Ubuntu.

---

### Post by madhat1 on 2011-02-15
> **Anoroc said:**
> You might want to take a vacuum to the fan to try and clean it up and maybe remove any dust bunnies hindering the air flow. Use an anti-static vacuum if you can. Also, use a toothpick or something thin and non-metallic to keep the fan from spinning while using the vacuum - don't want to overspin the fan. Using canned air can push stuff furhter inside, so that's why I recommend using a vacuum.
 
I don't know the dv5000 series, but if it has easy access to the fan via a cover then all the better. My friends Acer had easy access and I removed a quater sized dust ball that was blocking air flow. Myself, I have several pets and their hair wreaks havoc on my laptops - I can always tell when I need to do a cleaning because the fan runs harder when it's just sitting there.
 
--Anoroc

Took my laptop apart and turns out that there was a huge amount of dust blocking the exit path of the air.
Cleaned it with an air pressure dog and replaced the thermal stickers and THE TEMP DOESN'T GO ABOVE 60C NOW!!!

The reason that the machine shutdown before is because it reached 100C during heavy load... 

Bottom line: it's not the OS's fault it's the cooling mechanism!

---

### Post by e2hsan on 2011-09-28
i have the same issue for my Dell studio 15 laptop, works perfect on windows but reaches 93 in 5 min when loading ubuntu.

---

### Post by naptime on 2011-09-30
I have an update on this problem as I have installed Ubuntu 11.04 and this problem has gone away for me.  My laptop has never run cooler.  Thanks Ubuntu.

> **naptime said:**
> I have used Ubuntu for several years now and started noticing a lot of heat generated on my T42p laptop at least a year ago.  Recently the fan quit working and I replaced it.  After installing the new fan the laptop still generated a lot of heat.  I decided to measure the heat with cat /proc/acpi/ibm/thermal in a terminal and discovered my CPU ran consistently 85-90 deg C.  After reading a few threads on this problem I found that Mandriva runs cooler on Thinkpads.  I tested with some live CD versions and verified this.  I have now switched to PCLinuxOS (a Mandriva derivative).  My CPU temp now runs 55-60 deg C most of the time, with occasional excursions to 70 deg C.  

I suspect, but can't prove, that Ubuntu caused my fan to wear out prematurely.  Regardless, running 20 to 30 deg C cooler should definitely result in a longer life for my laptop.  I must say that I prefer Ubuntu in general, but will have to go with something else until I read of a fix I can use in Ubuntu.

---

