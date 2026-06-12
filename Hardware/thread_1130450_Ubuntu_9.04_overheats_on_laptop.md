---
title: "Ubuntu 9.04 overheats on laptop"
date: 2009-04-19
forum: Hardware
---

### Post by Oram on 2009-04-19
Hey, I'm running Ubuntu 9.04 on my laptop. My laptop would overheat on 8.04 but not 8.10 and now in 9.04 it overheats again :S. I have a compaq cq50 110us. When ever I play any games in wine it overheats. I have tried cleaning out all of the fans and it still over heats after playing games for about 20 minutes. I'm not sure why it overheats in 9.04 but not in 8.10. Any help would be greatly appreciated.

Hmm It seems to turn off when I'm doing to many things at once, I was running wine and pidgin and it turned off. I don't know if it was overheating i touched my laptop and it wasn't hot.

---

### Post by Oram on 2009-04-20
Does anyone know how to fix this? Also last time it turned off my keyboard stoped working for 10 minutes. Did this happen to anyone else?

---

### Post by SeaWeedz on 2009-04-22
having the same problem on a compaq presario f500.

on 8.10 I could throw anything at my laptop and the fan might wind up to full throttle here and there..but now, it goes to full throttle and about 5-7 minutes later the computer just powers off.

It doesn't turn on until it has cooled off.  I installed a bios update (had to install and boot into Windows just to do this :confused: ) that had some bits that address the fan but it didn't help.

