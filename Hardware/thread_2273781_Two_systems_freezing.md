---
title: "Two systems freezing"
date: 2015-04-15
forum: Hardware
---

### Post by Diskdoc on 2015-04-15
I'm having problems with the system locking up completely. Fan spins, no switching to console, no alt+sysrq combinations work, no hints of trouble looking at the logs afterwards. I messed around with linux-crashdump but it didn't seem to save anything to a crashdump at all when the system froze.

This is occuring pretty randomly on two different systems running Xubuntu 14.04 and Linux Mint XFCE 17.1. What's interesting is they have the same Radeon chip: XPRESS 200M 5955 (PCIE) (according to Xorg.log.0). I thought this might be related to Dynamic Power Management being enabled per default in the kernel so I played around with radeon.dpm=0, but to no avail.

I'm putting this out there to see if anyone else has the same problem. Pretty sad to see this in the LTS, if it's indeed a driver problem :-/

Can provide dmesg, logs and stuff if anyone wants them.

---

### Post by Diskdoc on 2015-04-15
Here are the logs, just in case.

---

### Post by weatherman2 on 2015-04-15
This is the Hardware forum, so you are more likely to get hardware-related suggestions here.  Your problem could be hardware or software, though.

Here are some hardware-related suggestions I posted yesterday in response to a similar query.  It might be a good idea to rule out hardware and shouldn't take long to check the basic things:

[http://ubuntuforums.org/showthread.php?t=2273664](http://ubuntuforums.org/showthread.php?t=2273664)

---

### Post by Diskdoc on 2015-04-15
Oops, sorry for posting to the wrong forum! It's been a while since I hung out here :) Hopefully an admin can send me to the right place.

Thanks for your tips. I have checked with Memtest and SMART info, that checks out. Have played with lm-sensors, think the cooling works properly on both machines. Working on filing a bug report now.

---

### Post by user_of_gnomes on 2015-04-15
Did you try using the proprietary drivers instead?

---

### Post by Diskdoc on 2015-04-15
It would certainly be interesting to try - perhaps the problem isn't with the ATI-driver after all..but I don't think the proprietary driver is offered for as old hardware as this.

---

### Post by Vladlenin5000 on 2015-04-15
> **Diskdoc said:**
> but I don't think the proprietary driver is offered for as old hardware as this.

Unfortunately, you're 100% correct.

---

### Post by user_of_gnomes on 2015-04-16
> **Diskdoc said:**
> It would certainly be interesting to try - perhaps the problem isn't with the ATI-driver after all..but I don't think the proprietary driver is offered for as old hardware as this.

Try an Nvidia videocard instead, rule out a driver problem?

---

### Post by Diskdoc on 2015-04-16
Well, I forgot to mention that these are laptops, so no changing the graphics.. Thanks for the suggestion though, exactly what I'd do otherwise.

Filed a bug report here:[ https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati-lts-utopic/+bug/1444680]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati-lts-utopic/+bug/1444680")

My friend suggested the other common factor, XFCE, might be the problem. I'm doubtful but will try other OS:es/GUIs to rule it out.

---

### Post by Diskdoc on 2015-04-16
Found this..similar problem, earlier kernel, other GPU.. [http://www.linuxquestions.org/questions/slackware-14/frozen-xfce-session-4175459545/]("http://www.linuxquestions.org/questions/slackware-14/frozen-xfce-session-4175459545/")

---

### Post by user_of_gnomes on 2015-04-16
Memtest and hard drive test comes out clean?

---

### Post by VMC on 2015-04-16
I have to use: **'radeon.modeset=0**' on an old radeon laptop. In fact, that's the only way I can boot the system.

---

### Post by Diskdoc on 2015-04-22
Memtest and SMART clean, yes. Ran Memtest for three hours. Tried changing OS to Linux Mint 17.1 but it locked up again.


Thanks, VMC, I'll try that. Otherwise I'll throw in the previous LTS (Mint probably) and see how that goes.

---

### Post by Diskdoc on 2015-04-22
I gave radeon.modeset=0 a shot but it resulted in software rendering and the wrong resolution, at least on Mint 17.1. Made everything too slow. I'll try the old Ubuntu LTS next.

---

### Post by Diskdoc on 2015-05-03
Well guys, just wanted to post an update on my findings. Tried 15.04 and it froze up too. Worked fine when I tested the system for an hour but my friend who owns the laptop had a freeze after ten minutes.

I've been scouring the web and it's starting to look like this is a hardware bug specifically with the ATI EXPRESS 200M GPU in combination with AMD CPUs. I think it might have something to do with the frequency scaling on the CPU. Must have worked in Windows though, or they'd have pulled these models from the market.. So if it's treatable with software, maybe there's hope for a kernel fix.

Working now to try and lock the cpu frequency and see if it stabilises the system(s). Have updated my bugreport with the same information.

---

### Post by Diskdoc on 2015-05-24
I've ploughed through probably every kernel option and xorg.conf option (for radeon) there is but the only thing that seems to work is actually locking the CPU frequency. On some BIOSes you can disable Powernow!, setting the CPU at full speed. On some BIOSes you can't but I used this method instead, adding these lines to /etc/rc.local:

echo 1600000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
echo 1600000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq

This way, I can choose some medium CPU frequency instead of settling for the lowest or highest frequency by changing the governor.

---

