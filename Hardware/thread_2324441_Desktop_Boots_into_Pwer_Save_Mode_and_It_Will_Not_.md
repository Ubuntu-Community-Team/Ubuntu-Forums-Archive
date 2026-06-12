---
title: "Desktop Boots into Pwer Save Mode and It Will Not Wake Up"
date: 2016-05-13
forum: Hardware
---

### Post by Plumtreed on 2016-05-13
I have a Lenova M58 Thinkcentre 4GB Ram.....I recently replaced the VGA cable which was connected to the 'on-board' graphics and connected a DVI/Display port cable. The PC was previously a business use only machine. This cable change brought the Ati Radeon Hd 3470 Pci-E Video card into play, probably for the first time. Much like a new installation.

When I checked the card with the terminal using "sensors" it reported high temperatures for the GPU, from 65 to 72 degrees also suggesting that 120 was critical. I searched via google and learned that by entering Radeon.dpm=1 in grub would bring the temp down, which it does very effectively! The temp came down to the 40s and 50s. 

The downside is that this seems to have introduced a 'Boot-up' problem.......the monitor regularly boots to 'Power-Save' mode and it is impossible to wake it up with the keyboard or mouse. A reboot is necessary with an edit to remove the grub phrase Radeon dpm=1. This problem seems to be irregular and the machine can go quite happily until it decides to fail again.

My first question is.......should I be concerned about a GPU temperature in the70degees C .........this is not a gaming unit, nor is the demand ever excessive?

My second question then is ......how do I get the unit to boot consistently?

---

### Post by DuckHook on 2016-05-13
GPUs do run hot. My nVidia chips on older machines never go below 65°C. So far, it's been going on 8 years with no problems, but this doesn't speak to your situation which involves a different chip.

It seems a bit on the high side of normal. You mentioned that this is secondhand.

[LIST=1]
[*]Is the fan working?
[*]Also, try blowing out the fan-space with a can of compressed air. Be careful. Immobilize the fan first to prevent damage. Also, blow from the exhaust side first. Dust tends to get sucked in through the intake and you must reverse the flow for best results.
[*]If you are the sort who likes to take things apart and put them back together again, open the unit up and check to see that the thermal paste is still effectively transferring heat from GPU to heat sink.
[*]
[/LIST]

The radeon.dpm=1 switch just activates dpm management in older cards like yours and shouldn't have any bad effects as far as I know. However, it is meant to be used with additional parameters like "battery", "balanced", or "performance", in ascending order of load and heat. Given what you have stated, you probably just want "battery" as the lowest performance but lowest heat mode. Will get back to that in a moment.

Your disappearing screen problem may be due to another cause altogether. You have an on-board GPU installed that may be preempting your ATI card from time to time. Your system may actually be fine, just sending its output to the wrong GPU. The easiest way to check for this is to plug your monitor into the VGA port of the other card the next time you get a black screen. If you get a picture, you've diagnosed the problem.

The next steps may help to solve both your problems. Please post back the output of:```
ls -la /sys/class/drm
``````
xrandr
``````
lspci -vk | grep -iA13 vga
```...please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by Plumtreed on 2016-05-13
The fan is working. The Radeon card has been installed in the pc for many years but has never had a monitor plugged into it?.....I will give the card a clean to see if that improves things enough.

Just to clarify, I have not experienced any monitor problems when I operate without the DPM=1 switch. Does this make sense? .......this may mean I should consider this an overheating GPU difficulty. When I open the box fully the temp seems to drop about 5 degrees.

Thanks

---

### Post by DuckHook on 2016-05-13
> **Plumtreed said:**
> The fan is working. The Radeon card has been installed in the pc for many years but has never had a monitor plugged into it?.....I will give the card a clean to see if that improves things enough.

Just to clarify, I have not experienced any monitor problems when I operate without the DPM=1 switch. Does this make sense? .......this may mean I should consider this an overheating GPU difficulty. When I open the box fully the temp seems to drop about 5 degrees.

ThanksI doubt that the issue is overheating because the card runs cooler with DPM enabled. If temperature is the culprit, it should have trouble without DPM. Speculation in the absence of data won't get us far. The first order of business is posting back those outputs.

---

### Post by bdoe on 2016-05-14
If you're no longer using the onboard graphics, do you have it disabled in BIOS? As DuckHook alluded to, it could be causing a conflict. It could be just a coincidence that you've had no problem without the DPM flag set. Also, are you using the mesa radeon driver, or the proprietary ATI driver? It's possible the opensource driver might have issues with the DPM flag.

---

### Post by Plumtreed on 2016-05-14
As suggested, the following output was produced

```
total 0
drwxr-xr-x  2 root root    0 May 14 15:41 .
drwxr-xr-x 56 root root    0 May 15  2016 ..
lrwxrwxrwx  1 root root    0 May 14 15:42 card0 -> ../../devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0
lrwxrwxrwx  1 root root    0 May 14 15:42 card0-DP-1 -> ../../devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0/card0-DP-1
lrwxrwxrwx  1 root root    0 May 14 15:42 card0-DP-2 -> ../../devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0/card0-DP-2
lrwxrwxrwx  1 root root    0 May 14 15:42 controlD64 -> ../../devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/controlD64
lrwxrwxrwx  1 root root    0 May 14 15:42 ttm -> ../../devices/virtual/drm/ttm
-r--r--r--  1 root root 4096 May 14 15:42 version
```


