---
title: "General Tips for Improving Battery Life"
date: 2011-08-20
forum: Hardware
---

### Post by romber on 2011-08-20
Hi,

I am still fairly new to Ubuntu 11.04 with a switch from Windows 7. On my laptop, with Windows 7, I could get 4-6 hours of battery life, no problem. However, with Ubuntu 11.04, I am getting 2.5 hours MAX. This is a huge discrepancy! 

Anyways, I figured it has to do with settings. I have adjusted my power settings, but it hasn't got me back to where I am with Windows. 

My question is what other things can I do to increase the battery life? I have pretty much default settings packaged with Ubuntu 11.04, and I have Compiz and Ubuntu Tweak.

Any help would be greatly appreciated! Any questions, just ask!

---

### Post by sanderd17 on 2011-08-20
try this here, it really saved a lot of my battery life.

Edit: including the link is probably not a bad idea: [http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)

---

### Post by romber on 2011-08-21
Thanks!

I did this an it did improve my battery life by about 10%, which is great. However, my battery life is incredibly low compared to Windows. From my understanding, it looks like a Bug in the Kernel, so I'm not sure how much can be done for it.

But, any more tips that people have would be fantastic!

Thanks again!

---

### Post by romber on 2011-08-21
bump

---

### Post by romber on 2011-08-22
bump

---

### Post by sbraz on 2011-08-22
what does powertop say?

```
sudo apt-get install powertop
sudo powertop
```

---

### Post by Stubby Holders on 2011-08-22
Hello I am newbie in ubuntu and I have a question which is at what percent of the battery life should I plugged in and charge?

---

### Post by romber on 2011-08-23
> **sbraz said:**
> what does powertop say?

```
sudo apt-get install powertop
sudo powertop
```

First screen:

Your CPU supports the following C-states : C1 C2 C3 
Your BIOS reports the following C-states : C1 C2 C3

And the test screen:


Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 1.7%)       Turbo Mode     6.6%
polling          10.4ms ( 0.2%)         2.27 Ghz     0.0%
C1 mwait          0.1ms ( 0.1%)         2.14 Ghz     0.0%
C2 mwait          4.0ms (23.7%)         1.74 Ghz     0.0%
C3 mwait          3.1ms (74.4%)         1199 Mhz    93.4%

---

### Post by sbraz on 2011-08-23
my bad, wrong command.
```
sudo powertop **-d**
```

---

### Post by sbraz on 2011-08-23
> **Stubby Holders said:**
> Hello I am newbie in ubuntu and I have a question which is at what percent of the battery life should I plugged in and charge?
batteries are optimized per design to work between 25% and 75% of their charge.

if you keep the charge between those ranges it's a great idea, of course it's okay to fill it up if you you need it at 100%. :)

---

### Post by romber on 2011-08-23
Not sure what is important here, so I just copied it all.

