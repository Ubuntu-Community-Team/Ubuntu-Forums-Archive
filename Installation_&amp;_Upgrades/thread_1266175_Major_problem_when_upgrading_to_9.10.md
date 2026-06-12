---
title: "Major problem when upgrading to 9.10"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by Rick Abraham on 2009-09-14
Hi guys I recently went to the update manager and noticed a upgrade from 9.04 to 9.10 so I clicked upgrade. It tool a bit over an hr to download and install the package after it finished installing it restarted my system. Everything was looking good BIOS screen loaded then the ubuntu logo came up with the load bar. The bar loaded about 80% then the screen went black and no more happened. I restarted a number of times but no good a black screen everytime. Does anyone know what happened and how to fix it ? Can I restore to the 9.04 OS ? I don't want to have to reformat.

---

### Post by stlsaint on 2009-09-14
Well you have done a upgrade from 9.04 Jaunty to 9.10 Karmic. Bad news is that Karmic is not released as stable version yet. Are you seeing any errors at all? Can you boot into recovery mode and try and repair broken packages, then select the option for normal boot!

---

### Post by Rick Abraham on 2009-09-14
How do you boot into recovery mode so I can try and repair any broken packages. I don't get any errors at all just a black screen

---

### Post by omega_drh on 2009-09-14
I also just ran an upgrade from 9.04 to 9.10 using update-manager -d, and can never get the system to fully come up. Twice I've been able to get to the login screen before the system hangs, but when I tried booting into the recovery mode kernel option in Grub, the screen just goes black and, after a little hard drive light flickering, also appears to completely hang.

Hardware is a Thinkpad T41, ATI MobilityRadeon 7500, ipw2200bg, etc.

---

### Post by omega_drh on 2009-09-14
Update: I was able to ssh into the system while it was at the login prompt (normal boot). I can post the full syslog, but these appear to be the last lines before dying:
```
Sep 14 15:46:02 dixon kernel: [  317.157275] [drm:radeon_cp_idle] *ERROR* radeon_cp_idle called without lock held, held  -2147483648 owner db0a7d80 de188540
Sep 14 15:46:02 dixon kernel: [  317.157316] [drm:radeon_cp_reset] *ERROR* radeon_cp_reset called without lock held, held  -2147483648 owner db0a7d80 de188540
Sep 14 15:46:02 dixon kernel: [  317.157331] [drm:radeon_cp_start] *ERROR* radeon_cp_start called without lock held, held  -2147483648 owner db0a7d80 de188540
Sep 14 15:46:02 dixon kernel: [  317.157346] [drm:radeon_cp_idle] *ERROR* radeon_cp_idle called without lock held, held  -2147483648 owner db0a7d80 de188540
Sep 14 15:46:02 dixon kernel: [  317.157387] [drm:radeon_cp_reset] *ERROR* radeon_cp_reset called without lock held, held  -2147483648 owner db0a7d80 de188540
Sep 14 15:46:02 dixon kernel: [  317.157402] [drm:radeon_cp_start] *ERROR* radeon_cp_start called without lock held, held  -214748360
Sep 14 15:46:02 dixon kernel: [  317.210420] [drm:radeon_cp_start] *ERROR* radeon_cp_start called without lock held, held  -2147483648 owner db0a7d80 de188540
Sep 14 15:46:02 dixon kernel: [  317.210436] [drm:radeon_cp_idle] *ERROR* radeon_cp_idle called without lock held, held  -2147483648 owner db0a7d80 de188540
Sep 14 15:46:02 dixon kernel: [  317.210477] [drm:radeon_cp_reset] *ERROR* radeon_cp_reset called without lock held, held  -2147483648 owner db0a7d80 de188540
Sep 14 15:46:02 dixon kernel: [  317.210492] [drm:radeon_cp_start] *ERROR* radeon_cp_start called without lock held, held  -2147483648 owner db0a7d80 de188540
Sep 14 15:46:02 dixon kernel: [  317.210507] [drm:radeon_c: wesnoth-tsg
```
This was then oddly followed immediately by a *ton* of lines talking about packages on my system, like:
```
Package: libclutter-0.9-dev
Unseen: yes
State: 3
Dselect-State: 0
Remove-Reason: 0

Package: info2man
Unseen: yes
State: 3
Dselect-State: 0
Remove-Reason: 0

Package: gpgkeys
Unseen: yes
State: 
```
before the next system boot appeared in the log.

