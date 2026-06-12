---
title: "USB mouse fails 5 minutes after startup"
date: 2009-02-23
forum: Hardware
---

### Post by Grendelmon on 2009-02-23
Something strange has happened to one of my Ubuntu boxes.  I've searched the threads and can't seem to find anyone else that has my specific issue.  I was running Ubuntu 8.04 on it for sometime, but use the machine primarily for gaming under XP Pro, and recently made some changes and I'm not sure what happened.

I'm using an Asus P5N32-SLI Premium motherboard with 3gb of RAM.  Originally, I had an E6300 1.86ghz core 2 duo with dual nVidia 7900GS cards in SLI.  8.04 ran great, and I installed nVidia's drivers and even had SLI enabled.  I use Windows XP more than Ububntu on this box, since it's my gaming rig, but never really had any (serious) issues in Ubuntu.

About two month ago, I upgraded both my video cards to nVidia 9600GTs.  Everything still worked, and the drivers worked fine in Ubuntu.  Then about a month ago, I upgraded my processor to an E6600 2.4ghz dual core, and dropped an extra 1gb of RAM for a total of 4gb.  I then upgraded Ubuntu to 8.10, rebooted, checked the version and went back to XP.

Since I mostly use XP, I'm not sure when this issue started happening, but now my USB port that my mouse is plugged into dies in Ubuntu 8.10, after booting up and using the machine for about 3-5 minutes.  The cursor appears to just hang, but the machine is still running.  I use a PS2 keyboard since I used to have problems getting into the BIOS config with a USB keyboard.  I can ALT-TAB to applications I opened and type just fine.  I figured with all the hardware changes I made something got bumped or the USB cable wasn't plugged in properly.  So I unplugged the mouse, plugged it back in, but nothing.  I rebooted, the mouse came back, but after about 3 minutes it died again.

Odd thing was that the optical light was still on, and I had a terminal running.  lsusb still showed the (Logitech) USB mouse was connected.  Nothing reported in dmesg.  No USB errors in the syslog or anywhere else.

SO... I thought the 8.10 upgraded messed something up, maybe a kernel upgrade or whatnot.  I booted off a Live CD of 8.04, and same issue.  2 minutes later the mouse died.  WTH?  I booted off 7.10 Live CD... same thing.
I swapped USB mice with a Microsoft mouse.  Rinse and repeat, same issue.  I did notice that when the mouse dies, I can plug a notebook USB mouse in one of the front ports, and it works.  Didn't use it long enough to see if that one died, too though.  Now I'm thinking I have a motherboard problem, since I've swapped mice, and the issue exists in mutiple versions of Ubuntu.  The weird thing is that XP never has ANY USB problems at all.  I can game all night long without any issues.

I feel like I broke something, somewhere, but have no idea.  If I don't see any errors in the logs, how should I go about fixing this?

Thx for your help.

Update: One thing I forgot to mention is that when the mouse dies, I try to CNTRL-ALT-F1 to get to a main prompt, and it doesn't switch.  The machine locks up after that.

---

### Post by Grendelmon on 2009-02-23
I think that I got it working again...

It appears to be a BIOS setting that got reset.  The Asus P5N32 boards have a USB option for "USB Legacy Support."  I found another thread where someone said to DISABLE this option.  Mine was set to enabled.  I *thought* I was using the default BIOS settings, and when I got the E6600 cpu I overclocked it too far, thus requiring a CMOS reset.  I think that when I did this, the USB Legacy Support got re-enabled.

Disabling it fixed the problem (for now...?).  Been using Ubuntu for about 30 minutes which is much longer than I could before without the mouse failing.  This probably explains why it was affecting multiple versions of the Ubuntu Live CDs.

---

