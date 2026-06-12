---
title: "HP Laptop Refuses to Wake Up After Improper Suspension"
date: 2014-08-03
forum: Hardware
---

### Post by LillyDragon on 2014-08-03
I'm currently typing this from a new Windows 8 notebook, and I am in serious need of help; weeks of research has helped me learn a lot, but not enough to actually fix the problem I have. Three weeks ago, I attempted to suspend my main laptop as usual before going to bed, but Ubuntu hanged on a blank screen after unmounting the drive, and refused to shut off, so I turned it off manually.

Then, I tried turning it on, and I was met with a non-blinking underscore, like it was frozen and couldn't respond. The laptop behaves exactly like it's attempting to wake up from suspend mode, but can't once it tries to access the OS.

All of the hardware comes on normally. The fan spins up, the HDD and DVD drives are running, (But no read/write activity.) and the fact that something came on-screen at all tells me my GPU is still good too. There was no sign of hardware degradation prior to this as well. No artifacts or colored bars were on the screen, nor were there crashing programs or OSes. Everything was stable and working as usual. If the memory modules were failing, HP computers won't even make it past post, so that's not it either.

This is why I believe all my attempts to look into BIOS corruption or failing memory modules led to dead ends, so I have to assume that the poor thing had a bad suspension, and "waking it up" might be complicated than on Windows. The whole fiasco makes me never want to trust Suspend mode on an OS ever again, as it is apparently a common problem from what I've been googling lately.

Before I got my notebook, this is the answer I received on AskUbuntu from amanthethy, since I couldn't access the Ubuntu forums from a Wii. (I also couldn't log back in to Ask Ubuntu afterwards on my new account either from the Wii, the login button didn't work, so I couldn't answer back until now.)

[quote="amanthethy"]
This is a longshot, but it sounds like your machine might be making it past the BIOS and then just hanging at boot. My MBP used to do this. Had something to do with not being able to resume from the memdisk when booting from EFI. Every boot would take me to the same screen you're getting.

If this is the case, and you are indeed getting through the BIOS, think you could manage it to boot from CD? If so, you could burn a copy of Super Grub Disc 2 and boot up with that. It'll find your exisiting GRUB install. Edit that to include acpi_sleep=nonvs before the quiet splash params and then boot up. That'll force your Ubuntu to wake from its slumber.
[/quote]

Of course, with the laptop in this state, I can't boot to a Live CD, so the only option here is to buy a SATA to USB converter and edit GRUB on the hard drive from this notebook. However, I am still not 100% confident this is the problem, since the CAPSLock test is telling me BIOS corruption with two blinks, (Not sure if this means corrupt settings, or a bricked bios altogether.) so I wanted to ask around for more insight before investing in an adapter.

---

### Post by weatherman2 on 2014-08-03
Sounds like nothing to do with the hard drive, so forget about editing Grub.

The laptop could be stuck in a weird state or it could be a hardware failure.

Things to try:
- remove the battery, unplug the power cord.  Then hold down the power button for 60 seconds.  Then replace battery + power cord and try again.  This should clear out any previous state of suspend.
- remove your RAM and re-seat it.  If you have two RAM sticks, try removing both and trying one stick at a time in each slot.
- remove the hard drive completely, then see if you can POST.  If no, then nothing at all to do with the hard drive.  If you can post after removing the hard drive, then the hard drive has probably failed or is corrupt somehow (suspend doesn't write anything to your hard drive, only hibernation does).
- if you can find out where the CMOS battery is on the laptop, see if you can unplug it briefly and plug it back in.  This could be difficult to do - taking it completely apart in some cases - depending on where the CMOS battery is located on the laptop.  I would try this only if the CMOS battery is easy to get to and can easily be removed briefly.
- leave the main battery and power cord out overnight and try again in the morning.

Motherboards fail in weird ways. It could also be in a weird state you need to clear. I vaguely recall a similar problem with an HP laptop I was working on, and one of the above solutions worked after about 30 minutes of frustration. Never understood why it happened or what exactly I did to fix it. Leaving battery out + power cord out + leave it sit an hour is what I think fixed it.

---

### Post by LillyDragon on 2014-08-03
It is good knowing that Suspend mode doesn't commit a write to the hard drive, so if my HDD hasn't failed, it should be fine.

In the first two weeks, I have tried all of those things, as well as plugging in my original hard drive with Windows 7 in it, and none of it works. That easily makes this the most frustrating problem I have ever had with a computer. I cannot understand why it's behaving this way. It does this even with the hard drive removed.

As for the CMOS battery, that definitely does not work on modern laptops. Settings are stored in flash memory these days, leaving the battery dedicated to the real-time clock. I have tried many ways to look for a CMOS jumper to reset my settings to no avail; my model is HP 2000-299WM, if that is helpful. So even if the battery has died and needs a replacement, (Which, my CMOS battery isn't, since I got it to power a small electric motor.) that won't change anything. If only this was a desktop PC, CMOS jumpers are standard there! All I have to look for are most laptops are weird solder blob pins that *might* be the jumper.

All of this makes me afraid I have fallen prey to a kernel bug before 12.04's release that corrupts your BIOS settings with a written variable that is longer than the NVRAM can store. I have no idea if the bug was fixed before release. If that is the case, then I can only hope making a bootable USB drive to restore the BIOS altogether would work.

---

### Post by weatherman2 on 2014-08-03
Making a USB flash drive sounds pointless, because it sounds like nothing will boot.  If you could boot the flash drive, you could probably boot your hard drive.

I re-read your description.  My problem was different than what you describe: I would get text upon power-up (trying to POST) but it would freeze looking for a boot device.  I could not boot anything until I played those tricks I described.

If all you see is a blinking "-" and no keys respond (can't enter BIOS Setup, can't get a boot menu) and you never see any text or HP logo on your screen, then I do suspect hardware failure.  It does happen.  Motherboards fail all the time on laptops, without any sort of prior warning.  It may have had nothing at all to do with suspend.

One further test: remove all the RAM and try powering on.  Does the laptop beep or otherwise behave differently than it does with RAM?  If it beeps, then maybe the motherboard is alive after all.  If it behaves in exactly the same way, I suspect the motherboard has failed.

I would continue troubleshooting this problem on an HP forum or a laptop hardware forum.  I suspect the problem has nothing at all to do with Ubuntu.  I am not an expert on HP laptops and cannot offer you much more in the way of help.

---

