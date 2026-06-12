---
title: "Ubuntu 9.04: No Resume After Suspend, No Hash Match in pm_trace, Fresh Install, Lenov"
date: 2009-04-28
forum: Hardware
---

### Post by meatlover on 2009-04-28
Hello,

I have a Brand New (3 days old) Lenovo Ideapad model 2PU. The computer suspends fine, and goes to a blank screen from X, however, the hardware lights never turn off and caps lock flashes. After it flashes and harddrive spins down, the computer is unresponsive, and no key combination results in a reboot. However, the fan never turns off. I am forced to hard reboot. I have the same problem when I attempt to suspend without X, i.e. press Ctrl+Alt+F2, then type pm-suspend. The computer does not generate a pm-suspend log.

This computer has no driver installed for its graphics card (Nvidia Geforce 9300M). In fact, this is a completely new install with NO new software whatsoever. There is no partition on the disk, and the swap size 7.1 GB with 3Gb of ram.

Previously, I had installed ubuntu with the proprietary drivers from Nvidia's website, and I had a similar problem there, except at that time the computer would power down for a split second, and then return to a screen with a blinking cursor. In this case the computer did generate a pm-suspend log, which indicated success. I have a post about this here:

[http://ubuntuforums.org/showthread.php?t=1140717](http://ubuntuforums.org/showthread.php?t=1140717)

-------------------------------------------------------------------------------------------------------------------------------------
Attempting to suspend using the method listed here

[https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume](https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume)

gave no results. Enabling no_console_suspend did not change anything and entering the commands:

setfont /usr/share/consolefonts/Uni1-VGA8.psf.gz
sudo pm-suspend

did not make any extra text appear on the prompt.

-------------------------------------------------------------------------------------------------------------------------------------
Attempting to trace the error using the method here:

[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

gave no results. The dmesg file only had the "Magic number," listed once and there were no "hash matches." This method did not work either

[http://lxr.linux.no/linux/Documentation/power/s2ram.txt](http://lxr.linux.no/linux/Documentation/power/s2ram.txt)

-------------------------------------------------------------------------------------------------------------------------------------
Attempting to use the s2ram method listed here

[http://en.opensuse.org/S2ram](http://en.opensuse.org/S2ram)

gave no results. Every combination I tried did not work.

-------------------------------------------------------------------------------------------------------------------------------------
Attempting to look add "quirks" manually as they do here

[http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-debug.html](http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-debug.html)

gave no results. In fact I ran the script listed at the top of the page and it said that my computer will suspend correctly.

-------------------------------------------------------------------------------------------------------------------------------------
Attempting to use the debugging here

[https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting](https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting)

gave no results. The computer had the exact same systems under this test, and no report was generated with apport.

-------------------------------------------------------------------------------------------------------------------------------------
The bios has no power settings either then allowing the screen to dim, or to allow the computer to use Wakeonlan. I disabled wakeonlan and tried to suspend and there was still no difference.

-------------------------------------------------------------------------------------------------------------------------------------


Relevant Specs:
3GB ddr3 Ram
Nvidia Geforce 9300M
Intel Core 2Duo p7350 2Ghz
320GB Harddrive
Ubuntu 9.04
Bluetooth

Finally, I have a notable error in my Syslog:

Apr 28 13:39:51 computer-laptop kernel: [ 59.816133] Corrupted low memory at c000fcf4 (fcf4 phys) = 83840000
Apr 28 13:39:51 computer-laptop kernel: [ 59.816138] Corrupted low memory at c000fcf8 (fcf8 phys) = 0010000a
Apr 28 13:39:51 computer-laptop kernel: [ 59.816145] ------------[ cut here ]------------
Apr 28 13:39:51 computer-laptop kernel: [ 59.816148] WARNING: at /build/buildd/linux-2.6.28/arch/x86/kernel/setup.c:719 check_for_bios_corruption+0xc8/0xd0()
Apr 28 13:39:51 computer-laptop kernel: [ 59.816151] Memory corruption detected in low memory
Apr 28 13:39:51 computer-laptop kernel: [ 59.816153] Modules linked in: binfmt_misc ppdev bridge stp bnep input_polldev lp parport joydev snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi arc4 ecb snd_seq_midi_event snd_seq snd_timer snd_seq_device iwlagn iwlcore uvcvideo snd mac80211 sdhci_pci compat_ioctl32 psmouse intel_agp soundcore ricoh_mmc sdhci pcspkr videodev v4l1_compat serio_raw agpgart iTCO_wdt iTCO_vendor_support snd_page_alloc cfg80211 video asus_laptop output led_class ohci1394 ieee1394 tg3 fbcon tileblit font bitblit softcursor

The trace of this is at the end of each of the syslog's attached below. I have seen this error elsewhere, and memtest has found nothing wrong with my ram, so I'm not sure what this means.




Please see the attached files at [https://bugs.launchpad.net/ubuntu/+bug/368873](https://bugs.launchpad.net/ubuntu/+bug/368873)

Thanks you

---

