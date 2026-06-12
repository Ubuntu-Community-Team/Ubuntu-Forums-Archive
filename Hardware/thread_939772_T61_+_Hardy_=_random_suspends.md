---
title: "T61 + Hardy = random suspends"
date: 2008-10-06
forum: Hardware
---

### Post by mrz80 on 2008-10-06
I have a ThinkPad T61 running Hardy with all the latest updates.  At random times, even when plugged into AC power, the laptop will suspend, and then not resume.  I can't duplicate the problem, nor can I find a combination of wireless, ACPI, VPN and other parameters that will stop the random suspends.  If I force maxcpus=1 on bootup, it's less likely to occur, but it does still happen.  Has anyone else seen anything even remotely like this?  Random hangs on *RESUME* everyone gets. Random *SUSPENDS*, however, appears to be a whole nuther kettle of fish!

Oh, none of this nonesense occurs when I boot the thing on XP.  Argh.

---

### Post by nixscripter on 2008-10-06
Wait for it to happen, reboot, and then look in your log files, especially kern.log (Ubuntu menu -> System -> Administration -> System Log). See if you can figure out what happened in the kernel right before suspend. That should provide a start.

---

### Post by dsm iv tr on 2008-10-07
My laptop randomly suspends (and resumes fine) about ten minutes after I switch the onboard Radeon to "low voltage" mode.

Very strange.

---

### Post by mrz80 on 2008-10-22
> **nixscripter said:**
> Wait for it to happen, reboot, and then look in your log files, especially kern.log (Ubuntu menu -> System -> Administration -> System Log). See if you can figure out what happened in the kernel right before suspend. That should provide a start.

Nothing out of the ordinary in the log files.  I see dropped frames from the wireless adapter (but I get those **CONSTANTLY**);  then out of a clear blue sky, 

```
Oct 22 13:40:39 glasgow kernel: [  128.482100] Syncing filesystems ... done.
Oct 22 13:40:39 glasgow kernel: [  128.588771] PM: Preparing system for mem sleep
Oct 22 13:40:39 glasgow kernel: [  128.588779] Freezing user space processes ... (elapsed 0.00 seconds) done.
Oct 22 13:40:39 glasgow kernel: [  128.591505] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Oct 22 13:40:39 glasgow kernel: [  128.591608] PM: Entering mem sleep
Oct 22 13:40:39 glasgow kernel: [  128.591612] Suspending console(s)
Oct 22 13:40:39 glasgow kernel: [  128.675292] sd 2:0:0:0: [sda] Synchronizing SCSI cache
Oct 22 13:40:39 glasgow kernel: [  128.674963] sd 2:0:0:0: [sda] Stopping disk
Oct 22 13:40:39 glasgow kernel: [  129.047213] ACPI handle has no context!
Oct 22 13:40:39 glasgow kernel: [  129.047253] ACPI: PCI interrupt for device 0000:15:00.2 disabled
Oct 22 13:40:39 glasgow kernel: [  129.047264] ACPI handle has no context!
Oct 22 13:40:39 glasgow kernel: [  129.053735] ACPI handle has no context!
Oct 22 13:40:39 glasgow kernel: [  131.069147] NVRM: RmPowerManagement: 4
Oct 22 13:40:39 glasgow kernel: [  133.571980] wlan0: No ProbeResp from current AP 00:11:5c:e5:4f:a0 - assume out of range
Oct 22 13:40:39 glasgow kernel: [  134.562491] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Oct 22 13:40:39 glasgow kernel: [  134.562936] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Oct 22 13:40:39 glasgow kernel: [  134.569055] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Oct 22 13:40:39 glasgow kernel: [  134.569163] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Oct 22 13:40:39 glasgow kernel: [  134.569269] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Oct 22 13:40:39 glasgow kernel: [  134.572860] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Oct 22 13:40:39 glasgow kernel: [  134.576121] ACPI: PCI interrupt for device 0000:00:1a.7 disabled
Oct 22 13:40:39 glasgow kernel: [  134.581492] ACPI: PCI interrupt for device 0000:00:1a.1 disabled
Oct 22 13:40:39 glasgow kernel: [  134.581599] ACPI: PCI interrupt for device 0000:00:1a.0 disabled
Oct 22 13:40:39 glasgow kernel: [  134.623044] ACPI: PCI interrupt for device 0000:00:19.0 disabled
Oct 22 13:40:39 glasgow kernel: [  134.638548] Disabling non-boot CPUs ...
Oct 22 13:40:39 glasgow kernel: [  134.638573] CPU0 attaching NULL sched-domain.
Oct 22 13:40:39 glasgow kernel: [  134.638576] CPU1 attaching NULL sched-domain.
Oct 22 13:40:39 glasgow kernel: [  134.741400] CPU 1 is now offline
Oct 22 13:40:39 glasgow kernel: [  134.741404] SMP alternatives: switching to UP code
Oct 22 13:40:39 glasgow kernel: [  134.743183] CPU0 attaching sched-domain:
Oct 22 13:40:39 glasgow kernel: [  134.743187]  domain 0: span 01
Oct 22 13:40:39 glasgow kernel: [  134.743189]   groups: 01
Oct 22 13:40:39 glasgow kernel: [  134.743488] CPU1 is down
```

