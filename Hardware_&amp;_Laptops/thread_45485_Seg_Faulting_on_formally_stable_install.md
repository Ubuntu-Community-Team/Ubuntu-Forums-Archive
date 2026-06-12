---
title: "Seg Faulting on formally stable install"
date: 2005-06-30
forum: Hardware &amp; Laptops
---

### Post by Joeb on 2005-06-30
I have Ubuntu 5.04 installed since the day it came out and it has run pretty much flawlessly.  Earlier in the week, I did an upgrade, which installed a new kernel (although I don't think that is the problem, since it didn't happen right away).

Well, yesterday, when I got home for work, I noticed the computer was locked up hard on the screensaver (I normally leave the computer up 24/7).  I had to do a hard boot to recover and that is where the problems began.

If I boot into a graphical login, I get a lot of errors in gnome when various panels and panel applets load.  And most applications will simply just abort.  Gnome itself would disappear and I'd be back a the GDM.  Or sometimes, when booting the GDM wouldn't even load.  There would be an error message and then XDM would be displayed.

If I boot to the console, very often, there are seg faults displayed for just about every command issued or app launched.  

Thinking that the last kernel update hosed the system, I tried booting off of the livecd and guess what?  The same thing happens.  I even tried a livecd from a different distro and had the same results.  The only time this problem didn't manifest itself was if I booted into an old Windows98 install that is still sitting on a partition or if I boot into the memtest.


The Windows 98 working has me a bit perplexed, because to me, this sounds like a hardware problem (even though Ubuntu has run very stable for months).  Thinking it might be memory going bad, I pulled some from a different computer and installed it but that didn't make a difference.

Some other symptoms are that when the computer is first turned on, there is a long delay before the POST begins.  Although the drives seem to spin up normally, the monitor says there is no video signal for about 40 seconds, then the boot begins normally, first displaying the NVIDIA bios information, then the memory count and finally, the regular hardware boot process (you know, all that info about what drives, ports, interrupts, etc.) and finally GRUB.

The long delay makes me think there might be a problem with the video or the motherboard itself.  But I'm not sure and since I don't have a lot of money (I work for a religious organization), I really can't just go out and by random parts and hope to fix it.

Again, I don't think it is a problem caused by the kernel, specifically since the livecd has the problem and so does another unamed distro's live cd.  I also don't think it is the CPU (AMD XP 1900+, since the Windows 98 seems to run fine, but then it doesn't stress the system at all).  Finally, I don't think it is the RAM, since I swapped that out and the problem still exists.  I'm leaning towards a video card going bad (NVIDIA) or the motherboard.  I did notice that if I drop the buss speed to 100mhz from 133mhz the system seems more stable but still has some problems (plus that drops the CPU speed to 1200 instead of 1900).

So, although this isn't specifically an Ubuntu problem, I'm hoping someone here can give me some insight as to what might be causing this.  Again, the computer has run flawlessly with Ubuntu since Warty.

Joeb

---

### Post by Devi0s on 2005-06-30
[QUOTE=Joeb]The Windows 98 working has me a bit perplexed, because to me, this sounds like a hardware problem (even though Ubuntu has run very stable for months).  Thinking it might be memory going bad, I pulled some from a different computer and installed it but that didn't make a difference.[/QUOTE]

Windows tends to be more tolerant of bad RAM.  That is, Windows will run on top of bad RAM until it becomes corrupted enough that it can't do anything but bluescreen.

Have you tried testing for bad RAM by with a low level RAM diagnostic utility, i.e. running memtest86 from the install or livecd?  I think it comes on the knoppix cd as well as a boot option.

---

### Post by davahmet on 2005-06-30
[QUOTE=Joeb]I have Ubuntu 5.04 installed since the day it came out and it has run pretty much flawlessly.  Earlier in the week, I did an upgrade, which installed a new kernel (although I don't think that is the problem, since it didn't happen right away).

Well, yesterday, when I got home for work, I noticed the computer was locked up hard on the screensaver (I normally leave the computer up 24/7).  I had to do a hard boot to recover and that is where the problems began.

If I boot into a graphical login, I get a lot of errors in gnome when various panels and panel applets load.  And most applications will simply just abort.  Gnome itself would disappear and I'd be back a the GDM.  Or sometimes, when booting the GDM wouldn't even load.  There would be an error message and then XDM would be displayed.

If I boot to the console, very often, there are seg faults displayed for just about every command issued or app launched.  

