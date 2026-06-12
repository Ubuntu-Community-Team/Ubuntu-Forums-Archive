---
title: "Load_Cycle_Count: final verdict"
date: 2008-04-27
forum: Hardware
---

### Post by dennis4b on 2008-04-27
Hi,

There are so many threads about posts about this topic I thought I would summarize what is going on, since there seems to be a lot of confusion:

There are 2 degrees of power saving on most laptop disks:

[LIST=1]
[*]parking the heads, and
[*]parking the heads and spinning down the disk
[/LIST]

(both increase the Load_Cycle_Count. Both also protects against shocks of course; when doing 1 as compared to 2 the disk is online faster since it doesn't have to spin up, at a cost of less power savings from leaving the disk spinning).

Regardless of all the discussion about who is responsible for the settings, whether the firmware or the BIOS is to blame, it boils down to this:

There is no magic way to save power, it happens through parking and optionally spinning down the disk. Arguing about "hdparm -B 1" versus "hdparm -B 200" or what the spindown timeout should be is all pointless: *if laptop_mode is not active, no power savings setting is going to do  anything other than ultimately kill your disk.* Your disk is not going to spin down with normal kernel settings (not for very long anyway). 

And if you're unlucky enough, you'll end up parking-unparking the heads all the time and increase the Load_Cycle_Count every few seconds.

It's very simple:
[LIST]
[*]APM is enabled (hdparm -B is < 254): Laptop_mode MUST be enabled and active!
[*]Laptop_mode is disabled or not active: APM MUST BE DISABLED.
[/LIST]

A kernel which is not in laptop-mode is not going to do anything to save power on the disk, and the disk is not going to be able to save any power if the kernel keeps accessing it. (Note that while the disk can trade performance for accoustic noise, there is no real way to trade performance for power)

It's pointless to argue that the BIOS or firmware set certain power saving settings - the BIOS / firmware expect the OS to be in the equivalent of Linux' laptop_mode. NO APM setting, not 1, not 100, not 180, not even 250 makes ANY sense when not in laptop_mode.

IMHO, Ubuntu must:
[LIST]
[*]explicitly disable APM at boot, and
[*]if it wants to enable APM, it must also activate laptop_mode
[/LIST]

It should NOT allow the disk to be in "-B 128" when laptop mode is not active; how is the disk going to save any power ? Depending on the aggressiveness of the settings, you will either end up in Load_Cycle_Count hell, or effectively nothing happens since the kernel always touches the disk before any power saving can kick in. 

*There is no magic "inbetween" setting that allows power savings while the kernel is not in laptop-mode.*

Doesn't it all make sense? :)

Hope it helps someone :)

---

### Post by Vadi on 2008-04-27
So by default 8.04, on a laptop, does no powersaving on the HD or no killing the HD?

---

### Post by ethanay on 2008-05-03
On my Hardy install, the disk-killing hardware default setting didn't appear until after suspend/resume.  There was a [bug #89269]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/89269") preventing me from applying any meaningful patches.  With the help of several people pointing me gradually in the right direction, it seems to be under control now.  Of course, power management is still a complete mess, and I still have no idea whether and/or with what priority laptop_mode, hdparm.conf, etc/pm/config.d/disk, and usr/lib/pm-utils are setting hdparm apm values.  to be safe, everything is 254 right now.  I'll probably change it over the next few weeks as I optimize laptop mode while on battery power.

In the process of trying to get it resolved on my laptop, I've learned a few things....

Couple of points of clarification:
hdparm -B settings are broken up into three parts: 1-127 (enable spin down + head parking), 128 - 253 (head parking only) and 254/255 (power management off).  Within the distinction between the two power management levels, lower numbers = do the action sooner (i.e., -B = 1 or 128 means spin down and/or park heads almost immediately).

On my disk, the hardware default is 128.  Which brings me to my 2nd point of clarification:  This isn't necessarily a hardware bug or a software bug.  A default APM value of 128 isn't inherently insane, nor is frequent intermittent disk access.  However, these two things together create several problems: 1) lowered i/o performance (I'm assuming logically; haven't run any tests) 2) a much higher rate of hard drive wear and tear, shortening the drive's lifespan by several orders of magnitude 3) Little or no bump protection benefit from hdd head parking, because it unparks again almost immediately and 4) higher, rather than lower power consumption from having to execute mechanical commands frequently (spin down/head parking).