```
Your CPU supports the following C-states : C1 C2 C3 
Your BIOS reports the following C-states : C1 C2 C3 
Cn	          Avg residency
C0 (cpu running)        ( 0.0%)
polling		  1.5ms ( 0.0%)
C1 mwait	  0.2ms ( 0.2%)
C2 mwait	  1.1ms (14.3%)
C3 mwait	  3.9ms (86.7%)
P-states (frequencies)
  2.27 Ghz     7.0%
  2.00 Ghz     0.1%
  1.87 Ghz     0.0%
  1333 Mhz     0.4%
  1199 Mhz    92.5%
Disk accesses:
The application 'flush-8:0' is writing to file 'data_1' on /dev/sda6
The application 'flush-8:0' is writing to file 'data_0' on /dev/sda6
The application 'chrome' is writing to file 'History-journal' on /dev/sda6
The application 'chrome' is writing to file 'History-journal' on /dev/sda6
The application 'chrome' is writing to file '?' on /dev/sda1
The application 'chrome' is writing to file '?' on /dev/sda1
The application 'chrome' is writing to file '?' on /dev/sda1
The application 'chrome' is writing to file '?' on /dev/sda1
The application 'gconfd-2' is writing to file 'saved_state.tmp' on /dev/sda6
The application 'gconfd-2' is writing to file 'saved_state.tmp' on /dev/sda6
The application 'chrome' is writing to file 'Current Session' on /dev/sda6
The application 'chrome' is writing to file 'Current Session' on /dev/sda6
The application 'chrome' is writing to file 'Current Session' on /dev/sda6
Wakeups-from-idle per second : 362.8	interval: 15.0s
no ACPI power usage estimate available
Top causes for wakeups:
  14.8% ( 63.1)   [i915] <interrupt>
  12.6% ( 54.0)   SignalSender
   4.4% ( 18.7)D  chrome
   8.3% ( 35.5)   [ehci_hcd:usb2] <interrupt>
   8.3% ( 35.5)   USB device 2-1.2 : USB Receiver (Logitech)
   6.8% ( 28.9)   alsa-sink
   6.6% ( 28.1)   [iwlagn] <interrupt>
   5.5% ( 23.3)   kworker/0:0
   5.3% ( 22.7)   [kernel scheduler] Load balancing tick
   4.4% ( 19.0)   [Rescheduling interrupts] <kernel IPI>
   3.7% ( 16.0)   kworker/0:1
   3.3% ( 14.1)   compiz
   2.3% ( 10.0)   ubuntuone-syncd
   2.3% ( 10.0)   gwibber-service
   2.3% ( 10.0)   iPodService.exe
   1.7% (  7.4)   [ahci] <interrupt>
   0.1% (  0.3)D  flush-8:0
   0.0% (  0.1)D  gconfd-2
   1.2% (  5.0)   syndaemon
   1.2% (  5.0)   banshee
   1.1% (  4.9)   wineserver
   0.5% (  2.0)   AppleMobileDevi
   0.5% (  1.9)   [kernel core] iwl_bg_watchdog (iwl_bg_watchdog)
   0.4% (  1.8)   [TLB shootdowns] <kernel IPI>
   0.4% (  1.8)   [kernel core] hrtimer_start (tick_sched_timer)
   0.3% (  1.2)   gnome-terminal
   0.2% (  1.0)   [hda_intel] <interrupt>
   0.2% (  1.0)   gvfs-afc-volume
   0.2% (  0.9)   kworker/u:19
   0.1% (  0.6)   [Function call interrupts] <kernel IPI>
   0.1% (  0.5)   udisks-daemon
   0.1% (  0.5)   threaded-ml
   0.1% (  0.3)   [kernel core] cfq_arm_slice_timer (cfq_idle_slice_timer)
   0.1% (  0.3)   gnome-settings-
   0.1% (  0.3)   gnome-screensav
   0.1% (  0.3)   unity-applicati
   0.1% (  0.3)   rtkit-daemon
   0.1% (  0.3)   Xorg
   0.1% (  0.3)   unity-panel-ser
   0.0% (  0.2)   update-notifier
   0.0% (  0.1)   gnome-power-man
   0.0% (  0.1)   NetworkManager
   0.0% (  0.1)   ips-adjust
   0.0% (  0.1)   irqbalance
   0.0% (  0.1)   rsyslogd
   0.0% (  0.1)   wpa_supplicant
   0.0% (  0.1)   ssh-agent
   0.0% (  0.1)   cron

An audio device is active 100.0% of the time:
hwC0D0 Realtek ALC272 

A USB device is active 100.0% of the time:
/sys/bus/usb/devices/2-1

Suggestion: Enable USB autosuspend for non-input devices by pressing the U key


Suggestion: increase the VM dirty writeback time from 5.00 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs 
This wakes the disk up less frequently for background VM activity

Suggestion: enable the power aware CPU scheduler with the following command:
  echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
or by pressing the C key.

Suggestion: Enable SATA ALPM link power management via: 
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.

Suggestion: Enable wireless power saving mode by executing the following command:
  iwconfig wlan0 power timeout 500ms
This will sacrifice network performance slightly to save power.

Suggestion: enable HD audio powersave mode by executing the following command:
   echo 1 > /sys/module/snd_hda_intel/parameters/power_save 
or by passing power_save=1 as module parameter.

Suggestion: Enable the CONFIG_INOTIFY kernel configuration option.
This option allows programs to wait for changes in files and directories
instead of having to poll for these changes

Suggestion: Enable the CONFIG_PM_ADVANCED_DEBUG kernel configuration option.
This option will allow PowerTOP to collect runtime power management statistics.

The program 'chrome' is writing to file 'Current Session' on /dev/sda6.
This prevents the disk from going to powersave mode.

The program 'chrome' is writing to file 'Current Session' on /dev/sda6.
This prevents the disk from going to powersave mode.

The program 'chrome' is writing to file 'Current Session' on /dev/sda6.
This prevents the disk from going to powersave mode.

The program 'gconfd-2' is writing to file 'saved_state.tmp' on /dev/sda6.
This prevents the disk from going to powersave mode.

The program 'gconfd-2' is writing to file 'saved_state.tmp' on /dev/sda6.
This prevents the disk from going to powersave mode.

The program 'chrome' is writing to file 'History-journal' on /dev/sda6.
This prevents the disk from going to powersave mode.

The program 'chrome' is writing to file 'History-journal' on /dev/sda6.
This prevents the disk from going to powersave mode.

The program 'flush-8:0' is writing to file 'data_0' on /dev/sda6.
This prevents the disk from going to powersave mode.

The program 'flush-8:0' is writing to file 'data_1' on /dev/sda6.
This prevents the disk from going to powersave mode.

Recent USB suspend statistics
Active  Device name
100.0%	USB device 2-1.2 : USB Receiver (Logitech)
  0.0%	USB device 1-1.6 : Chicony USB 2.0 Camera (Chicony)
100.0%	/sys/bus/usb/devices/2-1
  0.0%	/sys/bus/usb/devices/1-1
100.0%	USB device usb2 : EHCI Host Controller (Linux 2.6.38-11-generic-pae ehci_hcd)
  0.0%	USB device usb1 : EHCI Host Controller (Linux 2.6.38-11-generic-pae ehci_hcd)

Runtime Device Power Management statistics
Active  Device name
  0.0%	02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 
  0.0%	01:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet 
  0.0%	00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem 
  0.0%	00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller 
  0.0%	00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller 
  0.0%	00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 
  0.0%	00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 
  0.0%	00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 
  0.0%	00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio 
  0.0%	00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller 
  0.0%	00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller 
  0.0%	00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller 

Devices without runtime PM















3f:02.3 Host bridge: Intel Corporation Core Processor Reserved 
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved 
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder 
5 more devices without runtime PM ommitted

Recent audio activity statistics
Active  Device name
100.0%	hwC0D0 Realtek ALC272 
  0.0%	hwC0D3 Intel IbexPeak HDMI 

Recent SATA AHCI link activity statistics
Active	Partial	Slumber	Device name

```