Thinking that the last kernel update hosed the system, I tried booting off of the livecd and guess what?  The same thing happens.  I even tried a livecd from a different distro and had the same results.  The only time this problem didn't manifest itself was if I booted into an old Windows98 install that is still sitting on a partition or if I boot into the memtest.


The Windows 98 working has me a bit perplexed, because to me, this sounds like a hardware problem (even though Ubuntu has run very stable for months).  Thinking it might be memory going bad, I pulled some from a different computer and installed it but that didn't make a difference.

Some other symptoms are that when the computer is first turned on, there is a long delay before the POST begins.  Although the drives seem to spin up normally, the monitor says there is no video signal for about 40 seconds, then the boot begins normally, first displaying the NVIDIA bios information, then the memory count and finally, the regular hardware boot process (you know, all that info about what drives, ports, interrupts, etc.) and finally GRUB.

The long delay makes me think there might be a problem with the video or the motherboard itself.  But I'm not sure and since I don't have a lot of money (I work for a religious organization), I really can't just go out and by random parts and hope to fix it.

Again, I don't think it is a problem caused by the kernel, specifically since the livecd has the problem and so does another unamed distro's live cd.  I also don't think it is the CPU (AMD XP 1900+, since the Windows 98 seems to run fine, but then it doesn't stress the system at all).  Finally, I don't think it is the RAM, since I swapped that out and the problem still exists.  I'm leaning towards a video card going bad (NVIDIA) or the motherboard.  I did notice that if I drop the buss speed to 100mhz from 133mhz the system seems more stable but still has some problems (plus that drops the CPU speed to 1200 instead of 1900).

So, although this isn't specifically an Ubuntu problem, I'm hoping someone here can give me some insight as to what might be causing this.  Again, the computer has run flawlessly with Ubuntu since Warty.

Joeb[/QUOTE]
 Segmentation faults normally come from either memory boundary violations in the software or hardware memory defects.  Since this happens on your installed OS as well as a LiveCD, we can pretty much rule out software as the culprit.

Since you have replaced the memory and it still happens, we can rule out your memory chips as well.  Possibly the problem could be in your bus on the motherboard, in the CPU, or in your power supply (probable).  As you say, Win98 seems OK, which to me suggests it is not the CPU or the video card.

Also, the problem starts very early in the POST, before the video card is active it sounds like.  At the beginning stages of the POST, the hardware waits for voltage level stabalizatiosn which is normally very quick, but a failing power supply could explain the long delay of the POST.

Power supply problems can be very difficult to troubleshoot since it usually starts with system instability.  One way to verify this is to remove all but the essential devices (CD-ROM, sound cards, modems, etc) and look for changes in stability as the load on the PS is reduced.  This is not a definite test but it may offer some insight.

I hope this helps

---

### Post by Joeb on 2005-06-30
[QUOTE=davahmet]Segmentation faults normally come from either memory boundary violations in the software or hardware memory defects.  Since this happens on your installed OS as well as a LiveCD, we can pretty much rule out software as the culprit.

<snip>

Power supply problems can be very difficult to troubleshoot since it usually starts with system instability.  One way to verify this is to remove all but the essential devices (CD-ROM, sound cards, modems, etc) and look for changes in stability as the load on the PS is reduced.  This is not a definite test but it may offer some insight.

I hope this helps[/QUOTE]

Thanks, I'll try swapping out the power supply tonight, if I get a chance.  The only reason I was suspecting the video card was that the nvidia binary driver seemed a little problematic earlier (but then the problem persisted, even with the "free" drivers).  Of course, if I'm not mistaken, the video card is power hungry, so if the power supply is starting to fail, then maybe that would contribute to the flakeness of the driver.

I'll post back what I find out, but it might be a couple of days before I get a chance to try it.

Thanks.

Joeb

ps  to DeviOs, I've let memtest run on both the old and new memory for an hour or so, each, and there weren't any problems detected.  Thanks, though.

---

### Post by Joeb on 2005-06-30
Okay,  I tried a brand new power supply and it didn't make a difference.  However, in the process, I reset the CMOS and it started working.  I went in and checked what the settings were and I noticed that the CPU and Memory speeds were both set at 100mhz instead of the normal 133mhz.  As it turns out, I can set the memory back to 133mhz, but if I increase the CPU speed to 133mhz, I have the problem.  Leave it at 100mhz and all works fine.  Of course, at 100mhz, the CPU is running at 1200mhz instead of the 1600mhz.  

I can live with that (for now), however, does this mean that the CPU is most likely the problem and is on it's last legs?  Or could this still be a problem with the motherboard?

---

