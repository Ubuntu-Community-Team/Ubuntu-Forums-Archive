---
title: "Dell C600: Mouse freezes during CPU throtteling"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by petit_prince on 2006-07-14
Hey everyone,

I got three Dell C600 laptop computers sitting around. On Ubuntu 6.06, they all have the same problem: Whenever powernowd slows down the CPU frequency or speeds it up, the mouse freezes for a second. This is sort of annoying as it makes the laptop almost unusable.
`/etc/init.d/powernowd stop` solves the problem temporarly, but I enjoy the longer battery life.

All the machines are equipped with a Coppermine based Pentium III. This is what /proc/cpuinfo reads:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 10
cpu MHz         : 1002.467
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
bogomips        : 2006.35

As long as powernowd runs, the following message shows up every now and then in /var/log/syslog:
"cpufreq: change failed with new_state 0 and result 0"
(Sometimes, the new_state says 1 instead, while result always seems to be 0.)

Oh, just for the records... I searched the forums and tried the cpufreq-detect.sh patch from [1], but to no avail. speedstep-smi seems to be the right module (in fact, speedstep-ich won't even load)... I am running the latest 2.6.15-26 kernel which already contains this new cpufreq-patch from 2.6.16 (I checked in the sources, but I don't have the launchpad-link handy right now).

