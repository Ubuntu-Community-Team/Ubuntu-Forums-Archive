---
title: "HP Omnibook 6000 help!!! pls."
date: 2004-11-24
forum: Hardware &amp; Laptops
---

### Post by ramzez on 2004-11-24
Hi,

I installed ubuntu and everything works fine apart from power management.

i have P3 800 (Coopermine) which supports SpeedStep. (works fine in windows)

I have powernowd and acpi installed. (out of the box)

on boot nothing complains.

i can see by doing /sbin/lsmod

that speedstep-lib is there
i can see that /sys is mapped

but when i do sudo powernowd it says all this errors about can't find file check yada yada yada.

What do i need to do to make it work?

also is there a way of activating sleep, hibernate and volume buttons?

thank you vey much in advance.

---

### Post by spirospr on 2004-11-25
Well i can't help you much, but about the buttons you could use the Gnome keyboard shortcuts and set the ones you want. This is a trick i did. I know it is not a solution like the keyboard special keys are recognized but it is doing the same so....

---

### Post by malmjako on 2004-12-13
I bought a HP Omnibook 6000 the other day and installed Ubuntu. I can't get suspending to work. ramzez, is it working for you? What do I need to do to get it to work?

SpeedStep doesn't seem to work either...

---

### Post by malmjako on 2004-12-14
I changed to APM, by adding acpi=off apm=on to the kernel options in /boot/grub/menu.lst, and the computer now suspends to RAM when I press the sleep button. However, the hard disk is constantly on, which is a bit annoying. Where do I adjust the settings for the hard disk spin down time? Is it possible to get ACPI working on this machine?

It also takes quite some time for the computer to wake up after sleep - something like 15 seconds. How can I improve this?

---

### Post by malmjako on 2004-12-15
I managed to get ACPI sort of working. I followed the instructions at [https://www.ubuntulinux.org/wiki/SuspendHowto/view?searchterm=acpi](https://www.ubuntulinux.org/wiki/SuspendHowto/view?searchterm=acpi).
I can now put the computer to sleep by pressing the sleep button. However, when it wakes up, the fan comes on and won't stop. Any ideas?

---

### Post by malmjako on 2005-02-12
I got speedstep working! Added the following to /etc/modules:
```
speedstep-lib
speedstep-smi smi_port=0xb2 smi_cmd=0x82 smi_sig=1
```
I got the extra options from [http://www.poupinou.org/cpufreq/](http://www.poupinou.org/cpufreq/).

---

### Post by Redis on 2007-02-20
I know that this thread is a bit old, but
I'm having problems with speedstep on my omnibook 6000 pIII coppermine 800mhz,
I've modprobed the modules as said in the post above, and (especially when on battery power) my laptop freezes totally and i have to reset or shutdown it with the power button.
I've been searching google and launchpad for any solution but without success. When i work without the speedstep-lib and speedstep-smi modules, it's fine.
Since i have dual boot with windows xp, the speedstep works fine on windows.
Any ideas?
Thanks
Redis

I had edgy eft running until 3 days ago, then dist-upgraded to feisty, same problem.

---

### Post by Redis on 2007-03-04
I found a sort of solution, uninstalling all the cpu frequency daemons, and using the cpufreq-powersave and cpufreq-performance kernel modules, and letting guidance powermanager change governor while switching power supply, so i'm at 650mhz on battery and 800mhz on ac power. No more dynamic switching though, but at least i can save battery life.

---

