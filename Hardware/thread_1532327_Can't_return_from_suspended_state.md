---
title: "Can't return from suspended state"
date: 2010-07-16
forum: Hardware
---

### Post by hnrkg on 2010-07-16
Since a couple of days I can't return from suspension. (Returning from hibernation is not a problem, though.) When in suspension and a key is pressed the fan, hard drive and DVD awakes, but the monitor doesn't. It doesn't not even light up. Then nothing happens and I have to a hard reboot.

I upgraded to grub2 a couple of days ago, so maybe it has something to do with that? I can't find any relevant information in syslog/dmesg. This may indicate that the problem lies in the early "awakening process"...?

Any thoughts on this?

EDIT: Running Ubuntu 10.04, thought I mentioned it...

---

### Post by cutterjohn on 2010-07-16
I haven't tried hibernate myself yet, but on occasions I have problems where resuming from a suspend seems like it triggers some sort of endless disk grind.  I just had one of those instances this morning, and let it run for c. 15m before forcing a powerdown/powerup as that's a ridiculously useless resume from suspsend time given the speed of rebooting...

some time is resumes like older Ubuntu releases(9.10 & 9.4) did, which is to say fairly quickly... but others are like the above making suspend useless ATM.

Brand new squaky clean install of:
Ubuntu 10.4 x86-64
Intel P8600/4GB DDR2-800
ATI Mobility Radeon 4850 HD 512MB GDDR3 + Catalyst 10.6
(an MSI GT-725 actually)

I did the squeaky clean install as a cheap way to reclaim disk space, get full ext4 support, and GRUB updates w/o mucking around.  (Plus it forced me to do a backup re-assessment and create a new data backup set as a bonus...)

I'm still on the base install plus a few extra apps, but nothing that should've affected any of the basic system files...

---

### Post by hnrkg on 2010-07-16
My problem is that I really don't know where to start looking for a solution (or for the problem, for that matter), because the logs don't give me any hints.

I'm hoping that this is a known bug, otherwise I'll have to doing some detective work myself. And I rather not, it's to time consuming.

---

### Post by cutterjohn on 2010-07-16
I know.  It seems like every new release that there's some niggling problem that needs to be tracked down and either fixed or worked around.

All I've had open every time that this happened was firefox(OR Chromium from the PPA daily build) and a terminal with three shells running.

Maybe it's something browser related... possibly the flash plugin?  (I'm using the adobe flash player with GPU accell enabled...)

Just to give further idea of how bad it is, I wasn't even able to CTRL-ALT-F# into a virt text terminal...  forgot to try the ultimate shutdown key combo though...

ALT-SYSRQ+R+S+E+I+N+U+B

(First w/this nb I had 9.4 which meant that I had to use the alternate text install installer, then had to setup some basics by hand(long time since I had to do that!), get catalyst, get the GUI going and undo my hand changes so as not to screw up the GUI setups, and then deal with the "hdd killer bug".

9.10 was a little smoother, can't recall exactly what went awry with that one offhand, but I know that something did but not as badly as I did a dist-upgrade that time.

Then last, but not least, we have that ghastly pulseaudio screwing up audio everywhere it shows it's ugly mug...)

---

### Post by hnrkg on 2010-07-16
I can confirm that my issue is caused by me upgrading to grub2. I can successfully suspend and return after I downgraded to grub 1.5 using this HowTo:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

I will file a bug on Launchpad.

EDIT: Done.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/606532](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/606532)

---

### Post by cutterjohn on 2010-07-19
Well, my problem is that it DOES resume from SUSPEND MOST of the time, however there are times when disk activity goes absolutely bonkers upon resuming from suspend to the point tha even if I manage to unlock it back to the desktop that it is unusable for quite some time... just faster to reboot at that point.

I see udisk-daemon and gvfs processes in the top of the top list(using 7-14% CPU), presumably whats whacking on the hdd constantly.  Plenty of free RAM usually at least a 1GB or so unused, so it's not doing any swapping nastiness...

so the whole problem is caused by some rogue disk access that sometimes occurs when resuming from suspend only, as I've never noticed it happening while generally up and running.

---

### Post by libssd on 2010-07-19
Are you **sure** that this process hasn't started swapping while it's in suspend mode? I experienced something like this with 9.04 on an Acer D150 netbook; after closing the lid for a few hours, so much swap was being used that it felt like the machine was frozen. A BIOS update fixed the problem (as did installing 10.04).

However, I did notice that resume from suspend always took longer than I thought it should under 10.04, so I turned off password checking on resume; now it wakes up and is ready for use in less than 3 seconds. I can still lock the screen manually, if I want to require a password.

---

### Post by cutterjohn on 2010-07-19
> **libssd said:**
> Are you **sure** that this process hasn't started swapping while it's in suspend mode? I experienced something like this with 9.04 on an Acer D150 netbook; after closing the lid for a few hours, so much swap was being used that it felt like the machine was frozen. A BIOS update fixed the problem (as did installing 10.04).

However, I did notice that resume from suspend always took longer than I thought it should under 10.04, so I turned off password checking on resume; now it wakes up and is ready for use in less than 3 seconds. I can still lock the screen manually, if I want to require a password.Yes, it has NOT started swapping in suspended mode(WTF?! there should be NO swapping while suspended so that would be a MAJOR bug, [EDIT] AND I have over 1GB free RAM with each "swapping incident... it's just HUGELY annoying [/EDIT]), but anyways I've not muvh to go on ATM as it doesn't consistently happen when running on battery power nor AC...  it just "seems" to be "random", nevertheless it's a HUGE blackmark against Ubuntu ATM, but I'm just used to dealing with problems with any and every new release, Ubuntu or otherwise...   just sad to say that I still expect and experience them after so many years...

[continue EDIT]
It's just a good thing that the boot time of ubuntu is so low that I can force a reboot and get a new Desktop MUCH more quickly rather than waiting around for some rogue processes to **** around with themselves...
[/cEDIT]

[EDIT2]
At this rate I'm about ready to point the finger at ext4(and userspace interactions), but I can't back that up given I've just installed this ext4 based distro...

something yet again is just ****ed up with suspend & Ubuntu...  I just wish that I had access to my old desktop with my log to match up some things...
[/EDIT2]

---

### Post by cutterjohn on 2010-07-20
It's just getting worse... I suspect the udisk-daemon & gvfs **** from GNOME is interefereing with normal operations, perhaps even having behavior like in ext2 days when there wa sno journalling and they had to work...

---

