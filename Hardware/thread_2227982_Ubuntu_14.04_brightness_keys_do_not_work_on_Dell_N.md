---
title: "Ubuntu 14.04 brightness keys do not work on Dell N411Z"
date: 2014-06-05
forum: Hardware
---

### Post by madvinegar on 2014-06-05
Hi to all. I really need your help and expertize to try to find a solution to the problem I describe in the title of this post.
I own a Dell n411z laptop. I have installed in the past ubuntu 12.04,  12.10, 13.04. In all these releases the brightness keys worked out of  the box without me having to add any grub parameter or create any conf  file inside xorg.conf.d

As of ubuntu 13.10 and 14.04 the brightness keys (Fn+F4 and Fn+F5) are  completely dead. They do not produce any results in xev, or acpi_listen  or evdev.
I have tried all the parameters i can think of in grub and I have also  created the 20-intel.conf file inside xorg.conf.d but I have not managed  to solve the matter.
acpi_backlight=vendor, acpi_osi=Linux, acpi_osi=\"!Windows 2012\" etc  etc etc. Maybe the syntax is wrong? Or do I need to use a combination of  parameters? I really don't know.

It is really disappointing and frustrating as the keys work fine up to ubuntu 13.04. 
All the rest of the function keys (wifi, volume, keyboard brightness etc) work just fine.
I also upgraded my BIOS to A06 (A06 being the last recomended and  available BIOS for my N411z according to DELL), but again it did not  solve the matter.

For your information I can adjust the brightness just fine either via  terminal or via the brigthness bar in system settings > brigthness.  But the function keys are just dead.

I have also participated in a launchpad bug but no solution yet: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1229591](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1229591)
Tried later kernels (3.14 and 3.15) but still no solution.

Below you can find some terminal results that might help you produce any ideas or suggestions.