---

### Post by dennis4b on 2008-05-12
> **ethanay said:**
> A default APM value of 128 isn't inherently insane, nor is frequent intermittent disk access.  However, these two things together create several problems: 1) lowered i/o performance (I'm assuming logically; haven't run any tests) 2) a much higher rate of hard drive wear and tear, shortening the drive's lifespan by several orders of magnitude 3) Little or no bump protection benefit from hdd head parking, because it unparks again almost immediately and 4) higher, rather than lower power consumption from having to execute mechanical commands frequently (spin down/head parking).

IMO (no offense to you!) having a value of 128 *is* insane, if there are no provisions made to limit disk access. The kernel *will* flush every so many seconds (5 by default?) so you either park after <5 seconds and unpark straight after, or you park after >5 seconds which means you don't park at all. You are simply guaranteeing 10+ parks per minute.

I agree power management and savings are a bit of mess (or confusing to configure), but IMO, and anyone who is better informed please step in and correct me, there is NO point at all to have APM enabled if you're not also enabling some kind of minimize-disk-access scheme. 

Without laptop_mode, how are you going to save power ?? Please, with Ubuntu (as per standard Linux kernel) flushing to disk every 5 seconds (I have no idea what Windows does by default, how and if it limits disk access) exactly what benefit is APM=128 going to bring ?

---

### Post by ethanay on 2008-06-01
> IMO (no offense to you!) having a value of 128 *is* insane, if there are no provisions made to limit disk access. 

no offense taken...that is pretty much what i said!  it is only insane when power management configuration allows constant writes to the disk.  your "..., if" is the same as my "...not inherently" so i don't really know why the argument...

yes, you are absolutely right, apm should be disabled unless disk access is controlled.  that is what i do right now, until i set up some disk access controls.  likewise, there is no point to disk access controls if apm is disabled.  so it is either both or neither.  it is  stupid to have one without the other...but neither on their own are *inherently* stupid.  they just have to work together, and they don't by default.  what is stupid is ubuntu saying, "we don't touch the default setting -- that's a hardware mfr issue" and hardware manufacturers saying at the same time, "look at our advanced power management, and how well it works**" (**under ideal conditions).  it is fundamentally a communication issue.

imho, power savings aren't huge with the hard-drive, anyway.  the big plus is the bump protection by parking the hdd head while unplugged.

---

### Post by sergiom99 on 2008-06-02
please, how do I enable laptop-mode? Should I? Im a bit confused on this laptop HDD thing.
Thanks, Gracias!

---

### Post by sdennie on 2008-06-02
dennis4b: While I more or less agree with you, I think the primary problem is simply that the ext3 journal commit time is set to 5 seconds by default.  This is the primary cause of the Load_Cycle_Count stuff.  Using hdparm -B just fixes one of its symptoms.

---

### Post by athiwatc on 2008-06-03
I agree my disk cycle increase every 1 a minute or less
For now am using vista
I can hear the sound like gig-gog from my hard disk i thing that the sound of the parking
and i also measure with a tool and it will use up to 300 cycel per day !!!

that mean 300*365 about 100000 almost 1/6 of its life per year

lol i holp ubuntu solve this problem soon :)

---

### Post by sdennie on 2008-06-03
> **athiwatc said:**
> I agree my disk cycle increase every 1 a minute or less
For now am using vista
I can hear the sound like gig-gog from my hard disk i thing that the sound of the parking
and i also measure with a tool and it will use up to 300 cycel per day !!!

that mean 300*365 about 100000 almost 1/6 of its life per year

lol i holp ubuntu solve this problem soon :)

Six years on a laptop disk sounds pretty reasonable to me...

---

### Post by athiwatc on 2008-06-03
> **vor said:**
> Six years on a laptop disk sounds pretty reasonable to me...


that mean you use 300 every day but in some day it can go up to 500-1000 that is a lot

---

### Post by erythrocyte on 2008-11-02
i'm promoting an idea on ubuntu's brainstorm related to this issue. would appreciate all your votes! thanks!

[[IMG]http://brainstorm.ubuntu.com/idea/15153/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/15153/)

---

