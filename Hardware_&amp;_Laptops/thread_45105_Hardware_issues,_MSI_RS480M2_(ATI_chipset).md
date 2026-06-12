---
title: "Hardware issues, MSI RS480M2 (ATI chipset)"
date: 2005-06-28
forum: Hardware &amp; Laptops
---

### Post by Jiilik on 2005-06-28
I've been playing around with an AMD64 system I bought a while back (for the purposes of 'playing around').  Here are some details:

MSI RS480M2-IL mobo (3200+ XP 64 chip, 512MB RAM)
 + ATI Radeon Express 200 onboard
 + ATI RS480 northbridge
 + ATI RS400 southbridge
80GB IBM IDE harddisk circa four years old
8x4x32 Sony IDE CDRW circa six years old

Before attempting anything, I reset my CMOS to Performance default (and turn off the floppy disk... don't have one)

Using Hoary Hedgehog 5.04 for amd64

**Part 1: Installation**

During installation from CD, hard disk access is VERY slow - turns out the ATI IXP IDE driver isn't supported (fully? at all?) so methinks it's using pure bios calls... ewww

After the very long installation (hdparm tells me my hda access speed is 0.5MB/s), it hard-locks the first time it loads X.

HW reboot into recovery mode, and # nano /etc/X11/xorg.conf, and insert 
Option "NoAccel" "true" in the ati device driver section.  Reboot, and we get to X.

**Part 2: Initial Issues**

At this point there are five issues I've determined:
1. IDE access is still slow
2. sound server (arts) crashes on boot due to CPU being busy (this is related to #1) - sound works if I wait for the cpu to calm down after booting
3. keyboard input is stuttering in an unusual fashion, pausing and doubling keypresses.
4. lack of X accelleration

Tackling the issues one at a time:

Using Universe, I update the kernel from 2.6.10-amd64-generic to 2.6.11-amd64-generic, and reboot.

5. During loading modules phase of boot, system hangs (in loop, I suppose) while trying to load the ide-cd drivers.  Error is: 
hdd: cdrom_pc_intr: The drive appears confused (ireason = 0x01)

I can specify hdd=noprobe at boot and get the system running, without the CD-ROM.  Issues #1, #2 and #3 have been solved, but issue #5 has been created.

#4: Installing the fglrx ATI drivers from ati.com (most recent is June 22, today is the 28...) works via alien, and X runs fine in 2-D acellerated mode using this driver.  Had to specify --force-overwrite upon installation for libGL.  Using the included 'fglrxconfig' script, I have a working xorg.conf - X works, but is not using the fglrx kernel module for DRI.  glxgears gives 130 fps.  Trying to run in /lib/modules/fglrx/build_mod/ 'sudo sh make.sh' fails (I've installed gcc3.3)  I will shortly try the older fglrx drivers from restricted to see if that behaves any differently (will report back)

#5: hdd (cdrom) hangs system on boot still.  I tried 2.6.12 from breezy to the same effect.  This does not happen when I use the knoppix 3.9 live cd using 2.6.11 so I'm thinking it's possibly something I'm doing wrong when updating the kernel, or something to do with the hardware detection portions.  Any ideas would be greatly appreciated.  I will also shortly be trying a different cdrw to see if that makes any difference as well. (will report back)

If anyone has any advice re: #4, #5, please don't hold back.

**Update**
#4: I still cannot build the kernel module from ATI's sources.

The module in hoary is 2.6.10 specific, and as you can see above, I need 2.6.11 for the IDE related IO fixes.  The 2.6.10 module will not load into 2.6.11.

#5: I tried pci=routeirq since the cdrom issue seems to be an irq type problem.  No change.

If anyone knows a way to fix the IDE performance under 2.6.10, it would fix #4 and #5 as a side effect.

**Update, July 22/2005**
#3 this is related to the clock running at nearly double speed.

#4 still having issues installing the ATI kernel module

BIOS 3.5 fixes the CD-ROM issue with the newer kernels

Sound, LAN, etc. works for me out of the box with Ubuntu 5.04

The new ATI fglrx accellerated X drivers DO WORK, if you're up to the hassle of getting them installed...

#3: Disabling APIC in bios fixes the clock issue for me, or if you have kernel 2.6.12 or better, give the option 'no_timer_check' at boot and it'll do the same thing without sacrificing APIC.

At this point I have no remaining issues expept the fglrx installation, which can be handled using other sources.

---

