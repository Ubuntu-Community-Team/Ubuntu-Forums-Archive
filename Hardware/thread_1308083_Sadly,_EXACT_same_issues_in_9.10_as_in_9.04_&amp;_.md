---
title: "Sadly, EXACT same issues in 9.10 as in 9.04 &amp; 8.10"
date: 2009-10-31
forum: Hardware
---

### Post by CylnZ on 2009-10-31
[FONT=Georgia]Well, after high hopes that maybe [/FONT]this release something worthwhile may have been fixed in addition to (imo) worthless eyecandy being added, it seems I'm back in the same exact place as ever on a new version install.

[COLOR=DarkRed]**_Gateway 6860FX laptop._**[/COLOR]

1. **still no sound**. However this time around, instead of mis-configuring the hardware so it failed, 9.10 doesn't even recognize there is any sound at all. [HDA Intel]

2. **overheating already**. Thankfully, I was already prepared for this inexcusable failure on any operating system's part by having a couple of desk fans ready to do the job that Linux apparently isn't capable of doing (simply turning on the fans) [Intel 965pm]

3. **nvidia**. A little more pathetic this time. Doesn't even know it exists. Sees an 8800gts chip as generic video. At least 9.04 saw it. The performance was crap until the 190 drivers 2 or 3 months after release, but at least we could point at nvidia and shout "Closed source!" Not so this time, it's just a 9.10 failure. [Nvidia 8800GTS]

[COLOR=DarkGreen]_**Acer 5620 laptop**_[/COLOR].

1. **[COLOR=Black]overheating[/COLOR]**. Same problem different series chip, Intel 865. At least we're consistent

2. **wireless**. Works (sort of) slowly, if I delete and manually create a new network connection on each and every reboot, at least for a while, then it craps out randomly, and can only be reconnected by repeating the reboot process steps. [IWL3945]

3. **video performance**. Much better off the bat than 9.04, Still crap. It has better performance in windows ME using the Intel 845 drivers than it does on a brand new 9.10 install. Both are still a pathetic regression from 8.10 in performance. [Intel 865]

Fortunately, I have as good a fixes (I hope) as in 9.04. Custom DSDT files for both systems, manually installed drivers for nvidia, trashing the network manager in favor of the ancient wifi connector, following the hda intel audio fix guide, grabbing whatever fixes come out immediately etc.

What's the point of this whining, you ask? 

In 9.10, Ubuntu made me boot faster into a system that I have to spend 10 minutes redoing to get network, dont have sound in, and cant stand to look at. There's a nifty, useless, app store like an i-phone that I, cant get to, cant hear, and looks like crap with my default setup. 9.10 offers cloud services. Who cares? I cant install 9.04 or 9.10 in 4 labs with 28 systems a piece, and 32 classrooms with 6 systems each and 40 support staff systems because 80% of the systems are Dell and (you guessed it Intel 865 or 945) will overheat, have Intel onboard video and Intel HDA audio. The administrators have nvidia/intel laptops. Do you think I could care less about cloud computing? or app stores? or boot times? 

How can I promote and move our inner city school over to Linux, which, in theory, is better in every way and I enjoy and can get behind, if I have to spend ridiculous, inordinate time reconfiguring systems with issues1, 2 or more years old?

Once I get the bloody things ripped apart and manually reconfigured they work pretty good, at least the 6860 does. Except for the re-occuring audio loss, and the unpardonable heat issues. I am happy to guarantee you that my boss would fire me, and trash Linux in our school forever after experiencing these issues for about 2 days.

If you cant make a deployable system for people who want to go your way and support you, in favor of a slightly faster boot time, an app store that will be lacked out from 99% of the users, and cloud computing services rendered worse than useless by inability to maintain connection and a laughable $150 per system cost.

And this is just a k-8 school. Certainly non-critical. If Ubuntu cant be deployed here for these reasons, why would anyone, anywhere, think it would be deployed in in money making business? It's not as if we were talking about tiny vendor hardware on seriously outdated systems. It's Intel and Nvidia xp hardware for goodness sake.

Here's a tip for Ubuntu 10. Skip the froo-froo crap, dump the foolish cloud computing, save the app store for later, and

[COLOR=Red]**FIX THE LONG-STANDING BUGS/ERRORS/FAILURES**[/COLOR]

that fill these forums every day, year after year, with little notice or success by the developers working on things no user gives a damn about since the platform doesnt provide working, consistent computing basics like Heat Management, Audio-Video & Connectivity on major, widespread mass hardware.

Well, it's time to start over, and go through a week of needless tear downs and fixes to get a working system worth using, cya :wave:
___________________________________________

Here's my links to threads that have helped fix these things. Maybe mod or insider can pass them on to the Ubuntu developers so users get a usable OS in version 10.

