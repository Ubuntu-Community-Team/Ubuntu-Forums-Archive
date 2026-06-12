---
title: "USB mouse stops working after logging in"
date: 2011-09-24
forum: Hardware
---

### Post by Grendelmon on 2011-09-24
Hi everyone,

I've tried sifting through the forums and can't find anything as specific as my scenario, so I'll take a shot. First off all, my hardware:

-ASUS p5n-32 sli premium wi-fi motherboard
-e6600 core 2 duo @ 2.4ghz
-4gb 667mhz ddr2 ram
-dual nVidia 9600gt video cards, linked via SLI
-3 SATA hard drives, running: sda WinXP 64bit Pro, sdb: Xub 11.04, sdc: Xub 9.04

I have a custom PC I made back in 2006, using an ASUS p5n-32 sli premium motherboard. The box has worked great, and I've used Ubuntu 7.04 up to 11.04. Staring with 9.04, I switched to Xubuntu. It's worked great up until about 9+ months ago. After about upgrading to Xubuntu 10.10, for some reason when I log in, after what appears to be a random amount of time, my USB mouse stops responding. My PS2 keyboard still worked, so I could ALT-TAB to a terminal and cleanly reboot. It seems to be random when it occurs, sometimes it happens within a minute, sometimes it can take 30 minutes. No pattern in when it occurs, but one thing that seems consistent is that it always dies when I'm trying to move the mouse. I've never seen the mouse already dead after leaving the machine and coming back to it later.

Well, the problem seems more widespread. I'll fast forward and just list the scenarios it has occurred. I'm beginning to think that I might have a hardware issue:

-Happens in Xubuntu 11.04 now with USB keyboad and a different USB mouse, the mouse dies but keyboard works
-Booted a separate drive running Xubuntu 9.04, and it starting happening there as well
-Now it happens while booted off all Live CDs I've burned, including Xub 9.04, 10.10, both 32-bit and 64-bit
-4 USB ports in back, 2 in front. Have tried every USB port in ever combo above and still happens (even daisy-chained off an Apple USB keyboard as well)

The strange thing is, I've had the same copy of XP Pro 64-bit running on the primary drive and have *never* had any USB problems. So my question is, even if it is a potential hardware failure, why does XP run just fine?

I have never seen any device errors in any logs, including the syslog and Xorg log. I have even tailed both logs in term windows and watched the mouse die, and nothing gets reported.

Time for a new motherboard? :confused:

---

### Post by searchfgold6789 on 2011-09-24
If possible try running (using your ps2):```
lsusb
```or even```
lshw
```when it happens and post back, don't forget to but it in CODE tags, you probably already knew that, but it doesn't hurt to just remind you.
But something is telling me it's actually a voltage/power issue, something embedded deep within the code of the kernel USB driver (I call these "wisdom teeth"). This apparent nugget of intuition is powered by the fact that Linux thinks you're unplugging the devices yourself. So what I would do is buy/rent/obtain/make/"borrow" a USB hub with a power adapter for it included - one of the fancy ones - and try it. This way it has absolutely no excuse to power off your USB devices

---

