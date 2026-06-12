---
title: "No Battery Detected on Toshiba laptop [11.04]"
date: 2011-09-29
forum: Hardware
---

### Post by Gelegenheit on 2011-09-29
I've installed 64-bit versions of Ubuntu 11.04 and Linux Mint 11 inside my Toshiba 655's Windows 7 partition and have been having problems with the battery.  Last I checked on Linux Mint (uninstalled it to see if reinstalling would fix and cannot find the DVD at the moment) it said that no battery was detected.  I can't even find anything in Ubuntu.  It still runs but I have no clue how much time or charge I have left, which is a pain because I spend most of the day off of the AC cord.  It also runs pretty hot but I will worry about that later, but it might be related.

 

 I would prefer not to rely on Windows 7 just because it is easier when I prefer Linux.  I am not very proficient with Linux and have no clue how to deal with this at all, so sorry in advance to anyone who doesn't like holding people's hand through everything.  Thanks for any help.

---

### Post by matt_symes on 2011-09-29
Hi

I might have to continue this tomorrow as it's late here (unless someone else jumps in). However in the meantime.

Open a terminal and type

```
ls /sys/class/power_supply/
```

See if your battery is listed there. Here is mine.....
```

matthew@matthew-laptop:~$ ls /sys/class/power_supply/
ADP1/ BAT0/ 
matthew@matthew-laptop:~$ 
```

My battery is BAT0. If you have a battery (it may be named differently) navigate into that directory.

Again, this is mine.

```

matthew@matthew-laptop:~$ ls /sys/class/power_supply/BAT0/
alarm               charge_full_design  current_now         manufacturer        power/              serial_number       subsystem/          type                voltage_min_design
charge_full         charge_now          device/             model_name          present             status              technology          uevent              voltage_now
matthew@matthew-laptop:~$
```

Look for something along the lines of

```
matthew@matthew-laptop:~$ ls /sys/class/power_supply/BAT0/charge_now 
/sys/class/power_supply/BAT0/charge_now
matthew@matthew-laptop:~$ cat /sys/class/power_supply/BAT0/charge_now 
3194000
matthew@matthew-laptop:~$ cat /sys/class/power_supply/BAT0/charge_full
3194000
matthew@matthew-laptop:~$ 

```

Do you have something similar ? If do do it will eliminate part of your system. Post your results back here.

Kind regards

---

### Post by Gelegenheit on 2011-09-29
```
chris@ubuntu:~$ ls /sys/class/power_supply/
ACAD
chris@ubuntu:~$ ls /sys/class/power_supply/ACAD
device  online  power  subsystem  type  uevent
chris@ubuntu:~$ ls /sys/class/power_supply/ACAD/type
/sys/class/power_supply/ACAD/type
chris@ubuntu:~$ ls /sys/class/power_supply/ACAD/power
autosuspend_delay_ms    wakeup               wakeup_last_time_ms
control                 wakeup_active        wakeup_max_time_ms
runtime_active_time     wakeup_active_count  wakeup_total_time_ms
runtime_status          wakeup_count
runtime_suspended_time  wakeup_hit_count
chris@ubuntu:~$ ls /sys/class/power_supply/ACAD/device/driver
ACPI0003:00  bind  uevent  unbind
chris@ubuntu:~$ ls /sys/class/power_supply/ACAD/charge_now
ls: cannot access /sys/class/power_supply/ACAD/charge_now: No such file or directory
```It isn't showing the same code as in your example so I played around in the terminal a bit and posted what I found.  Tell me if you need me to go into anything else, please ask and I'll get back asap.  Thank you so much for helping, Matt.

---

### Post by matt_symes on 2011-09-30
Hi

> I've installed 64-bit versions of Ubuntu 11.04 and Linux Mint 11 inside my Toshiba 655's Windows 7 partition

This is a WUBI install ?

As far as i can tell, your battery is not being recognised. I think ACAD is your power adaptor (but i am not 100% sure as i have never owned a Toshiba 655). You do not have an entry for a battery. This would mean the issue is in a lower part of the operating system; maybe an ACPI issue.

Can you run from a LiveCD/USB and check to see if the battery is recognised from there. That would help to eliminate/implicate a WUBI issue.

Kind regards

---

### Post by bcbc on 2011-09-30
It's not a wubi issue. [http://www.linuxquestions.org/questions/slackware-14/battery-detection-issue-acpi-878227/](http://www.linuxquestions.org/questions/slackware-14/battery-detection-issue-acpi-878227/)

