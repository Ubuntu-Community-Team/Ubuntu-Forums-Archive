---
title: "Feisty on Thinkpad R51e"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by Vitus on 2007-06-15
Hej!

I've updated my R51e from Dapper via Edgy to Feisty and have some hardware issues.  The R51e is equipped with a Celeron M, Atheros AR5212 and an ATI chipset, see [http://thinkwiki.org/wiki/Category:R51e](http://thinkwiki.org/wiki/Category:R51e).  None of the following problems happened in Dapper.

[LIST]
[*]Interrupts.  In the default configuration the interrupts for WLAN and Sound (probably more) stop occuring after some time.  10 Minutes, 3 hours, the sound just loops, the wlan connection is lost and /proc/interrupts shows no updates for that interrupt.  It doesn't happen at once for all interrupts, just one after the other with possible a lot of time in between.  This issue is fixed by added NOAPIC to the kernel commandline.

[*]Bootup time.  With NOAPIC or without, the system needs more than 7 minutes to boot.
There a long delays after "loading ACPI modules" and "load hal modules".  I do have dmesg and ps outputs taken during that pauses as one can switch to the console and login but I don't see anything strange in those informations.

[*]Suspend to RAM.  Takes forever, 30 seconds to suspend.  The resume works half ways: display and keyboard is there but the half moon is still blinking (showing "coming back from resume") and WLAN is not functioning.  With NOAPIC the blinking half moon stops after some time but WLAN is dead nevertheless.  One has to reboot to get it working again, had no success with unloading.

[*]2.6.20-16-generic.  From what I heard one should use the "-generic" kernel nowerdays.  When I select that kernel from Grub ath_pci.ko is not loaded: there is no ath_hal.ko module found.  I copied the one from the "-386" modules and could load the driver chain.  But got bitten by the above interrupt problem and haven't retried it with NOAPIC so far.
[/LIST]

The R51e seems to be a very rare Thinkpad, I haven't found any installation reports at the usual sites.  So I'm on my own and would appriciate if someone points me to things I could try to get the R51e up and running again.  Of course there is still the option to restore the Dapper backup...

By[t]e,
    Vitus

---

### Post by Vitus on 2007-06-15
One last point: when I change the scheme in kpowersave and that program changes rhe display brightness accordingly that happens very slowly.  No idea why and it's not very important but my sched more light to the hardware problems.

---

### Post by DagMan on 2007-06-15
Just a thought on the suspend part, have you suspended it to ram from the command line to see what might be taking so long to accomplish.
sudo /etc/acpi/sleep.sh force

Also removing splash from the kernel line on grub maybe you can see what's delaying on boot.

I thought that generic is the only kernel.. anyhow, on that processor that isn't hyperthreading or 2 cores or anything, you might actually be better running a non generic kernel.  It would depend also on which processor the kernel is compiled for, like if the 386 one has a kernel for a 386 or 486 and the generic is 586.  Once installed you can look at this in the corresponding config file in grub
gedit /boot/config-`uname -r`
and then in the part under the text** # Processor type and features**
the bolded parts would be relevant for the processor and the CONFIG_SMP is on where there is more than one core, hyperthreading, etc, but will actually run a little slower on a cpu that doesn't use it.
**CONFIG_SMP=y**
CONFIG_X86_PC=y
# CONFIG_X86_ELAN is not set
# CONFIG_X86_VOYAGER is not set
# CONFIG_X86_NUMAQ is not set
# CONFIG_X86_SUMMIT is not set
# CONFIG_X86_BIGSMP is not set
# CONFIG_X86_VISWS is not set
# CONFIG_X86_GENERICARCH is not set
# CONFIG_X86_ES7000 is not set
CONFIG_PARAVIRT=y
CONFIG_VMI=y
[B]# CONFIG_M386 is not set
# CONFIG_M486 is not set
CONFIG_M586=y
# CONFIG_M586TSC is not set
# CONFIG_M586MMX is not set
# CONFIG_M686 is not set
# CONFIG_MPENTIUMII is not set
# CONFIG_MPENTIUMIII is not set
# CONFIG_MPENTIUMM is not set
# CONFIG_MCORE2 is not set
# CONFIG_MPENTIUM4 is not set
# CONFIG_MK6 is not set
# CONFIG_MK7 is not set
# CONFIG_MK8 is not set[/B]

