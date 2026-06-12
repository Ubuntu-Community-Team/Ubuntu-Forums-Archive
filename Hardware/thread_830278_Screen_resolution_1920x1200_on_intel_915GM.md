---
title: "Screen resolution 1920x1200 on intel 915GM"
date: 2008-06-15
forum: Hardware
---

### Post by quercus54 on 2008-06-15
Unable to set screen resolution 1920x1200 on intel 915GM with ubuntu 8.04

The native resolution 1920x1200 was possible with SuSE 10.1, then also with ubuntu 7.10 (with the 915resolution package). But so far not with ubuntu 8.04. Maximum is 1024x768 ! The 915resolution didn't help anything. Using the old xorg.conf of ubuntu 7.10 didn't help either.
It is said, that with ubuntu 8.04 the 915resolution package is obsolete. The new xorg-server recognizes the intel 915GM resolutions correctly. But in fact it doesn't ! And I cannot find, how to configure it. Help is very appreciated.
Computer: Barebone shuttle XPC SD11G5. (pentium mobile processor for low power consumption)
Graphics: intel 915GM
Monitor: Dell 2405FPW (24" wide screen TFT, connected via DVI)

When 915resolution is used to show the display modes, no wide formats appears:

Intel 800/900 Series VBIOS Hack : version 0.5.3
Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36
Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel

---

### Post by quercus54 on 2008-07-06
Got no answer to my posting, but I don't give up on ubuntu 8.04 !

Hardware (repeated):
  Computer: Barebone shuttle XPC SD11G5. (pentium mobile processor)
  Graphics: intel 915GM
  Monitor: Dell 2405FPW (24" wide screen TFT, connected via DVI)

Problem (repeated):
  Native screen resolution 1920x1200 was possible with ubuntu 7.10. But is no longer possible with ubuntu 8.04, probably because the new Xorg does no longer need the package 915resolution, but handles the hardware itself or with a new experimental intel driver.

In the meanwhile I found:
a) The tool displayconfig-gtk is able to temporarily set the desired resolution 1920x1200@60 !
b) displayconfig-gtk applied as root generates a fine xorg.conf with all the possible modeline. But when rebooting, the display is 1024x768 again.
c) The systems generates 2 xorg log files within a minutes after boot:
  Xorg.0.log, Xorg.0.log.old (because 2 gdm processes are running?)
d) Xorg.0.log reports the following problems:
  X.Org X Server 1.4.0.90
  ...
  (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
  (II) Primary Device is: PCI 00:02:0
  (WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
  (--) Chipset 915GM found
  ...
  (EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
  ...
  (EE) intel(0): First SDVO output reported failure to sync
  ...
  (II) intel(0): Output VGA connected
  (II) intel(0): Output LVDS connected
  (II) intel(0): Output TMDS-1 connected
  (II) intel(0): Output TV disconnected
  (II) intel(0): Output VGA using initial mode 1024x768
  (II) intel(0): Output LVDS using initial mode 1024x768
  (II) intel(0): Output TMDS-1 using initial mode 1024x768
e) These problems are reported in the log of ubuntu 7.10, too. But there the display resolution 1920x1200 is achieved by gdm nevertheless.

Any hints very much appreciated !

---

### Post by Nikitas350 on 2008-07-06
Did you installed the restricted drives?

---

### Post by Nikitas350 on 2008-07-06
Try replacing the monitor section (of xorg.conf) to this one:

Section "Monitor"
	Identifier	"DELL 2405FPW"
	Vendorname	"Dell"
	Modelname	"Dell 2405FPW (Digital)"
	HorizSync         30-80
      VertRefresh      55-75
	Gamma	1.0
EndSection

---

### Post by quercus54 on 2008-07-08
Thanks for your answers!

Resctricted drivers? How can I find out
a) which ones are installed?
b) which ones are restricted?
Besides Xorg, there is a package intel-??? installed, but I didn't install any additional drivers after ubuntu 8.04 standard installation.

But I tried the package 915resolution, which to my understanding is not a driver and did not help either.
At least this utility showed me that the 915GM is proposing inappropriate resolutions (1920x1440, ... instead of 1920x1200, ...)
With 915resolution I patched this list of possible modes before starting X, but without any change of Xorg's behaviour.

Your proposition about xorg.conf: I will of course try it, too. Unfortunately I am not at home right now and cannot do it before the next week end.
Hans

---