[http://paste.ubuntu.com/7582689/](http://paste.ubuntu.com/7582689/)

```
mike@Linux-Dell:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.13.0-27-generic root=UUID=849fb8e5-8216-4cec-a2d2-4d0ce8a2130d ro quiet splash vt.handoff=7

```

```
mike@Linux-Dell:~$ lspci -nnk | grep -iA3 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd  Generation Core Processor Family Integrated Graphics Controller  [8086:0116] (rev 09)
    Subsystem: Dell Device [1028:051b]
    Kernel driver in use: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200  Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)

```

```
mike@Linux-Dell:~$ for i in /sys/class/backlight/*; do echo $i;  cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
16
16
16
/sys/class/backlight/intel_backlight
4845
4845
4882

```

Finally just to add that the brightness adjustment via the function keys  works just fine when I am in BIOS or even in the Grub menu. So the  function keys stop working after loading the OS (!)

Your kind assistance would really be very much appreciated.
Any ideas and/or suggestions are more than welcomed.

---

### Post by jeremy31 on 2014-06-05
Do you use virtualbox?

---

### Post by madvinegar on 2014-06-05
Why...? Does it have anything to do with the brightness keys? Would you like me to try something?

---

### Post by jeremy31 on 2014-06-05
That is one thing that your bug report and the other guys have in common in addition to having the same model.  But you should be able to test by booting up the installation iso and then see if you get any response from your hotkeys.  And I think you both had at least one module mentioned in dmesg that said "tainting kernel"

```
ls /proc/acpi/
``` Let see what is in there

---

### Post by madvinegar on 2014-06-06
The result of the command you gave me is:

```
mike@Linux-Dell:~$ ls /proc/acpi/
button  wakeup
```


What does that mean...?

---

### Post by jeremy31 on 2014-06-06
> **madvinegar said:**
> The result of the command you gave me is:

```
mike@Linux-Dell:~$ ls /proc/acpi/
button  wakeup
```


What does that mean...?

I just wanted to see if it had a third folder there like one of my toshiba's.  Did you do all your acpi_osi tests before updating BIOS?

Have you tried FN + up arrow and Fn + down arrow to see if they might control the backlight?

---

### Post by jeremy31 on 2014-06-07
You might want to look through your BIOS options again.  The one Toshiba I have actually is UEFI and the option wasn't as obvious as on the Lenovo- where it is in the Boot menu.  The Toshiba was actually a sub-menu of Advanced, it was at the bottom and called System Configuration

It also looks like module dell_laptop has had its share of changes and problems, see if ```
sudo modprobe -r dell_laptop
``` allows you to use the brightness keys

---

### Post by jeremy31 on 2014-06-15
If you are still watching this thread, file a bug report here [https://bugs.freedesktop.org/](https://bugs.freedesktop.org/)
I was able to get a N411Z cheap and was trying different ISO's on it.  With Ubuntu 13.04, the acpi_listen worked and xev reported about the same as my newer Lenovo while trying the brightness hotkeys which is this
```
RRNotify event, serial 34, synthetic NO, window 0x3a00001,    subtype XRROutputPropertyChangeNotifyEvent
    output eDP1, property BACKLIGHT, timestamp 609993755, state NewValue
``` I do think the output was LVDS1 instead of eDP1

I booted up the Live version of 13.04 and this if the result ```
RRNotify event, serial 42, synthetic NO, window 0x3a00001,
    subtype XRROutputPropertyChangeNotifyEvent
    output LVDS1, property BACKLIGHT, timestamp 86835, state NewValue


```
and the serial number changes for every time the hotkey is pressed

---

### Post by seven2 on 2014-06-28
Not sure if you're still having this issue, but this post fixed it on my Dell laptop: [http://itsfoss.com/fix-brightness-ubuntu-1310/](http://itsfoss.com/fix-brightness-ubuntu-1310/)

---

### Post by jeremy31 on 2014-06-29
> **seven2 said:**
> Not sure if you're still having this issue, but this post fixed it on my Dell laptop: [http://itsfoss.com/fix-brightness-ubuntu-1310/](http://itsfoss.com/fix-brightness-ubuntu-1310/)

Those fixes only work if the brightness hotkeys are recognized.  There was a change made at some point and Ubuntu 14.04 doesn't even acknowledge the brightness hotkeys.  No response from acpi_listen, xev, showkey, and not a peep of an unknown keypress in dmesg- but it worked in Ubuntu 12.04.

One of the bug reporters did a kernel bisect and reported the last good kernel was 3.10 and the first bad one was 3.11 and the older kernels don't seem to even work with Ubuntu 14.04

---

### Post by madvinegar on 2014-07-22
Exactly as Jeremy said.

I really do not know what was changed/added/deleted/broken in 13.10 and 14.04 and the hotkeys are completely DEAD.

---

### Post by jeremy31 on 2014-07-22
> **madvinegar said:**
> Exactly as Jeremy said.

I really do not know what was changed/added/deleted/broken in 13.10 and 14.04 and the hotkeys are completely DEAD.
Do you still have 12.04 around as I noticed something strange.  If you turn brightness down to about 33% and then try to turn brightness up the brightness goes up a little and then down with the next attempt to brighten and also causes error in dmesg about an invalid value returned

---

### Post by matthew.t.sanogma on 2015-02-21
Hello madvinegar.

Were you able to find a fix or workaround to this issue?

I have the same exact model laptop and problem as you.

I just installed Ubuntu 14.04.2 to try its' new kernel but the same problem exists. I then installed kernel 3.2.0 76-generic in 14.04.2 (the kernel that I used for 12.04.5 LTS) and all of the fn keys worked fine (although it did leave the rest of the system fairly unstable). 

I love 14.04 for its speed, its' stability and I just donated some money to Canonical for their work, but it is a bit annoying when a feature which was working fine in previous releases no longer works. Anyway, I know this thread is a bit old now but I was just curious if you have ever found a fix for this. 

Thanks in advanced for your time. :p

Best regards,

Matt

---

### Post by jeremy31 on 2015-02-22
> **matthew.t.sanogma said:**
> Hello madvinegar.

Were you able to find a fix or workaround to this issue?

I have the same exact model laptop and problem as you.

I just installed Ubuntu 14.04.2 to try its' new kernel but the same problem exists. I then installed kernel 3.2.0 76-generic in 14.04.2 (the kernel that I used for 12.04.5 LTS) and all of the fn keys worked fine (although it did leave the rest of the system fairly unstable). 

I love 14.04 for its speed, its' stability and I just donated some money to Canonical for their work, but it is a bit annoying when a feature which was working fine in previous releases no longer works. Anyway, I know this thread is a bit old now but I was just curious if you have ever found a fix for this. 

Thanks in advanced for your time. :p

Best regards,

Matt

No fix found yet.  About the only thing you can do is make a script to change the value of /sys/class/backlight/intel_backlight/brightness or /sys/class/backlight/acpi_video0/brightness using keys other than the FN combo

---

### Post by matthew.t.sanogma on 2015-02-26
> **jeremy31 said:**
> No fix found yet.  About the only thing you can do is make a script to change the value of /sys/class/backlight/intel_backlight/brightness or /sys/class/backlight/acpi_video0/brightness using keys other than the FN combo  Yup, I figured something like that. Oh well, at least it is not a major bug.   Thank you.

---