and [http://ubuntuforums.org/showthread.php?t=1641931](http://ubuntuforums.org/showthread.php?t=1641931)

---

### Post by matt_symes on 2011-10-01
Hi
 
> **bcbc said:**
> It's not a wubi issue. [http://www.linuxquestions.org/questions/slackware-14/battery-detection-issue-acpi-878227/](http://www.linuxquestions.org/questions/slackware-14/battery-detection-issue-acpi-878227/)

and [http://ubuntuforums.org/showthread.php?t=1641931](http://ubuntuforums.org/showthread.php?t=1641931)

Cheers for this. A custom dsdt :shock: ? Year of the Linux desktop :shock: ? As much as i love Linux ....

Kind regards

---

### Post by Gelegenheit on 2011-10-01
Should I try seeing if Ubuntu Netbook works or if I should try modifying the kernel (That will require help).  From what I understand, Toshiba does something differently with their laptops (like a different hardware format or something).

I'm not averse to using Windows 7 while not on the AC.  I just find it a little frustrating that I have to use Linux based on what my power situation is rather than the job I need to do.

---

### Post by bcbc on 2011-10-01
There is no Ubuntu-netbook in 11.04. The fact that wubi offers it is a bug.

In any case, the problem you are having is not likely to be different between 'flavours'.

So... I agree with matt_symes that the whole dsdt thing is overkill. I've read in those threads that the battery is working - just there is no indicator shown. However it's been reported that the battery light turns red when it is low - so it is still functioning normally - and you get a warning if it's low.

Also, there is release 11.10 coming out in a couple of weeks. You could try that.

My advice is: 
1. make sure your bios is up to date. This might make a difference.
2. try to make contact with other people who are using Ubuntu with this netbook (post on the threads as they are likely subscribed). That way you'll hear if they've found a simpler workaround.
3. create or subscribe to the bugs so you get updates.
4. try Ubuntu by creating a bootable USB - so you can see whether the problem is fixed before installing. There're 3 active releases: 10.04, 10.10 and 11.04 - and soon 11.10 - that may have different results.

Good luck

---

### Post by Gelegenheit on 2011-12-02
I realize it has been a while but the release of Linux Mint 12 and the  realization of how little I use Windows 7 native applications when at  school (Most often use Firefox, Thunderbird, and a port of Tomboy Notes)  made me miss Linux and redouble my efforts to solve the mystery of the  missing battery.

During my quest, I came across two links that seem to explain and fix the problem but most of it is utter gibberish to me.
[http://techinterplay.com/fix-toshiba-battery-issue-linux.html](http://techinterplay.com/fix-toshiba-battery-issue-linux.html)
[http://blog.michael.kuron-germany.de/2011/03/patching-dsdt-in-recent-linux-kernels-without-recompiling/](http://blog.michael.kuron-germany.de/2011/03/patching-dsdt-in-recent-linux-kernels-without-recompiling/)

Unless  someone can tell me a better way that doesn't leave me going "Umm...",  I've opted to see if I can get the patch by the author of the  TECHINTERPLAY article to work on my Linux Mint inside Windows  partition.  But, before I start this, I must ask if this will, in any  way, affect my Windows partition.  I would rather know that modifying  DSDTs is perfectly safe and won't turn an annoyance into Armageddon  (backup in progress) if I do this wrong before I start doing it.

Many thanks.

---

### Post by Gelegenheit on 2011-12-02
The patch works.  Not sure I'm happy to see how quickly my battery drains on Linux, though.

---

### Post by matt_symes on 2011-12-03
Hi

I'm glad a custom dsdt works for you. 

Not many people would have tried what you did :popcorn:. It's not too hard but not a job for your average user.

You may have to do that for each kernel release though, so you may want to pin your kernel so it does not get upgraded. Or you can just make sure you don't upgrade you kernel.

Kind regards

---

### Post by bcbc on 2011-12-03
> **Gelegenheit said:**
> The patch works.  Not sure I'm happy to see how quickly my battery drains on Linux, though.

There is a kernel bug that causes increased power use and it's just been fixed now (in the kernel that will be used for the next release 12.04 - and I'm not sure if there's a plan to backport it to prior releases). That probably explains the shorter battery time. ([http://linux.slashdot.org/story/11/11/11/2036245/linux-kernel-power-bug-is-fixed](http://linux.slashdot.org/story/11/11/11/2036245/linux-kernel-power-bug-is-fixed))

---