### Post by quercus54 on 2008-07-13
First my thanks to Nikitas350. Even if his proposition finally was not the direct solution, it helped keeping me motivated to further dive into the details. After all it feels good, not to be left fully alone, stuck with a unresolvable linux problem.
Résumé: When changing from ubuntu 7.10 to 8.04 the monitor resolution falls back from 1920x1200 to 1024x768. No modification on xorg.conf, no other steps seemed to help. (Hardware: Dell 2405FPW monitor, 24", 1920x1200 native resolution, connected via DVI, intel 915GM onboard graphics controller)
Problem finally solved, but I don't know how. Once, when rebooting, fully unexpectedly the screen resolution was correct: 1920x1200. Then step by step I undid all the changes I tried so far, until I had the original configuration. But the resolution was still correct. So I didn't find out what was the cure and my satisfaction is only about 3/4. Neverthelesse some readers in the same stituation might be interested in reading what were the single steps:
0. Running ubuntu 7.10, resolution 1920x1200 correct.
1. New installation of ubuntu 8.10, multi boot in parallel with existing 7.10 on another partition.
   --> Only possible resolutions 1024x768 and below. All with aspect ration 4:3 instead of wide 16:10.
2. Install package 915resolution, because this was needed with ubuntu 7.10.
   --> Still the same 1024x768
3. Fiddle around with vbesave.
   --> Resulting resolution even worse.
4. New installation of ubuntu 8.10.
   --> Again the same 1024x768
5. Using the xorg.conf of ubuntu 7.10 in 8.04
   --> Still the same 1024x768
6. 915resolution -l shows, that there are no wide screen modes among the listed ones.
   Thus I set them explicitly: 915resolution 5c 1920 1200 32; 915resolution 5a 1440  900 32; ...
   Before starting xorg (in gdm)
   --> Still the same 1024x768
7. Generated new /etc/X11/xorg.conf with dexconf (details forgotten)
  --> Still the same 1024x768   
8. Somewhere in between the updated version of xorg.conf automatically downloaded and installed.
   --> Still the same 1024x768
9. Used GUI tool displayconfig-gtk to change screen resolution
   --> In current session 1920x1200 available. Still the same 1024x768 after reboot.
10. Used displayconfig-gtk as root to generate a detailed xorg.conf with all appropriate modes. (xorg_detailed_modes.conf)
    --> Still the same 1024x768 after reboot.
11. In /etc/rc2.d disactivated:
    S10xserver-xorg-input-wacom to K90xserver-xorg-input-wacom
    S12915resolution            to K88915resolution
    S20nvidia-kernel            to K80nvidia-kernel
    --> Still the same 1024x768 after reboot.
12. Worried about the warning in /var/log/xorg.0.log
    (WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
    Used this one in xorg.conf instead of 0:2:0
    --> No longer any display at all.
13. Worried about the warnings and errors in /var/log/xorg.0.log
    (WW) intel(0): Bad V_BIOS checksum
    (EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
    --> But found the same in ubuntu 7.10, where screen resolution was ok.
14. Used the command line tool "xrandr  --output TMDS-1 --mode 1920x1200" to change current screen resolution.
    --> In current session 1920x1200 available.
15. Detected inappropriate monitor modes in current xorg.conf, version yxz. Corrected them.
    --> Reboot, and ... unexpectedly ... the 1920x1200 was there, Heureka !
16. From now on I was eager to find the configutration that didn't work, just in order to spot the problem and its cure. First I peplaced xorg.conf with that of step 10.
    --> Reboot, 1920x1200 still ok.
17. Undo all disactivations in rc2.d
    --> Reboot, 1920x1200 still ok.
18. Used original ubuntu 8.04 xorg.conf, that is almost empty with respect to graphics and monitor. (xorg_orig_8.04.conf)
    --> Reboot, 1920x1200 still ok.
So finally I ended up with a configuration working correctly with the desired 1920x1200, but I don't know what brought the cure. I only suspect, that xrandr might have stored something, I don't know where and what, that triggers xorg to use the correct screen resolution now.
Remaining difference with ubuntu 7.10: There the "ubuntu" splash during booting already was in the correct resolution. In 8.04 the correct resolution is only achieved when the final Gnome desktop appears. Greeting-login is in low resolution in both cases.
Remaining lack of perfectnes: The utility System/Preferences/ScreenResolution still shows wrong resolutions and does not alter anything at all.
So, if anybody encounters the same problem, I hope the miracle will happen with him, too. Or even better, she/he finds out, what is the exact cause and cure.
Hans

---

### Post by no drinking water on 2008-07-24
> **quercus54 said:**
> 
So, if anybody encounters the same problem, I hope the miracle will happen with him, too. Or even better, she/he finds out, what is the exact cause and cure.
Hans

Thanks for all your work.
It is somehow consoling to find out that others are dealing with the same sort of inexplicable behavior. And it is bitter to discover that, obviously, one is more or less left alone with it.

I've been having a similar problem:
Kubuntu 7.04 began to dislike working properly with my 1600x1200 display, in an increasing manner (hardware being ok). That ended sukddenly after a period of 5 months - I never got out precisely why and how.

I'm currently having a quite similar problem:
Kubuntu 8.04 Live-CD is working properly with that same display, but the installed, and continuously updated, version of Kubuntu Hardy Heron dislikes to work properly with my display, in an increasing manner...

What frustrates most when stuck in such a situation is the lack of a reliably competent instance where such tricky problems could be placed - at least I couldn't find one.
My frustrating experience is that eventually, you painfully explain them just to the endless, silent void.

---