This is the generic kernel and it is set up for a 586 processor or later and has SMP enabled for multithreading, dual cores, etc.  As long as the kernel that works for you is a 586, SMP and other options that you'de find in this section that would be turned off automaticially with SMP would not matter.  A 486 kernel would still drive your machine as well.


Also, try disabling any network interfaces that you aren't using by unticking them in 
sudo network-admin
This would be the first thing I'd try.

---

### Post by Vitus on 2007-06-18
> **DagMan said:**
> Just a thought on the suspend part, have you suspended it to ram from the command line to see what might be taking so long to accomplish.
sudo /etc/acpi/sleep.sh force


Thank you!  Will try to do the commandline suspend later (when I no longer need the Laptio).


> Also removing splash from the kernel line on grub maybe you can see what's delaying on boot.

As I said, it's delayed at the following points:

```

* Loading ACPI modules...
(Pause)
* Starting system log daemon...
...
* Starting Hardware abstraction layer hald
(Pause, 99.3% idle)
* Starting DHCP D-Bus daemon dhcdbd

```

The second pause takes some minutes, so there is time to switch to the console and do a little research.  Top shows no significant CPU usage and ps:

```

root      4759     1  0 22:50 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4776     1  0 22:50 ?        00:00:00 /sbin/syslogd
root      4826     1  0 22:50 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4828     1  0 22:50 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmsg
root      4835  4496  0 22:50 ?        00:00:00 /bin/sh /etc/rc2.d/S12dbus start
104       4849     1  0 22:50 ?        00:00:00 /usr/bin/dbus-daemon --system
root      4852  4835  0 22:50 ?        00:00:00 run-parts --arg=start /etc/dbus-1/event.d
root      4853  4852  0 22:50 ?        00:00:00 /bin/sh /etc/dbus-1/event.d/20hal start
root      4864  4853  0 22:50 ?        00:00:00 /usr/sbin/hald
108       4865  4864  0 22:50 ?        00:00:00 /usr/sbin/hald
root      4866  4865  0 22:50 ?        00:00:00 hald-runner
108       4872  4866  0 22:50 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event1
108       4873  4866  0 22:50 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event4
root      4875  4866  0 22:50 ?        00:00:00 /usr/lib/hal/hald-addon-cpufreq
108       4876  4866  0 22:50 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
108       4877  4866  0 22:50 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event5
108       4878  4866  0 22:50 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event6
108       4888  4866  0 22:50 ?        00:00:00 /usr/lib/hal/hald-addon-storage

```

I haven't found a file in /var/log where those messages are logged but think the following lines from dmesg are related (look at the time stamps):

