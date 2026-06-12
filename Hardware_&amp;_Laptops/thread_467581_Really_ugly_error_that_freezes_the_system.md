---
title: "Really ugly error that freezes the system"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by LucasLinard on 2007-06-07
Hi,
I've been using ubuntu for a few yeras and decided to upgrade my pc. I bought a new MOBO new ram and new proc. I tryed  feisty both 64 bits and 32. BUT I keep getting this weird error that just freezes the pc, th video becomes ugly and the system stops responding. Can anyone help me? Can it be a hardware problem? if so, wich part? (mobo, proc, memory)?
THe system is:

MObo: ecs c51gm-m (new)
Proc: Athlon x2 3800+ (new)
512 mb ddr2 667 (new)
hd samsung ide 80GB (6 months of use)

I'm posting some pictures of the monitor.
The error happens at random times, once it happened while installing ubuntu, other timem when I was converting videos via mencoder.

---

### Post by 444 on 2007-06-07
Looks like broken hardware...

---

### Post by kmoffat on 2007-06-07
Maybe the video is not configured correctly, or not yet supported. Can you boot to single user mode?

---

### Post by Megatog615 on 2007-06-07
When does this problem occur? Does it start at bootup, or all throughout, even POST? If it happens all the time it means your video card might not be seated properly in the slot, or there is defective hardware. If it starts after the boot process, it means some extended video call is causing it, and your video card(still) might not be seated properly in the slot, or the driver is going haywire.

Try to run it in recovery mode and post the output of dmesg.

---

### Post by 444 on 2007-06-08
You can run memtest and prime95 for a few hours each to eliminate the cpu and memory as the cause. Looks like a video problem.

---

### Post by LucasLinard on 2007-06-08
> **444 said:**
> You can run memtest and prime95 for a few hours each to eliminate the cpu and memory as the cause. Looks like a video problem.

Thank you all
the video is a nvidia 6100 onboard video (the motherboard is a c51gm-m)
is there any chance of a hard disk problem??
It happens at random times, I can use the pc for hours, of for minutes. can be doind nothing, or running many programs.
Las night for example I whent to bed, turned of my monitor and lçeft the pc on with azureus running. here is the massage log.
> 
Jun  8 00:04:52 linard-desktop -- MARK --
Jun  8 00:24:53 linard-desktop -- MARK --
Jun  8 00:44:53 linard-desktop -- MARK --
Jun  8 01:04:53 linard-desktop -- MARK --
Jun  8 01:24:53 linard-desktop -- MARK --
Jun  8 01:44:53 linard-desktop -- MARK --
Jun  8 02:04:53 linard-desktop -- MARK --
Jun  8 02:24:54 linard-desktop -- MARK --
Jun  8 02:44:54 linard-desktop -- MARK --
Jun  8 03:04:54 linard-desktop -- MARK --
Jun  8 03:24:54 linard-desktop -- MARK --
Jun  8 03:44:54 linard-desktop -- MARK --
Jun  8 04:04:55 linard-desktop -- MARK --
Jun  8 04:24:55 linard-desktop -- MARK --
Jun  8 04:44:55 linard-desktop -- MARK --
Jun  8 05:04:55 linard-desktop -- MARK --
Jun  8 05:24:56 linard-desktop -- MARK --
Jun  8 05:44:56 linard-desktop -- MARK --
Jun  8 07:14:34 linard-desktop syslogd 1.4.1#20ubuntu4: restart.
Jun  8 07:14:35 linard-desktop kernel: Inspecting /boot/System.map-2.6.20-16-generic
Jun  8 07:14:35 linard-desktop kernel: Loaded 25650 symbols from /boot/System.map-2.6.20-16-generic.
Jun  8 07:14:35 linard-desktop kernel: Symbols match kernel version 2.6.20.

whe can sse that somewhere between 5:44 and 07:14, it freezed.
7:14 is the time that I rebooted the pc when I woke up and noticed the wierd video again.

---

### Post by LucasLinard on 2007-06-08
> **Megatog615 said:**
> When does this problem occur? Does it start at bootup, or all throughout, even POST? If it happens all the time it means your video card might not be seated properly in the slot, or there is defective hardware. If it starts after the boot process, it means some extended video call is causing it, and your video card(still) might not be seated properly in the slot, or the driver is going haywire.

Try to run it in recovery mode and post the output of dmesg.

IT happens at random times and with both restricted nvidia drivers and the not restricted one.

---

### Post by 444 on 2007-06-08
I think a hard drive problem is very unlikely, you'd get some sort of readable error for that.

---

### Post by CrispyFried on 2007-06-08
since its a new build, try unplugging all cards/cables/memory/PS connectors and reseating them. heat might be causing thermal expansion and unseating a connection somewhere. its also possible the mobo might not be seated well and shorting out against the case or a hardware standoff or mounting point. check that all fans are running well too but I would think if its fan related it would only hang under heavy load.

I notice you didnt list a new PSU, is it rated to run your new hardware?

---

### Post by LucasLinard on 2007-06-08
> **CrispyFried said:**
> since its a new build, try unplugging all cards/cables/memory/PS connectors and reseating them. heat might be causing thermal expansion and unseating a connection somewhere. its also possible the mobo might not be seated well and shorting out against the case or a hardware standoff or mounting point. check that all fans are running well too but I would think if its fan related it would only hang under heavy load.

I notice you didnt list a new PSU, is it rated to run your new hardware?

Sorry if I wasn't clear
The only "old" thing is my hard disk. new PSU (is it power suply?, english is not my native lang...), new mobo, new case, new keyboard, new ddr2 667, new prc, new mouse and keyb.
everything but the hard disk is new.
I can't unplug much stuff because there isn't much to unplug. jus a hard disk and a cdrom drive. No pci / pci-e cards inserted.

---

### Post by CrispyFried on 2007-06-08
its still worth a shot to unplug everything you can and reseat it. you could also check that the mobo is secure.. all screws are tight and its not warped. just to be sure Id swap out the HD/CDROM cables but thats probably not it.

---

### Post by LucasLinard on 2007-06-08
> **CrispyFried said:**
> its still worth a shot to unplug everything you can and reseat it. you could also check that the mobo is secure.. all screws are tight and its not warped. just to be sure Id swap out the HD/CDROM cables but thats probably not it.

Thanks. I'll try that.
There's a bios update. should I try to update the bios?

---

### Post by Megatog615 on 2007-06-08
Is there a changelog for the bios update? Only update the bios if you need the changes, or are affected by a fixed bug. The bios is a hit or a miss thing when it comes to upgrading. Fail and it's off to the hardware store for a new motherboard.

---

### Post by ohzopants on 2007-08-08
I have the same problem, and the only part we have in common is the motherboard.
This also happens to me when I boot into windows, it seems to happen more frequently in windows then it does under Ubuntu, and usually after a shorter period of time.

I personally suspect the video chipset, I think I'm going to invest in a proper video card and hope that it solves my problem.

---

