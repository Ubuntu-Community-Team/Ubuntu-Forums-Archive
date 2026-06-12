---
title: "Suspend &lt;1 hour is fine, &gt;1 hour locks up HP Pavilion G7"
date: 2011-06-05
forum: Hardware
---

### Post by mdmayfield on 2011-06-05
Hello,

I recently installed Xubuntu 11.04 on an HP Pavilion G7 1075dx. It has an AMD Phenom II P650 CPU and a Radeon HD 4250 graphics card. I'm using the open source Radeon drivers.

After fixing the wireless connection by inserting "wl" into Suspend_Modules, sleep mode seemed to work just fine. But if the computer is left in suspend for greater than a certain amount of time, it will not wake up (black, unlit screen; fan running; and Caps Lock, Num Lock, and F12 lights come on but unresponsive), and I have to remove the battery and power adapter before the laptop will boot at all again.

So far, I hypothesize that the critical length of time is exactly one hour; so far my experiments show it is between 31 minutes and 68 minutes.

Is my computer going into an auto-hibernate mode that is not compatible with it, or something? What could explain this? Where should I start?

Thanks in advance for any help.

Matt

---

### Post by Toz on 2011-06-05
There may some important information in /var/log/pm-suspend that can help pinpoint the issue.

---

### Post by mdmayfield on 2011-06-05
Thanks! I wondered where a relevant log might be; I'll check that.

---

### Post by mdmayfield on 2011-06-05
On reviewing /var/log/pm-suspend.log, I'm not finding very much that is helpful. The only difference I'm seeing is that when the laptop was able to resume, the log shows all the pre-suspend hooks running, up through:
```
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Sun Jun  5 06:28:47 CDT 2011: performing suspend
Sun Jun  5 07:00:20 CDT 2011: Awake.
Sun Jun  5 07:00:20 CDT 2011: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
```----and so forth, listing many other hooks and their success at resuming.

When the laptop crashes, there is simply nothing more (only the next sleep attempt after a full power cycle) after:
```
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Sun Jun  5 07:14:12 CDT 2011: performing suspend
```...and then at that point it just lists the next suspend attempt over an hour later, after I pull the battery out & restart the computer after its hard crash.

Are there any other useful places I can look for clues? My BIOS does not seem to offer any options for ACPI.

If any kind and knowledgeable soul wants to look over the entire log, please let me know and I will upload it. Thanks,

Matt

---

### Post by mdmayfield on 2011-06-05
A couple other things. On digging through kern.log, I found this:

```
Jun  5 01:06:55 PavilionG7MM kernel: [   12.330727] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SMBI [io 0xb00-0xb0f]
Jun  5 01:06:55 PavilionG7MM kernel: [   12.330729] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
```This is a bit more advanced than my current knowledge; I don't know exactly what it refers to, but I wonder if it might be relevant. Also this:

```
Jun  5 01:16:05 PavilionG7MM kernel: [    1.330251] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jun  5 01:16:05 PavilionG7MM kernel: [    1.380273] ACPI: AC Adapter [ACAD] (on-line)
Jun  5 01:16:05 PavilionG7MM kernel: [    1.380370] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Jun  5 01:16:05 PavilionG7MM kernel: [    1.380374] ACPI: Power Button [PWRB]
Jun  5 01:16:05 PavilionG7MM kernel: [    1.380422] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
Jun  5 01:16:05 PavilionG7MM kernel: [    1.380595] ACPI: Lid Switch [LID]
Jun  5 01:16:05 PavilionG7MM kernel: [    1.380629] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jun  5 01:16:05 PavilionG7MM kernel: [    1.380632] ACPI: Power Button [PWRF]
Jun  5 01:16:05 PavilionG7MM kernel: [    1.380739] ACPI: acpi_idle registered with cpuidle
Jun  5 01:16:05 PavilionG7MM kernel: [    1.380794] ACPI: processor limited to max C-state 1
Jun  5 01:16:05 PavilionG7MM kernel: [    1.580572] [Firmware Bug]: Invalid critical threshold (0)
Jun  5 01:16:05 PavilionG7MM kernel: [    1.581147] thermal LNXTHERM:00: registered as thermal_zone0
Jun  5 01:16:05 PavilionG7MM kernel: [    1.581149] ACPI: Thermal Zone [THRM] (58 C)
Jun  5 01:16:05 PavilionG7MM kernel: [    1.581170] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared

```Processor limited to max C-state 1? Doesn't that mean it can't sleep?

---

### Post by mdmayfield on 2011-06-07
If nothing is being logged at the moment when the computer "dies" about an hour into suspend mode, what steps can I take to troubleshoot this?

---

### Post by mdmayfield on 2011-06-07
I don't know why this works, but I seem to have fixed this problem by following the directions in this blog:

[http://www.wzzrd.com/2010/10/resume-from-suspend-broken-on-recent.html](http://www.wzzrd.com/2010/10/resume-from-suspend-broken-on-recent.html)

to add "acpi_sleep=nonvs" to the GRUB default command line. This was used on other laptops to fix a different suspend-to-RAM issue.

---

### Post by Toz on 2011-06-07
Interesting. According to the document you linked to, the issue should have been fixed in kernel 2.6.36. If you are using Natty then you're using 2.6.38. 

Anyways, good find and thanks for posting back the fix.

---

### Post by mdmayfield on 2011-06-08
Stranger and stranger... Suspend/resume worked fine a few times - once for 7 hours, once for 9 hours - but after the computer "slept" for 26 hours, it crashed again in the same way as before.

No idea what could be causing this. Still no clues in the log; the last entry in pm-suspend.log before the crash is simply "performing suspend."

---

### Post by mdmayfield on 2011-06-12
Well.... I started investigating ACPI and DSDT files. iasl shows several errors and a bunch of warnings in my BIOS' DSDT. I can only assume that the solution to the problem lies there, someplace.

**[http://xkcd.com/456/](http://xkcd.com/456/)**

---

### Post by mdmayfield on 2011-08-15
:confused:

Still no luck on this issue, even after trying a fixed DSDT table. I've just been shutting down the computer whenever I'm not going to use it for a while. Any ideas or resources?

---

### Post by Toz on 2011-08-15
Is the laptop warm after an hour or more of sleep? I'm wondering if it can be an overheating issue. Have a look at this post: [http://ubuntuforums.org/showthread.php?t=902332]("http://ubuntuforums.org/showthread.php?t=902332")

---

### Post by mdmayfield on 2011-08-16
Thanks a lot for the reply - that's interesting. The laptop is not warm to the touch after suspend, but I suppose that might be possible.

I never did try sleep under Windows; I reformatted the drive after buying the laptop and it didn't come with an install disc. But I think I'd rather live with turning it off than having to install Win 7.

Thanks again!

---

### Post by mdmayfield on 2011-08-22
Recently I saw a firmware update was available from HP's web site, so I booted using the demo version of Active@ and ran the updater off a USB drive.

The firmware update worked, but there is no difference in the machine's behavior.

Then I thought that maybe there could be a kernel module like VirtualBox causing a conflict, and removed that, but with no luck.

This is getting very frustrating and I'm getting ready to reinstall Windows and sell the laptop to somebody who wants Win 7. I haven't tried it but I can only assume suspend/resume will work fine under Windows.

I was thinking I might try this: [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)   but that seems like so much work when I could just take a small monetary loss and get a different laptop, probably a MacBook since I like OSX and I could just make a small Linux partition on it for dual-booting.

Final call for help. Anybody have any last ideas?

---

