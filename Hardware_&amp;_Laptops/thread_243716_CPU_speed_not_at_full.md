---
title: "CPU speed not at full?"
date: 2006-08-25
forum: Hardware &amp; Laptops
---

### Post by jperez on 2006-08-25
Hey guys,

I have a stumper for you.  My laptop has the maximum capacity to run at 1Ghz and being a speed step processor, it switches between the two speeds when the AC power is on and off the device.  Well, I just placed the CPU Monitor and my AC is plugged in.  It should be reading 1Ghz or around that amount.  I'm only getting a reading of 731Mhz.  Anyone know how to crank out the extra power from the CPU?  I want the CPU to run at the fiull speed allowed without overclocking.  Anyone got any ideas?  Thanks guys!

SPECS:
Dell Inspiron 8100
Ubuntu - Dapper Drake 6.06 LTS i386 (Through Upgrade)
CPU: 1Ghz/733Mhz Intel PIIIm SpeedStep
RAM: 256MB

Any other specs I should give are available on request.

Jesse~

---

### Post by VirtuAlex on 2006-08-25
what when you're running glxgears? it does not speed up either?

---

### Post by Belyel on 2006-08-25
If you are using the CPU monitor that comes in gnome, you can click directly on the icon on your deskbar and select a speed.  I've found that ubuntu does a good job of scaling your processor speed to keep the system quiet and cool, so I don't worry about the proc not running full speed on AC, as it switches to full speed when I need it to.  You can check the clock value of your processor by typing ```
sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
```into a terminal.  I have found that sometimes the cpumonitor does not correctly display my processor speed after manually changing it unless I type that code (only for my second processor though).

---

### Post by jperez on 2006-08-25
Well, I input the command and it shows 731500.  I tried directly clicking on the icon and nothing.  I right clicked on it and chose Properties and all it gave me was the configuration window for the CPU Frequency Scaling Monitor.  Is there a different way of cranking out my 1Ghz?  I know that it would help my laptop since Windows XP Home (first partition) works at 1Ghz while on the AC and 733Mhz on Battery.

Jesse~

**EDIT**
Quick edit!  After running the command, I didn't close the Terminal.  After posting, I exited out and the CPU monitor jumped to 993 for about 1 second and went back to 731.  Glitch or what's going on?

**EDIT #2**
I just noticed something rather odd!  The reason why owners of the Inspiron 8100 experience studdering during use is because it's trying toi figure out whether to use 1Ghz or 733Mhz.  I figured this was the case, but now I know for sure.  Whenever the studder happens, the CPU is jumping to 1Ghz but jumping back down to 733Mhz.  Is there a way to make the CPU stay at a constant 1Ghz since the CPU monitor on my panel won't let me do it?  Thanks guys for all your help.

---

### Post by VirtuAlex on 2006-08-25
why do you want to force it to run where it can walk? If you browsing internet there is no point to overload your processor, it will be just running empty cycles. When you run something processor intensive it will swithch automatically. Seriously run glxgears. It should immediately jump to 1GHz

---

### Post by jperez on 2006-08-25
**VirtuAlex**, you were right.  Now it's showing 997Mhz.  Thanks buddy.

Jesse~

---

### Post by daller on 2006-08-26
I'm running on an Inspiron 8600

It  stays at 600MHz no matter what I do!

It should be 1300MHz, but it doesn't go there, even with 100% load at 600MHz...

What can Ido to fix it?

---

### Post by Castar on 2006-09-30
> **daller said:**
> I'm running on an Inspiron 8600

It  stays at 600MHz no matter what I do!

It should be 1300MHz, but it doesn't go there, even with 100% load at 600MHz...

What can Ido to fix it?

