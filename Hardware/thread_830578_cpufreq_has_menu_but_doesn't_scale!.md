---
title: "cpufreq has menu but doesn't scale!"
date: 2008-06-16
forum: Hardware
---

### Post by robert.cooper on 2008-06-16
[SIZE=1][FONT=monospace](8.04)
r@r-laptop:/usr/bin$ cpufreq-info

cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [EMAIL="linux@brodo.de"]linux@brodo.de[/EMAIL], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1.73 GHz and 1.73 GHz.
                  The governor "conservative" may decide which speed to use
                  within this range.
  current CPU frequency is 1.73 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1.73 GHz and 1.73 GHz.
                  The governor "conservative" may decide which speed to use
                  within this range.
  current CPU frequency is 1.73 GHz.

[/FONT][/SIZE]

---

### Post by sdennie on 2008-06-16
I'm not sure how you got the scaling governor to "conservative" without specifically setting it to that but, this will probably at least temporarily fix your problem:

```

sudo sh -c "echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"

```

Though, you will want to figure out how you got to "conservative" in the first place.  I'm not aware of any GUI utility that sets the governor to "conservative".

---

### Post by robert.cooper on 2008-06-16
thank you for the reply. previously, "conservative" mode could be set with gnome-applets cpu frequency and scaling monitor by simply left clicking, and it had the effect of setting to the lowest clock setting available to scale.
the contents of the file that you pointed to are:
powersave
that's it! oddly and much to my surprise, the applet indicates 1.07, the second to lowest freq... and selecting other modes moves the bullet but it doesn't adjust the frequency display.
i would be happy making adjustments (workarounds) with cmds in a terminal, but what i really want is the lowest possible setting, whether it's "conservative" or "800Mhz"
what exactly does your command do?
ooh...
in the sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq file the value is set to the current speed indicated by the applet! so i'll just edit it, but first, i will repeat what i did in the first post to see if the range is changed...

cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1.07 GHz and 1.07 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.07 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1.07 GHz and 1.07 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.07 GHz.

aha! it did change.. so all i have to do is change the file? let's see..
whoo! it worked! hooray for battery life! now to test and set max to max and min to min and adjust applet..
ok, max set to 1730000, and applet actually adjusts! however, it indicates, when set to 1.73, 1.3. oh well, this intel beast overheats anyway. this should save some trouble. thank you kindly for pointing me to that directory!
p.s... in cpuinfo_max_freq, it indicates that the max is in fact 1733000, not 1730000. whoops. ah. now all works. yay!

---

### Post by sdennie on 2008-06-16
Are you using a Core 2 Duo?  I'm assuming so with the 800Mhz speed.  If so, and your primary reason for setting the governor to peg the CPU at the lowest speed is to save battery power, you are actually better off leaving the governor at ondemand.  It sounds non-intuitive but, letting the CPU switch to max speed when needed means that it can return to idle faster and save more power.  Google for "intel race to idle" for more information on why this is true.

---

### Post by robert.cooper on 2008-06-16
suppose i wanted to set max freq on ac power to 1.33.., 800000 on battery power? what then?
I noticed in
[http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644)
that 'echo' is used often. what does echo do? is there a way to update the file contents of cpu_max_freq this way?
would you link me to a thread about sata disk power-saving, please?

---

### Post by sdennie on 2008-06-16
> **robert.cooper said:**
> suppose i wanted to set max freq on ac power to 1.33.., 800000 on battery power? what then?
I noticed in
[http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644)
that 'echo' is used often. what does echo do? is there a way to update the file contents of cpu_max_freq this way?


You could probably set this up but, I don't recommend it.  "echo", as used in that thread, just sends a value to a file.

> 
would you link me to a thread about sata disk power-saving, please?

If you are really interested in power savings, [www.lesswatts.org](www.lesswatts.org) contains a huge amount of excellent information.

---

### Post by robert.cooper on 2008-06-16
i read the lesswatts description and i understand the logic, but if It's actually mainly for heat. i'm dual core pentium, not core 2 ~shrug~. I would agree to have conservative for battery mode, and ondemand for ac (with max at 133000). you're probably right about the ondemand thing though.. not only getting the work out of the way so idle is sooner, but making faster gui loads and such.
by sending a value to a file.. is that appending a value, or replacing it, or what? does the arg after echo determine this? (40, 50, 1500, etc)
thanks for the time :)

---

### Post by sdennie on 2008-06-16
Most of the commands in the thread you are talking about are setting options that simply appear to be files.  Unix people really enjoy it when things appear as files but, in this case, they are special files and you are essentially just setting the option that the file represents.

---

### Post by stchman on 2008-06-16
> **robert.cooper said:**
> [SIZE=1][FONT=monospace](8.04)
r@r-laptop:/usr/bin$ cpufreq-info

cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [EMAIL="linux@brodo.de"]linux@brodo.de[/EMAIL], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1.73 GHz and 1.73 GHz.
                  The governor "conservative" may decide which speed to use
                  within this range.
  current CPU frequency is 1.73 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1.73 GHz and 1.73 GHz.
                  The governor "conservative" may decide which speed to use
                  within this range.
  current CPU frequency is 1.73 GHz.

[/FONT][/SIZE]

What processor do you have?  That looks like an Athlon 64 X2 series.

If the processor supports frequency scaling (Core, Core 2, Athlon 64, Pentium Dual, Phenom).

Some of the other forum members can correct me, but don't you need the -generic kernel and not the -386 kernel installed to support both multiple processor support and frequency scaling.

What kernel are you using?  To find out type uname -a in a terminal.

---

### Post by robert.cooper on 2008-06-16
Linux r-laptop 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux

---

### Post by robert.cooper on 2008-06-16
over some time, the value keeps creeping back up...
how do i keep scaling_min_freq from increasing automatically?
oh.. i remember when this was configured correctly on the previous installation.. a change to acpower from batpower from latter to former reset to ondemand, if that helps at all.

---

