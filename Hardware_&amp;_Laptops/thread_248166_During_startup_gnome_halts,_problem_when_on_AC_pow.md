---
title: "During startup gnome halts, problem when on A/C power only"
date: 2006-08-31
forum: Hardware &amp; Laptops
---

### Post by sgornick on 2006-08-31
When on battery, my HP zx5078cl w/ Ubuntu Dapper Drake 6.06 LTS starts up into gnome just fine.  When on A/C power, gnome starts, begins playing about a 1/2 second of audio and then the desktop stops loading. 

I can restart X (ctrl-alt-backspace) and then before logging back in to desktop from the shell manually kill the orphaned processes (gnome-terminal, esd, etc.) and, unplug the A/C to go back to battery, and then re-login to gnome successfully. 

And once I am past the desktop login I can then plug in my a/c with no problems thereafter noticed.   If I disable the startup sound (System -> Preferences -> Sound -> Log In set to "No Sound") then I can start up on A/C with no problems thereafter as well.  So it is only during gnome startup, on  A/C power and with Log In Sound that I have the problem.

On A/C and Log In Sound enabled (unsuccessful login), syslog shows:

Aug 31 14:07:25 localhost kernel: [17180177.820000] [drm] Loading R200 Microcode
Aug 31 14:07:30 localhost gdm[4424]: Error reinitilizing server
Aug 31 14:07:32 localhost kernel: [17180184.444000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Aug 31 14:07:32 localhost kernel: [17180184.444000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
Aug 31 14:07:32 localhost kernel: [17180184.444000] agpgart: Putting AGP V3 device at 0000:01:05.0 into 4x mode
Aug 31 14:07:32 localhost kernel: [17180184.680000] [drm] Setting GART location based on new memory map
Aug 31 14:07:32 localhost kernel: [17180184.680000] [drm] Loading R200 Microcode
Aug 31 14:07:32 localhost kernel: [17180184.688000] [drm] writeback test failed
Aug 31 14:07:44 localhost kernel: [17180196.004000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR


and when on Battery (successful login), syslog shows:
Aug 31 14:40:10 localhost kernel: [17182142.296000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Aug 31 14:40:10 localhost kernel: [17182142.296000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
Aug 31 14:40:10 localhost kernel: [17182142.296000] agpgart: Putting AGP V3 device at 0000:01:05.0 into 4x mode
Aug 31 14:40:10 localhost kernel: [17182142.296000] [drm] Loading R200 Microcode

My audio, according to lscpi:
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
        Subsystem: Hewlett-Packard Company: Unknown device 006b
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 5
        Memory at e8003000 (32-bit, non-prefetchable) [size=256]

In dmesg, some of the ACPI messages during startup show:
[17179605.140000] ACPI: AC Adapter [ACAD] (on-line)
[17179605.252000] ACPI: Battery Slot [BAT1] (battery present)
[17179605.556000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)

Any suggestions?

---

### Post by sgornick on 2006-11-05
I did a clean install of Edgy and am getting the same thing.

I believe it is similar to this bug reported:
[https://launchpad.net/bugs/40176](https://launchpad.net/bugs/40176)

---

### Post by sgornick on 2007-09-29
Problem ( Bug #86162 ) no longer exists in Gutsy.

---