```

[   76.332000] lo: Disabled Privacy Extensions
[   76.780000] Adding 899600k swap on /dev/disk/by-uuid/54f5a768-c9dc-4b4d-a616-ef8955f3dd82.  Priority:-2 extents:1 across:899600k
[   78.164000] Using specific hotkey driver
[   79.204000] ACPI: AC Adapter [AC] (off-line)
[   79.264000] No dock devices found.
[   79.360000] input: Power Button (FF) as /class/input/input4
[   79.364000] ACPI: Power Button (FF) [PWRF]
[   79.400000] input: Lid Switch as /class/input/input5
[   79.400000] ACPI: Lid Switch [LID]
[   79.416000] input: Sleep Button (CM) as /class/input/input6
[   79.416000] ACPI: Sleep Button (CM) [SLPB]
[   87.296000] ath0: no IPv6 routers present
[  145.492000] ACPI: Battery Slot [BAT0] (battery present)
[  145.548000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[  286.872000] ppdev: user-space parallel port driver
[  288.852000] Non-volatile memory driver v1.2
[  288.904000] input: /usr/sbin/thinkpad-keys as /class/input/input7
[  294.840000] PM: Writing back config space on device 0000:02:00.0 at offset c (was 4fe0000, writing 0)
[  295.020000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  391.084000] Bluetooth: Core ver 2.11
[  391.084000] NET: Registered protocol family 31
[  391.084000] Bluetooth: HCI device and connection manager initialized
[  391.084000] Bluetooth: HCI socket layer initialized
[  547.516000] Bluetooth: L2CAP ver 2.8
[  547.516000] Bluetooth: L2CAP socket layer initialized
[  547.724000] Bluetooth: RFCOMM socket layer initialized
[  547.724000] Bluetooth: RFCOMM TTY layer initialized
[  547.724000] Bluetooth: RFCOMM ver 1.8
[  622.892000] hub 3-0:1.0: resuming
[  622.892000] hub 3-0:1.0: PM: resume from 2, parent usb3 still 2
[  622.892000] hub 3-0:1.0: resuming
[  622.892000] hub 2-0:1.0: resuming
[  622.896000] hub 2-0:1.0: PM: resume from 2, parent usb2 still 2
[  622.896000] hub 2-0:1.0: resuming
[  622.896000] hub 1-0:1.0: resuming
[  622.896000] hub 1-0:1.0: PM: resume from 2, parent usb1 still 2
[  622.896000] hub 1-0:1.0: resuming
[  884.380000] ehci_hcd 0000:00:13.2: remove, state 4
[  884.380000] usb usb3: USB disconnect, address 1
[  884.388000] ehci_hcd 0000:00:13.2: USB bus 3 deregistered
[  884.392000] ACPI: PCI interrupt for device 0000:00:13.2 disabled
[  884.556000] ohci_hcd 0000:00:13.1: remove, state 4
[  884.556000] usb usb2: USB disconnect, address 1
[  884.572000] ohci_hcd 0000:00:13.1: USB bus 2 deregistered
[  884.572000] ACPI: PCI interrupt for device 0000:00:13.1 disabled
[  884.572000] ohci_hcd 0000:00:13.0: remove, state 4
[  884.572000] usb usb1: USB disconnect, address 1
[  884.576000] ohci_hcd 0000:00:13.0: USB bus 1 deregistered
[  884.580000] ACPI: PCI interrupt for device 0000:00:13.0 disabled
[ 1024.080000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[ 1461.524000] ACPI: PCI interrupt for device 0000:04:02.0 disabled
[ 1461.524000] ath_pci: driver unloaded
[ 1461.544000] ath_rate_sample: unloaded
[ 1461.544000] ath_hal: driver unloaded
[ 1597.704000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[ 1597.744000] ath_pci: 0.9.4.5 (0.9.3)
[ 1597.748000] ACPI: PCI Interrupt 0000:04:02.0[A] -> GSI 22 (level, low) -> IRQ 19
[ 1598.012000] ath_rate_sample: 1.2 (0.9.3)

```

Which reminds me to deinstall bluetooth support.  There is no bluetooth in the R51e.


> I thought that generic is the only kernel.. anyhow, on that processor that isn't hyperthreading or 2 cores or anything, you might actually be better running a non generic kernel.

I don't mind whether it's -386 or generic.  As -386 doesn't support SMP it may actually be faster.  It was just an information that that kernel doesn't load ath_hal.ko at all and that it has the same problems otherwise.


> Also, try disabling any network interfaces that you aren't using by unticking them in 
sudo network-admin
This would be the first thing I'd try.

There are only 3 interfaces listed in /etc/network/interfaces, I've removed anything else long ago.  Other than bluetooth, this has to be done.  And there is no network-admin on this machine, scripts suit me better.

By[t]e,
    Vitus

---

### Post by dib058 on 2007-06-20
Hi...
I also install feisty on my r51e (fresh install, dualboot with xp). The installation went smooth like silk.
However, after installation, loading acpi took approx 2 minutes. Even longer with hal (about 3 minutes) for total more than 5 min only to boot.
When I disabled ACPI (and APM), boot time reduces down to 1 min. The downside is I can't monitor battery state (needs acpi obiviously). 
Is there workaround to solve this problem?

My system :
R51e (pentium M 740)
256 DDR2 memory

ps. 1. Sorry for my bad english.
2. This problem didn't occure on my other instalattion on desktop computer (duron 1800, nforce 220D, 256 MB memory).
3. I don't need soft.suspend

