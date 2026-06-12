---
title: "ASUS M2N-MX SE Motherboard"
date: 2008-05-27
forum: Hardware
---

### Post by eryksun on 2008-05-27
PowerNow (Cool N' Quiet)

The APIC support on the ASUS M2N-MX SE motherboard is incompatible with Linux, even with the latest BIOS (0503) and kernel (2.6.24-17-generic). To get around this, I disabled APIC in the BIOS setup, which seemed to work ok. However, I couldn't load the powernow-k8 system to get CPU frequency scaling. Re-enabling APIC in the BIOS and starting the kernel with the option "noapic" solved this problem.

----
AL662 Audio

Audio disappeared on me after resuming from suspend. I fixed the problem by adding the following line to "/etc/modprobe.d/alsa-base":

options snd-hda-intel model=3stack-dig

I'm simply amazed by the mess that is the ALSA and OSS mixers:

ALSA
Master - mute doesn't work
PCM - mute works, but causes crackling noise
Front - mute doesn't work; seems redundant

OSS
Volume - same as ALSA Master
PCM-2 - controls the headphones;
        mutes headphones without noise

Now that I have PulseAudio working with Flash, I leave the volume applet set to the PulseAudio master control, which mutes quietly unlike the noisy crackling of the ALSA PCM mute. I'd like to get PulseAudio running as a system daemon, as opposed to user level, for no better reason than to get sound back in GDM; I miss the the drum greeting. I'd also like to be able to mute the speakers when the headphones are plugged in, either automatically or manually. Currently I have to physically turn them off. 

----
Suspend (S3)

Suspend still doesn't work for me. Actually it works perfectly, but only once per session. If I try to suspend again after resuming from a previous suspend, the system either bounces automatically back into normal operation or hangs. I suspect the glitch is caused by the restricted NVIDIA graphics driver.

----
Fast User Switch

Switching users would return me to GDM even if the other user was already logged in. The NVIDIA graphics driver has yet another bug that causes the GDM screen to come up blank/white in this scenario. The login is still there, allowing you to type the password and switch; you just can't see where/what you're typing. I'm not that security conscious, so I disabled the option to "Lock the screen after switching users" in the Fast User Switch preferences. Now at least the system doesn't have to load GDM to get the password. :)

---

### Post by ubiubi on 2008-06-14
Hi

I have the same apic problem and disabled it in the same way in Bios to install ubuntu. The problem is I have an xp dual boot system . This means every user in the house has to enter the bios and toggle the 'APIC' disable option. What a pain and not very practical for my wife, for example. Would this 

[B][FONT="Verdana"]"Re-enabling APIC in the BIOS and starting the kernel with the option "noapic" solved this problem."
[/FONT][/B]

noapic  proceedure help me and how do you do it?
Cheers

---

### Post by eryksun on 2008-06-20
> **ubiubi said:**
> Hi

I have the same apic problem and disabled it in the same way in Bios to install ubuntu. The problem is I have an xp dual boot system . This means every user in the house has to enter the bios and toggle the 'APIC' disable option. What a pain and not very practical for my wife, for example. Would this 

[B][FONT="Verdana"]"Re-enabling APIC in the BIOS and starting the kernel with the option "noapic" solved this problem."
[/FONT][/B]

noapic  proceedure help me and how do you do it?
Cheers

