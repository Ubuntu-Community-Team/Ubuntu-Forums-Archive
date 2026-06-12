---
title: "Several problems with FSC Amilo Xa 1526"
date: 2008-10-27
forum: Hardware
---

### Post by tho.kra on 2008-10-27
Hi people!

Since I was tired of Windows not working properly with my notebooks WLAN adapter I chose to switched to Ubuntu, which I had been using for a while as second system for testing purposes. Fixed one problem, revealed several others... To be clear: I'm quite new to Linux but willing to learn as much as possible, so please excuse inaccurate reports! ;)

1. The cooling fan is always running - almost ...

This is the most strange behavior I've ever seen in an OS. The cooling fan installed in the system is running constantly and seems not to be recognized by the acpi, at least running acpi -V suggests that. Here's the kicker: After suspending and resuming the fan stays quiet and starts working as intended. What's even more interesting, after running the processor at maximum speed and load for a while also "cures" it, i.e. after running a pretty time consuming custom build of a piece of software like WINE. After doing the two steps mentioned above acpi -V reports the fan correctly and thermal triggering works as intended.

What's going on? :)

2. The Brightness can't be adjusted

Regarding this I'm quite lost. The hot keys aren't working, nor does the brightness applet or anything else, suggesting that the necessary devices aren't recognized properly. I installed xbacklight hoping to be able to adjust the brigtness with it. No success. 

Any ideas?

3. Integrated "subwoofer" isn't working

The notebook was designed to a multimedia platform, providing several components to enhance media experience. This includes a more sophisticated sound system providing some kind of low frequency speaker at the bottom of the case. The front speakers are addressed correctly by ALSA, the third speaker is not and isn't even reported as a channel. How do I address this speaker?


Again, I'm sorry for any inaccuracy since I'm in the process of getting to know the OS better at this time. All the problems described above are non-existent on Windows, so I guess the have to be solvable.

Thanks in advance!

Thomas

---

### Post by tho.kra on 2008-11-02
Nothing on this? Anyone? 

May my bump be excused. :)

---

### Post by indrekots on 2008-12-12
Hi

I also have an Amilo Xa 1526 and have experienced the same problems you mentioned. I got my subwoofer working by ticking the center option in the alsa-mixer preferences. Hope this helps.

If you can't find the center option, try adding this line to /etc/modprobe.d/alsa-base 
> options snd-hda-intel model=3stack-dig
Then reboot and check your alsa-mixer preferences again. There should be a center and LFE option there. Tick them and enjoy your favorite music.

For more information check [http://forum.notebookreview.com/showthread.php?t=216000]("http://forum.notebookreview.com/showthread.php?t=216000")

As for the other issues, I haven't found a fix.

---