And the machine is suspended.  Slam the lid and open it again and this occurs:

```
Oct 22 13:40:39 glasgow kernel: [    0.271641] Back to C!
Oct 22 13:40:39 glasgow kernel: [    0.272082] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.272864] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.272900] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.272926] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.272955] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.272980] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273008] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273034] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273059] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273087] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273111] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273140] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273166] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273193] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273221] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273234] Enabling non-boot CPUs ...
Oct 22 13:40:39 glasgow kernel: [    0.273250] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273275] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273302] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273327] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273355] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273380] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273407] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273433] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273460] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273486] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273519] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273545] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273572] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273597] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273626] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273653] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273687] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273714] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273740] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273772] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273798] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273825] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273851] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273880] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273904] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273932] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273957] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.273985] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274011] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274038] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274068] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274092] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274119] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274144] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274171] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274196] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274223] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274248] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274276] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274301] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274328] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274353] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274380] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274406] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274433] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274458] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274490] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274520] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274545] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274571] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274597] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274624] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274649] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274683] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274709] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274734] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274758] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274783] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274810] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274835] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274863] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274887] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274914] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274939] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274966] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.274991] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275018] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275045] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275077] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275102] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275131] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275158] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275183] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275209] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275238] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275268] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275293] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275319] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275344] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275373] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275400] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275427] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275453] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275481] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275507] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275532] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275557] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275583] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275611] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275636] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275665] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275701] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275727] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275756] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275781] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275814] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275845] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275870] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275899] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275924] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275951] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.275976] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276002] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276027] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276054] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276080] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276107] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276132] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276161] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276191] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276217] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276245] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276271] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276298] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276323] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276352] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276377] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276406] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276431] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276463] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276488] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276515] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276540] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276569] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276595] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276628] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276654] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276667] CPU0 attaching NULL sched-domain.
Oct 22 13:40:39 glasgow kernel: [    0.276690] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276718] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276743] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276771] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276796] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276827] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276853] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276882] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276907] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276936] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276966] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.276991] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277018] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277044] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277071] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277096] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277125] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277149] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277180] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277205] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277233] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277258] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277290] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277316] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277344] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277373] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277401] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277427] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277455] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277480] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277512] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277537] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277565] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277594] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277623] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277647] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277681] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.277739] SMP alternatives: switching to SMP code
Oct 22 13:40:39 glasgow kernel: [    0.278452] Booting processor 1/1 eip 3000
Oct 22 13:40:39 glasgow kernel: [    0.289512] Initializing CPU#1
Oct 22 13:40:39 glasgow kernel: [    0.349113] Calibrating delay using timer specific routine.. 4389.34 BogoMIPS (lpj=2194674)
Oct 22 13:40:39 glasgow kernel: [    0.349119] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000001
Oct 22 13:40:39 glasgow kernel: [    0.349123] monitor/mwait feature present.
Oct 22 13:40:39 glasgow kernel: [    0.349126] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct 22 13:40:39 glasgow kernel: [    0.349127] CPU: L2 cache: 4096K
Oct 22 13:40:39 glasgow kernel: [    0.349129] CPU: Physical Processor ID: 0
Oct 22 13:40:39 glasgow kernel: [    0.349130] CPU: Processor Core ID: 1
Oct 22 13:40:39 glasgow kernel: [    0.349131] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e3bd 00000000 00000001 00000001
Oct 22 13:40:39 glasgow kernel: [    0.349274] CPU1: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping 0b
Oct 22 13:40:39 glasgow kernel: [    0.349354] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.349391] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.349423] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.349451] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.349481] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.349511] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.349539] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.349573] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.349617] CPU0 attaching sched-domain:
Oct 22 13:40:39 glasgow kernel: [    0.349619]  domain 0: span 03
Oct 22 13:40:39 glasgow kernel: [    0.349620]   groups: 01 02
Oct 22 13:40:39 glasgow kernel: [    0.349622] CPU1 attaching sched-domain:
Oct 22 13:40:39 glasgow kernel: [    0.349624]  domain 0: span 03
Oct 22 13:40:39 glasgow kernel: [    0.350154] ACPI Error (evgpe-0705): <7>  groups:No handler or method for GPE[ D], disabling event 02 [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.349628]  01
Oct 22 13:40:39 glasgow kernel: [    0.350188] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350218] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350246] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350278] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350308] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350337] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350376] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.349881] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.349914] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.349944] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.349975] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350005] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350035] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350064] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350098] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling eventCPU1 is up
Oct 22 13:40:39 glasgow kernel: [    0.350101]  [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350133] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350176] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350219] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350263] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350306] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350350] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350394] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350437] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350481] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350525] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350568] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351141] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351172] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351199] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351230] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351259] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351287] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351315] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351344] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351375] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350889] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350933] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350963] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.350992] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351031] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351075] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351119] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351163] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351206] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351250] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351294] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351338] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351381] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351425] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351468] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351512] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351555] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351608] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352171] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352201] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352229] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352257] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352292] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352321] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352349] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351870] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351913] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351957] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.351994] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352022] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352051] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352087] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352130] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352174] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352218] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352262] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352305] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352348] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352392] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352436] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352479] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352523] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.352562] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353137] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353168] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353198] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353229] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353258] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353290] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353318] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353349] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353388] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353418] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353446] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353479] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353507] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353536] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353564] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353594] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353623] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353655] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353682] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353710] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353739] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353766] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353795] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353822] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353853] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353881] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353912] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353940] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353969] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353998] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.354026] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.354056] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.354085] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.354119] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.354149] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.354177] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.354209] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.354238] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.354270] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.354298] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.354331] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.354367] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353870] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353898] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.353929] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
Oct 22 13:40:39 glasgow kernel: [    0.409426] PM: Writing back config space on device 0000:00:01.0 at offset 1 (was 100107, writing 100507)
Oct 22 13:40:39 glasgow kernel: [    0.409446] PCI: Setting latency timer of device 0000:00:01.0 to 64
Oct 22 13:40:39 glasgow kernel: [    0.419826] PM: Writing back config space on device 0000:00:19.0 at offset 1 (was 100107, writing 100507)
Oct 22 13:40:39 glasgow kernel: [    0.419869] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 20 (level, low) -> IRQ 17
Oct 22 13:40:39 glasgow kernel: [    0.419879] PCI: Setting latency timer of device 0000:00:19.0 to 64
Oct 22 13:40:39 glasgow kernel: [    0.496225] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 17
Oct 22 13:40:39 glasgow kernel: [    0.496235] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Oct 22 13:40:39 glasgow kernel: [    0.496322] usb usb1: root hub lost power or was reset
Oct 22 13:40:39 glasgow kernel: [    0.496346] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
Oct 22 13:40:39 glasgow kernel: [    0.496352] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Oct 22 13:40:39 glasgow kernel: [    0.496429] usb usb2: root hub lost power or was reset
Oct 22 13:40:39 glasgow kernel: [    0.507091] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 19
Oct 22 13:40:39 glasgow kernel: [    0.507099] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Oct 22 13:40:39 glasgow kernel: [    0.518026] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100106, writing 100102)
Oct 22 13:40:39 glasgow kernel: [    0.518097] ACPI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 21
Oct 22 13:40:39 glasgow kernel: [    0.518116] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Oct 22 13:40:39 glasgow kernel: [    0.518251] PM: Writing back config space on device 0000:00:1c.0 at offset 1 (was 100107, writing 100507)
Oct 22 13:40:39 glasgow kernel: [    0.518375] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Oct 22 13:40:39 glasgow kernel: [    0.518469] PM: Writing back config space on device 0000:00:1c.1 at offset 1 (was 100107, writing 100507)
Oct 22 13:40:39 glasgow kernel: [    0.518593] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Oct 22 13:40:39 glasgow kernel: [    0.518687] PM: Writing back config space on device 0000:00:1c.2 at offset 1 (was 100107, writing 100507)
Oct 22 13:40:39 glasgow kernel: [    0.518811] PCI: Setting latency timer of device 0000:00:1c.2 to 64
Oct 22 13:40:39 glasgow kernel: [    0.518906] PM: Writing back config space on device 0000:00:1c.3 at offset 1 (was 100107, writing 100507)
Oct 22 13:40:39 glasgow kernel: [    0.519030] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Oct 22 13:40:39 glasgow kernel: [    0.519124] PM: Writing back config space on device 0000:00:1c.4 at offset 1 (was 100107, writing 100507)
Oct 22 13:40:39 glasgow kernel: [    0.519267] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Oct 22 13:40:39 glasgow kernel: [    0.519288] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 22 13:40:39 glasgow kernel: [    0.519302] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Oct 22 13:40:39 glasgow kernel: [    0.519435] usb usb4: root hub lost power or was reset
Oct 22 13:40:39 glasgow kernel: [    0.519472] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 21
Oct 22 13:40:39 glasgow kernel: [    0.519486] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Oct 22 13:40:39 glasgow kernel: [    0.519617] usb usb5: root hub lost power or was reset
Oct 22 13:40:39 glasgow kernel: [    0.519650] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 22
Oct 22 13:40:39 glasgow kernel: [    0.519661] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Oct 22 13:40:39 glasgow kernel: [    0.519790] usb usb6: root hub lost power or was reset
Oct 22 13:40:39 glasgow kernel: [    0.531077] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 23
Oct 22 13:40:39 glasgow kernel: [    0.531092] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Oct 22 13:40:39 glasgow kernel: [    0.531378] PM: Writing back config space on device 0000:00:1e.0 at offset 1 (was 100005, writing 100007)
Oct 22 13:40:39 glasgow kernel: [    0.531443] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Oct 22 13:40:39 glasgow kernel: [    0.531657] PM: Writing back config space on device 0000:00:1f.1 at offset 1 (was 2800005, writing 2880005)
Oct 22 13:40:39 glasgow kernel: [    0.531687] ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 16
Oct 22 13:40:39 glasgow kernel: [    0.531701] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Oct 22 13:40:39 glasgow kernel: [    0.531836] ata2: port disabled. ignoring.
Oct 22 13:40:39 glasgow kernel: [    0.542999] PM: Writing back config space on device 0000:00:1f.2 at offset 1 (was 2b00007, writing 2b00407)
Oct 22 13:40:39 glasgow kernel: [    0.543155] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Oct 22 13:40:39 glasgow kernel: [    0.891944] ata1.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
Oct 22 13:40:39 glasgow kernel: [    0.891949] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Oct 22 13:40:39 glasgow kernel: [    0.893406] ata1.00: ACPI cmd e3/00:1f:00:00:00:a0 succeeded
Oct 22 13:40:39 glasgow kernel: [    0.894431] ata1.00: ACPI cmd e3/00:02:00:00:00:a0 succeeded
Oct 22 13:40:39 glasgow kernel: [    1.206360] ata1.00: configured for UDMA/33
Oct 22 13:40:39 glasgow kernel: [    1.542627] NVRM: RmPowerManagement: 5
Oct 22 13:40:39 glasgow kernel: [    1.844723] ata4: SATA link down (SStatus 0 SControl 0)
Oct 22 13:40:39 glasgow kernel: [    1.845527] ata5: SATA link down (SStatus 0 SControl 0)
Oct 22 13:40:39 glasgow kernel: [    1.998339] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct 22 13:40:39 glasgow kernel: [    1.999047] ata3.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
Oct 22 13:40:39 glasgow kernel: [    1.999049] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
Oct 22 13:40:39 glasgow kernel: [    1.999154] ata3.00: ACPI cmd ef/5f:00:00:00:00:a0 succeeded
Oct 22 13:40:39 glasgow kernel: [    1.999269] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 succeeded
Oct 22 13:40:39 glasgow kernel: [    2.000355] ata3.00: configured for UDMA/100
Oct 22 13:40:39 glasgow kernel: [    2.001453] ata3.00: configured for UDMA/100
Oct 22 13:40:39 glasgow kernel: [    2.012282] ata3: EH complete
Oct 22 13:40:39 glasgow kernel: [    2.012310] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Oct 22 13:40:39 glasgow kernel: [    2.012321] sd 2:0:0:0: [sda] Write Protect is off
Oct 22 13:40:39 glasgow kernel: [    2.012322] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 22 13:40:39 glasgow kernel: [    2.012337] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 22 13:40:39 glasgow kernel: [    2.012352] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Oct 22 13:40:39 glasgow kernel: [    2.012360] sd 2:0:0:0: [sda] Write Protect is off
Oct 22 13:40:39 glasgow kernel: [    2.012362] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 22 13:40:39 glasgow kernel: [    2.012375] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 22 13:40:39 glasgow kernel: [    3.073330] Coming out of suspend...
Oct 22 13:40:39 glasgow kernel: [    3.078305] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 100106, writing 100506)
Oct 22 13:40:39 glasgow kernel: [    3.150577] PM: Writing back config space on device 0000:15:00.1 at offset 4 (was 0, writing f8101000)
Oct 22 13:40:39 glasgow kernel: [    3.150583] PM: Writing back config space on device 0000:15:00.1 at offset 3 (was 800000, writing 804000)
Oct 22 13:40:39 glasgow kernel: [    3.150597] PM: Writing back config space on device 0000:15:00.1 at offset 1 (was 2100000, writing 2100006)
Oct 22 13:40:39 glasgow kernel: [    3.202780] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[f8101000-f81017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Oct 22 13:40:39 glasgow kernel: [    3.219997] PM: Writing back config space on device 0000:15:00.2 at offset 4 (was 0, writing f8101800)
Oct 22 13:40:39 glasgow kernel: [    3.220003] PM: Writing back config space on device 0000:15:00.2 at offset 3 (was 800000, writing 804000)
Oct 22 13:40:39 glasgow kernel: [    3.220009] PM: Writing back config space on device 0000:15:00.2 at offset 1 (was 2100000, writing 2100006)
Oct 22 13:40:39 glasgow kernel: [    3.220034] ACPI: PCI Interrupt 0000:15:00.2[C] -> GSI 18 (level, low) -> IRQ 22
Oct 22 13:40:39 glasgow kernel: [    3.610518] sd 2:0:0:0: [sda] Starting disk
Oct 22 13:40:39 glasgow kernel: [    4.527683] PM: Finishing wakeup.
Oct 22 13:40:39 glasgow kernel: [    4.527688] Restarting tasks ... <6>usb 1-2: USB disconnect, address 4
Oct 22 13:40:39 glasgow kernel: [    4.577946] NVRM: Xid (0001:00): 13, 0001 00000000 00005097 00000680 01170008 00000080
Oct 22 13:40:39 glasgow kernel: [    4.634877] NVRM: Xid (0001:00): 13, 0001 00000000 00005097 00000680 01170008 00000000
Oct 22 13:40:39 glasgow kernel: [    4.635565] done.
Oct 22 13:40:39 glasgow kernel: [    4.646565] usb 5-2: USB disconnect, address 3
Oct 22 13:40:39 glasgow kernel: [    4.701702] NVRM: Xid (0001:00): 36,  L0 -> L0
Oct 22 13:40:39 glasgow kernel: [    5.367614] usb 1-2: new full speed USB device using uhci_hcd and address 5
Oct 22 13:40:39 glasgow kernel: [    5.528050] usb 1-2: configuration #1 chosen from 1 choice
Oct 22 13:40:41 glasgow kernel: [    7.438995] usb 5-2: new full speed USB device using uhci_hcd and address 4
Oct 22 13:40:42 glasgow kernel: [    7.613876] usb 5-2: configuration #1 chosen from 1 choice
Oct 22 13:40:43 glasgow kernel: [    8.602784] NVRM: Xid (0001:00): 13, 0001 00000000 0000502d 00000208 00000020 00000100
Oct 22 13:40:43 glasgow kernel: [    8.630433] NVRM: Xid (0001:00): 13, 0001 00000000 0000502d 00000208 00000020 00000100
Oct 22 13:40:43 glasgow kernel: [    8.658372] NVRM: Xid (0001:00): 13, 0001 00000000 0000502d 00000208 00000020 00000100
Oct 22 13:40:43 glasgow kernel: [    8.686335] NVRM: Xid (0001:00): 13, 0001 00000000 0000502d 00000208 00000020 00000100
Oct 22 13:40:43 glasgow kernel: [    8.714367] NVRM: Xid (0001:00): 13, 0001 00000000 0000502d 00000208 00000020 00000100
Oct 22 13:41:02 glasgow kernel: [   28.354407] wlan0: No STA entry for own AP 00:11:5c:e5:4f:a0
```

And the machine is at that point left with a blank screen, an occasional flicker on the hard disk activity light, and an unresponsive keyboard.  Powercycling the T61 is the only recovery option.

---

### Post by mrz80 on 2008-11-05
It gets even better.  I can stop acpid and *still* I get random suspends.

---

