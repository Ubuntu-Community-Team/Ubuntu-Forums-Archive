---
title: "Horrible Battery Life"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by Pixel on 2006-06-05
This is on my Apple Powerbook G4, 1.5 ghz.

I have dapper installed on it, along with a few other programs, but i never do very much on it, usually just browsing the web.

I get almost less than an hour of battery life at full charge.

Any idea why?

---

### Post by ariel on 2006-06-05
I was going to start a thread on this too. I've got a Thinkpad X60s with extended battery. In winblows, it runs cold and with light continuous use it can do an unbelievable 8.5 hours. With Dapper/Final, including:

[LIST]
[*] 686smp stock kernel and frequency scaling
[*]Latest "laptop-mode-tools" (from: [[IMG]https://wiki.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] http://www.xs4all.nl/~bsamwel/laptop_mode/tools/debian.html]("http://www.xs4all.nl/%7Ebsamwel/laptop_mode/tools/debian.html")) and  laptop mode enabled in the machine, with an aggressive  3-second idle timer for spinoff (same as what I use in Win).
[*]laptop mode daemon allowed to control the frequency scaling and governor, and governors set to "powersave" mode[/LIST]Even with all the above, Dapper on the X60s makes it run really hot and drains the battery about forty percent faster than Windows (even with all the radios turned off), which is very frustrating for me. 

Any suggestion, anyone?

---

### Post by randomlaughter on 2006-06-13
I have the same problem. With very agressive settings in ubuntu I get 1 hour and 20 min compared to 2 hours with suse or windows.

seems like this is pretty common sort of problem.

---

### Post by nolongerlivecd on 2006-06-13
Funnily, I get the same, or better in Dapper. But my battery isn't much anyway...

---

### Post by rokky on 2006-06-13
Is anyone else seeing that the disk access LED is almost constantly on?  This would certainly account for poor battery life and a lot of heat.  I also saw this with Simply Mepis 3.4.3, and posted the following query about it:

[INDENT]This is on a Thinkpad X30 notebook PC running Simply Mepis 3.4-3.

It has 1 GB of RAM, so I doubt swapping is an issue (top showing "0k used" for Swap).

top also shows 90%+ idle for the most part, Mem used around 430MB with Gaim, Mozilla browser and mail client running (mostly idle).

I set up ksysguard to show graphs for all the "Disk Throughput" nodes, and all have been showing zero for total accesses.

I have only / mounted most of the time this is going on, and its entry does have "noatime" set in fstab.

This joker is running *hot*, and I have no confidence it would last long at all on the battery if I wanted to roam around with it. This is not the way it acts when I have it booted to WinXP, so I don't think it is hardware.
[/INDENT]

There has been no response in 5 days, so that prompted me to give Xubuntu a try.   I had pretty good results with Edubuntu 5.10 on my previous X20, but gave up on it when the update manager updated Mozilla to 1.7.13, but uninstalled Mozilla Mail because it was a level or 2 behind, and absolutely refused to let me get a matching "set" installed - don't mess with my Mozilla/Netscape Mail client habit of 7+ years!!  Mepis was quite happy to let me have them together, but this constant disk light issue got my eye to roving again.  

However, Xubuntu (6.06 final) seems to have the same issue, plus it won't let me get the 1280x1024 resolution setting on an external 17-inch LCD monitor that Mepis picked right up - can't seem to get it all together with one distro... :-(

Rokky

---

### Post by odix on 2006-06-14
Hi,
laptopmode is disabled by default in dapper (to enable edit /etc/default/acpi-support), I'm not sure if it was enabled in the previous releases. If it is enabled it should give you longer battery power. Another "trick" is to mount the /tmp partition to tmpfs (memory mapped), if you have enough memory, this reduces also disk accesses alot

regards

---

### Post by RhettNyeDotOrg on 2006-06-14
looks like cpufreqd is the way to go, in combination with laptop_mode.  cpufreqd will turn down the cpu frequency when not plugged in, and laptop_mode will make the hard drive a bit more efficient in terms of power.  I don't have laptop_mode enabled by default, but instead i have a script on my desktop to run if i'm not plugged in (which isn't that often.)

you can turn on laptop_mode in /etc/default/acpi-support along with other acpi options which will manage power use for peripherals like unneeded cd-rom, etc. 
do yourself a favour and educate yourself a bit on this so you know what you're turning on and off in there.

FYI, here's my cpufreqd.conf:

```

                                      
[General]
	pidfile=/var/run/cpufreqd.pid
	poll_interval=2
	enable_plugins= programs,acpi_ac,cpu,acpi_battery,acpi_temperature,nforce2,sensors,nvclock,apm,pmu
	verbosity=4
#	enable_remote=1
#	remote_group=root
[/General]

[Profile]
name=AC
minfreq=100%
maxfreq=100%
[/Profile]

[Profile]
name=Battery
minfreq=20%
maxfreq=20%
[/Profile]

[Rule]
name=AC Rule
ac=on                    # (on/off)
profile=AC
[/Rule]
 
[Rule]
name=AC Off - Low Battery
ac=off                   # (on/off)
profile=Battery
[/Rule]


```

---

### Post by rokky on 2006-06-14
I installed laptop_mode tools, and enabled laptop_mode, and now the disk LED is off most of the time, and the heat level has dropped noticeably (installed somethings or other for monitoring temps and other laptop-related info, but I don't see it/them on any menus, so I need to go back into Synaptic pkg mgr to see if I can find them again to know what commands to try - always the fun part of so many Linux choices with the wide variety of "logically named" tools ... depends on your logic ;-)

With that and the full Mozilla suite (why no SeaMonkey?), I am a much happier 'buntu camper now - just need to get the 1280x1024 display mode working on the external monitor for my X30.

I would still like to know what was keeping the disk so busy before that mod - guess I need to study up on laptop_mode to understand that.  I'm more used to Solaris and Windows buffer cache minimizing disk access under "normal" server/desktop usage.

Rokky

---

### Post by ariel on 2006-06-19
Good trick! Can you recommend a size for the ram-mounted /tmp ? I have no idea what to use.

---

### Post by yzord on 2006-06-19
In the end though, if you have a laptop that allows for speedstep (Pentium-M and ULV), Ubuntu is always going to have a higher power requirement. This is because, unlike speedstep on windows, ubuntu's implementation only steps frequency and not voltage.
There's a thread on one of the general forums regarding Linux-PHC, or Processor Hardware Control, which is a patch for the kernel to control CPU voltage. It's something that's been implemented in Gentoo and some others, but is still somewhat involved to do on Ubuntu (ie. recompiling the kernel, etc). Until it gets rolled in, we'll have to make do. Personally, I get around 5 hours with XP, 3.5 hours with Ubuntu on an X31 - which sucks, as I can't stand going back to XP.

Yz

ps. Here's the link to the discussion:
[http://www.ubuntuforums.org/showthread.php?t=146366&highlight=phc+voltage+ubuntu](http://www.ubuntuforums.org/showthread.php?t=146366&highlight=phc+voltage+ubuntu)

---

### Post by tribaal on 2006-06-19
> Good trick! Can you recommend a size for the ram-mounted /tmp ? I have no idea what to use.

Well if you use tempfs you don't actually need to specify a size. Yup, that's magic. The system will auto-regulate it's memory usage, swapping it if ever needed, just like a regular process. Swap almost never happends for me, however (except when I *really* push my laptop to it's limits, like with blender, the gimp and BOINC doing stuff at the same time).

Cheers :)

- trib'

---

### Post by chichilalescu on 2006-07-27
hi all.

i had this problem with overheating myself (i have kubuntu installed), and I tried everything untill today i just lost my temper and i did a "killall kded", even though i have no idea what kded is supposed to do, and like magic all weird and frequent (every half a minute or minute) hard drive access stopped. i suppose i shouldn't have done this, as i probably need kded, but i will do it again.
it's not so much the battery life that i care about, because i always have my laptop plugged in, but it's the overheating and the annoying sound of the hard drive starting and stopping all the time that got to me. anyway, now it's cool and silent, so it feels more like linux.

---

### Post by UltraMathMan on 2006-08-07
chichilalescu, your hard drive may be spinning down as per power mangement. You may want to check out [this thread]("http://www.ubuntuforums.org/showthread.php?t=143591&highlight=laptop-mode") for a fix.

Hope this helps :)

---