---

### Post by romber on 2011-08-23
bump

---

### Post by romber on 2011-08-24
bump

---

### Post by sbraz on 2011-08-24
```
uname -a
```

also, what cpu are you running? if it's a sandy bridge there are bugs in the kernel unsolved as of today, even using 3.0.3.
those bugs will be solved soon i hope. :(

---

### Post by realzippy on 2011-08-24
> **sbraz said:**
> ```
uname -a
```
also, what cpu are you running? if it's a sandy bridge there are bugs in the kernel unsolved as of today, even using 3.0.3.
those bugs will be solved soon i hope. :(

..*especially* when running 3.03.
2.6.38.10 is (relative) fine with sandybridge.

---

### Post by sbraz on 2011-08-24
if you actually have a sandy bridge cpu, we're discussing bugs here:
[http://ubuntuforums.org/showthread.php?t=1822629](http://ubuntuforums.org/showthread.php?t=1822629)

read subscribe and wait for an answer from kernel developers. :)

---

### Post by romber on 2011-08-26
> **sbraz said:**
> ```
uname -a
```

also, what cpu are you running? if it's a sandy bridge there are bugs in the kernel unsolved as of today, even using 3.0.3.
those bugs will be solved soon i hope. :(

```
Linux eric-Satellite-E205 2.6.38-11-generic-pae #48-Ubuntu SMP Fri Jul 29 20:51:21 UTC 2011 i686 i686 i386 GNU/Linux
```

By cpu, do you mean processors? 

Also, thanks for all the help and responses!

---

### Post by sbraz on 2011-08-26
> **romber said:**
> ```
Linux eric-**Satellite-E205** **2.6.38-11-generic-pae** #48-Ubuntu SMP Fri Jul 29 20:51:21 UTC 2011 i686 i686 i386 GNU/Linux
```

By cpu, do you mean processors? 

Also, thanks for all the help and responses!
yes, the processor.

based on the hostname i think you have a toshiba satellite E205, with 4GB ram and an i5-430M, so no sandy bridge.

i see you have a PAE kernel installed... why didn't you install ubuntu 64bit right away? :)

---

### Post by afoglia on 2011-08-29
> **romber said:**
> Not sure what is important here, so I just copied it all.

If you look, powertop gives you suggestions on what to try:



```
Suggestion: Enable USB autosuspend for non-input devices by pressing the U key


Suggestion: increase the VM dirty writeback time from 5.00 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs 
This wakes the disk up less frequently for background VM activity

Suggestion: enable the power aware CPU scheduler with the following command:
  echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
or by pressing the C key.

Suggestion: Enable SATA ALPM link power management via: 
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.

Suggestion: Enable wireless power saving mode by executing the following command:
  iwconfig wlan0 power timeout 500ms
This will sacrifice network performance slightly to save power.

Suggestion: enable HD audio powersave mode by executing the following command:
   echo 1 > /sys/module/snd_hda_intel/parameters/power_save 
or by passing power_save=1 as module parameter.

Suggestion: Enable the CONFIG_INOTIFY kernel configuration option.
This option allows programs to wait for changes in files and directories
instead of having to poll for these changes

Suggestion: Enable the CONFIG_PM_ADVANCED_DEBUG kernel configuration option.
This option will allow PowerTOP to collect runtime power management statistics.

```

Any one with a command you can run yourself at the command-line, which are the following
```

echo 1500 > /proc/sys/vm/dirty_writeback_centisecs 
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
iwconfig wlan0 power timeout 500ms
echo 1 > /sys/module/snd_hda_intel/parameters/power_save 

```

As for the others, the last two are kernel options, which involves compiling your own kernel, which is too much trouble.  (Plus I believe inotify is already enabled in the Ubuntu kernels.)  And the first doesn't seem to have a command, but if you run powertop interactively (i.e. without the -d option), powertop will eventually offer to make that change itself.

I haven't done timing tests, but my computer runs noticeably cooler with the powertop suggestions enabled.

At this point, I would suggest adding those commands to /etc/rc.local, so they'll run on startup.  But that does not work.  Something later on the in the process cancels them.  Instead, store them in a single script file that you run yourself.

---