Same thing here with a Latitude X1 :(

---

### Post by KingArthur10 on 2006-09-30
You're both running the i686 kernal aren't you?

I had the same problem when I installed it.  The 386 kernal is the only one that works on my laptop right now (Pentium M).  A bug report has been filed long ago, and they are still working on it, from what I hear.

---

### Post by OpticalIllusion on 2006-09-30
First, you need to add the CPU Frequency Scaling Monitor to one of your panels.

Next, you need to put in

```
sudo chmod +s /usr/bin/cpufreq-selector
```

Then put in

```
sudo dpkg-reconfigure gnome-applets
```
Answer YES to the question that it asks about setting the suid of the cpufreq-selector executable.

Now, you should be able to left click on the CPU Frequency Scaling Monitor and manually change your CPU speed.

---

### Post by Castar on 2006-09-30
> **KingArthur10 said:**
> You're both running the i686 kernal aren't you?


For my part, I'm running the 2.6.17-10-generic kernel coming with the latest Edgy updates.

> **OpticalIllusion said:**
> 
Now, you should be able to left click on the CPU Frequency Scaling Monitor and manually change your CPU speed.

I'm running Kubuntu. Still, the point isn't really to change it manually but the system to change it automatically... :( 

At least, if there is a filed bug report then it should be corrected, right?

---

### Post by OpticalIllusion on 2006-09-30
> **Castar said:**
> For my part, I'm running the 2.6.17-10-generic kernel coming with the latest Edgy updates.



I'm running Kubuntu. Still, the point isn't really to change it manually but the system to change it automatically... :( 

At least, if there is a filed bug report then it should be corrected, right?
Oh, I was refering to the original poster.  He wanted to get the maximum clock speed out of his CPU and that's how you can do it.

Sorry I can't help you though.  I haven't used Kubuntu.

---

### Post by KingArthur10 on 2006-09-30
I'm still on Dapper (Edgy won't boot for me), but if you're having CPU freq scaling issues on the newest kernel, I'd search launchpad and see if there are any bug reports.  If not, then post one so they can fix it :-)

---

### Post by JayTee on 2006-10-08
I tried this on my system. I have a Pentium D 940 dual core. It will only let me adjust the CPU speed of CPU0 but won't let me adjust the speed of CPU1. Is this a bug in the i686 kernel? I'm running version 2.6.15-27 of the i686 kernel.

---

### Post by daller on 2006-10-09
The fix for me, was to upgrade to edgy...

If that can be clasified as a fix.

---

### Post by rushin_911 on 2006-11-13
Hello

I apologize for bumping this up but I'm having similar problems and tried to fix them with no answer

I'm running on Ubuntu Edgy currently, which I had upgraded to from dapper because I had these problems on dapper.

My laptop is a dell inspiron 6000d, and up until a few days ago (perhaps a week? didn't notice it till lately) it had been running fine. However now it's stuck at 800Mhz. No matter what I try to do it doesn't go increase beyond that, even though my laptop is capable of processing at 2.0 Ghz. It does show the different speeds with the cpufreq-selector app, however if I choose any speed it automatically chooses 800Mhz, the lowest speed :( .

I tried uninstalling powernowd, uninstalling gnome-applets, reinstalling them etc.. Tried cpufreq-utils (which I used to use back when I was on Debian). I made sure that anything relating to the kernel was 386 (so I uninstall 686 / generic modules etc...) and reinstalled the 386 ones. Still the problem isn't solved. I tried KDE to see if it might work, and used kpowersave - still no solution.

So here I ask, can anyone help me out please? If there's anymore information you need I will happily provide it.

---

### Post by Unicast on 2006-11-13
Have a read of my thread: [http://www.ubuntuforums.org/showthread.php?t=283060](http://www.ubuntuforums.org/showthread.php?t=283060) for my tale of woe!

There's a bug in the cpufreq.c driver that basically results in scaling_max_freq = scaling_min_freq (look in /sys/devices/system/cpu/cpu0/cpufreq)

Have a look at the bug report: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36014](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36014)

The most useful bit in there is the hack for the cpufreq.c driver. Unfortunately this also requires a kernel recompile, so that the hacked driver gets compiled into the kernel.

---

### Post by rushin_911 on 2006-11-13
> **Unicast said:**
> Have a read of my thread: [http://www.ubuntuforums.org/showthread.php?t=283060](http://www.ubuntuforums.org/showthread.php?t=283060) for my tale of woe!

There's a bug in the cpufreq.c driver that basically results in scaling_max_freq = scaling_min_freq (look in /sys/devices/system/cpu/cpu0/cpufreq)

Have a look at the bug report: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36014](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36014)

The most useful bit in there is the hack for the cpufreq.c driver. Unfortunately this also requires a kernel recompile, so that the hacked driver gets compiled into the kernel.

Thank you very much. I'm going to recompile the kernel.

It's unfortunate that this has to be done, since I'm sure such a task would be too much for the average joe who just wants to check his e-mail and play games etc...

---

