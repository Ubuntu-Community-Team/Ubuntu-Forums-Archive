---
title: "Cannot restore all the way from sleep/hibernation since some days ago!"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by motin on 2007-04-20
I began trying Feisty around 22st of March, and it has really been a pleasure!

Since some days ago however, I cannot restore all the way from sleep nor hibernation!

I get back into a black screen with a mousepointer displaying the "Thinking" mouse pointer. Every 15 seconds or so the pointer goes away and repositions itself in the middle of the screen. Is GDM constantly restarting? I don't know - because I find no way to troubleshoot it!

I cannot access any other terminal (Ctrl + Alt + #), and Ctrl + Alt + Backspace does nothing...

If I press the power button on my laptop it will eventually shutdown (displaying some garbled lines of graphics in the top of the screen before going down all the way). 

This is so annoying - since I really rely on the suspend function to be able to use my laptop the way I am used to!

Please help! Where should I start investigating?

---

### Post by sudo_nym on 2007-04-21
It does sound like Xorg or GDM's acting weird, but at least the bare-minimum system is loading.

I don't know what to do about this, but as for getting to a console; try hitting ESC at boot time, as soon as the `Grub Loading...' message appears.  Then Grub will show you a menu of boot options.  Try `Recovery Mode'.  This will boot into single-user mode, bypassing the graphical login.

But with a newer kernel, you'll probably be prompted for the root passord before you can start a console session.  By the way, unlike sudo and gksu [I think that's short for `graphical sudo'], this one really does want the *root* password, not your password.

Don't know the root password?  If you've upgraded to Feisty, try the *oldest* kernel that appears in your Grub menu.  It might not prompt you for one.

From the console you can type `startx' to manually start an X session.  Once you get to the desktop, you'll find that root isn't allowed to do as much as you'd think, but maybe you can look around enough to figure out what's wrong.  Maybe you can also do a `nested login' from there, as yourself.

I'm sorry I can't help you with the problem, but maybe this will help you figure out what the problem is.


Good luck,

Patrick.

---

### Post by sudo_nym on 2007-04-21
> **motin said:**
> [...]

I cannot access any other terminal (Ctrl + Alt + #), and Ctrl + Alt + Backspace does nothing...

Sorry, I forgot to mention; it's `Ctrl + Alt + [F1 to F6]' -- function keys, not number keys.

But maybe you knew that already.


Patrick.

---

### Post by motin on 2007-04-22
Thanks Patrick for your reply! 

Luckily, it seems the problem has mostly gone away after I uninstalled beagle. The weird behavior was only apparent after resume from sleep/hibernation - so after a reboot everything works as expected. 

A problem that persists however is what one should do if something similar happens again? I'd love a message after reboot like "Your computer was manually restarted due to a problem awakening from resume. The conflicting application is "beagle", do you want to remove it?" or similar...

PS Yes I knew about the Function-keys - my mistake writing a lone number... Sorry.

---

### Post by sudo_nym on 2007-04-24
> **motin said:**
> Thanks Patrick for your reply! 

Luckily, it seems the problem has mostly gone away after I uninstalled beagle. The weird behavior was only apparent after resume from sleep/hibernation - so after a reboot everything works as expected. 

Okay, I thought you were completely locked out of your desktop.  Glad it wasn't that bad.  :-)

> A problem that persists however is what one should do if something similar happens again? I'd love a message after reboot like "Your computer was manually restarted due to a problem awakening from resume. The conflicting application is "beagle", do you want to remove it?" or similar...

Well, to some extent they try to.  That's why Synaptic won't let you install some programs without removing something else, where the two obviously conflict.  But unfortunately, the package maintainers don't know everything [that's what bug reports are for  ;-) ].

For older, pre-X MacOSes there were a lot of diagnostic tools to catch extension conflicts.  System extensions = libraries, basically.  There's probably similar for Linux, but if so I don't know what.

