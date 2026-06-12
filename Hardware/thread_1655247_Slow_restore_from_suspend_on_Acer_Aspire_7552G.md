---
title: "Slow restore from suspend on Acer Aspire 7552G"
date: 2010-12-29
forum: Hardware
---

### Post by spencercarran on 2010-12-29
I just got a new Acer Aspire 7552G and the first thing I did was install Ubuntu 10.10 x64 on it. Everything works out of the box (I'm using the fglrx driver for the ATI graphics card) but it takes 5 minutes to resume from suspend, and coming back from hibernate is even worse. Any ideas on why, or how to fix it?

---

### Post by ialdobaeth on 2011-02-25
I have the same machine.  After spending way too many hours troubleshooting this problem, I've at least managed to get the wireless restored when the darn thing wakes.

Nothing all that interesting in /var/log/messages or /var/log/pm-suspend.log.  Between the time that the machine suspends and when it finishes its 5 minute restore process, nothing is written to either log.  When the system first tries to restore, the hard drive indicator flashes quickly, then remains dark throughout the 5 or so minutes it takes to come up again (which is completely consistent with what's being seen in the logs). 

Obligatory include from /var/log/pm-suspend.log:

> 
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Fri Feb 25 13:32:58 PST 2011: performing suspend
Switching from vt7 to vt1
switching back to vt7
Fri Feb 25 13:38:12 PST 2011: Awake.
Fri Feb 25 13:38:12 PST 2011: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


Note that in the above log snippet, I started to wake the system at 13:33:something. 


And /var/log/messages

```

Feb 25 13:32:58 thebrokenworld kernel: [   68.800574] ath9k 0000:06:00.0: PCI INT A disabled
Feb 25 13:32:58 thebrokenworld kernel: [   68.800602] ath9k: Driver unloaded
Feb 25 13:38:12 thebrokenworld kernel: [   70.692365] PM: Syncing filesystems ... done.
Feb 25 13:38:12 thebrokenworld kernel: [   70.732124] Freezing user space processes ... (elapsed 0.01 seconds) done.
Feb 25 13:38:12 thebrokenworld kernel: [   70.750139] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
Feb 25 13:38:12 thebrokenworld kernel: [   70.770155] Suspending console(s) (use no_console_suspend to debug)
Feb 25 13:38:12 thebrokenworld kernel: [   70.770445] sd 2:0:0:0: [sda] Synchronizing SCSI cache
Feb 25 13:38:12 thebrokenworld kernel: [   70.836486] [fglrx] IRQ 46 Disabled
Feb 25 13:38:12 thebrokenworld kernel: [   70.836493] ohci_hcd 0000:00:13.0: PCI INT A disabled
Feb 25 13:38:12 thebrokenworld kernel: [   70.836522] [fglrx] Preparing suspend fglrx in kernel.
Feb 25 13:38:12 thebrokenworld kernel: [   70.836527] ohci_hcd 0000:00:12.0: PCI INT A disabled
Feb 25 13:38:12 thebrokenworld kernel: [   70.850094] ehci_hcd 0000:00:12.2: PCI INT B disabled
Feb 25 13:38:12 thebrokenworld kernel: [   70.850124] ehci_hcd 0000:00:13.2: PCI INT B disabled
Feb 25 13:38:12 thebrokenworld kernel: [   70.872903] sd 2:0:0:0: [sda] Stopping disk
Feb 25 13:38:12 thebrokenworld kernel: [   70.940088] HDA Intel 0000:02:00.1: PCI INT B disabled
Feb 25 13:38:12 thebrokenworld kernel: [   70.940958] HDA Intel 0000:00:14.2: PCI INT A disabled
Feb 25 13:38:12 thebrokenworld kernel: [   71.177532] [fglrx] Suspending fglrx in kernel completed.
Feb 25 13:38:12 thebrokenworld kernel: [   71.177536] [fglrx] Power down the ASIC .
Feb 25 13:38:12 thebrokenworld kernel: [   71.500318] PM: suspend of devices complete after 729.996 msecs
Feb 25 13:38:12 thebrokenworld kernel: [   71.500322] PM: suspend devices took 0.730 seconds
Feb 25 13:38:12 thebrokenworld kernel: [   71.540178] PM: late suspend of devices complete after 39.849 msecs
Feb 25 13:38:12 thebrokenworld kernel: [   71.540224] ACPI: Preparing to enter system sleep state S3
Feb 25 13:38:12 thebrokenworld kernel: [   71.890308] PM: Saving platform NVS memory
Feb 25 13:38:12 thebrokenworld kernel: [   71.890411] Disabling non-boot CPUs ...
Feb 25 13:38:12 thebrokenworld kernel: [   71.900324] Broke affinity for irq 9
Feb 25 13:38:12 thebrokenworld kernel: [   71.900357] Broke affinity for irq 43
Feb 25 13:38:12 thebrokenworld kernel: [   72.010115] CPU 1 is now offline
Feb 25 13:38:12 thebrokenworld kernel: [   72.090274] Broke affinity for irq 12
Feb 25 13:38:12 thebrokenworld kernel: [   72.200085] CPU 2 is now offline
Feb 25 13:38:12 thebrokenworld kernel: [   72.230207] Broke affinity for irq 46
Feb 25 13:38:12 thebrokenworld kernel: [   72.340109] CPU 3 is now offline
Feb 25 13:38:12 thebrokenworld kernel: [   72.340112] SMP alternatives: switching to UP code
Feb 25 13:38:12 thebrokenworld kernel: [   72.345002] Extended CMOS year: 2000
Feb 25 13:38:12 thebrokenworld kernel: [   72.345002] PM: Restoring platform NVS memory
Feb 25 13:38:12 thebrokenworld kernel: [   72.345002] PCI-DMA: Resuming GART IOMMU
Feb 25 13:38:12 thebrokenworld kernel: [   72.345002] PCI-DMA: Restoring GART aperture settings
Feb 25 13:38:12 thebrokenworld kernel: [   72.345002] Extended CMOS year: 2000
Feb 25 13:38:12 thebrokenworld kernel: [   72.345002] Enabling non-boot CPUs ...
Feb 25 13:38:12 thebrokenworld kernel: [   72.345002] SMP alternatives: switching to SMP code
Feb 25 13:38:12 thebrokenworld kernel: [   72.345002] Booting Node 0 Processor 1 APIC 0x1
Feb 25 13:38:12 thebrokenworld kernel: [   72.010210] Switch to broadcast mode on CPU1
Feb 25 13:38:12 thebrokenworld kernel: [  372.338974] Clocksource tsc unstable (delta = 7879047227 ns)
Feb 25 13:38:12 thebrokenworld kernel: [  372.339046] Switching to clocksource hpet
Feb 25 13:38:12 thebrokenworld kernel: [  372.380508] CPU1 is up
Feb 25 13:38:12 thebrokenworld kernel: [  372.380637] Booting Node 0 Processor 2 APIC 0x2
Feb 25 13:38:12 thebrokenworld kernel: [   72.200170] Switch to broadcast mode on CPU2
Feb 25 13:38:12 thebrokenworld kernel: [  372.650610] CPU2 is up
Feb 25 13:38:12 thebrokenworld kernel: [  372.650807] Booting Node 0 Processor 3 APIC 0x3
Feb 25 13:38:12 thebrokenworld kernel: [   72.344674] Switch to broadcast mode on CPU3
Feb 25 13:38:12 thebrokenworld kernel: [  372.950647] CPU3 is up
Feb 25 13:38:12 thebrokenworld kernel: [  372.950998] ACPI: Waking up from system sleep state S3
Feb 25 13:38:12 thebrokenworld kernel: [  373.610136] ehci_hcd 0000:00:12.2: BAR 0: set to [mem 0xd0506000-0xd05060ff] (PCI address [0xd0506000-0xd05060ff]
Feb 25 13:38:12 thebrokenworld kernel: [  373.630136] ehci_hcd 0000:00:13.2: BAR 0: set to [mem 0xd0506400-0xd05064ff] (PCI address [0xd0506400-0xd05064ff]
Feb 25 13:38:12 thebrokenworld kernel: [  373.630645] PM: early resume of devices complete after 40.107 msecs
Feb 25 13:38:12 thebrokenworld kernel: [  373.630804] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb 25 13:38:12 thebrokenworld kernel: [  373.630841] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb 25 13:38:12 thebrokenworld kernel: [  373.630965] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb 25 13:38:12 thebrokenworld kernel: [  373.631039] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb 25 13:38:12 thebrokenworld kernel: [  373.631161] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 25 13:38:12 thebrokenworld kernel: [  373.631385] HDA Intel 0000:02:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Feb 25 13:38:12 thebrokenworld kernel: [  373.632120] sd 2:0:0:0: [sda] Starting disk
Feb 25 13:38:12 thebrokenworld kernel: [  373.636301] [fglrx] Power up the ASIC
Feb 25 13:38:12 thebrokenworld kernel: [  373.636342] [fglrx] Preparing resume fglrx in kernel.
Feb 25 13:38:12 thebrokenworld kernel: [  373.652237] [fglrx] Resuming fglrx in kernel completed.
Feb 25 13:38:12 thebrokenworld kernel: [  373.652508] [fglrx] IRQ 46 Enabled
Feb 25 13:38:12 thebrokenworld kernel: [  373.890148] usb 2-5: reset high speed USB device using ehci_hcd and address 2
Feb 25 13:38:12 thebrokenworld kernel: [  374.160142] usb 1-5: reset high speed USB device using ehci_hcd and address 2
Feb 25 13:38:12 thebrokenworld kernel: [  374.190131] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Feb 25 13:38:12 thebrokenworld kernel: [  374.190144] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 25 13:38:12 thebrokenworld kernel: [  374.223938] ata4.00: configured for UDMA/100
Feb 25 13:38:12 thebrokenworld kernel: [  375.811077] tg3 0000:03:00.0: eth0: Link is down
Feb 25 13:38:12 thebrokenworld kernel: [  377.737205] ata3.00: configured for UDMA/133
Feb 25 13:38:12 thebrokenworld kernel: [  377.758251] PM: resume of devices complete after 4127.576 msecs
Feb 25 13:38:12 thebrokenworld kernel: [  377.758451] PM: resume devices took 4.120 seconds
Feb 25 13:38:12 thebrokenworld kernel: [  377.758485] Restarting tasks ... done.
Feb 25 13:38:12 thebrokenworld kernel: [  377.782791] video LNXVIDEO:00: Restoring backlight state
Feb 25 13:38:12 thebrokenworld kernel: [  377.870105] cfg80211: Calling CRDA to update world regulatory domain
Feb 25 13:38:12 thebrokenworld kernel: [  377.883914] cfg80211: World regulatory domain updated:

```

Now that I look closer, it looks a lot like it's trying to go to sleep while it's waking up...

---

### Post by Hemiptera on 2011-02-26
To speed things up try adding "nohz=off highres=off" to the GRUB_CMDLINE_LINUX_DEFAULT variable in /etc/default/grub

then run update-grub and reboot.  If that doesn't work then add "nomemset" and try again.

How did you get the wireless to work on resume?

---

### Post by ialdobaeth on 2011-02-26
> **Hemiptera said:**
> To speed things up try adding "nohz=off highres=off" to the GRUB_CMDLINE_LINUX_DEFAULT variable in /etc/default/grub

then run update-grub and reboot.

That definitely solved the speed issue.  It makes troubleshooting all these suspend problems that much easier (at least I don't have to wait 5 minutes between attempts now).

Unfortunately, now I can't get wireless to come up after restore.  I had done so by adding SUSPEND_MODULES="ath9k"  to /etc/pm/config.d/00sleep_module and then running sudo modprobe ath9k on restore.  That doesn't seem to be working now...

As a side note, network-manager doesn't enable wireless on boot.  I have to manually enable wireless on every boot.  I'm not completely certain, but I have a feeling the issues are related...

---

### Post by ianmac on 2011-03-08
> **ialdobaeth said:**
> That definitely solved the speed issue.  It makes troubleshooting all these suspend problems that much easier (at least I don't have to wait 5 minutes between attempts now).

Unfortunately, now I can't get wireless to come up after restore.  I had done so by adding SUSPEND_MODULES="ath9k"  to /etc/pm/config.d/00sleep_module and then running sudo modprobe ath9k on restore.  That doesn't seem to be working now...

As a side note, network-manager doesn't enable wireless on boot.  I have to manually enable wireless on every boot.  I'm not completely certain, but I have a feeling the issues are related...

This also solved speed issues here.  Thanks for the tip.  Now to figure our the wireless issues - manually starting it is a pain.

Ian

---

### Post by spencercarran on 2011-03-21
> **ialdobaeth said:**
> That definitely solved the speed issue.  It makes troubleshooting all these suspend problems that much easier (at least I don't have to wait 5 minutes between attempts now).

Unfortunately, now I can't get wireless to come up after restore.  I had done so by adding SUSPEND_MODULES="ath9k"  to /etc/pm/config.d/00sleep_module and then running sudo modprobe ath9k on restore.  That doesn't seem to be working now...

As a side note, network-manager doesn't enable wireless on boot.  I have to manually enable wireless on every boot.  I'm not completely certain, but I have a feeling the issues are related...

I actually never had the wireless failing on resume- everything would work fine, it would just take forever. I had the same issue of having to manually enable wireless in network-manager. However, ever since the recent upgrade of network-manager, it is saying that "wireless is disabled" and ignores my attempts to enable it.

---

### Post by ialdobaeth on 2011-03-21
I haven't had a network-manager problem other than the aforementioned problem with wifi being disabled on resume.  However, I just managed to fix that ("fix" may be too strong of a word right now) upon resume with:

```
sudo rfkill unblock wifi
```

I've put this computer to sleep and resumed four times now and still have wifi!

---