---

### Post by Vitus on 2007-06-20
@dib058: nice to see someone with a R51e!  I thought I'm the only one in the whole world ;) 

I'm currently at the suspend issue and running "sudo /etc/acpi/sleep.sh sleep" (i didn't try try "force", sounded a little harsh to me :) ) does allow suspend / resume!  Some modprobe's take awhile (ibm_acpi, battery) but this is bearable and perhaps can the reload be disabled in some way?

But when I use kpowersave to suspend it hangs as described.  Perhaps kpowersave isn't supported on Feisty (they have this ugly new thing), so I just suspended using the Logout dialog.  Stay tuned...

---

### Post by Vitus on 2007-06-21
> **Vitus said:**
> But when I use kpowersave to suspend it hangs as described.  Perhaps kpowersave isn't supported on Feisty (they have this ugly new thing), so I just suspended using the Logout dialog.  Stay tuned...

When I use kpowersave to suspend the resume "ends" with the following ps output:

```

root      6892  5750  0 08:35 ?        00:00:00 [prepare_suspend] <defunct>
root      6946  5750  0 08:35 ?        00:00:00 [do_screen_saver] <defunct>
root      6947  5750  0 08:35 ?        00:00:00 /bin/bash /usr/lib/powersave/do_acpi_sleep suspend2ram
root      6954  6947  1 08:35 ?        00:00:15 /usr/lib/powersave/myecho /sys/power/state mem

```

And when I do it from the logoff dialog I get

```

vitus     6259  6020  0 22:41 ?        00:00:00 /usr/bin/kdesktop_lock --forcelock
root      6262  5732  0 22:41 ?        00:00:00 [prepare_suspend] <defunct>
vitus     6306  6259  0 22:41 ?        00:00:00 penrose -window-id 27262988 -delay 10000 -ncolors 64 -size 40
root      6316  5732  0 22:41 ?        00:00:00 [do_screen_saver] <defunct>
root      6317  5732  0 22:41 ?        00:00:00 /bin/bash /usr/lib/powersave/do_acpi_sleep suspend2ram
root      6324  6317  3 22:41 ?        00:00:14 /usr/lib/powersave/myecho /sys/power/state mem

```

Not much difference!  So the solution is to deinstall powersave as this is causing the hang?  Go for this ugly powermanager?

Is there any connection from kpowersave of another GUI to "sudo /etc/acpi/sleep.sh sleep"?  As that script works well.  Perhaps can a get the script to be called when I press the suspend button on the thinkpad itself?

Vitus

---

### Post by Vitus on 2007-06-21
> **dib058 said:**
> Hi...
However, after installation, loading acpi took approx 2 minutes. Even longer with hal (about 3 minutes) for total more than 5 min only to boot.


I've looked at the process list.

First delay:

```

/etc/rc2.d/S10acpid start
...
modprobe -b battery

```

Strange!  Modprobing battery takes it's time even on resume but never so long.  And what does "-b" do???   It's not in the manual page and a problematic expression in google.  Any hints?

Second delay:

```

<don't remember>/S12dbus start
...
/etc/dbus-1/event.d/20hal start
...
hald-addon-keyboard: listening on /dev/input/event6

```

As this hald-addon-keyboard is still running on the booted system it's probably not the source of the delay.  What comes after starting that process?  Where is the place to look at?

Any hints?

Vitus

---

### Post by Vitus on 2007-06-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/92647](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/92647) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				"modprobe -b" tells modprobe to take the blacklist into account.

See the link to launchpad, we may have hit that bug.  I will try to get an update via the backports and will report back if it speedups my bootup time.

Vitus

---

### Post by Vitus on 2007-06-22
> **Vitus said:**
> 
See the link to launchpad, we may have hit that bug.  I will try to get an update via the backports and will report back if it speedups my bootup time.

Backport package sources were already enabled :o

I went back to hal 0.5.8 from the normal archives, still the same timing.   Do I have to backlevel more packages?  How do you guys think about backports?  Good or Bad?  I don't think one can easily remove all backports already installed?

---

