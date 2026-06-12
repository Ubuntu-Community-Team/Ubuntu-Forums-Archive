---
title: "Laptop battery broken??!"
date: 2009-01-03
forum: Hardware
---

### Post by ajyrds on 2009-01-03
Hi,

Whenever I log in, I'm getting a message which says that my battery's capacity is only 41% and it means that the battery is broken or too old. This started after I upgraded the kernel (not very well and messed up everything, so had to reinstall) to 2.6.28 yesterday. The laptop is just over an year old and so is the battery. Is there anything akin to the HP Battery Check app (works on on Windows) in Ubuntu, so that I can verify this?
Here's the output of cat /proc/acpi/battery/BAT*/info -
present:                 yes
design capacity:         6000 mAh
last full capacity:      2496 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 127 mAh
design capacity low:     77 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            LION
OEM info:                Hewlett-Packard

and of cat /proc/acpi/battery/BAT*/state -
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            unknown
remaining capacity:      1696 mAh
present voltage:         11789 mV

Quite obviously, the battery is not getting charged to its full capacity :(. Is there any simple fix (other than buying a new battery).

---

### Post by ajyrds on 2009-01-05
The ubuntu warning now says that the capacity now is only 29% :(.
Please help!

---

### Post by Lee_Machine on 2009-01-05
Your laptop is not pluged into a power source. 

*charging state: discharging*

After a time a battery will not hold as much as it used to. The rule of thumb for a heavily used laptop battery is after about a year get a new one. That or a new laptop, what I usually do.

---

### Post by ajyrds on 2009-01-05
Yeah the screenshot is from when i  had just taken the plug out.
And yes I am a heavy user and the laptop is just over an year old.
The reason for my concern was the suddenness with which this happened, and the kernel upgrade with which this event (the battery problem) coincided. So i was wondering if maybe the kernel upgrade broke something. Anyway, a new battery looks like the only option for me now :(.

Regards,
Ajay

---

### Post by meditatingfrog on 2009-11-10
> **ajyrds said:**
> Yeah the screenshot is from when i  had just taken the plug out.
And yes I am a heavy user and the laptop is just over an year old.
The reason for my concern was the suddenness with which this happened, and the kernel upgrade with which this event (the battery problem) coincided. So i was wondering if maybe the kernel upgrade broke something. Anyway, a new battery looks like the only option for me now :(.

Regards,
Ajay

I just experienced this problem.  I'm considering installing Hardy (the Long Term Support Ubuntu), or booting off of the Live CD to see what things look like there.  Here is another thread with someone that has the same problem:  [http://ubuntuforums.org/showthread.php?p=8286161#post8286161](http://ubuntuforums.org/showthread.php?p=8286161#post8286161), but there hasn't really been anything else.  It would be great if you could check to see if another operating system *cough* windows *cough* is exhibiting the same problem.  

I don't know about you, but I haven't had this laptop for very long (~ 1 year), and I've used/owned laptops in the past for years, that never exhibited this problem.  I think something fishy is going on.

---

### Post by PhonicsMonkey on 2009-11-19
I have the same problem I believe it is driver related. The error began after I did a clean install of Karmic. Jaunty worked fine and so did the battery. It is getting better but not quite fixed. Rather than showing 29% batter it now shows 68% but the time remaining is what it has always been...3 hours. My laptop has always (Hardy to Jaunty to Karmic) had 3 hours of battery [well xp got 2 hours and vista had 45min...oh windows you're so fat]. This is what leads me to the belief that it is a software problem. Hope this helps...

---

### Post by meditatingfrog on 2009-11-19
> **PhonicsMonkey said:**
> I have the same problem I believe it is driver related. The error began after I did a clean install of Karmic. Jaunty worked fine and so did the battery. It is getting better but not quite fixed. Rather than showing 29% batter it now shows 68% but the time remaining is what it has always been...3 hours. My laptop has always (Hardy to Jaunty to Karmic) had 3 hours of battery [well xp got 2 hours and vista had 45min...oh windows you're so fat]. This is what leads me to the belief that it is a software problem. Hope this helps...

I think my battery problem is almost certainly hardware related.  I was running the laptop without the battery on ac power(i read somewhere that it is more efficient to do this) but didn't pay attention to how long the battery was out for, and i think this caused the battery to permanently discharge (memory effect).  It also made sense to run without battery on ac since i was having the problem of battery power running completely dry without a warning, and the laptop powering off.  Now I'm at half the battery capacity I was at before.  Maybe this will help me figure out why i wasn't getting a low battery warning.  I'm playing around with the Enlightenment desktop environment, but maybe it will prove more functional in the power management arena (and not just be smoother looking).  Good luck to all.

---

### Post by Auraq on 2009-11-20
> **PhonicsMonkey said:**
> I have the same problem I believe it is driver related. The error began after I did a clean install of Karmic. Jaunty worked fine and so did the battery. It is getting better but not quite fixed. Rather than showing 29% batter it now shows 68% but the time remaining is what it has always been...3 hours. My laptop has always (Hardy to Jaunty to Karmic) had 3 hours of battery [well xp got 2 hours and vista had 45min...oh windows you're so fat]. This is what leads me to the belief that it is a software problem. Hope this helps...

I guess my problem is related (?), so I will post in this topic.

I installed Karmic UNR on my netbook some days ago, and noticed that running on battery the power never seems to go down from 100% and instead my Aspire One just shuts down with a pop when it runs out of juice. On Jaunty (which I first installed a few months ago), this seemed to work OK... kinda irritating, I rather fancy Karmic's fresh look and wouldn't want to change back!

Does anybody have any tips on how to solve this? I tried searching the forums and googling, but didn't find much anything helpful. It's possible I just failed to notice the helpful bits, though, being the Linux-illiterate newbie lost in the Ubuntu Realm that I am. :redface: So help would be muchly appreciated...

---

### Post by psychoelf on 2009-11-20
I installed Karmic just a few days ago and thats when my battery problems started.  Worked fine with Jaunty and Win7.  I used to get 1.5 hours even last week and the other day I booted up Karmic and it tells me my battery is broken and only has 39% capacity!  WTF!  Now my battery is messed up even under Windows.  So either it is a coincidence that my battery decided to just up and lose more then half its capacity or Karmic is a battery killer.  Judging by the other "coincidences" I've read about I'm guessing it IS software related.

---

### Post by Jakus on 2009-11-29
Same problem but sure it's software not hardware.  

I just upgraded to Karmic and dual boot with MS Vista.  On Vista battery reads 100%, Switching to Ubuntu it pops up the Battery low 43% or failed dialog.

Any ideas?

---

### Post by cwwees on 2009-11-29
Ah!  A discussion of my problem!  I'm an ultra-ultra newbie on Linux.  I've been investigating 30 minute life on my HP laptop battery under Karmic.  I think it ran longer before I upgraded, but I'm not sure.  It definitely ran 90-120 minutes on XP Pro.

Battery is 3 months old, lightly used.  Gnome-power-manager 2.28.1 now reports "energy when full" 3.3 Whr  for the battery.  Label specs are about 70 Whr.  Over the past three days, I've rebooted a few times and tried to totally run-down the battery.  I've seen "energy when full" read 5.2 and 7.0 Whr over those three days of intense investigation.   If I reboot now, I suspect I'll get another different value.

Power consumption, on AC, is ~ 40W.  When I'm on battery, it's 17-18 W.  That suggests to me that the power management is working.  The problem is monitoring or resetting the Li-Ion charge manager memory in the battery.  

The HP literature says to re-calibrate the battery as much as every month.  The re-calibrate instructions are for Windows.  Anyone know a way to do this in Linux?

One further option...   I have a slightly newer laptop from work that's running XP Pro.  It has a matching battery.  When *that* battery is installed, gnome-power-manager reads 52 Whr available.

---

### Post by meditatingfrog on 2009-11-29
Has anyone considered booting into a command line, then checking to see if there is still a problem with their battery?  When I type acpi in a shell, it agrees with gnome-power-manager that my battery, at 60% capacity will only last 23 minutes.  

I'm running Jaunty, and I'm not dual booting so I can't check to see if the problem still occurs using a different operating system.  I did consider booting from a LiveCD to see what then is reported regarding the battery, but my LTS Hardy LiveCD doesn't seem to be working when I try to boot from it.  I'll try booting off it again.  Good luck to everyone, hopefully a solution is found.

---

### Post by meditatingfrog on 2009-11-29
> **ajyrds said:**
> Hi,

Whenever I log in, I'm getting a message which says that my battery's capacity is only 41% and it means that the battery is broken or too old. This started after I upgraded the kernel (not very well and messed up everything, so had to reinstall) to 2.6.28 yesterday. The laptop is just over an year old and so is the battery. Is there anything akin to the HP Battery Check app (works on on Windows) in Ubuntu, so that I can verify this?
Here's the output of cat /proc/acpi/battery/BAT*/info -
present:                 yes
design capacity:         6000 mAh
last full capacity:      2496 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 127 mAh
design capacity low:     77 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            LION
OEM info:                Hewlett-Packard

and of cat /proc/acpi/battery/BAT*/state -
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            unknown
remaining capacity:      1696 mAh
present voltage:         11789 mV

Quite obviously, the battery is not getting charged to its full capacity :(. Is there any simple fix (other than buying a new battery).

I just read your OP again.  I upgraded my kernel too, i was running 2.6.30, so i decided to reboot and try an older kernel, 2.6.28.14.  I thought it was worth mentioning that when i booted up using 2.6.28.14 gnome-power-manager stated i had 32.9% battery left and 5 minutes remaining (which doesn't make sense to me).

You may want to try using an older kernel (or if you already have, what were your results?).

Here is my cat /proc/acpi/battery/BAT1/info results:

present:                 yes
design capacity:         5200 mAh
last full capacity:      959 mAh
battery technology:      rechargeable
design voltage:          10876 mV
design capacity warning: 300 mAh
design capacity low:     200 mAh
capacity granularity 1:  32 mAh
capacity granularity 2:  32 mAh
model number:            NS2P3SZNJ5WR
serial number:           17249
battery type:            LION
OEM info:                SANYO

and cat /proc/acpi/battery/BAT1/state:  

present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            1540 mA
remaining capacity:      34 mAh
present voltage:         10716 mV

and acpi:

     Battery 0: Discharging, 3%, 00:01:11 remaining

---

### Post by TheOnlyMrK on 2009-11-29
My laptop has this problem, I let my mom have the laptop when she gave me money for computer parts so I could build a desktop in exchange for her getting the laptop, she used it once then it sat in her house with a dead battery for months and gave it back saying she has no use for it and doesn't know how to work it. I was pissed when I saw the battery was dead, I wiped the hard drive and installed Ubuntu then saw the battery warning "You're battery has a very low capacity (22.8%)".
BUT I did the usual "fit all" to extend a bad battery for any modern electronic... Disabled all power save features then unplugged the laptop and let it run on battery till it was completely dead, plugged it in to charge then when it was finished turned it back on, it's now up to 43%, still not good but a lot better then before.

---

### Post by meditatingfrog on 2009-12-01
I've been doing some research, and i've come across some information that i think would probably be useful for those of us experiencing this problem.  I've given up hope on the possibility that the battery is capable of greater capacity, as it turns out, a LION battery can lose capacity if it is completely drained enough times.  This has happened with my battery several times (to the point that my laptop powers off without any warning).  I believe the reason is because of how gnome-power-manager calculates the % battery (i've been looking at the source code of gnome-power-manager), but i can't say with certainty yet.  

I think that there may be a better way, but I think trying to find a way to solve the lowered capacity is futile (the battery is damaged, and the consensus is that when the battery is damaged, there isn't a way to fix it).  I think at this point the goal should be trying to prevent this from happening to other users, and i was thinking that, if it isn't already, gnome-power-manager should be using the low battery and warning mAh levels from the battery info in /proc/acpi/battery/BAT*/info to determine warning and critical action levels.

I also noticed there isn't a bug report created for this particular problem, so i'll create a bug report in launchpad.

---

### Post by Kasary on 2009-12-02
I have a question:
Generally, how long can a battery 4000mAh work?

---

### Post by TheOnlyMrK on 2009-12-02
> **Kasary said:**
> I have a question:
Generally, how long can a battery 4000mAh work?
Depends on the laptop, see howmuch your laptop is discharging per minute (or seconds, depending how the computer measures it) then divide the 4000mAh by that, that will be your *average* battery time in minutes (or seconds), average because computers don't constantly use the same amount of power.

---

### Post by meditatingfrog on 2009-12-02
I went to launchpad to create a bug report, but I came across this bug in gnome-power-manager, which I think is actually what is causing the damaged batteries.  [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/481576]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/481576")

Please subscribe to the bug in launchpad, unless you haven't experienced the complete draining of your battery (power cuts out without warning) that seems to affect only some of us.  

If you haven't experienced the cutting off of power (complete battery drain), I'd love to hear from you.

---

### Post by cwwees on 2009-12-03
I reported above a 30 minute life (and decreasing) in 9.10.  I also get a 6 minute recharge time - which implies that the battery isn't really dead when the machine shuts down.

I have a different laptop with the same battery model running WinXP.  It also gets 20-30 minutes operation (with all power conserving features turned off).  I cycled it four times in Windows and got no improvement in the battery rating.

/proc/acpi/battery has two files, C177 and C178 (apparently for the two battery serial numbers that have been plugged into this computer).  Each has 3 files, "alarm" "state" and "info".      more info lists the battery parameters - *as reported by the battery management chip* in the battery!  This is designed to prevent the battery getting over-charged (and being a fire hazard).  

I take it that these values in the battery memory need to be reset to regain capacity.  But I don't know how to do that.  Both Windows and Ubuntu (on different machines) have the same 30 minute discharge/6 minute full charge cycle for this battery.  

Charlie

---

### Post by jualin on 2010-02-01
The problem is not software related, the problem is with the battery. Windows is just too "quiet" or too dumb to notice that your battery performance has decreased. Windows warns you when your battery is pretty much under 30% of its supposed capacity. Ubuntu starts telling you after 75% of its capacity. 
Do not waste time installing a new kernel, or installing a different version of Ubuntu. The reason why a fresh installation does not warn you is because the system may not have enough information (charge and discharge times) to make a judgement about the battery's life. After a year of heavy use, the battery will start to die until eventually it gives only 40 min or less of battery life. You can either buy a new battery, or replace the internal batteries inside of the battery. Look on google for instructions on how to do it. 
If you need more proof, then boot into Windows, and measure how much time it takes to discharge in Windows. You will see that even thought the Windows Power Manager says that you may have 100% it will go down very fast and it should last the same as in Ubuntu.
Hope this helps!

---

