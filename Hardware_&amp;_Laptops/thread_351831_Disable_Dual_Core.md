---
title: "Disable Dual Core"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by FFfanatic on 2007-02-02
I have an AMD 64 Turionx2 and I need to know, is there a way to temporarily disable one of them when on running on battery so that I can extend my battery life, and then when plugged in, have it bring the 2nd processor back to life. Also, if this is possible, have that single processor in ondemand mode so I get a bit of performance at least. (Steps between 800MHz/800mV and 1600MHz/1100mV)

---

### Post by FFfanatic on 2007-02-02
After a little bit of searching, I found these pages:
[http://www.novell.com/documentation/nw42/index.html?superenu/data/hzzyzhr5.html](http://www.novell.com/documentation/nw42/index.html?superenu/data/hzzyzhr5.html)
[http://lists.apple.com/archives/mt-smp/2002/Feb/msg00013.html](http://lists.apple.com/archives/mt-smp/2002/Feb/msg00013.html)
[http://oracle-rac.blogspot.com/2005/11/disabling-cpus-on-linux-part-one.html](http://oracle-rac.blogspot.com/2005/11/disabling-cpus-on-linux-part-one.html)
but I'm not sure what the commands would be to check if my computer supports dynamic interrupt distribution and recovery. Anyone have any ideas?
PS for the 3rd link, I searched for the grub.conf file on filesys but I couldn't find a plain grub.conf. And if this does work, is there any way to make a kernel to run on one processor through this method and a 2nd kernel to have both?
Ie. in grub boot up screen:
...kernel..._1_cpu
...kernel..._2_cpu
....

---

### Post by FFfanatic on 2007-02-05
bump
Anyone?

---

### Post by FFfanatic on 2007-02-12
I'm gonna re-phrase my question to maybe shed some light on the subject. At the moment I am running the 2.6.17-10-generic kernel which supports SMP, so both processors are available. What I would like is to have just one processor available, the other turned off, so that I can increase my battery life by 1.5-2x when at school. Is there a way to do this in my current kernel, OR would I need to make a kernel that doesn't support SMP so that only one of the processors gets used, and the other is off? Also, I don't care if I have to reboot in between to change kernels to achieve dual core performance. And one final note, my BIOS is locked down so I can't disable dual core through that. Hope that helps.

---

### Post by RandomJoe on 2007-02-12
I've not heard of a way to do this dynamically.  However, if you could you aren't going to see a 1.5-2x increase in battery life just from this.  The bulk of the power consumed is by the LCD backlight and the hard drive.  Throw in everything else that will still be consuming power, whether running one or two cores, and you might not even notice the difference between one and two cores.

Best bet for extending battery life would be to turn the backlight down, make the hard drive stop spinning as much as possible (which can be a challenge on Linux, due to the way some daemons work there can be frequent writing to the drive - there are some HOWTOs around that discuss modifying settings to correct that), and be sure you CPU frequency scaling is functioning as efficiently as possible.

You could also change the speed scaling governor so that it just keeps the processor at a low speed all the time when on battery.  Some (all?  not sure...) systems scale the processor voltage back when the speed scales back, which will also help reduce consumption.  (Primarily through reduced heat, so the fans don't have to run.)

---

### Post by FFfanatic on 2007-02-12
I get your point of <1.5x, probably would get closer to 1.25 since my processors run at (see 1st post) and turning down backlight, etc, I've done and now have a little over 3 hrs life. I've already got it governed at 800MHz/800mV but I want to lower this somehow, in XP I used rmclock to find I could run it at 925mV on 1.6GHz but I couldn't set my low spec different. But I digress, do you think that my single kernel without SMP support has a chance? Also, how could I shut down unused processes to help reduce power? I would like to turn off: USB, wireless, ethernet, etc., but be able to call them back quickly if needbe.

---

### Post by RandomJoe on 2007-02-12
I don't know if running a non-SMP kernel would help - I imagine the second core would still be powered.  I guess the only thing to do there is try it and see what your runtime is like.

In the same vein, you can disable other devices by just not loading the drivers, but again I imagine they would still be powered.  In some cases, there would be some savings since they aren't active so perhaps every bit helps. 

The trick is in how to do that - the first thing that comes to mind is to put together two blacklists (/etc/modprobe.d/blacklist) that would get swapped out - one for "on AC" and one for "on battery".  Not sure, though, if you could swap them out early enough in the boot sequence to work.  Another possibility is just to blacklist all the "unnecessary" peripherals, then have a script you run manually or that runs later in the boot sequence that detects "on AC" that adds those modules back in.

Shutting down unneeded daemons is always a good idea since it'll free up resources for other uses.  Some of the running services are in System -> Administration -> Services, but there are still a few I'm not sure of the location in the GUI - you may have to dig into the init scripts.  I'm sure there are some HOWTOs floating around that go into detail on this.  (I'm "old school" - I just edit init scripts directly, sometimes managing to mess up other things in the process! ;) )

---

### Post by dresnu on 2007-05-19
I was searching for a way to turn off one core too, but this guy is most probably right [http://www.macsimumnews.com/index.php/archive/macosg_how_to_extend_your_battery_life](http://www.macsimumnews.com/index.php/archive/macosg_how_to_extend_your_battery_life).

Check point 14.

---

### Post by philheaton on 2008-06-12
disable second core:

```
echo 0 | sudo tee /sys/devices/system/cpu/cpu1/online
```

re-enable second core:

```
echo 1 | sudo tee /sys/devices/system/cpu/cpu1/online
```

works on a core 2 duo, not sure about amd systems.

phil

---

