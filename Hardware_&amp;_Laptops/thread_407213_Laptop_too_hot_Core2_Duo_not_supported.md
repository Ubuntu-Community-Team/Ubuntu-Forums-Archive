---
title: "Laptop too hot: Core2 Duo not supported?"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by Miles_Prower_fr on 2007-04-11
Hi,

I'm experiencing some serious problems with my laptop: the poor thing is litteraly burning, and so hot i'm still wondering why it does not even automatically shut down. The fan is always running at 100%, same for the CPU.

Here are the specs:

Ubuntu 6.10 Edgy Eft & Ubuntu 7.04 Feisty Fawn
HP nc8430 (laptop)
CPU1 : Intel Core 2 Duo T5600 @ 1.83GHZ
CPU2 : Intel Core 2 Duo T5600 @ 1.83GHZ

Paquet "laptop-mode" is installed.

When using the CPU-freq-applet, I get this error message:

[IMG]http://img389.imageshack.us/img389/3244/capturecpufreqappletrf1.png[/IMG]

Basically saying "unsupported hardware".

More pieces of information:

```
miles@foxbox:~$ cat /proc/acpi/processor/CPU0/power
active state:            C1
max_cstate:              C8
bus master activity:     00000000
maximum allowed latency: 8000 usec
states:
   *C1:                  type[C1] promotion[--] demotion[--] latency[000] usage[00000000] duration[00000000000000000000]

```

This problem is actually damaging my laptop, I had to contact HP as my power supply fried (getting hot too). I'm pretty sure this later point is only related to software, because this laptop was actually provided by our school and I was the only one not running WinXP Pro affected with that problem. As I'm not willing to use this other OS at all, this problem is kinda critical to me.

Thanks for your help!

---

### Post by revilodraw on 2007-04-11
that is very weird.... so weird i am froced to think it is a hardware issue... not to state the obvious, but you are allowing the thing to breathe by having the air intakes clear? i would format, reinstall, and if nothing was improved i would send back to hp...

i have a core 2 duo and it all works fine (apart from when i try to copy an arcoss dvd)

---

### Post by IcemanV9 on 2007-04-11
You ***might*** have some old cpufreq settings for gnome-power-manager in gconf. You can reset them to their (new) default values by running the following commands:

```
gconftool-2 -u /apps/gnome-power-manager/cpufreq_ac_policy
gconftool-2 -u /apps/gnome-power-manager/cpufreq_battery_policy

```

---

### Post by Miles_Prower_fr on 2007-04-12
Thanks for the answer.

I already tried this little trick (read the Planet) but it did not solve anything; both keys are currently "ondemand". I updated my laptop's BIOS too, which reduced a bit the problem (a little less noise from the fan), however the CPU is still running at 100% and reported "unsupported". I cannot force another mode (or do not how how I should do it).

The laptop has of course its air intakes clear. I did a fresh install of Ubuntu 7.04 over Edgy (my /home is on another partition) and this didn't help either. Other students in my school reported having a similar problem.

I'll try contacting HP but I'm pretty sure it won't be of any help (might raise Linux-awareness, who knows) as the laptop is definitely working fine with Windows XP Pro SP2. But as I use this OS only 3% of the time... well...

If you guys have any other clues, I'm definitely willing to try ;)

---

### Post by moixa on 2007-04-13
Are you sure you have those fancy kernel modules for your CPU loaded?
say speedstep, frequency scaling stuff.

Sometimes they don't load automatically

---

### Post by Miles_Prower_fr on 2007-04-16
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
fuse
tifm_sd
```

Is that supposed to be in this file?

---

### Post by Miles_Prower_fr on 2007-04-27
&#8593; Up

---

### Post by schmolch on 2007-04-27
Not surprising your CPU is running hot, you are missing the C2 and C3 Power-States and therefore the CPU keeps running at full throttle.

Did you mean that by saying "cpu is always running at 100%" or is there actually cpu load visible on the system-monitor?

---

### Post by Miles_Prower_fr on 2007-04-28
Well, the CPU-freq-applet is the one app telling me it's running 100% all the time. The system actuallly uses only 3% of ressources at mostwhen idle, so it doesn't need to run @ 1,83GHz all that time.

[IMG]http://img155.imageshack.us/img155/3061/captureec8.jpg[/IMG]

---

### Post by schmolch on 2007-04-29
So you miss both the C2 and C3 States as well as Speedstepping.

The question is why though.
Im new to Ubuntu and since we all use the same kernel here im pretty much lost cause i would say "check your kernel configuration" usually.

I could speculate, ask you if there are any errors in dmesg, but somebody more familiar with ubuntu would certainly be better here.

---

### Post by Miles_Prower_fr on 2007-05-01
No clue on how to use dmesg but I found this is in it:

```
[    2.724378] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.724383] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.724809] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [HP    ] OemTableId [ Cpu1Ist] [20060707]
[    2.725012] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [HP    ] OemTableId [ Cpu1Cst] [20060707]
[    2.725567] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.725572] ACPI: Processor [CPU1] (supports 8 throttling states)