I'm sorry for not replying sooner. Adjusting this boot option is fairly simple to do. I actually switched to doing it this way in order to get suspend and cpu frequency scaling to work right. You just edit the grub menu file:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo nano /boot/grub/menu.lst
```

Scroll down to the kernel configurations, which should begin just after the line 

> ## ## End Default Options ##

There are two configuration sections for each kernel installed: normal and recovery mode. For each kernel config line that begins 

> /boot/vmlinuz-#.#.##-##-generic ...

append the option "noapic" (without quotes) to the end of the list of kernel parameters. Note however that every time the system kernel gets updated to a new version you will have to manually edit this file to add the "noapic" option to the new kernel's configuration. I wish the update system were smart enough to configure a new kernel with your existing parameters, but apparently it's not.

---

### Post by ubiubi on 2008-06-22
Cheers, it worked a treat!

---

### Post by eryksun on 2008-06-22
> **ubiubi said:**
> Cheers, it worked a treat!

You're welcome. :)  According to the "Setting kernel parameters" section of this [[COLOR="Blue"]Grub Howto[/COLOR]]("http://help.ubuntu.com/community/GrubHowto#head-28c697721b2f5d2352e43074a55f4621c415293d"), you can apply the noapic setting to all newly installed kernels by appending it to the kopt option. Just follow the link for detailed instructions.

---

### Post by Murz on 2009-03-10
> **eryksun said:**
> Suspend (S3)

Suspend still doesn't work for me. Actually it works perfectly, but only once per session. If I try to suspend again after resuming from a previous suspend, the system either bounces automatically back into normal operation or hangs. I suspect the glitch is caused by the restricted NVIDIA graphics driver.

Suspend on this MB isn't works for me with latest bios (0602) and latest kernel (2.6.27-11-generic). I try with enabled and disabled APIC and with/without 'noapic' kernel option.

Other: PowerNow (Cool N' Quiet), Fast User Switch, etc - works good without 'noapic' option.

Suspend (S3) works with this steps:
1. I start the pm-suspend
2. Computer goes to sleep (go to text mode, screen goes to black, power button light turns off.
3. After 3-5 seconds (I don't touch keyboard, mouse, etc) computer automatically wakes up! I see text mode, after that I see GUI with all functional interface.
In /var/log/pm-suspend.log I see:
```
Tue Mar 10 16:14:54 MSK 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/00clear suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend: success.
/usr/lib/pm-utils/sleep.d/05led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/10NetworkManager suspend: success.
/usr/lib/pm-utils/sleep.d/48hid2hci suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend: not applicable.
/usr/lib/pm-utils/sleep.d/50modules suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend: success.
/usr/lib/pm-utils/sleep.d/95led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend: success.
Tue Mar 10 16:14:56 MSK 2009: performing suspend
Tue Mar 10 16:15:01 MSK 2009: Awake.
Tue Mar 10 16:15:01 MSK 2009: Running hooks for resume
/usr/lib/pm-utils/sleep.d/99video resume: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume: success.
/usr/lib/pm-utils/sleep.d/95led resume: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume: success.
/usr/lib/pm-utils/sleep.d/90clock resume: success.
/usr/lib/pm-utils/sleep.d/50modules resume: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume: not applicable.
/usr/lib/pm-utils/sleep.d/48hid2hci resume: No devices in HID mode found
Returned exit code 1.
/usr/lib/pm-utils/sleep.d/10NetworkManager resume: success.
/usr/lib/pm-utils/sleep.d/05led resume: not applicable.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume: success.
/usr/lib/pm-utils/sleep.d/00clear resume: VT_DISALLOCATE: Device or resource busy
deallocvt: could not deallocate console 63
Returned exit code 1.
Tue Mar 10 16:15:03 MSK 2009: Finished.

```
You can see the sleep interval in log (16:14:56 - 16:15:01).

---

### Post by Murz on 2009-04-13
Same problem on ASUS M2NBP-VM CSM ACPI BIOS Revision 0902
Setting noapic to kernel didn't help.

But in this motherboard I can't disable APIC support on BIOS: this item is grayed out.

eryksun, what version of BIOS you have using?

---

### Post by anv on 2009-04-20
I just received new components from friend and this motherboard M2N-MX is included, so the installation fails due this apic thing, it tells in beginning that apic bug something, and installation fails at quite last meters during installing kernel, would it be possible to adjust the installation somehow to complete it?

---

### Post by phill on 2009-07-17
I've fixed Suspend to Ram (S3)!

I've installed acpi, acpid and acpi-support from Karmic (using pinning, no other dependencies) and then linux-image-2.6.31-3-generic.

After that I could suspend a second time but the screen didn't come back up.  I changed my bios to S3 Only, ACPI 2.0, APIC Enabled and under the hardware options disable ACPI HPET Tables (in the same menu as you choose your graphics card, enable on-baord lan and boot rom etc).

Now I can suspend as many times as I need (so far fourth time)!

Hope that helps someone...  :P

---

### Post by anv on 2009-07-24
I don't have the SE version but M2N-MX and I really can't install system in it. it is something with apic, I have updated bios but that didn't help

---