### Post by Vitus on 2007-06-27
Here is a bootchart of the booting of Feisty on my Thinkpad R51e, backports enabled, last update today: [http://crazy-teaparty.dyndns.org/linux/feisty-20070627-1.png](http://crazy-teaparty.dyndns.org/linux/feisty-20070627-1.png)

As you see there is a 65s delay while "modprobe" is running (that would be "modprobe -b battery")
And another 140s delay while hald, hald-runner or the like is running.  Can't see what is really executing here.

Any tips?  I mean other than going back to Dapper Drake?

---

### Post by Vitus on 2007-07-28
I've restored the saved copy of Dapper to another partition and am using that now.
Feisty Fawn was updated to Gutsy Gibbon which worked exactly as Feisty Fawn, long boot times and no suspend.

Additionally Dapper Drake has the following advantages to me:
* a working wifi driver for atheros chipsets
* faster reaction to power changes
* APIC working
* -686 kernel working (no wifi in Feisty)
* working automount of usb disks

Yes, Dapper has it's faults (USB interrupts running wild, kmail traps, ...) and I will never get CONFIG_NO_HZ but as least the basics work.

---

### Post by hkphooey on 2007-12-25
I have an R51e as well. I found a workaround, although not exactly a fix. 

Adding ec_intr=0 at the end of boot stanza greatly reduces the boot time, but doesn't _solve_ the apic problem. e.g. 
```
/vmlinuz-2.6.22-14-generic root=/dev/hda8 ro quiet splash ec_intr=0
```

This is based on a recommendation at the kernel bugtracker here [http://bugzilla.kernel.org/show_bug.cgi?id=8246](http://bugzilla.kernel.org/show_bug.cgi?id=8246)

---

### Post by Vitus on 2007-12-30
> **hkphooey said:**
> I have an R51e as well. I found a workaround, although not exactly a fix. 

Adding ec_intr=0 at the end of boot stanza greatly reduces the boot time, but doesn't _solve_ the apic problem. e.g. 
```
/vmlinuz-2.6.22-14-generic root=/dev/hda8 ro quiet splash ec_intr=0
```

This is based on a recommendation at the kernel bugtracker here [http://bugzilla.kernel.org/show_bug.cgi?id=8246](http://bugzilla.kernel.org/show_bug.cgi?id=8246)

Thank you!

I'm still at Dapper Drake but installed gentoo as a second distri and hald in gentoo has this problem, too (as it's distri-independent).  Added ec_intr=0 and bootup was quick and smooth.  I haven't tried suspend with ec_intr=0.

---

### Post by anton_mellit on 2008-01-22
I decided to share my experience of several days of configuring Gutsy on Thinkpad R51e. I have Gutsy with kernel 2.6.22-14-generic. There are several issues:
1. Too long boot time. Fixed by kernel option ec_intr=0.
2. Suspend-to-ram. 
First I removed different power managers, i tried to play with, and installed just standard ones:

sudo apt-get remove --purge power*
sudo apt-get remove --purge acpi-support acpid acpi
sudo apt-get install acpi acpid acpi-support powermgmt-base powernowd kde-guidance-powermanager

After this when i execute /etc/acpi/sleep.sh (in text mode, boot in recovery mode) my laptop goes to sleep and wakes up normally, but freezes after some time (approx 1 minute). This was cured by kernel option nolapic (i don't know what it means, just saw it on some forums)

Now suspend to ram works perfectly __unless__ there is fglrx in the kernel. If fglrx is there, even from text mode my laptop does not go to sleep, just remains frozen with screen turned off. So I am forced to use the 'radeon' driver 

so this is my boot string from /boot/grub/menu.lst:
/boot/vmlinuz-2.6.22-14-generic root=UUID=074...31 ro single nolapic ec_intr=0
(dots are mine)

3. There is one thing that bothers me. I don't get any events when I close lid or press any buttons, like power button or sleep (Fn+F4). I don't get anything in /var/acpi/log and when i do acpi_listen nothing happens. I tried to turn off acpid and listen to /proc/acpi/event - the same. I checked that module 'button' is enabled. So automatic standby on lid close does not work. However the corresponding value /proc/acpi/button/lid/LID/state correctly displays the state.

Anton

---