```

I'm puzzled.

---

### Post by stchman on 2007-05-01
> **Miles_Prower_fr said:**
> Hi,

I'm experiencing some serious problems with my laptop: the poor thing is litteraly burning, and so hot i'm still wondering why it does not even automatically shut down. The fan is always running at 100%, same for the CPU.

Here are the specs:

Ubuntu 6.10 Edgy Eft & Ubuntu 7.04 Feisty Fawn
HP nc8430 (laptop)
CPU1 : Intel Core 2 Duo T5600 @ 1.83GHZ
CPU2 : Intel Core 2 Duo T5600 @ 1.83GHZ

Paquet "laptop-mode" is installed.

When using the CPU-freq-applet, I get this error message:

[IMG]http://img389.imageshack.us/img389/3244/capturecpufreqappletrf1.png[/IMG]

Basically saying "unsupported hardware".

More pieces of information:

```
miles@foxbox:~$ cat /proc/acpi/processor/CPU0/power
active state:            C1
max_cstate:              C8
bus master activity:     00000000
maximum allowed latency: 8000 usec
states:
   *C1:                  type[C1] promotion[--] demotion[--] latency[000] usage[00000000] duration[00000000000000000000]

```

This problem is actually damaging my laptop, I had to contact HP as my power supply fried (getting hot too). I'm pretty sure this later point is only related to software, because this laptop was actually provided by our school and I was the only one not running WinXP Pro affected with that problem. As I'm not willing to use this other OS at all, this problem is kinda critical to me.

Thanks for your help!

There are numerous vendors that pre-install Ubuntu on Core2Duo equipped laptops.  It sounds like your laptop is not working properly.  I recommend sending the thing back.  Ubuntu cannot burn up a processor.

---

### Post by Miles_Prower_fr on 2007-05-02
Thanks for your answer. The processor is fine, but the bug it's just draining my battery life fast and this laptop's hardware is pretty weak. I do not hold Ubuntu responsible for this! :p

I just installed Ubuntu 7.04 (same version as mine) on a friend's laptop with the same hardware. Its Core2 Duo is pretty well supported, he tells me that at least two states are in use ("idle" and "full CPU power") when set "ondemand". I guess i'll give a try to format Ubuntu and reinstall it, but I'm not sure it will solve the problem as my /home is on another partition I will not format and may contains the problematic settings. Plus, I'm not too keen on this way on solving problems.

---

### Post by zgornel on 2007-05-02
Try this:
```
$ sudo dpkg-reconfigure gnome-applets
```
and answered “Yes” to the question regarding setting the suid of the cpufreq-selector executable.
Try then modifying the frequency or selecting the CPU governor.Anyway, even without frequency scaling, the processor should not get hot.

---

### Post by Miles_Prower_fr on 2007-05-03
No changes.

---

### Post by kaede on 2007-05-03
i'm just realized that running ubuntu is making my notebook more hot than running windows.
wonder why?

---

### Post by Miles_Prower_fr on 2007-05-13
Bump. Tried to reinstall Ubuntu with the 7.04 LiveCD and all I got was a Xorg error, which is really annoying since I'have been handing out a lot of those LiveCDs lately in my school and we all have the same hardware (ATI Mobility Radeon X1600). Why the heck such a problem made it to the final release is a wonder to me, but that's another story.

I'm not to keen on reinstalling Edgy then upgrading, I'll try later with the alternate CD. Or better, if someone has a solution to my current CPU problem...

---

### Post by Miles_Prower_fr on 2007-05-13
Reinstalled Ubuntu 7.04 today from the alternate CD. CPU frequency now works (from 1Ghz to 1.84GHz); my laptop is still running kinda hot, but far from burning as it was before.

```
miles@foxbox:~$ cat /proc/acpi/processor/CPU0/power
active state:            C3
max_cstate:              C8
bus master activity:     00000000
maximum allowed latency: 8000 usec
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[001] usage[00002190] duration[00000000000000000000]
    C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[00019287] duration[00000000000066835616]
   *C3:                  type[C3] promotion[--] demotion[C2] latency[057] usage[00196847] duration[00000000000935976645]

```

---

### Post by bapoumba on 2007-05-14
After my own laptop had to go for repairs due to over heating (CPU frequency was working. They had to work on the cooling system), I would recommend buying an external cooling system. I do not know the English word for it, its basically an usb device with fans (I have 3 fans here), quite quiet, that extract warm air from below the laptop. There is an usb hub on it too, so that's 4 extra usb ports. It really brings the CPU temp down by more than 20°C as far as I can tell. Got it for €25 in a local store.

---

