---
title: "Non-laptop fan speed problem: bug, en.req. or just self-configure?"
date: 2006-07-30
forum: Hardware &amp; Laptops
---

### Post by donut on 2006-07-30
Hi 

A couple of months ago, I purchased a Dell Dimension 9150 PC (pentium dual-core PD 930 processor 3.00GHz, 800FSB, 2x2MB).

I currently dual bool this Machine with both WinXP and Ubuntu 6.06 mainly because of the fan problem I am having with Ubuntu (and also with other linux variants such as FC5)

When I turn on the machine, the fan on the machine starts spinning fairly fast and is quite loud. The BIOS loads, the Grub menu appears and then after a few seconds WinXP is auto-selected by Grub and the WinXP loader is initiated. The WinXP boot screen appears and about 3 seconds after this boot screen first appears, the fan goes quite (spins much slower). This implies to me that by default, these machines spin the fans at the fastest rate (maybe as a safeguard) and then rely on the O.S., if its cabaple, to pick up the management of the fans if it chooses to. Note: The bios doesn't seem to enable fan settings to be re-configured.

Therefore when running the machine with WinXP, the fans are normally quite and only go louder when the system is under stress (as to be expected).

However, when booting Ubuntu, it is a different story, On machine start-up the fans spin fast as they always do. However, this time after selecting Ubuntu from the Grub menu, Ubuntue boots up but the fans never slow down. This means when running Ubuntu on my machine, the PC's fans are always making a loud distracting noise.

Now I can't work out whether this should be regarded as a Ubuntu/Linux bug, a Ubuntu/Linux enhacnement request or just something that a normal user who has installed Ubuntu should be expected to sort out and configure post-installation. Any thoughts? 

Note: I run Ubuntu also on a centrino based laptop and the fan management seems to work fine - varying as necessary when under load.

Note: If this situation is something that an end-user should be expected to sort out themselves then do people recommend me just installing and configuraing something like lm-sensors? See: [http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737) and [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780) .

Thanks

Paul

---

### Post by irober02 on 2006-07-31
Dear Paul,

Your problem sounds like the one I reported ([http://ubuntuforums.org/showthread.php?p=1322954#post1322954](http://ubuntuforums.org/showthread.php?p=1322954#post1322954)) a few days ago  with my new Dell laptop. I'm developing the theory that this is a grub problem because it occurs even if I pause the boot process while the grub menu is displayed (no kernel/OS loaded). I've been resorting to pressing the restart menu a few times until I get a boot that works properly. One strange observation: this problem seems to only occur on the first boot of the day -perhaps my laptop is a night owl rather than a morning lark! ;-)

---

### Post by frankuzzo on 2006-07-31
This is my fan experience on laptops:

On my old centrino laptop (acer travelmate 290) 1400Mhz, the fan run for a fixed amount of time at the very beginning of the power-up (it is linked to the power button I think). Then it stays quite throughout lilo and the os. If I go in the BIOS setup it starts fan again after a while, because I think the CPU is heavy loaded (dunno why) in the bios. 

My new lappie does differently (centrino T2300E). It waits until the os kernel loads before setting fan off.
I think so it is not a software issue because before installing ubuntu and grub I still needed to wait for the windows os kernel before fan off. I think also it should be a sw controlled feedback instead of hardware direct control (which is better and less dangerous!!), and probably in your case your CPU is not correctly handled.

Hope I was helpful.

ps. please check my post on c3 state in the laptop section, and provide your outputs if you have a t2x00 dual core cpu laptop. Thanks!

---

### Post by donut on 2006-08-03
I checked the following on my Desktop machine:

pdone@homepc:/etc/init.d$ uname -a
        Linux homepc 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux
        pdone@homepc:/etc/init.d$ cat /proc/acpi/processor/CPU0/power
        active state:            C1
        max_cstate:              C8 
        bus master activity:     00000000
        states:
           *C1:                  type[C1] promotion[--] demotion[--] latency[000] usage[00000000]
pdone@homepc:/etc/init.d$ cat /proc/acpi/processor/CPU1/power
        cat: /proc/acpi/processor/CPU1/power: No such file or directory

So the acpi stuff only seems to pick up 1 CPU - is this correct for a dual core? Also I noticed Ubuntu was running the Kernel 'linux-386'. Why isn't it running linux-686 or actually why not linux-686-smp because it is dual-core (does smp not apply to dual cores?). I don't know anything about ACPI but there only being on C state (C1) may be the issue? Shoudn't there be a few states listed or is that more typical of laptops?

If the kernel doesn't pick up more than one possible C state does that mean it will never try to to vary fan speeds, etc, or am I completely missing the point?

Paul

---

### Post by irober02 on 2006-08-06
(K)ubuntu adopt a lightweight, lowest common denominator approach to their distribution. Once you've installed Dapper using the basic 386 distro you can install other kernels compiled for specific architectures (apt-get install linux-686-smp, etc -you may want to dowload corresponding linux-restricted-modules-686). New boot options will be added to your grub menu. Once you reboot into the SMP kernel it should recognise two processors. I'm configured like that (but still having problems with my fan:-().

---

### Post by donut on 2006-08-08
Thanks for the info - I've upgraded my kernel to 686 which seems to have smp support built in. Now I get...

pdone@homepc:~$ uname -a
Linux homepc 2.6.15-25-686 #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006 i686 GNU/Linux
pdone@homepc:~$ cat /proc/acpi/processor/CPU0/power
active state:            C1
max_cstate:              C8
bus master activity:     00000000
states:
   *C1:                  type[C1] promotion[--] demotion[--] latency[000] usage[00000000]
pdone@homepc:~$ cat /proc/acpi/processor/CPU1/power
active state:            C1
max_cstate:              C8
bus master activity:     00000000
states:
   *C1:                  type[C1] promotion[--] demotion[--] latency[000] usage[00000000]
pdone@homepc:~$

Therefore, both processor's ACPI settings seem to be detected, but both only show one possible state (C1). Is this a bios bug or acpi bug that only one state is detected. Or do I now understand what I'm seeing. How can the kernel adjust fan speeds if there is only one state listed or does it not work like that for Desktop machines?

Paul

---

### Post by donut on 2006-08-08
Also I noticed this on my machine - not sure if it has any relevance..

pdone@homepc:~$ acpi -t
No support for device type: thermal

---

### Post by donut on 2007-12-30
Bit of a late reply to myself, but I recently installed 7.10 on this machine and the fan works like a dream -very quite unless under load.

Paul

---