My temporary workaround has been to use "CPU Frequency Scaling Monitor" and run the box at 800mhz instead of 1.8ghz :( Will probably have to go back to 8.04.

---

### Post by Cheburator on 2009-04-25
What kind of gpu's do You have? On my compaq 6715b i have an ATI X1250, in ubuntu 9.04 it has to use the open-source drivers. On 8.10 i used the fglrx driver, temperatures on idile were about 45 C, now on the open-source drivers it runs on 55 C.

---

### Post by dtoronto on 2009-04-25
run a:

```
ps aux | less
```

to see if you have running processes that may be overworking your system.  You might also need to reconfigure your bios.

---

### Post by dtoronto on 2009-04-25
you may also want to check out this thread:

[http://ubuntuforums.org/showthread.php?t=597998](http://ubuntuforums.org/showthread.php?t=597998)

It's hard to say what to do because I'm not sure what's causing it to overheat.

---

### Post by SeaWeedz on 2009-04-26
Yes.. I found out that my laptop on 8.04 and 8.10 was not overheating possibly because the CPU frequency was being adjusted accordingly.  

Maybe Ondemand has a bit different algorithm now that tries to get a little more power?  I speculate this because when I'd adjust the frequency manually on 9.04 I could prevent the crash.

GPU info from lspci is..  then there are many other nvidia memory controllers listed as well. 

00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)

I had added to my modules something like powernow_k7 (oops, realize now that my processor is k8) in 9.04 but still had a overheating issues.  I would not be suprised if the gpu was causing the problem..and maybe setting the CPU freq to 800mhz was enough to slow everything down to prevent overheating.  

I switched back to 8.04 and haven't had any crashes from overheating.  I do have 9.04 on a harddrive here still so I can try testing things out if it would help.  

I've been seeing some other overheating reports for 9.04 as well
[http://ubuntuforums.org/showthread.php?t=1136575](http://ubuntuforums.org/showthread.php?t=1136575)
[http://swiss.ubuntuforums.org/showthread.php?t=1134717](http://swiss.ubuntuforums.org/showthread.php?t=1134717)
[http://wedontsupportyou.com/2009/04/14/cooling-off/](http://wedontsupportyou.com/2009/04/14/cooling-off/)

Should I try powernow_k8 in the modules to see if it helps?

---

### Post by martinbures on 2009-04-26
I am having the exact same problem.  I am on a macbook pro santa rosa.

I am not gaming.  I just installed 9.04 - I was running 8.10 previously just fine.  I walked out of the room while it was sitting there with no programs loaded after booting.  It is very tempermental about finding wifi and for some reason refused to connect.  I left the room for 5 minutes and came back and it was boiling.

---

### Post by SeaWeedz on 2009-04-26
martin: boiling.. Try running dtorontos command sometime when it is hot. Did it crash or power down, or just hot to the touch (more than other times you have used it?)  

The way you describe it, I'm imagining a seemingly idle computer getting very hot.

---

### Post by martinbures on 2009-04-27
That is exactly it.  I finished installing everything.  I then ran update manager.  After that was done, I got up to change some laundry, came back and touched it became very alarmed and immediately shut it down.  I do a lot of scientific programming on it and heavy data crunching.  It NEVER got anywhere near this hot when I was doing serious work on it.  When I get home tonight I will try what you said.

martin.

---

### Post by martinbures on 2009-04-27
And with the heat this high, the fans were not running, which was very strange.

---

### Post by calhau0 on 2009-04-28
my laptop lg e500 is also overheating

> 28Abr2009 22:28:56	ACPI	THRM	146 that's Celsius 
hdd temperature at 39ºC 
but the laptop isn't hot at all :confused:

when i play a non power demanding games the temperature stays at 146ºC and 15 min later "shut down".

---

### Post by jako on 2009-04-29
Had similar problem with a HP nc8430, ati graphics (X1600) with xserver radeon driver, i.e. open source. Put option "DynamicClocks" "on" in my xorg.conf, solved problem. With the propietary driver I'd always used aticonfig to throttle things, but of course that's not possible now.

---

### Post by calhau0 on 2009-04-30
i've found this on my messages log > ACPI: BIOS _OSI(Linux) query ignored

is there anyway to fix acpi detecting problems?

---

### Post by m4cph1sto on 2009-04-30
My laptop is overheating with Jaunty as well.  Pentium M/Centrino 2.0 ghz.  It did not overheat with Hardy or Intrepid.  After installing Jaunty my CPU temperature is 15 degrees C higher when idling and 25 degrees higher under moderate load.  The fan is running MORE in 9.04, not less, so it's not a fan issue.  System Monitor isn't showing any unusual activity.  The on-demand governor keeps the CPU at the lowest speed most of the time, but it still gets too hot.

This is absolutely a software issue.  Perhaps the voltage tables are wrong.  For the first time, in Jaunty acpi_cpufreq is hard-coded into the kernel.  Maybe this is part of the problem.  You can't even undervolt the processor in 9.04 without recompiling the entire kernel, which would take forever and cause my laptop to overheat.   

Overall I'm loving Jaunty, but this overheating issue is a killer for a lot of people.  I don't even know where to start to troubleshoot it.  There are several threads here about this issue.  Has someone filed a bug report yet?

---

### Post by m4cph1sto on 2009-04-30
> **m4cph1sto said:**
> 
This is absolutely a software issue.  Perhaps the voltage tables are wrong.  For the first time, in Jaunty acpi_cpufreq is hard-coded into the kernel.  Maybe this is part of the problem.  You can't even undervolt the processor in 9.04 without recompiling the entire kernel, which would take forever and cause my laptop to overheat.   


In fact, my laptop runs speedstep.centrino by default, not acpi_cpufreq.  Prior to Jaunty, I could switch to acpi_cpufreq by blacklisting the speedstep-centrino module and loading the acpi_cpufreq module.  Now that they are hard-coded into the kernel I don't know how to do this.  I would like to try using acpi_cpufreq instead of speedstep-centrino for my processor, to see if that solves the overheating issue.  Does anyone know how to do this at one time simple task in Jaunty?

---

### Post by calhau0 on 2009-05-01
updating the bios solved my problem now cpu normal temp is 45-56ºC sometimes it goes to 80ºC never past that

:P

---

### Post by idlesign on 2009-05-01
I've created launchpad bug entry for that issue - [https://bugs.launchpad.net/ubuntu/+bug/370173](https://bugs.launchpad.net/ubuntu/+bug/370173)
Please confirm the problem there. If you have it :)

---

### Post by klemzy on 2009-05-01
Hi!

I recently installed Ubuntu 9.04, and ran into some "overheating" problems. My problem is that cpu fan runs all the time (in vista it didn't, it was more flexible to the temperatures). Average cpu temp is about 33-34, and it doesn't go below (vista 26-27). What I also noticed is when I open this link:
[http://www1.euro.dell.com/content/products/superview.aspx?c=si&cs=sibsdt1&l=en&pageoverride=gallery_view1&s=bsd&xdb=Z2xvYmFsOnByb2R1Y3RzOmxhcHRvcF9zdHVkaW86Zmxhc2g6bGFwdG9wLXN0dWRpby0xNTU1I3JlZ2lvbg==](http://www1.euro.dell.com/content/products/superview.aspx?c=si&cs=sibsdt1&l=en&pageoverride=gallery_view1&s=bsd&xdb=Z2xvYmFsOnByb2R1Y3RzOmxhcHRvcF9zdHVkaW86Zmxhc2g6bGFwdG9wLXN0dWRpby0xNTU1I3JlZ2lvbg==)
Temperatures go from 34 to like 50C, and if I leave tab  opened, and use another page, temperatures are stil around 40C.  When I close the tab the temperatures go slowly lower.
I don't know what might be causing this problem. Is this normal for ubuntu, that temperatures are a bit higher? I'm pretty new to this OS and I'm still learning things.
Is it maybe the gpu, I'm using open source driver?
A bit offtopic: I tried to install lm-sensors, however it displayed only sensors for cpu temps. 
I used following commands:
```
sudo apt-get install lm-sensors
```
```
sudo sensors-detect
```
I've also seen the tutorial for lm-sensors, but is it safe to use them, because they seem a bit outdated.

Does anyone has any suggestions?
Thank you in advance!

---

### Post by calhau0 on 2009-05-03
no it's not normal to have such high temperatures on this OS.

About the lm-sensors there's no problem on installing them

---

### Post by estebandid0 on 2009-05-05
Hi there

I am having this trouble also, It just appeared a few days ago.

I decided first to give it a try to Ubuntu AMD 64 on a live disk, since that day the machine change it, it started to crash and then one day it was dead.

I took it to the hp service they checked and they said that the mainboard was death, so they replaced.

Today i was installing 9.04 and so far the machines has shutdown 4 times, because of the overheating, I have not having this trouble since 7.04 and 7.10.

I am also using a fan cooler but it is not working properly. For the moment I am going back to 8.10 I am writting my master thesis and I can not loose time, If some one finds the answer please let us know to see it, 9.04 looks beautiful.

My laptop is HP tx1420us AMD64x2

---

### Post by Master Chief on 2009-05-05
Are these two buddies going nuts on your system?

/etc/xdg/autostart/trackerd.desktop
/etc/xdg/autostart/tracker-applet.desktop

You can disable them one by one by adding: Hidden=true to these files.

---

### Post by scorchedbysun on 2009-05-15
9.04 manages the CPU speed in a new way, it seems.

I had an unrelated problem, but maybe my solution can help with the overheating:

[http://ubuntuforums.org/showthread.php?t=1159923](http://ubuntuforums.org/showthread.php?t=1159923)

---

### Post by The Doell on 2009-05-16
I also had the same problem with my hp dv2700.  I upgraded to 9.04 and would overheat in 5min.  Once I updated my bios problems are gone. I hope that works for the rest of you.

---

### Post by junalmeida on 2009-05-18
I'm issueing this problem with tx2110us too (Jaunty 64), but hp did not released any bios update for me. 

System shuts down after minutes when I'm using some intensive app. On Intrepid 64, i can use the same app without overheating.

Windows Vista 32 is running good too.

:(

---

### Post by Favux on 2009-05-19
Hi junalmeida,

Maybe this applies?  It's a little extreme so be very sure you know what you are doing:  [https://wiki.edubuntu.org/LaptopTestingTeam/HPdv5z](https://wiki.edubuntu.org/LaptopTestingTeam/HPdv5z)

This user on post #554 said it worked for his TX2500:  [http://ubuntuforums.org/showthread.php?t=845911&page=56](http://ubuntuforums.org/showthread.php?t=845911&page=56)  Some other posts a page or two earlier refer to this problem too.

---

### Post by hewart on 2009-05-22
Hi everyone

A similar problem here... My laptop (Acer TM 4000) runs ubuntu nicely, but it overheats very easily. It hasn't powered off suddenly, but the difference with xubuntu 7.10 is remarkable. The cpu scaling has worked fine since the first startup, so it might not be the problem. The system runs at 600Mhz almost all the time. Also the cpu usage is similar to xubuntu and windows for normal tasks (internet, music, java, flash), that's the point.

It would be great to fix this. That's the only problem I found in this great version.

---

### Post by U2XS on 2009-05-25
> **hewart said:**
> Hi everyone
It would be great to fix this. That's the only problem I found in this great version.
I feel similarly!

I have an Acer Extensa 4420 with a ATI X1250 graphics card.  It doesn't overheat to the point of danger, but it is uncomfortably hot in comparison to my Windows XP partition.  

I started using Ubuntu **much more** since 9.04 so I can't be sure if it was the same prior to this update.

---

### Post by Oram on 2009-05-25
Hmm it's kinda odd. Ubuntu overheated like 3 times, and now it seems to run fine. I can run any program on it without it overheating, the fans run as well as they did in vista too.  Maybe an update or something?

---

### Post by cloud69 on 2009-05-26
Notice this automatic shutdown also but did not thought that it was a problem. I am also experiencing that my laptop is much hotter when running on ubuntu than in windows. Think that it is always running in performance mode. Anybody have a solution for this? Mine is a IBM Thinkpad R51 laptop. What a waste if I have to go back to windows when I am already starting to like Ubuntu.

---

### Post by CapnBoost on 2009-06-02
I didn't have this problem at all with 8.10 which was my first experience with Ubuntu.  I had it after I had freshly updated to 9.04, then it went away entirely, and now it's back with a vengeance.  I've changed my frequency stepping, fan control, etc.  It overheats and shuts down when I download and view a PDF, when I open a new tab, basically whenever it pleases.  This morning it seems to have corrupted my install because grub won't boot.

I didn't sign up for this.

---

### Post by estebandid0 on 2009-06-02
> **CapnBoost said:**
> I didn't have this problem at all with 8.10 which was my first experience with Ubuntu.  I had it after I had freshly updated to 9.04, then it went away entirely, and now it's back with a vengeance.  I've changed my frequency stepping, fan control, etc.  It overheats and shuts down when I download and view a PDF, when I open a new tab, basically whenever it pleases.  This morning it seems to have corrupted my install because grub won't boot.

I didn't sign up for this.


Be careful with that thing, I had the same problem when 9.04 just came up.  I will try to install again 9.04 next week to see if something has changed

When i just installed 9.04 my machine was over heating every time, one day the grub and boot where gone I send it to technical department, they said the mother board has a damage, they changed and works fine with 8.10, I have not tested with 9.04, I really hope it was not because of the OS.

I really think that the pavilion so far are very bad even to work with windows or ubuntu, they over heat on both systems, this is my second HP pavilion, and has the same problem, I will not recommend to anyone to buy HP.

---

### Post by CapnBoost on 2009-06-03
Well, my installation was in wubi so it was completely irrecoverable (unless i missed something- tried live ubuntu and knoppix)

Before I installed via wubi I cracked the lappy open, vacuumed it and inspected the thermal compound (replaced a year ago).

I haven't properly "tested" it since i wiped the disk, partitioned and installed a fresh Ubuntu straight to the drive (yesterday).  But, otoh, I haven't had a failure yet despite ambient temperatures similar or higher to those when I was experiencing 5 or more failures a day.

When I first replaced the factory thermal compound (splattered all over the place) with arctic silver my cpu temps dropped 5-10 C (per speedfan in windows)  If you haven't already done this I would recommend it.

---

### Post by 67GTA on 2009-06-03
For anyone having heating problems (mostly HP/Compaq) check here: [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

---

### Post by abhiroopb on 2009-06-05
I have collated all the various posts regarding this overheating issue into one ubuntuforums post...please help advise there...

[http://ubuntuforums.org/showthread.php?p=7399158#post7399158](http://ubuntuforums.org/showthread.php?p=7399158#post7399158)

---

### Post by juustomuna on 2009-07-25
I have HP NX8220 laptop with ATI Radeon Mobility X600, which overheated. I solved with this:

Install these packages from [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

libdrm2_2.4.12+git20090717.9aed44be-0ubuntu0sarvatt~jaunty_i386.deb
libdrm-radeon1_2.4.12+git20090717.9aed44be-0ubuntu0sarvatt~jaunty_i386.deb
xserver-xorg-video-ati_6.12.99+git20090723.2afc46fa-0ubuntu0sarvatt~jaunty_i386.deb
xserver-xorg-video-radeon_6.12.99+git20090723.2afc46fa-0ubuntu0sarvatt~jaunty_i386.deb

sudo dpkg -i libdrm*.deb xserver*.deb

Also, make sure that you have this in your /etc/X11/xorg.conf:

Section "Device"
        Identifier "Configured Video Device"
        Driver "radeon"
        Option "ClockGating" "true"
        Option "DynamicPM" "true"
EndSection


----------------

Also I was using Spotify, where I had to use (in winecfg) ALSA and emulation. Changed that to OSS and Full HW accelleration.

- Juusto Muna

---

### Post by Payo on 2009-10-22
I have had really bad problems with overheating on my Dell Latitude Laptop since installing 9.04 last April.

I just installed Ubuntu 9.10 (Karmic - beta) and it has solved the problem.

Yesterday it was running at 89.9 degrees C and constantly stalling and occasionally crashing today (running the same appliations) my sensors show 65.5 degrees C and no sign of it increasing.

So my advice is to upgrade as soon as Karmic comes out of Beta (just a few days now) and see if that fixes your problem.

---