```
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 8192 x 8192
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
DisplayPort-1 connected primary 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9*+   75.0  
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
```

```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV620 PRO [Radeon HD 3470] (prog-if 00 [VGA controller])
	Subsystem: Dell Device 3243
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fc200000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at 2000 [size=256]
	[virtual] Expansion ROM at fc220000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
```

Thanks for your help

---

### Post by Plumtreed on 2016-05-14
> **bdoe said:**
> If you're no longer using the onboard graphics, do you have it disabled in BIOS? As DuckHook alluded to, it could be causing a conflict. It could be just a coincidence that you've had no problem without the DPM flag set. Also, are you using the mesa radeon driver, or the proprietary ATI driver? It's possible the opensource driver might have issues with the DPM flag.

It is a standard ATI Radeon driver and, no, I have not disabled the onboard graphics in BIOS..............and also, your observation regarding the coincidence is very valid because it is very hard to reproduce the problem when I try.

Thanks

---

### Post by DuckHook on 2016-05-14
The good news is that your output shows no conflict with your on-board GPU. It doesn't even show up on *lspci*, so you don't need to go through extraordinary measures to disable it. That eliminates one worry.

This means that your problem is contained in the combo of your video card/driver/kernel parameters and your initial instincts may be correct: the radeon.DPM=1 switch may be the problem. A quick Google search shows that others have experienced this problem as well. [Here]("https://bugs.freedesktop.org/show_bug.cgi?id=90889") is one such bugzilla report.

Since you said you wanted to hunt down this problem, the next time your system freezes up, please try the following:

[LIST=1]
[*]At next occurrence, try <Ctrl>+<Alt>+<F1> to get to a command line TTY from where you can diagnose the issue and also shut the system down cleanly with *sudo poweroff*.
[*]
[*]If that doesn't work, try to *ssh* into your machine. This is only practicable if you have another computer you can use to ssh into the balky one. You first have to set your balky machine up as an ssh server. Instructions [here]("https://help.ubuntu.com/lts/serverguide/openssh-server.html").
[*]
[*]If both the above fail, then here is a safe shutdown method so that you won't cause possible disk and file corruption the next time your computer freezes. It's called the *REISUB* method and instructions are [here]("http://www.howtogeek.com/119127/use-the-magic-sysrq-key-on-linux-to-fix-frozen-x-servers-cleanly-reboot-and-run-other-low-level-commands/?PageSpeed=noscript").
[/LIST]
The point in #1 and #2 above is to not only to shut down cleanly, but to allow you to get to the logs which might tell us something useful. In particular, *dmesg* and *kern.log*

*dmesg* can be invoked simply by typing:```
dmesg
```The output is long, so it is best to pipe it to a file with:```
dmesg > ~/Desktop/dmesg
```...which will create a file on your desktop called *dmesg*.

*kern.log* is a little more complicated, and needs to be shown (and piped to its own similar file) with:```
cat /var/log/kern.log > ~/Desktop/kern.log
```When you recover, post both files back to this thread as attachments.

If you don't care to go to all of the above trouble, then the best course of action for now would seem to be: turn off DPM and live with the higher GPU temperature. 70°C is not excessively high, and the risk of disk/file corruption in the event of a forced physical power-down may not outweigh the marginally increased wear and tear on your system.

---

### Post by Plumtreed on 2016-05-14
Thanks for your help, but the problem is getting harder to replicate so I will use 'watchful waiting' over the next few days to confirm that things have settled before rushing into other ideas.

---

### Post by DuckHook on 2016-05-15
If it recurs, then in addition to the logs, please also post:```
uname -a
```and:```
lsb-release -a
```I will continue subscribing to this thread for another week.

---

### Post by Plumtreed on 2016-05-15
When I interrupted the Grub Boot process via the Edit process and manually introduced 'radeon.dpm=1' the process was allowed to proceed successfully and the GPU temperatures operated at the lower and more reasonable temperatures.

When I tried to effect the same change permanently in /etc/default/grub the process failed and the monitor dropped out to 'power save mode'.

It occurred to me that the edit interruption was similar to a grub 'timeout' so I introduced a timeout=10 to the Grub Boot sequence just prior to the radeon.dpm=1 signal, and, so far, it seems to work. 

The timeout may be excessive but that might work if cut back a bit......I don't see any ill effect on the gpu card's performance. 

Thanks for the help.

---

### Post by DuckHook on 2016-05-16
> **Plumtreed said:**
> When I interrupted the Grub Boot process via the Edit process and manually introduced 'radeon.dpm=1' the process was allowed to proceed successfully...It occurred to me that the edit interruption was similar to a grub 'timeout' so I introduced a timeout=10 to the Grub Boot sequence just prior to the radeon.dpm=1 signal, and, so far, it seems to work...Very smart. I must say that you display an intuition for this sort of workaround. According to my limited Google-Fu, no one has been able to work out a solution to this problem aside from disabling DPM. If you manage to make this work, you will have come up with a, to my knowledge, unique solution.

Let's see if this solution works over the long term. If so, you may wish to start a Launchpad bug report and include your workaround.

---

### Post by Plumtreed on 2016-05-16
.....so far things are going OK but you have got me looking over my shoulder:(

lets see how it goes over 'the long term'!

---

