---
title: "Thinkpad questions"
date: 2008-11-09
forum: General Help
---

### Post by bluppfisk on 2008-11-09
Hi,

I've recently wiped Windows off my Thinkpad T42 and replaced it with Intrepid. Not too happy just yet about how it runs, here's why (I don't want to start a thread for every problem, should I?):

- Fan is always on. I installed tpfand to adjust fan toggle temperatures but it seems my CPU is much hotter than in Windows XP.

- Related to that, how can I enable the CPU's power saving mode. Now the battery will drain in 3 hours; in Windows the max was 5 or 6.

- Center button does not work. In Firefox it will perform a middle click (close tab, open link in new tab), but its scrolling function does not do anything.

- Harddrive advanced protection system (HDASP) does not seem to work.

- I would like to have my bluetooth and wireless toggle buttons separated instead of concentrated on one button. I want to know what I disable when. Is it possible to make fn-F6 disable bluetooth only and fn-F5 wireless only?

---

### Post by m_l17 on 2008-11-10
1-2. Do you have cpfrequtils installed? If not install it and should set your cpu governor to ondemand, but you can change it to powersave.

To install:

```
sudo apt-get install cpufrequtils sysfsutils
```

If you have cpufrequtils or after you install it. You can check what governor is being used by:

```
cpufreq-info
```

Will output something like this:

> cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.10 GHz
  available frequency steps: 2.10 GHz, 2.00 GHz, 1.80 GHz, 1000 MHz
  available cpufreq governors: powersave, ondemand, conservative, userspace, performance
  current policy: frequency should be within 1000 MHz and 2.10 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
analyzing CPU 1:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.10 GHz
  available frequency steps: 2.10 GHz, 2.00 GHz, 1.80 GHz, 1000 MHz
  available cpufreq governors: powersave, ondemand, conservative, userspace, performance
  current policy: frequency should be within 1000 MHz and 2.10 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.

To change the governor:

edit ```
$ sudo nano /etc/sysfs.conf
```

Read the file it has examples, if you have a dual core you will have to add two lines instead of one. Like cpu0 and cpu1.

Here is a more detailed explanation:

[http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html]("http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html")

3. Try this: [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#TrackPoint_under_Ubuntu_8.10_using_HAL]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#TrackPoint_under_Ubuntu_8.10_using_HAL")

---

### Post by kaptengu on 2008-11-10
3. For the middle-button I use this under Configured Mouse in xorg.conf on my X41:
```

	Option		"Emulate3Buttons"	"true"
	Option 		"EmulateWheel"		"true"
	Option 		"EmulateWheelButton"	"2" 

```

[EDIT]
Not sure if this still works in 8.10 though. Read somewhere that Input Devices are ignored. Have a look at the link m_l17 provided.
[/EDIT]

4. hdaps for linux is still under development, but you might want to have a look at this:
[http://hdaps.sourceforge.net/](http://hdaps.sourceforge.net/)

---

### Post by bluppfisk on 2008-11-10
Thanks both, that was really helpful! Now some more questions related to this:

1. Is there an easy way to change governors? I mean, in Windows, I just click on the battery icon and choose a different powersaving scheme, not so in Ubuntu. Any ideas on getting the same easy adjustment?

2. Is there a way to have Compiz disabled automatically upon activation of the powersave governor? Of course, my 4 year old thinkpad does not do graphics too well when the speed is clocked down to 600 Mhz.

3. Will the ATi card be clocked down automatically too (in Windows, there's a powersave modus for the card that is activated when the powersave scheme is selected). If not, how can I beget this effect?

edit: and actually, as a fourth question:

4. Shouldn't Compiz be completely GPU-dependent? I.e. when I underclock only my cpu, there should be no slowdown in its performance?

Extra questions- oh god I'm piling them up.

5. HDAPS: the site you gave seems no longer to work. I then went to sourceforge.net's download section ([http://sourceforge.net/project/showfiles.php?group_id=138242](http://sourceforge.net/project/showfiles.php?group_id=138242)) but I have no idea what to grab and much less how to install it. Any hints there?

6. Any ideas about disseminating functionality of the fn-F5 combination?

Thanks a lot!

---

### Post by ju2wheels on 2008-11-10
Are you truly sure that fan is on? My T42 ran hotter with Hardy because the fan was not enabled by default by Ubuntu. I havent installed Intrepid on it though so I dont know if that has changed.

I would recommend looking through [http://www.thinkwiki.org/wiki/Category:T42](http://www.thinkwiki.org/wiki/Category:T42) that is where I found all the information to configure my fan and make sure it was working properly and not causing my laptop to overheat.

---

### Post by kaptengu on 2008-11-10
Here you can find some information on processor scaling:
[http://ubuntuforums.org/showthread.php?t=597998](http://ubuntuforums.org/showthread.php?t=597998)

About the HDAPS:
[http://www.krizka.net/2008/01/23/thinkpad-x61-tablet-tilt-detection-and-ubuntu-hardy-heron/](http://www.krizka.net/2008/01/23/thinkpad-x61-tablet-tilt-detection-and-ubuntu-hardy-heron/)
(I haven't tried this. Not sure I recommend it for serious use)

---

### Post by sdjcwcba on 2008-11-11
Unfortunately, the link posted above will not allow you to actually stop the hard drive when a bump is detected.

For 8.04 try [http://suchaxplore.blogspot.com/2008/08/active-protection-system-in-ubuntu-8041.html]("http://suchaxplore.blogspot.com/2008/08/active-protection-system-in-ubuntu-8041.html") 

See [http://www.thinkwiki.org/wiki/How_to_protect_the_harddisk_through_APS]("http://www.thinkwiki.org/wiki/How_to_protect_the_harddisk_through_APS") for more in depth information about HDAPS on newer kernels (on 8.10, for example)

---

### Post by Lord Xeb on 2008-11-11
I wonder if that HDAPS will work one my T43... Also, my T43 runs nearly perfectly with Ubuntu 8.10 except I do not have HDAPS

---

### Post by sdjcwcba on 2008-11-12
Those patches will work on all HDAPS enabled Thinkpad models.

However, I have no idea how to compile/patch the Zen-Sources kernel that they recommend.

See [http://ubuntuforums.org/showthread.php?t=979155]("http://ubuntuforums.org/showthread.php?t=979155") and feel free to bump the thread if you also require assistance :)

---

### Post by bluppfisk on 2008-11-12
Hi,

I installed hdaps-utils and the tp_smapi 0.39, but when I try to run hdaps-gl (even though it exists) it says:

sander@sander-laptop:~/Desktop/tp_smapi-0.39$ dir /usr/bin/hdaps*
/usr/bin/hdaps-gl  /usr/bin/hdaps-pivot
sander@sander-laptop:~/Desktop/tp_smapi-0.39$ /usr/bin/hdaps-gl
open: No such file or directory

wtf?

---

### Post by kaptengu on 2008-11-12
Install it with this instead:
```
sudo apt-get install hdapsd hdaps-utils
```
After that you can just execute:
```
hdaps-gl
```
About patching the kernel, for the actual protection, I think you should be careful. Check this link, and try to understand what you are doing, if you wish to proceed:
[http://suchaxplore.blogspot.com/2008/08/active-protection-system-in-ubuntu-8041.html](http://suchaxplore.blogspot.com/2008/08/active-protection-system-in-ubuntu-8041.html)
If it doesn't work with that tutorial, the troubleshooting will be pretty heavy I guess.

---

### Post by kaptengu on 2008-11-13
I followed this guide:
[http://suchaxplore.blogspot.com/2008...untu-8041.html](http://suchaxplore.blogspot.com/2008...untu-8041.html)
compiled the patched kernel and managed to get hdaps to work on my X41.
Just remember you need about 3GB of free diskspace during the kernel compilation.

---

### Post by bluppfisk on 2008-11-14
I still get hdasp-gl: no such file or command... Even though I can _see_ the binary.

---

### Post by bendt on 2009-01-06
The no file problem is due to the hdaps module not being loaded.

Run this to load the module (valid for 8.10 at least): 
```
sudo modprobe hdaps
```

To enable hdaps at boot time:
```
echo 'hdaps' >> /etc/modules
```

---