I have a bad habit of installing/upgrading several programs at once, and then when something else starts acting strange, I have a lot of trouble figuring out why.  One at a time might be easier.  The syslog might also help track these things down, if you know how to read it [and by the way, no I don't know how to read it either...].


Thanks, you've given me a few things to think about,

Patrick.

---

### Post by motin on 2007-04-24
Yesterday evening I had the problem again. It is rather frustrating not knowing what is causing it... can't even file a bug report. Or can I? This unspecific?

I'll try to analyze the syslog next time, as well as following the guidance here: [http://ubuntuforums.org/showthread.php?t=409734](http://ubuntuforums.org/showthread.php?t=409734)

Thanks for your interest.

---

### Post by strabes on 2007-04-24
[http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200](http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200)

> Finally, the perhaps most important change goes into /etc/default/acpi-support. Change the line POST_VIDEO=true to read POST_VIDEO=. This was the point when it started working on my system.

---

### Post by motin on 2007-04-25
Dammit, now it does this again!

I am going to make a task trace using a SysRq magic key combination next time and paste it's output here...

EDIT: Updated the laptop hardware testing wiki page about this issue here: [https://wiki.ubuntu.com/LaptopTestingTeam/HPDV4000](https://wiki.ubuntu.com/LaptopTestingTeam/HPDV4000)

---

### Post by motin on 2007-04-27
> **motin said:**
> Dammit, now it does this again!

I am going to make a task trace using a SysRq magic key combination next time and paste it's output here...

EDIT: Updated the laptop hardware testing wiki page about this issue here: [https://wiki.ubuntu.com/LaptopTestingTeam/HPDV4000](https://wiki.ubuntu.com/LaptopTestingTeam/HPDV4000)

It is happening all the time now! ...

Attached is the output of Alt + SysRq + T (Loglevel 1) when the system is in it's non-responsive, restarting state.

What is going wrong here?

Is this a probable bug in the kernel? Or gdm? In what package to I report this?

---

### Post by groggyboy on 2007-05-12
motin, i have trouble resuming from long suspends, and my symptom is identical - the cursor in the middle of a black screen, switching between the arrow and the spinning wheel - it does that indefinitely, as a far as i can tell.  hibernate doesn't work at all for me (a swap problem).

i have a dell inspiron 6000.

this morning, i tried waking it after it had been sleeping all night.  i ended things by forcibly rebooting the computer.  you can see it all in /var/log/acpi:```
[Sun May 13 11:54:06 2007] received event "ac_adapter AC 00000080 00000000"
[Sun May 13 11:54:06 2007] notifying client 4647[107:114]
[Sun May 13 11:54:06 2007] notifying client 4772[0:0]
[Sun May 13 11:54:06 2007] client has disconnected
[Sun May 13 11:54:06 2007] executing action "/etc/acpi/power.sh"
[Sun May 13 11:54:06 2007] BEGIN HANDLER MESSAGES
[Sun May 13 11:54:07 2007] END HANDLER MESSAGES
[Sun May 13 11:54:07 2007] action exited with status 0
[Sun May 13 11:54:07 2007] completed event "ac_adapter AC 00000080 00000000"
[Sun May 13 11:54:07 2007] received event "button/lid LID 00000080 00000008"
[Sun May 13 11:54:07 2007] notifying client 4647[107:114]
[Sun May 13 11:54:07 2007] executing action "/etc/acpi/lid.sh"
[Sun May 13 11:54:07 2007] BEGIN HANDLER MESSAGES
[Sun May 13 11:54:12 2007] END HANDLER MESSAGES
[Sun May 13 11:54:12 2007] action exited with status 0
[Sun May 13 11:54:12 2007] completed event "button/lid LID 00000080 00000008"
[Sun May 13 11:54:12 2007] received event "battery BAT0 00000081 00000001"
[Sun May 13 11:54:12 2007] notifying client 4647[107:114]
[Sun May 13 11:54:12 2007] executing action "/etc/acpi/power.sh"
[Sun May 13 11:54:12 2007] BEGIN HANDLER MESSAGES
[Sun May 13 11:54:12 2007] END HANDLER MESSAGES
[Sun May 13 11:54:12 2007] action exited with status 0
[Sun May 13 11:54:12 2007] completed event "battery BAT0 00000081 00000001"
[Sun May 13 11:54:19 2007] client connected from 4772[0:0]
[Sun May 13 11:54:19 2007] 1 client rule loaded
[Sun May 13 11:54:26 2007] client connected from 30213[0:0]
[Sun May 13 11:54:26 2007] 1 client rule loaded
[Sun May 13 11:54:39 2007] client connected from 30302[0:0]
[Sun May 13 11:54:39 2007] 1 client rule loaded
[Sun May 13 11:54:49 2007] client connected from 30326[0:0]
[Sun May 13 11:54:49 2007] 1 client rule loaded
[Sun May 13 11:54:59 2007] client connected from 30350[0:0]
[Sun May 13 11:54:59 2007] 1 client rule loaded
[Sun May 13 11:55:44 2007] received event "button/power PBTN 00000080 00000001"
[Sun May 13 11:55:44 2007] notifying client 4647[107:114]
[Sun May 13 11:55:44 2007] notifying client 4772[0:0]
[Sun May 13 11:55:44 2007] client has disconnected
[Sun May 13 11:55:44 2007] notifying client 30213[0:0]
[Sun May 13 11:55:44 2007] client has disconnected
[Sun May 13 11:55:44 2007] notifying client 30302[0:0]
[Sun May 13 11:55:44 2007] client has disconnected
[Sun May 13 11:55:44 2007] notifying client 30326[0:0]
[Sun May 13 11:55:44 2007] client has disconnected
[Sun May 13 11:55:44 2007] notifying client 30350[0:0]
[Sun May 13 11:55:44 2007] executing action "/etc/acpi/powerbtn.sh"
[Sun May 13 11:55:44 2007] BEGIN HANDLER MESSAGES
```
here's /var/log/messages of the same event:```
May 13 11:54:09 localhost kernel: [32256.052000] Disabling non-boot CPUs ...
May 13 11:54:09 localhost kernel: [32256.052000] Stopping tasks ... done.
May 13 11:54:09 localhost kernel: [32256.248000] Suspending console(s)
May 13 11:54:09 localhost gnome-power-manager: (groggyboy) DBUS timed out, but recovering
May 13 11:54:09 localhost gnome-power-manager: (groggyboy) Resuming computer
May 13 11:54:09 localhost kernel: [32257.988000] ACPI: PCI interrupt for device 0000:03:01.2 disabled
May 13 11:54:09 localhost kernel: [32258.004000] ohci1394 does not fully support suspend and resume yet
May 13 11:54:09 localhost kernel: [32258.024000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
May 13 11:54:09 localhost kernel: [32258.040000] ACPI: PCI interrupt for device 0000:00:1e.2 disabled
May 13 11:54:09 localhost kernel: [32258.040000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
May 13 11:54:09 localhost kernel: [32258.056000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
May 13 11:54:09 localhost kernel: [32258.056000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
May 13 11:54:09 localhost kernel: [32258.056000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
May 13 11:54:09 localhost kernel: [32258.056000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
May 13 11:54:09 localhost kernel: [60156.100000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 18
May 13 11:54:09 localhost kernel: [60156.100000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 18
May 13 11:54:09 localhost kernel: [60156.100000] usb usb1: root hub lost power or was reset
May 13 11:54:09 localhost kernel: [60156.100000] PCI: Enabling device 0000:00:1d.1 (0000 -> 0001)
May 13 11:54:09 localhost kernel: [60156.100000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
May 13 11:54:09 localhost kernel: [60156.100000] usb usb2: root hub lost power or was reset
May 13 11:54:09 localhost kernel: [60156.100000] PCI: Enabling device 0000:00:1d.2 (0000 -> 0001)
May 13 11:54:09 localhost kernel: [60156.100000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
May 13 11:54:09 localhost kernel: [60156.100000] usb usb3: root hub lost power or was reset
May 13 11:54:09 localhost kernel: [60156.100000] PCI: Enabling device 0000:00:1d.3 (0000 -> 0001)
May 13 11:54:09 localhost kernel: [60156.100000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 16
May 13 11:54:09 localhost kernel: [60156.100000] usb usb4: root hub lost power or was reset
May 13 11:54:09 localhost kernel: [60156.116000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 18
May 13 11:54:09 localhost kernel: [60156.116000] usb usb5: root hub lost power or was reset
May 13 11:54:09 localhost kernel: [60156.120000] ehci_hcd 0000:00:1d.7: debug port 1
May 13 11:54:09 localhost kernel: [60156.120000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 16 (level, low) -> IRQ 18
May 13 11:54:09 localhost kernel: [60157.140000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
May 13 11:54:09 localhost kernel: [60157.224000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[dfdfc800-dfdfcfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
May 13 11:54:09 localhost kernel: [60157.248000] ACPI: PCI Interrupt 0000:03:01.2[C] -> GSI 17 (level, low) -> IRQ 17
May 13 11:54:09 localhost kernel: [60157.256000] pnp: Device 00:04 does not support activation.
May 13 11:54:09 localhost kernel: [60157.256000] pnp: Device 00:05 does not support activation.
May 13 11:54:09 localhost kernel: [60157.472000] Restarting tasks ... done.
May 13 11:54:09 localhost kernel: [60157.588000] Enabling non-boot CPUs ...
May 13 11:54:09 localhost kernel: [60157.784000] input: PS/2 Mouse as /class/input/input8
May 13 11:54:09 localhost kernel: [60157.804000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input9
May 13 11:54:09 localhost kernel: [60160.276000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
May 13 11:54:09 localhost kernel: [60160.292000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
May 13 11:54:09 localhost kernel: [60160.292000] ata1.00: configured for UDMA/100
May 13 11:54:09 localhost kernel: [60160.312000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
May 13 11:54:09 localhost kernel: [60160.328000] sda: Write Protect is off
May 13 11:54:09 localhost kernel: [60160.344000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 13 11:54:09 localhost kernel: [60160.440000] ata2.00: configured for UDMA/33
May 13 11:54:13 localhost kernel: [60164.672000] b44.c:v1.01 (Jun 16, 2006)
May 13 11:54:13 localhost kernel: [60164.672000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 19
May 13 11:54:13 localhost kernel: [60164.684000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:12:3f:de:fd:96
May 13 11:54:14 localhost kernel: [60164.920000] ieee80211: 802.11 data/management/control stack, git-1.1.13
May 13 11:54:14 localhost kernel: [60164.920000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
May 13 11:54:14 localhost kernel: [60164.988000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
May 13 11:54:14 localhost kernel: [60164.988000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
May 13 11:54:14 localhost kernel: [60164.988000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 17
May 13 11:54:14 localhost kernel: [60164.988000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
May 13 11:54:14 localhost kernel: [60165.508000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
May 13 11:54:19 localhost kernel: [60169.424000] input: Lid Switch as /class/input/input10
May 13 11:54:19 localhost kernel: [60169.428000] ACPI: Lid Switch [LID]
May 13 11:54:19 localhost kernel: [60169.428000] input: Power Button (CM) as /class/input/input11
May 13 11:54:19 localhost kernel: [60169.428000] ACPI: Power Button (CM) [PBTN]
May 13 11:54:19 localhost kernel: [60169.432000] input: Sleep Button (CM) as /class/input/input12
May 13 11:54:19 localhost kernel: [60169.432000] ACPI: Sleep Button (CM) [SBTN]
May 13 11:54:21 localhost kernel: [60170.612000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
May 13 11:54:21 localhost kernel: [60170.612000] ACPI: Processor [CPU0] (supports 8 throttling states)
May 13 11:54:21 localhost kernel: [60170.612000] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
May 13 11:54:21 localhost kernel: [60171.264000] ACPI: Thermal Zone [THM] (25 C)
May 13 11:54:22 localhost kernel: [60171.836000] ACPI: AC Adapter [AC] (off-line)
May 13 11:54:22 localhost kernel: [60172.224000] ACPI: Battery Slot [BAT0] (battery present)
May 13 11:54:24 localhost gconfd (groggyboy-5339): Received signal 15, shutting down cleanly
May 13 11:54:24 localhost gconfd (root-6841): Received signal 15, shutting down cleanly
May 13 11:54:24 localhost gconfd (root-6841): Exiting
May 13 11:54:24 localhost gconfd (groggyboy-5339): Exiting
```
obviously something is going wrong, but i have no idea what.

p.s. - don't mind the date - my computer was set one day forward - really freaked me out for a bit there.

---

### Post by motin on 2007-07-16
Then I aint alone - feels better :)

I reported this a while a go, and [the bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/112073") is now confirmed and assigned to the Kernel ACPI team. All we can do is is to wait for Gutsy I guess. Hopefully they have fixed it by then. 

Strange thing was that it worked flawlessly for a month or two in the beginning...

---

### Post by MikoLone on 2007-08-21
I am having the same problem with my desktop. I can wake from sleep and everything seems to be fine until I open a program and then I get the hang. Sometimes if I wait long enough the program will actually open. But I have yet to get out of it without rebooting.  

Thanks,

Michael

---

### Post by motin on 2007-08-30
Bad news on the bugreport - just got this comment:

> Thank you for taking the time to report this bug and helping to make Ubuntu better. This bug does not meet the criteria for a stable release update and is being marked as Won't Fix for this particular version of the kernel. You can learn more about the stable release update process at [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates) .
However, the issue that you reported is one that should be possible to test with the live environment of the Desktop CD of the development release - Gutsy Gibbon. It would help us greatly if you could test with it so we can work on getting it fixed in the actively developed kernel. You can find out more about the development release at [http://www.ubuntu.com/testing/](http://www.ubuntu.com/testing/) .
If you do decide to test with the development release of Ubuntu please comment on this bug report and include at least the minimal information requested at [http://wiki.ubuntu.com/KernelTeamBugPolicies](http://wiki.ubuntu.com/KernelTeamBugPolicies) . Thanks again and we appreciate your help.

MikeLone and groggyboy - I believe we have to test this out with the Gutsy kernel ASAP, attach the necessary information and at the same time propagate for that the bug matches these criterias for a stable release update. 

Check out my last comment on the bug report and please do post a comment yourselves about that it affects your computer model!

---

### Post by motin on 2007-11-07
Bah... Still no working suspend nor hibernate even after upgrade to Gutsy.

Have you guys have any success fixing this?

---