[1] [http://ubuntuforums.org/showthread.php?t=75598](http://ubuntuforums.org/showthread.php?t=75598)


Any help will certainly be appreciated.


Thanks,
Daniel

---

### Post by petit_prince on 2006-07-16
Anybody an idea?

---

### Post by NijelMcTavish on 2006-12-27
I'm getting the same trouble, and have attempted the same fix.  The speedstep-smi module seems to be the right one, but the mouse 'pauses' every time the CPU speed changes.  From what I've seen on the web, it looks like this problem has been around for a while :(

---

### Post by bodzasfanta on 2007-01-04
Hello!

I had a similar problem but thanks God someone told me a good way to fix it.

"In grub, hit e to edit the boot line. Then move the selection over the kernel line and hit e again. Move the cursor to the end of the line and add the following:
Code:

noapic irqpoll pci=routeirq

Then hit enter to get our of line editing mode and b to boot the modified kernel line.

This will set you up until you power down or reboot. Edit /boot/grub/menu.list to make it permanent." (thanks for Frem)

I hope I could help you

---

### Post by mfremont on 2007-01-27
I have a Dell CPx (J750GT) exhibiting the same symptoms. With the default install of 6.10 the system log is filled with messages like:

[INDENT]Jan 24 11:32:31 mrf kernel: [17180523.760000] cpufreq: change failed with new_state 0 and result 0
Jan 24 11:32:35 mrf kernel: [17180526.892000] psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Jan 24 11:32:35 mrf kernel: [17180526.892000] cpufreq: change failed with new_state 1 and result 0
Jan 24 11:32:35 mrf kernel: [17180527.168000] psmouse.c: resync failed, issuing reconnect request
Jan 24 11:32:36 mrf kernel: [17180528.212000] input: DualPoint Stick as /class/input/input6
Jan 24 11:32:36 mrf kernel: [17180528.232000] input: AlpsPS/2 ALPS DualPoint TouchPad as /class/input/input7
[/INDENT]

And like the original poster, mouse freezes are correlated with these messages appearing in the log. After doing some digging, I think I'm starting to piece together an explanation.

The CPU on my system is a Pentium III that supports an early version of SpeedStep: the processor can be switched between 600MHz and 750MHz by switching the processor frequency and voltage in step. The downside of this technique is that the processor is briefly unavailable during frequency transitions. (see: [Enhanced Intel SpeedStep® Technology and Demand-Based Switching on Linux]("http://www.intel.com/cd/ids/developer/asmo-na/eng/195910.htm?prn=Y"))

I suspect that this latency is related to the brief freezes and the messages from psmouse.c about loosing sync with the TouchPad device. It throws away some data an restarts the device which further causes erratic mouse behavior (I also was experiencing Firefox shutdowns for no apparent reason, or the browser jumping to links I didn't click).

My system originally had powernowd installed. The Ubuntu version of this package first attempts to use the cpufreq ondemand kernel module, and if this fails is starts the powernowd, which runs as a user space daemon that attempts to scale the processor based on demand and the capabilities of the processor (see: [http://www.deater.net/john/powernowd.html]("http://www.deater.net/john/powernowd.html"))

But ondemand fails on my system because of the latency associated with changing CPU frequency on my old PIII:

[INDENT]Jan 26 21:33:39 mrf kernel: [17191183.712000] ondemand governor failed to load due to too long transition latency[/INDENT]

This message is output by the kernel code when a CPU speed transition takes longer than 10ms. (see: [cpufreq_ondemand.c comments on lines 41-50]("http://www.gelato.unsw.edu.au/lxr/source/drivers/cpufreq/cpufreq_ondemand.c?a=i386"))

If I disable powernowd the cpufreq and psmouse.c messages stop and I don't experience the freezes and erratic mouse behavior. Of course, now my system is running at full speed all the time, something that may not be desirable when running on battery. cpudyn isn't an option, either. It causes the same frequency CPU switching bad behavior on my system.

So what's the solution? Right now, I'm hooking into the GNOME Power Manager's power save mode by modifying /usr/share/hal/scripts/hal-system-power-set-power-save to use the cpufreq interface to switch between "performance" and "powersave" CPU speeds. So, if I check "prefer power power savings over performance" in the "Running on Battery" tab, my system will switch to the slower CPU speed while on battery, then back to full performance when I plug into AC.

I added the following beginning at line 10:

```
# attempt to use cpufreq interface
for cpu in /sys/devices/system/cpu/*
do
        govctrl=$cpu/cpufreq/scaling_governor
        if [ -w $govctrl ] ; then 
                if [ $value = "true" ] ; then
                        echo powersave > $govctrl
                        RET=$?
                elif [ $value = "false" ] ; then
                        echo performance > $govctrl
                        RET=$?
                fi
        fi 
done

if [ $RET ] ; then
        exit 0
fi
```

Since I removed powernowd, I also added the following to /etc/modules in order to get the cpufreq modules loaded:
[INDENT]speedstep-smi
cpufreq_powersave
cpufreq_userspace
cpufreq_stats
[/INDENT]

The first of these modules, speedstep-smi, implements the CPU frequency change using the SMI BIOS interface, I couldn't find any docs that listed this as the correct module for my system, but it's the one that the /usr/share/powernowd/cpufreq-detect.sh script would load on my system, and attempts to load speedstep-ich fail.

I still get the cpufreq messages when the system transitions, but the system seems to make the transition. (Perhaps the speedstep-smi code doesn't properly detect the change, so it reports an error?)

Note that on systems that support Enhanced SpeedStep it's probably more desirable to just use the cpufreq ondemand module. You don't need powernowd if you list the appropriate speedstep module and cpufreq_ondemand in /etc/modules.

---

### Post by sdjkfhk123j4h2jk on 2007-04-20
Hi.

The same problem happens with Ubuntu Feisty 7.04.

I fixed it doing this:

[http://ubuntuforums.org/archive/index.php/t-75598.html](http://ubuntuforums.org/archive/index.php/t-75598.html)

> The incorrect speedstep module is being loaded.

To fix this, edit /usr/share/powernowd/cpufreq-detect.sh so it reads like this:


# Two modules for PIII-M depending the chipset.
# modprobe speedstep-ich$EXT || modprobe speestep-smi$EXT would be another way
if [ -f $IOPORTS ] && grep -q 'Intel .*ICH' $IOPORTS ; then
PIII_MODULE=speedstep-ich
else
# PIII_MODULE=speedstep-smi
PIII_MODULE=speedstep_ich
fi



But now the CPU seems to be always at max speed if I boot up connected to AC, and minimum speed if I boot up on battery power.

The ideal solution would be to switch CPU speed depending on if I'm on battery or AC, but now I can't even see the /sys interface to change the speed. At least the annoying mouse blocking has stopped.

Anyone knows how to change the speed depending on ACPI events? I suppose is using /etc/acpi/ac.d/ and /etc/acpi/battery.d/ but the interfaces for changing the speed are gone..

---

### Post by efreddi on 2007-04-20
The problem is pretty old and never fully solved.
Following thread gives some instruction:

[http://ubuntuforums.org/showthread.php?t=64558](http://ubuntuforums.org/showthread.php?t=64558)

on my Dell C600 it works since my first Ubuntu (5.10), but the CPU is then always at full speed.
Regs


Elia

---

