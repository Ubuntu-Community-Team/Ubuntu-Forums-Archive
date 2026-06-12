---
title: "Stuck in restart loop after GRUB, possible Secure Boot issue?"
date: 2016-07-29
forum: Hardware
---

### Post by EarlsFurniture on 2016-07-29
was: Restart right after boot from grub, can't boot ANY distro from ANY device

Specs:

system: Gateway DX4860
motherboard: Acer IPISB-VR rev 1.01 (can't find docs on this thing anywhere)
CPU: i3-2120 4 core @3.3 GHz
RAM: 16GB (4x4GB) DDR3 PC3-10600, 9-9-24
Boot drive: Kingston 240GB SSD
installed OS: Ubuntu 12.04
kernel: 3.13.0-92-generic x64
graphics: R5-220 card, IntelHD (H67 chipset) onboard
graphics drivers: fglrx was the last one used with the card.

After a close lightning strike, the system had garbled video.

A power down and restart resulted in zilch - nothing. (system was plugged into an APC BGX1000 UPS)

Opened the case, power up gets the fans going but nothing else.

Removing RAM and trying one at a time get one post beep on one of four sticks, the other three produce silence.

In no case is any video available, from either the video card or onboard, from any port. (DVI, HDMI, and VGA available on card, HDMI and VGA ports onboard)

Removed video card, tried again with each RAM stick one at a time - nothing, not even on the stick that POST beeped before.

Removed all RAM - beeped repeatedly. (as expected)

Reinstalled RAM in pairs - still nothing. Sometimes a beep, sometimes not.

Reinstalled all RAM, let it sit over night.

Tested the PSU - all is good except the +3V on the SATA lines. None of them work.

Tried a known good PSU.

Now I get a beep every time I power up.

Tried again with video card in - all three ports, one at a time - monitor complains that input timings are not set right. (but I can't set them because I can't get to a usable system) Last known timings match exactly what the monitor is asking for. (1920x1080@60Hz)

Yanked the card again, tried the onboard ports again. (with the good PSU)  Now I get a normal POST display, can get into BIOS and GRUB. But upon attempting to continue to boot - the screen flashes a very brief (<1/10th sec) of boot messages, the screen goes black, the monitor says it's going into power saving mode and the system restarts and ends up back at GRUB.

None of the boot entries for GRUB work. No recovery modes, no previous kernels. The only thing that works is MEMTEST, which the sticks pass.

I tried booting from USB sticks with LXLE and Lubuntu 16.04 alternate - same thing. I can get to the initial text screen, but as soon as the system gets near handing off from the console - it restarts.

Puppy Classic does the same, as do LiveCDs of Ubuntu 12.04.1 and .2 (which I had handy)

PLOP Linux stalls right away.

TinyCore does nothing.

Debian flashes the first installer screen and is gone in the blink of an eye and restarts.

I tried setting nomodeset guessing it might improve the console to vesa handoff, but no dice.

I tried removing quiet splash but all that gets me is more text I can't pause or read before the screen goes black and the system restarts.

I poked around in the GRUB command line, but none of the log files have any entries in the last few days since the lightning strike, none of the boot attempts from the HD (SSD really) appear in dmesg, syslog, or kern.log. None of their time stamps show anything more current than right when the strike happened. (and no, there is nothing in them to indicate what happened at the moment of the strike, though I did see lots of soft bugs connected to Xorg and fglrx with CPU hangs avg 22secs.)

I cleared the CMOS using the MB jumper and I pulled the battery for 3 minutes for good measure.

I tried the video card again, and on VGA got a partial screen that was garbled, on HDMI got a full screen that was garbled. (by garbled, I mean I could see the PC logo and POST text, but it had vertical 'black and blue' bars behind it) Once it got to the point GRUB should appear, I got the input timing warning again. (with an otherwise black screen) Hitting ENTER blind to hopefully boot anyway does nothing.

So I'm stuck. No media will boot at all, at least not past about 1/10th of a second and without any log entries to show for it to troubleshoot without an immediate power restart.

I can get to a GRUB command line routinely, and examine files, but I'm not sure what if anything else I could do.

I can't seem to locate any logs with recent boot activity for troubleshooting purposes.

The BIOS shows entries for EFI boot devices options, but there are no such devices. (I installed this system with Ubuntu as the sole OS in BIOS mode, not EFI mode) There is no option to turn on or off 'Secure Boot.'

I would attempt a re-install/upgrade using an alternate installer, but the one I already tried for rescue (Lubuntu 16.04) started up but then failed as well at some point on loading needed files.  Even a Rescue-Remix disc won't get far enough to boot.

Any ideas on what GRUB command line options I can try? (besides nomodeset)

Any way I can get a boot log to write to disc or even pause on the screen without the power restart?

Thanks for any suggestions.

ps—I did have an old XP disc laying around and that does get to the point of fully loading the installer, but that is a console screen. XP doesn't get to a graphical screen until after it writes the OS files to disc, and I'm not about to do that on this drive without a special partition for it (which I can't create without some type of usable system) to find out if it too will fail.

---

### Post by EarlsFurniture on 2016-08-02
So I've verified the video card is bricked. It won't work in another machine at all, or be recognized by it.

After resetting CMOS, I can get the machine to GRUB and then look at files on the drives, and attempt various boot parameters, but nothing is successful.

I get a short hop after 'loading initial ramdisk' and then the system gets a restart signal for some reason. If I could see the output on the screen instead of it flying by at mach10, I might be able to figure out why.

Alas, upstart has no boot logging facilities. So the machine is getting dropped to run level 6 before any logging takes place. Thus my only hope is the screen output which is not readable it's so fast.

I looked into setting up a serial console, but I don't even think this is possible with the current problems. I would have needed it already set up before this incident. Certainly, I can't even get a liveCD to work.

I did manage to put the SSD into an external docking station and chroot to it from another machine. I was able to turn on bootlogd and verify that it was installed, but upon attempting more boots, there still is nothing being written to any logs.

Interestingly, syslog, kern.log and dmesg all get updated time stamps on a reboot (well, some hours later, which is very odd) but nothing is being written to the files. They are apparently touched, but not appended to.

bootlogd doesn't appear to be loaded by the time the failure occurs, so it is useless. (I read notes it was discussed to one day make it load in the ramdisk, but I guess that was abandoned)

Could this perhaps be an issue with UEFI or Secure Boot?

I see that the BIOS screen (ahem, yes, really the UEFI screen) is telling me Secure Boot is enabled, but I see no way to disable it. As far as I recall, I never bothered with that when I installed the system in the first place. Does the Ubuntu installer disable it and somehow resetting CMOS turned it back on?

How can I possibly turn it off if the BIOS/UEFI screens don't offer the option?

What does the boot process look like when you attempt to load a non-signed OS with Secure Boot on? Does it endlessly restart like this or does it give an error message and halt?

---

### Post by him610 on 2016-08-03
Do you happen to have home owners or renters insurance? If so, submit a claim for the damages.

Several years ago, my home suffered a nearby lightning strike. The surge came right down the coax cable, took out the cable modem, a router, a network printer, and the motherboard of one of our computers. Estimated damage was around $1300. Cable company replaced the cable modem. The printer (Dell) was under a service contract. Home owners insurance paid about $900 for the router and computer.

It pays to consider "what if" scenarios.

---

### Post by EarlsFurniture on 2016-08-03
Thanks for the suggestion. The UPS was from APC which comes with a $10,000 equipment protection guarantee. They are replacing the unit, but it looks like they will only offer about $175-$200 for the computer because they claim it is already 5 years old and they don't pay 'replacement value.' I'll check into a homeowner's policy. The claim there might produce a better result.

It seems that value might not be so bad in the end.

I tried a Windows 8.1 and Windows 7 disk. Both dropped to a restart after the video switched out of console mode. So, the MB is likely toast or at likely the onboard GPU is.

So far, it looks like a dead PSU, Video Card, and either onboard GPU or just general MB problems. At least the case, drives, CPU, and data are still viable. I should probably find the three needed parts for $175 anyhow.

I'm closing the thread because I guess there's nothing left to solve or troubleshoot. It would have been nice to figure out how to see those Speedy Gonzales boot messages though for future reference.

*note, I wish I could mark this as pointless/closed/no-solution instead of 'solved.'

---