The most system boot was preceded by this:
```
D$¶
$(&#8240;D
èüÿÿÿ1À&#402;Äh[^_]Ã&#65533;Ç$`&#65533;]Úèüÿÿÿ&#65533;uíÇ$èüÿÿÿf&#65533;¶&#402;ÃÇ$&#8240;D$èüÿÿÿ9óuæ¶EíÇ$#&#8240;D$èüÿÿÿéþÿÿ&#65533;Couldn't read from EEPROM: not there?adapter has MAC addr = %.2x:%.2x:%.2x:%.2x:%.2x:%.2xadapter failed MAC signature checkencoded MAC from EEPROM was %.2x:%.2xdescription=Decode dvb_net MAC address from EEPROM of PCI DVB cards made by Siemens, Technotrend, Hauppaugeauthor=Ralph Metzler, Marcus Metzler, otherslicense=GPLsrcversion=63E1EC1501630331897545Fdepends=vermagic=2.6.28-13-generic SMP mod_unload modversions 586 ttpci_eeprom_parse_macyDsstruct_module½wDi2c_transferÕ&#8212;#·printkttpci_eeprom

































ase 020000000 mask FF0000000 write-back
Sep 14 16:24:58 dixon kernel: [    0.000000]   2 base 02FF80000 mask FFFF80000 uncachable
Sep 14 16:24:58 dixon kernel: [    0.000000]   3 disabled
```
which was preceded by some other gibberish, some lines like "/gnome/peripherals/mouse" "IOR:0100000017000000494[...]", and then a huge list of packages (such as would be extracted from the Packages.bz2 file on a repository).

---

### Post by omega_drh on 2009-09-14
The radeon problem looks similar to this: [https://bugs.launchpad.net/ubuntu/+bug/270646](https://bugs.launchpad.net/ubuntu/+bug/270646) , except I don't have any external displays attached, and am not explicitly calling xrandr. Does karmic do this automatically, or anything?

Other bugs in launchpad with this particular error message:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/305458](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/305458)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/305458](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/305458)

---

### Post by omega_drh on 2009-09-14
I checked out the Xorg log, and saw a message immediately before tons of messages corresponding to the same lock issue, which indicated that Xorg *did* believe that a device is attached to s-video (there is none).

This now somewhat mirrors the behavior seen in comment #10 of [the first bug I linked](https://bugs.launchpad.net/ubuntu/+bug/270646):
> On Intrepid x86_64 with some ATI integrated card, when X starts while my laptop is connected to my TV (with s-video), the laptop freezes, leaving me with a solid black screen.
The difference here, is that I don't actually have anything attached to s-video output (xorg just seems to think I do?).

---

### Post by omega_drh on 2009-09-15
Bleh. The condition has gone from bad to worse. I ssh'd into the system this morning and ran an aptitude update, then safe-upgrade, and renamed the xorg.conf to see if that was causing problems. Since rebooting, now the machine does just hang at a blank screen after the ubuntu logo / progress bar immediately after grub is done.

Single user mode still gives me *nothing,* so now the system is effectively entirely dead.

I'm going to try an alpha5 boot disk, to see if I can revive anything.

---

### Post by aonegodman on 2009-09-15
Think I am having similar problems, right now my system seems to be stable after having to restart several times after upgrade. How do you check to see what version "Jaunty" you are currently running?

---

### Post by Intrinsic on 2009-09-15
I am having the exact same problem.  Everything was working fine, then upgraded 9.10 to the latest release, etc.  Everything went fine.  Starts the Ubuntu loading bar then goes black.  Will not do anything at all.  Think it is still running though because when I hold down the power button, the Ubuntu shut down bar comes up and the system shuts down.

Not sure how to get out of this.  I tried running in the recovery mode, and it did some un-installing/installing then rebooted and it did the same thing.  Did not change anything hardware wise...

Here is the system specs: ( I am running ubuntu on a seperate partition, installed with wubi originally)

--------[ EVEREST Home Edition (c) 2003-2005 Lavalys, Inc. ]------------------------------------------------------------

    Version                                           EVEREST v2.20.405
    Homepage                                          [http://www.lavalys.com/](http://www.lavalys.com/)
    Report Type                                       Report Wizard
    Computer                                          INT
    Generator                                         Intrinsic
    Operating System                                  Microsoft Windows XP Professional 5.1.2600 (WinXP Retail)
    Date                                              2009-09-15
    Time                                              17:37


--------[ Summary ]-----------------------------------------------------------------------------------------------------

    Computer:
      Operating System                                  Microsoft Windows XP Professional
      OS Service Pack                                   Service Pack 3
      DirectX                                           4.09.00.0904 (DirectX 9.0c)
      Computer Name                                     INT
      User Name                                         Intrinsic

    Motherboard:
      CPU Type                                          Intel Pentium 4 530, 3000 MHz (15 x 200)
      Motherboard Name                                  Unknown
      Motherboard Chipset                               Intel Grantsdale-G i915G
      System Memory                                     2048 MB  (PC3200 DDR SDRAM)
      BIOS Type                                         Intel (10/31/05)
      Communication Port                                Communications Port (COM1)
      Communication Port                                ECP Printer Port (LPT1)

    Display:
      Video Adapter                                     NVIDIA GeForce 9500 GT  (512 MB)
      Monitor                                           Plug and Play Monitor [NoDB]  (737317545MKS)

    Multimedia:
      Audio Adapter                                     Intel 82801FB ICH6 - High Definition Audio Controller [B-1]

    Storage:
      IDE Controller                                    Intel(R) 82801FB Ultra ATA Storage Controllers - 2651
      IDE Controller                                    Intel(R) 82801FB/FBM Ultra ATA Storage Controllers - 266F
      Disk Drive                                        WDC WD2500JD-22HBB0  (232 GB, IDE)
      Disk Drive                                        eM Bay Reader USB Device
      Disk Drive                                        eM Bay Reader USB Device
      Disk Drive                                        eM Bay Reader USB Device
      Disk Drive                                        eM Bay Reader USB Device
      Disk Drive                                        WDC WD32 00JB-00KFA0 USB Device  (298 GB, USB)
      Disk Drive                                        WDC WD800JB-00ETA0  (74 GB, IDE)
      Optical Drive                                     HL-DT-ST DVDRAM GSA-4120B  (DVD+R9:2.4x, DVD+RW:12x/4x, DVD-RW:8x/4x, DVD-RAM:5x, DVD-ROM:16x, CD:40x/24x/40x DVD+RW/DVD-RW/DVD-RAM)
      SMART Hard Disks Status                           OK

    Partitions:
      C: (NTFS)                                         94993 MB (77765 MB free)
      S: (NTFS)                                         76308 MB (55784 MB free)
      U: (NTFS)                                         44994 MB (27201 MB free)
      X: (NTFS)                                         305234 MB (305161 MB free)
      Z: (NTFS)                                         98484 MB (78880 MB free)
      Total Size                                        605.5 GB (532.0 GB free)

    Input:
      Keyboard                                          HID Keyboard Device
      Keyboard                                          HID Keyboard Device
      Mouse                                             HID-compliant mouse

    Network:
      Network Adapter                                   Marvell Yukon 88E8050 PCI-E ASF Gigabit Ethernet Controller  (192.168.1.122)

---

### Post by mandarin77 on 2009-09-15
I have a similar problem:
 
After an upgrade (which went okay from 8.04 to 9.04 i think), I got an option to allow the Program Bar, or Start Bar to change to a different mode where the power button was moving and there were "auto updates for messaging..." or some such madness (and stupid me, I clicked "okay") then it restarted Gnome Display Manager, but ended in a black screen.
Every time I start my computer it ends at this same black screen (partial command line bootup messages at the top, but mostly black)
 
1. I can type on the screen. Sometimes I get a logon (tty1)
2. I can _always_ logon with ALT+F2 (tty2)
 
**_YOU GUYS SHOULD CHECK TO SEE IF YOU CAN LOGON HERE (ALT+F2), THEN YOU CAN AT LEAST GET IN FROM A COMMAND LINE AND MAKE CHANGES_**
 
3. I have a system setup for dual display in Windows. It has never worked in Ubuntu, and I have looked into but haven't tried to get it setup. I am running GeForce Hardware, one on-board with a monitor, and one discrete card with one monitor. SO BASED ON OTHER POSTS HERE, THIS MIGHT BE A MULTI-MONITOR problem with Gnome desktop/display manager. But not hardware specific. Or it has something to do with the status/IM updates?
 
4. if this gets fixed... how do i upgrade from command line? ;-p I only sorta know what I am doing with Linux! (mostly because what I want to do with my computer is always 'not available for Linux,' like the Move player for Fox.com)

---

### Post by omega_drh on 2009-09-16
Ok, so when I booted into the alpha5 liveCD, I *did* get to the full desktop, and could mount my drives, but the OS locked up ~3 minutes after I started. The first time in, I verified that xorg *was* using the ati/radeon driver, though I was seeing some display corruption around compiz borders, etc. I just got to look at the hard drive's syslog before it locked up, and saw some messages that appeared to indicate that dbus was failing, or not being created, which was apparently preventing init from progressing.

The second time, I tried booting with "safe graphics mode," which I assume uses the standard VESA driver (can anyone verify this?). While I didn't see any display corruption that time around, the system did lock up about three minutes after getting to a usable state, again.

Edit: I can *never* get anything on the other virtual terminals (ctrl-alt-f1, f2, etc...). removing 'quiet' from the grub boot line, and removing 'splash' (or changing it to 'nosplash') just gives me a blank screen during boot, too. I think that might've been that way for a while, though.

---

### Post by yourio5432 on 2009-09-16
I'm having this problem but I started with alpha 3. After restarting from update tonight gave me the blank screen on boot. For me alt +F2 doesn't do anything. I also can't get into recovery mode. I'm running a 260m nvidia card.

---

### Post by akernan on 2009-09-16
I upgraded my 9.10 version yesterday, now I can't boot my system.  My log files are not updated.  I tried the recover boot but that doesn't work, my system stops during the boot process.  I tried alt-F2 & other terminals, that doesn't work.  I can press ctrl-alt-del to reboot.  The last thing my system displays is 'Clocksource TSC unstable'.  This comes up with a regular boot, no splash, or recovery.

How can I recover w/o formatting or reinstalling?

---

### Post by akernan on 2009-09-18
I was able to use the live cd for recovery and issue the chroot cmd. I had to run apt-get upgrade a few times to get everything. I am able to boot with 2.6.31-9 but not 2.6.31-10. Boot seems slower, but at least I can boot now & recovered.

---

### Post by mandarin77 on 2009-10-13
Okay, got command line upgrades figured out. And I got my GUI back. I was able to log in to Alt F2, run
apt-get update
apt-get upgrade
apt-get purge
apt-get install nvidia
 
I did run through a few logs and found the nvidia drivers listed a few times. I removed them. Purged them. restarted a few times because nothing seemed to have changed. There was a mention of lib6c or libc6 (i forget which way it is!) so i tried removing that, and finally there was an auto-purge of some left-over nvidia package remnants.
With a final: apt-get install nvidia### i got back up on the GUI.
 
Not sure if that helps, but thought i'd throw it out there!
 
mandarin

---

### Post by ldlandis on 2009-11-01
> **omega_drh said:**
> I also just ran an upgrade from 9.04 to 9.10 using update-manager -d, and can never get the system to fully come up. Twice I've been able to get to the login screen before the system hangs, but when I tried booting into the recovery mode kernel option in Grub, the screen just goes black and, after a little hard drive light flickering, also appears to completely hang.

Hardware is a Thinkpad T41, ATI MobilityRadeon 7500, ipw2200bg, etc.
I have several T41's.  One did not exhibit the "hang" seen in 9.10 by several. It was the only one that did not have any of "compiz" active.

To get rid of the hang, I disabled all visual effects (compiz) and have not had any issues since, on 3 of my T41's.  I appears that things are pushed a bit too hard in Karmic.

To diable: right click on the desktop, select "Change Desktop Background" (last option), then "Visual Effects" tab (rightmost), select "None" and [Close].

Good Luck,
  [email]--ldl@linux.com[/email] in colaboration with [email]dlw@linux.com[/email]

---