sound:
[Jaunty 9.04 Sound Solutions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1130384&highlight=6860fx") 
[[ubuntu] snd-hda-intel sound - Ubuntu 64bit - Jaunty - It worked! - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1140667&highlight=6860+fx") 
[[ubuntu] snd_hda_intel options database - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1043568") 
[ALSA Upgrade Script - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1046137&highlight=remove+pulse") 

video:
[HOWTO: Jaunty Intel Graphics Performance Guide - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1130582&highlight=1136738") 
[HowTo: NViDIA Drivers]("http://ubuntuforums.org/showthread.php?t=1125400&highlight=HOWTO%3A+nvidia") 

heat:
[HOWTO Fix A Buggy DSDT File - Page 2 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=7340745#post7340745") 
[[ubuntu] Laptop getting very hot after jaunty upgrade - Page 4 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1129135&highlight=dsdt&page=4") 

networking:
[How To: Manual Network Configuration without the need for Network Manager - Page 89 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=571188&highlight=ping+local+network&page=89") 
[HOWTO: NFS Server/Client - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=249889") 
[[ubuntu] Updated connecting to windows network shares fix 9.04 - Page 3 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1135842&highlight=ping+ubuntu&page=3") 

overall:
[The Perfect Desktop - Ubuntu 9.04 (Jaunty Jackalope) | HowtoForge - Linux Howtos and Tutorials]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04") 
[Comprehensive Multimedia & Video Howto - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=766683") 
[Howto: Add custom color to directory listings. - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=7479161#post7479161") 

If you have a 865 Intel laptop, hopefully these links will help you out. Hopefully, they'll still work on 9.10 instead of 9.04. Hopefully, Ubuntu, and the Linux community developers, as a whole, will postpone the services users would enjoy in the future, just as soon as their base systems function at at least microsoft levels. Then, we'll be happy to enjoy the fluff. Because that's just exactly what boot times, login screens, app stores and cloud services are.

Fluff.

---

### Post by detroit/zero on 2009-10-31
> **CylnZ said:**
> Here's a tip for Ubuntu 10. Skip the froo-froo crap, dump the foolish cloud computing, save the app store for later, and

[COLOR=Red]**FIX THE LONG-STANDING BUGS/ERRORS/FAILURES**[/COLOR]

that fill these forums every day, year after year, with little notice or success by the developers working on things no user gives a damn about since the platform doesnt provide working, consistent computing basics like Heat Management, Audio-Video & Connectivity on major, widespread mass hardware.
Amen, brother!

I put off switching to Jaunty after reading all the horror stories. Luckily, by the time I did switch, fixes were established and well-documented. 

I won't say I regret switching to Karmic as soon as it appeared, but waiting a couple months might have been a better way to go. I fail to understand why the Intel drivers are still pure suck in this release - I thought Intel was all open-source and all that.

Anyhow, thanks for the links. I'll be giving some of them a go to see what I can fix and what I can't.

Be warned: From everything I've read, PulseAudio won't be as easy to ditch this time around. I guess the proof is in the doing, though.

---

### Post by wishdale on 2009-11-09
I'm on a Dell XPS1330 and i also still have these heat issues.

The main issue though seem to be the WIFI card generating tremendous amounts of heat.
Putting my finger on the touchpad gives me a burning sensation and the only thing beneath the touchpad is the WIFI card.

After reading around many people seem to have reported this and the cause might be the Power manager has been turned off lately.
Using iwconfig one can see that the power manager is turned off and it is not possible to turn it on again.

I think there are newer drivers out where the power manager is available again but i don't know how to install them.
It can be read here: [http://intellinuxwireless.org](http://intellinuxwireless.org)

My WIFI card is: [B]Intel® Wireless WiFi Link 4965AGN
[/B]Running: Xubuntu 9.10.

I hope this helps finding the problem.

---

### Post by CylnZ on 2009-11-23
Oh, I know what the problem is with the intel 865 series of chipsets, it's called QST which is Intels way of making you buy a new system just about the time your warranty runs out. See, the chipset has a new "feature", QST, which controls all your thermal controls, active and passive, and it wont give up control to any outside software aside from Intel's own IDCC ([http://www.intel.com/design/motherbd/software/dcc/index.htm](http://www.intel.com/design/motherbd/software/dcc/index.htm)). Which, of course is only available for Windows, complete with .net 3.0 phone home crap. The special <algorithms> Intel pre programmed your chipset with are merely a few instructions giving mode trip settings that are sure to burn up your hardware in a couple years. (Mine is set to _start_ my fans @ 55C! fan stage 2 @ 60C full fans @ 75C...)

It's total planned obsolescence. There have been several Linux projects that have been waiting on Intel to release white papers on the QST tech, but Intel has never produced and probably never will.

I fixed my heat issues by hard-wiring in a switch wired to all my fans (+1 I added to blow across my HDD's) and using the open 5v internal USB plug that could have I mounted in the never removed blank for the pcmcia slot, which means when i get a new lappy, I can move my switch and wiring to it without ruining either system by cutting drilling whatever and still spit in Intel's overly hot eye. :D

---

