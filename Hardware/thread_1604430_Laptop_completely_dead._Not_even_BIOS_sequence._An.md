---
title: "Laptop completely dead. Not even BIOS sequence. Any ideas?"
date: 2010-10-24
forum: Hardware
---

### Post by infinitejones on 2010-10-24
I've got a HP dv6000 laptop which has served me well for a couple of years. Single boot with 64bit Maverick, separate partitions for /boot, / and /home.

I turned it on this morning, went and did something else while it booted up, and came back to find the Plymouth boot screen dots still cycling through long after it should have booted. No problem, that happens occasionally, so I hard-reset it (by holding down the power switch) and let it re-boot, like I always do. Same thing happened again though.

So I hard-reset again (only thing I could do - F12 did nothing, escape did nothing) but this time - it refuses to do anything at all when I reboot.

The LED on the power switch lights up, the LEDs across the top of the keyboard (multimedia keys etc) light up, but the screen is completely blank. The fan whirs for a second or two then dies down. The CD drive clicks momentarily too. Nothing else happens.

The hard drive activity light is off, and it doesn't even get to the BIOS boot screen, let alone Grub or Plymouth. No keys respond - not F2 or F12 or escape.

I've tried inserting a Live USB while it's powered off and again, when I turn it on, nothing.

Now I fully admit that this might not even be an Ubuntu issue (especially considering it doesn't even get as far as grub), and I don't even know where to begin to diagnose it but... does anyone have any ideas at all?

(Or am I just buying a new laptop tomorrow...?)

---

### Post by gerowen on 2010-10-24
Check your RAM sticks and make sure they're seated properly.  Try booting with only one RAM stick if you have more than one inserted, try swapping them out one at a time and moving them into different slots.  RAM can go bad or come loose over time from the heating up and cooling down of the computer.  Take out your battery, let the computer sit for a few minutes, then put it back in and try booting it up.  These are just some troubleshooting measures, but it sounds like you're getting a new computer, :-(

---

### Post by infinitejones on 2010-10-24
Well... removing the battery for a few minutes seems to have done the trick! The boot sequence is still a bit erratic but at least I've got a booting computer that's actually doing something now...

Thanks very much.

---

### Post by P4man on 2010-10-24
DV6000 and 9000 series are notoriously bad. Overheating causes solder contacts to expand and contract and over time they break. IIRC there has been a recall from HP, thats the first thing I would check if yours is covered by it. But I fear its too late for that.

If the problem returns, and Im rather sure it will, and you feel adventurous, you can try and fix it yourself. Have a look here:
[http://www.youtube.com/watch?v=S2jPq8Qf6g0](http://www.youtube.com/watch?v=S2jPq8Qf6g0)

You wont have the IR equipment but you can use a heatgun instead.

---

### Post by PaulW21781 on 2010-10-24
Sounds like an issue which also affects the Acer 5735Z

[http://ubuntuforums.org/showthread.php?t=994382&highlight=5735z](http://ubuntuforums.org/showthread.php?t=994382&highlight=5735z)

Wonder if they are related somehow... perhaps same hardware specs inside?!  So something to do with the MB/ACPI controller...

I've noticed, with the Acer, that just before it does this, it completely stops charging.  It will have the charging indicator on at the front, but within Gnome Power Manager, it says the battery is discharging.  Then on rebooting, it does what you mentioned...  Keep an eye on how your laptop is running when plugged into the mains, and if the charging fun applies to you just before it fails to boot up.

---

### Post by P4man on 2010-10-24
I dont see anything in there that suggests its same problem?
Now obviously bad solders arent unique to the pavillion series, its just that they are known to be particularly poor in this regard. A poor thermal design exacerbates the problem; the hotter the components get, the worst the expansion/contraction and the faster it will die.

---

