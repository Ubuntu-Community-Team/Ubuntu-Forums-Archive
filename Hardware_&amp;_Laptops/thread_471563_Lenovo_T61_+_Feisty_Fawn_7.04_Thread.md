---
title: "Lenovo T61 + Feisty Fawn 7.04 Thread"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by manioc on 2007-06-12
OK... so I finally got 7.04 installed and running on the T61.  I want to start a thread addressing all the compatibility issues.  It would be nice if all yall who own the T61 contribute to this thread.  Thinkwiki's Ubuntu 7.04 section is pretty much empty.
[SIZE="4"]
**_What works well_**[/SIZE]
Pointing devices (Trackpoint, Trackpad)
NVidia NVS 140M after installing latest drivers (100.14.09)
Gigabit Ethernet Adapter
Battery charge monitor (although it takes like 30 seconds for the icon to update)
USB Ports
Sound card after compiling the latest build of ALSA using hda-intel drivers instead of AD1984 (thanks awry)

[SIZE="4"]**_What sorta works_**[/SIZE]
For me, it takes gnome forever to load because of a problem with gnome-settings-daemon.  I keep on getting this error:
[INDENT]"Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."[/INDENT]
Does anyone else have this problem?

Also, I haven't had a successful attempt resuming from hibernation or suspension so far... I've only tried twice but nevertheless it shouldn't crash at all.

[SIZE="4"]**_What doesn't work_**[/SIZE]
_DVD/CD Multi-burner_: for some reason after I upgraded from 6.10 /dev/cdrom went missing.  I believe it's because 2.6.20 is using the experimental SATA AHCI drivers.
_LCD Brightness Adjustment_: Can't adjust the brightness of the LCD screen.  The meter pops up but the actual brightness doesn't change at all.  99% of the time the screen run at the highest brightness level and once in awhile the lowest.
_Volume adjustment buttons doesn't work_
_Turbo Memory_: Shows up as unknown device.[SIZE="4"]
_4965AGN WiFi_: modprobe ndiswrapper causes a generic protection fault and latest iwlwifi (0.32) didn't work for me either
**_To be determined_**[/SIZE]
_X3100_
_ThnkPad 11a/b/g_
_ThnkPad 11a/b/g/n_
_Bluetooth_: bluetooth light comes on so I guess it works.  I don't have any bluetooth devices to test with.
_Firewire_
_Fingerprint reader_: It does show up under device manager as a PnP device I believe.  Gonna mess with [bioapi]("http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader") later this week.
_TPM Chip_
_CardBus Slot_
_ExpressCard Slot_
_SmartCard Reader_
_Memory Card Reader_
_Active HDD Protection System_


Let me know if I'm missing something or if I'm wrong about anything.

---

### Post by dj_unforgetable on 2007-06-12
Did you use the 64bit version?  What options did you have to add to get this to work ?

---

### Post by manioc on 2007-06-12
Yes I'm running the 64 bit version.  I was never able to boot the 7.04 LiveCDs.  It seems like the kernel doesn't load the SATA drivers correctly.  So I installed 6.10 and then did an upgrade.

---

### Post by manioc on 2007-06-12
This is what happens when I installed the 64 bit version of V11.1.1.0 of the Intel driver using ndiswrapper 1.46.  Those of you who got it to work... did you use 1.45?  Gonna try the open intel drivers now even though I hear it doesn't work.

[  217.224096] ndiswrapper version 1.46 loaded (smp=yes)
[  217.355916] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  217.355941] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  217.355964] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  217.355984] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  217.355998] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  217.356012] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  217.356026] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  217.356045] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[  217.356066] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[  217.356081] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[  217.356095] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[  217.356140] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  217.356154] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[  217.356168] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  217.356212] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  217.356238] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  217.356252] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[  217.356265] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[  217.356279] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[  217.356293] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  217.356306] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  217.356320] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  217.356334] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[  217.356348] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[  217.356362] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  217.356377] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[  217.356391] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  217.356404] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  217.356418] ndiswrapper (load_sys_files:216): couldn't prepare driver 'netw4v64'
[  217.357634] ndiswrapper (load_wrap_driver:118): couldn't load driver netw4v64; check system log for messages from 'loadndisdriver'

---

### Post by manioc on 2007-06-13
Oops... downloaded Vista drivers... not XP drivers... gonna try again.

---

### Post by manioc on 2007-06-13
No goose =[.  1st modprobe attempt froze the system... 2nd attempt...

[  288.905198] ndiswrapper version 1.46 loaded (smp=yes)
[  289.149551] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
[  289.165299] ndiswrapper: driver netw4x64 (Intel,04/30/2007,11.1.1.11) loaded
[  289.166115] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[  289.166309] ndiswrapper (NdisWriteErrorLogEntry:192): log: 40001B7C, count: 2, return_address: ffffffff88be916e
[  289.166318] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x56524457
[  289.166323] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xdd
[  289.166363] general protection fault: 0000 [1] SMP 
[  289.166369] CPU 1 
[  289.166373] Modules linked in: ndiswrapper binfmt_misc rfcomm l2cap nvram uinput ppdev acpi_cpufreq cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative tc1100_wmi pcc_acpi dev_acpi sony_acpi video sbs ibm_acpi i2c_ec dock button battery container ac asus_acpi backlight ipv6 fuse sbp2 parport_pc lp parport joydev snd_hda_intel snd_hda_codec snd_pcm_oss snd_pcm snd_mixer_oss snd_seq_dummy snd_seq_oss pcmcia snd_seq_midi snd_rawmidi snd_seq_midi_event af_packet snd_seq snd_timer snd_seq_device psmouse hci_usb pcspkr bluetooth serio_raw nvidia(P) i2c_core yenta_socket rsrc_nonstatic pcmcia_core snd soundcore snd_page_alloc intel_agp shpchp pci_hotplug tsdev evdev ext3 jbd mbcache sg sd_mod ata_generic ehci_hcd ahci ohci1394 libata scsi_mod ieee1394 generic uhci_hcd usbcore e1000 thermal processor fan capability commoncap vesafb cfbcopyarea cfbimgblt cfbfillrect fbcon tileblit font bitblit softcursor
[  289.166508] Pid: 6464, comm: modprobe Tainted: P      2.6.20-16-generic #2
[  289.166514] RIP: 0010:[<ffffc200039f85b9>]  [<ffffc200039f85b9>]
[  289.166524] RSP: 0018:ffff8100607cd670  EFLAGS: 00010202
[  289.166531] RAX: 1d98df468e2b878f RBX: ffff8100607cd980 RCX: ffffc20003cce9e1
[  289.166536] RDX: 0000000000000000 RSI: ffff810067040c00 RDI: 0000000000000001
[  289.166542] RBP: ffff8100607cd988 R08: 0000000000000000 R09: 0000000000000000
[  289.166547] R10: 0000000000000000 R11: 0000000000000006 R12: 0000000000000001
[  289.166552] R13: ffff810067040c00 R14: 0000000000000000 R15: 0000000000000000
[  289.166559] FS:  00002b08fd8a66f0(0000) GS:ffff81000133a2c0(0000) knlGS:0000000000000000
[  289.166566] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  289.166572] CR2: 00002ad6554d7550 CR3: 000000006d075000 CR4: 00000000000006e0
[  289.166579] Process modprobe (pid: 6464, threadinfo ffff8100607cc000, task ffff81005f1a8100)
[  289.166583] Stack:  ffff8100633e8e00 ffffffff88128f74 ffff810037ad60e8 0000000000000001
[  289.166595]  0000000000000001 ffffc200039f7657 ffff8100607cd980 ffff810067040c00
[  289.166606]  ffffffff805e157d 0000000000000000 00000000000000dd 383220205b3e363c
[  289.166614] Call Trace:
[  289.166649]  [<ffffffff88128f74>] :libata:ata_scsi_rw_xlat+0x144/0x1e0
[  289.166694]  [<ffffffff88123ed7>] :libata:ata_qc_issue+0x427/0x4c0
[  289.166722]  [<ffffffff88128f74>] :libata:ata_scsi_rw_xlat+0x144/0x1e0
[  289.166742]  [<ffffffff80265bbb>] thread_return+0x0/0xf5
[  289.166771]  [<ffffffff803c3a19>] pci_conf1_read+0xd9/0x100
[  289.166789]  [<ffffffff8028e13c>] __cond_resched+0x1c/0x50
[  289.166797]  [<ffffffff80265cde>] cond_resched+0x2e/0x40
[  289.166807]  [<ffffffff802d3c28>] kmem_cache_zalloc+0xd8/0x100
[  289.166823]  [<ffffffff802951dd>] __request_region+0x7d/0xd0
[  289.166875]  [<ffffffff88be906b>] :ndiswrapper:win2lin3+0x11/0x14
[  289.166922]  [<ffffffff88bdf1d5>] :ndiswrapper:IofCompleteRequest+0xa5/0x160
[  289.166969]  [<ffffffff88bdf178>] :ndiswrapper:IofCompleteRequest+0x48/0x160
[  289.167020]  [<ffffffff88be0ce3>] :ndiswrapper:pdoDispatchPnp+0x433/0x450
[  289.167072]  [<ffffffff88be9057>] :ndiswrapper:win2lin2+0xe/0x11
[  289.167119]  [<ffffffff88bde93b>] :ndiswrapper:IofCallDriver+0x8b/0xc0
[  289.167172]  [<ffffffff88be4b47>] :ndiswrapper:mp_init+0xa7/0x190
[  289.167218]  [<ffffffff88bdfd30>] :ndiswrapper:IoSyncForwardIrp+0x90/0xd0
[  289.167271]  [<ffffffff88be523b>] :ndiswrapper:NdisDispatchPnp+0xab/0xcb0
[  289.167282]  [<ffffffff80265bbb>] thread_return+0x0/0xf5
[  289.167351]  [<ffffffff88bdf3ab>] :ndiswrapper:IoInitializeIrp+0x3b/0x70
[  289.167409]  [<ffffffff88be9057>] :ndiswrapper:win2lin2+0xe/0x11
[  289.167455]  [<ffffffff88bde93b>] :ndiswrapper:IofCallDriver+0x8b/0xc0
[  289.167502]  [<ffffffff88bde910>] :ndiswrapper:IofCallDriver+0x60/0xc0
[  289.167546]  [<ffffffff88bdf88f>] :ndiswrapper:IoBuildSynchronousFsdRequest+0x2f/0x50
[  289.167595]  [<ffffffff88be0dec>] :ndiswrapper:IoSendIrpTopDev+0xac/0x100
[  289.167658]  [<ffffffff88be10df>] :ndiswrapper:pnp_start_device+0x4f/0xb0
[  289.167719]  [<ffffffff88be134b>] :ndiswrapper:wrap_pnp_start_device+0x20b/0x250
[  289.167780]  [<ffffffff88be13e0>] :ndiswrapper:wrap_pnp_start_pci_device+0x50/0x60
[  289.167795]  [<ffffffff80309fd9>] sysfs_make_dirent+0x29/0xb0
[  289.167815]  [<ffffffff8034d3f1>] pci_device_probe+0xe1/0x170
[  289.167833]  [<ffffffff803a6ae5>] really_probe+0xe5/0x190
[  289.167847]  [<ffffffff803a6dbc>] __driver_attach+0x7c/0xd0
[  289.167858]  [<ffffffff803a6d40>] __driver_attach+0x0/0xd0
[  289.167866]  [<ffffffff803a5d39>] bus_for_each_dev+0x49/0x80
[  289.167886]  [<ffffffff803a613e>] bus_add_driver+0x7e/0x1e0
[  289.167899]  [<ffffffff8034d6a7>] __pci_register_driver+0x87/0xd0
[  289.167937]  [<ffffffff88bd53ec>] :ndiswrapper:loader_init+0x15c/0x250
[  289.167968]  [<ffffffff8809207e>] :ndiswrapper:wrapper_init+0x7e/0xb6
[  289.167979]  [<ffffffff802ac375>] sys_init_module+0x1905/0x1ab0
[  289.168014]  [<ffffffff802315a1>] __up_write+0x21/0x130
[  289.168042]  [<ffffffff8026111e>] system_call+0x7e/0x83
[  289.168065] 
[  289.168068] 
[  289.168069] Code: 83 80 30 04 00 00 01 48 8b 5c 24 30 48 8b 74 24 38 48 83 c4 
[  289.168093] RIP  [<ffffc200039f85b9>]
[  289.168101]  RSP <ffff8100607cd670>
[  289.168105]

---

### Post by syxbit on 2007-06-13
this thread is a great idea
i ordered a T61 with nvidia and intel 4965.
b/c of major shipping issues, i don't know when i'll get it.
once it arrives, i'll help out.
until then, the more you post, the easier it'll be for me once i get it :)
2 suggestions.
you might have better luck with the 32bit version, and how about trying either Fedora 7 (for the newer kernel) or Gutsy (with 2.6.22) the newer kernels may fix some daemon problems you're having

---

### Post by raabobank on 2007-06-13
hi guys,

complete and utter linux newb here - waiting for my T61 to arrive.
was planning to throw out Vista at once and start using Ubuntu.
from reading on here and a few other places I understand it is not quite that easy, with the new Thinkpad build and all.
question I have is; how long do you reckon it will be, untill things settle down and I can read a newb install guide that works well with the hardware ?

no intention of hijacking the thread here ;)

---

### Post by wesleygriffin on 2007-06-14
Here's my report:

I managed to get the Fiesty LiveCD to install by setting the SATA mode to Compatible in the BIOS screen, so I *think* that means I'm running the 32bit version, but I'm not very Linux savvy, so I'm not 100% positive.

Brightness does not work for me either. The Intel XP drivers via NDIS do work, but its somewhat flaky. I've been turning the radio on and off and disabling/re-enabling networking to get it to work. Once I get it running, however, its happy.

I have not tried suspend/resume/lid closing. My bluetooth light comes on as well, but I haven't done anything with it. The CD/DVD works fine for me, but I haven't tried writing anything yet, just reading.

I also have the dock, and that works without issues. External video via the dock works fine as well. I have not tried external video via the laptop or more than a single screen (I was using the laptop docked with the lid closed).

I am having an issue with the NVIDIA drivers, where when I boot, X doesn't start, complaining on the NVIDIA module. I have to log on via console, 'rmmod nvidia' and 'modprobe nvidia' and then X starts fine. Not sure what's going on there, but if anyone can point me at a possible fix that would be great.

Also, as a general Ubuntu/Gnome question, is there any way to change the password on my default keyring? Gnome-keyring-manager doesn't seem to offer much feature-wise.

Thanks,
Wes

---

### Post by shadowarts on 2007-06-16
I managed to get it Feisty running on my T61 as well, i put up some of my notes at:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61)

Feel free to add more things to that page if you have anything to share.

Hopefully some of it may be helpful.  Has anyone had success getting the sound to work yet?  I upgraded to ALSA 1.0.14 but no luck yet.

---

### Post by syxbit on 2007-06-16
i hear there's a new wireless stack available in kernel 2.6.22
you should try out gutsy
at least the liveCD to see if that improves stuff.
i should have mine early next week, and i'm not looking forward to all this work
don't really want to have to use vista though, so i'll have to troubleshoot :)

---

### Post by awry on 2007-06-17
I just got a new T61, as well.

I got the IBM a/b/g wireless, which works out-of-the-box w/ madwifi drivers.

I managed to get sound working by installing the current development version of alsa - see here: [http://alsa.opensrc.org/index.php/AlsaCVS](http://alsa.opensrc.org/index.php/AlsaCVS)

I still have a problem with nvidia, like someone earlier mentioned.  When I reboot, kdm refuses to start.  I have to remove the nvidia module from the kernel, then reinsert it, then restart kdm.  Maybe something is getting loaded out of order?

Other than that, things seem to be rolling pretty smoothly now that I have sound!

---

### Post by syxbit on 2007-06-17
awry, could you post the settings you used for alsa
which card module
that way, i can worry about getting other things to work.

did you use the envy script to install the latest nvidia driver?

---

### Post by manioc on 2007-06-17
Wes,

Can you paste your dmesg and your modprobe config file so I can figure out how to get my CD/DVD multiwriter to work?  Thanks

---

### Post by manioc on 2007-06-17
syxbit,

I'm already pissed off that the T61 was shipped with the 32 bit version of Vista so no matter what I'm determined to be running a 64 bit OS one way or another.  Vista takes forever to boot even with the Turbo Memory.

---

### Post by syxbit on 2007-06-19
i installed Feisty alternate 32bit, gutsy alternate tribe 1 and Fedora 7
neither one worked
Ubuntu installed, but it would give a blank screen on first boot, and fedora gave a blank screen during installation

i really want to put linux on here, and can't stand vista

any ideas?

---

### Post by awry on 2007-06-20
syxbit,

The alsa module is hda-intel.

Once you get the current source tree via rsync, you basically want to do this:

```
cd alsa-driver
./cvscompile --with-cards=hda-intel
sudo make install

cd ../alsa-lib
./cvscompile
sudo make install

cd ../alsa-util
./cvscompile
sudo make install

sudo reboot
```

You need to have the kernel headers (maybe source too), and a bunch of dev packages, like automake, gettext, etc.  There's a README in each folder that also tells you all the commands to run to try to build manually in case the cvscompile script fails.

Good luck!

---

### Post by awry on 2007-06-20
Is anyone else getting IRQ errors from the kernel?

For awhile, I would get random IRQ 16 errors that would render the nvidia card on that interrupt unusable.  I discovered that adding pci=nommconf generally fixed this.  I still get IRQ errors on IRQ 23 though, which appears to be the EHCI (USB2) controller:

```
dmesg:

[  496.076000] irq 23: nobody cared (try booting with the "irqpoll" option)
[  496.076000]  [<c01543a4>] __report_bad_irq+0x24/0x80
[  496.076000]  [<c015465e>] note_interrupt+0x25e/0x290
[  496.076000]  [<f88b7f32>] usb_hcd_irq+0x22/0x60 [usbcore]
[  496.076000]  [<c01538d0>] handle_IRQ_event+0x30/0x60
[  496.076000]  [<c0154f91>] handle_fasteoi_irq+0xc1/0xf0
[  496.076000]  [<c0105b70>] do_IRQ+0x40/0x80
[  496.076000]  [<f8c49f04>] zz002daf00+0x90/0x220 [ath_hal]
[  496.076000]  [<c0104233>] common_interrupt+0x23/0x30
[  496.076000]  [<f8874e73>] uhci_irq+0x23/0x170 [uhci_hcd]
[  496.076000]  [<f889a266>] ehci_irq+0x26/0x170 [ehci_hcd]
[  496.076000]  [<f88b7f32>] usb_hcd_irq+0x22/0x60 [usbcore]
[  496.076000]  [<c01538d0>] handle_IRQ_event+0x30/0x60
[  496.076000]  [<c0154f4b>] handle_fasteoi_irq+0x7b/0xf0
[  496.076000]  [<c0105b70>] do_IRQ+0x40/0x80
[  496.076000]  [<c0219e3e>] acpi_hw_register_write+0x154/0x187
[  496.076000]  [<c0104233>] common_interrupt+0x23/0x30
[  496.076000]  [<f88537e2>] acpi_processor_idle+0x225/0x3f7 [processor]
[  496.076000]  [<c0101409>] cpu_idle+0x49/0xd0
[  496.076000]  [<c03d97f5>] start_kernel+0x365/0x420
[  496.076000]  [<c03d9230>] unknown_bootoption+0x0/0x260
[  496.076000]  =======================
[  496.076000] handlers:
[  496.076000] [<f88b7f10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  496.076000] Disabling IRQ #23

lspci -v:

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev
 03) (prog-if 20 [EHCI])
        Subsystem: Lenovo Unknown device 20ab
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at fe227000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

```

It seems like adding irqpoll to the kernel opts helps, but the startup performance with irqpoll activated is abysmal, and the kernel itself warns that it's bad for performance.  :(

I've tried a bunch of different kernels now... stock 2.6.20-6-generic, 2.6.21.5, 2.6.22-rc5... all three have some IRQ problem or another.  

Can anyone else confirm?  BIOS problem?  Suggestions?

---

### Post by awry on 2007-06-20
When in X, I am unable to control screen brightness via Fn+Home/Fn+End.  This works fine, incidentally, as long as X isn't started and running.  

As a workaround, I can switch to tty, adjust the brightness there, and then switch back to X.  Sometimes this causes the nvidia driver to crash.

Any ideas?

---

### Post by syxbit on 2007-06-21
are you all running with SATA on compatability (instead of AHCI) ??
cause i still can't get it to boot up even once after installation
i've now tried Feist 32 and 64bit, gusty tribe 1 32 and 64bit and fedora 32bit
first boot just hangs

---

### Post by chem on 2007-06-21
Has anyone with a T61 been able to get Suspend and Suspend2Disk working properly?   If so, how?  Thanks!

---

### Post by syxbit on 2007-06-22
could someone post some hints on getting it to actually boot up?
surely you guys had to do something to get it even booting up.

---

### Post by trivialnobvious on 2007-06-23
> **syxbit said:**
> could someone post some hints on getting it to actually boot up?
surely you guys had to do something to get it even booting up.

I'm in the same position as you. Fresh out of the box, trying to get Ubuntu going but I can't get the installer to run. I just get shot right into a bash shell.

---

### Post by syxbit on 2007-06-23
just tried open Solaris,,,,doens't work either.

seriously, nothing but windows works on this laptop!

it seems there are quite a few people who at least are able to boot Feisty.
what are you doing differently?
you must be doing something, as I can't even get it to boot!

---

### Post by meanimal on 2007-06-23
Hm not sure if I'm doing anything differently.

I turned on SATA compat in the BIOS, booted off the Feisty 7.04 32-bit alternate CD, and the install went quite smoothly.

After it installed, it even booted into X properly, however it used the VESA driver by default.  I'm in the process of getting the intel drivers to work.

PS: here are my specs:
15.4" WSXGA, T7500 CPU, 2GB RAM, Intel graphics, Thinkpad Atheros A/B/G wireless.

NO turbo memory & NO WWAN.  If you have turbo memory perhaps you should try taking it out.

---

### Post by meanimal on 2007-06-23
syxbit, perhaps it's the nvidia graphics card which is causing the trouble.

Does yours hang before starting X?  Which driver do you suppose X was configured to use by default?  Perhaps you can try VESA?  Perhaps you should also try booting to the command-line and upgrading the system first (including NVIDIA's latest drivers) and trying both.

---

### Post by syxbit on 2007-06-23
specs
14.1" 1440*900 | Core 2 Duo 7500 | 2GB 667mhz | 160GB Hitachi 5K160 | intel 4965 | nVidia 140M
no intel turbo mem. |  no wwan or anything else

it must be the nvidia card.
how can i change the video driver.
it doesn't even boot up. If i could take out the HD and that way edit the xorg on another machine, but this is a laptop, and i don't have a 2.5" enclosure.

is there a way to do this from grub?

---

### Post by manioc on 2007-06-24
> **syxbit said:**
> specs
14.1" 1440*900 | Core 2 Duo 7500 | 2GB 667mhz | 160GB Hitachi 5K160 | intel 4965 | nVidia 140M
no intel turbo mem. |  no wwan or anything else

it must be the nvidia card.
how can i change the video driver.
it doesn't even boot up. If i could take out the HD and that way edit the xorg on another machine, but this is a laptop, and i don't have a 2.5" enclosure.

is there a way to do this from grub?

No it's not the NVIDIA drivers causing the kernel not to boot up.  It's the SATA AHCI drivers in 2.6.20.  If you want to install the 64 bit version of Feisty:
1. install the 64 bit version of Edgy Edge using the alternative install
2. download the nvidia linux drivers and install them if you want to upgrade using synaptic or hold off on getting X to work and do an upgrade via aptitude
3. install/reinstall the nvidia linux drivers after upgrading

---

### Post by syxbit on 2007-06-24
then why doesn't gutsy tribe 1 work? (it uses kernel 2.6.22 or fedora kernel 2.6.21)
i hope they fix this by gutsy final, or a double distr-upgrade is gonna suck!
i'll try it tonight. I assume edgy alternate 32bit works too, right? as  i need my flash :)

---

### Post by chem on 2007-06-24
There must be a way to report hardware issues to the gutsy team, right?  I hope T61 owners can provide feedback, so this will work soon! :)

---

### Post by colby500 on 2007-06-24
I followed the follow instructions posted in this thread: [http://ubuntuforums.org/showthread.php?t=396204&highlight=4965](http://ubuntuforums.org/showthread.php?t=396204&highlight=4965) and I was able to get my 4965 card to work with my t61 thinkpad.  

Used Feisty, fully updated.  I got the ndiswrapper from apt.

"hello,

I too have the intel 4965 card and though there does not seem to be a linux compatible driver (yet)
it works perfectly well on my dell 640m laptop if ndiswrapper is used;

1) install ndiswrapper (I did it from source but I think it may be in apt)
2) look for the windows drivers on the intel website (V11.1.0.0_XP_DRIVERS.ZIP)
I think the one your looking for is netw4x32.INF

3)in the directory of the extracted driver file in the terminal type:
ndiswrapper -i NETw4x32.INF

4)then;
ndiswrapper -m

5)check its there with;
ndiswrapper -l
6) I think the driver may need forwarding with (though step 3 may do this);
modprobe ndiswrapper;


And that's it.

Some observations;

make sure that wireless is turned off when you exit/ enter ubuntu (fn + f2). If it remains on (wireless) then ubuntu can fail to boot or shutdown.

once in ubuntu, and having switched wireless the light should flash periodically (perhaps once every 5 seconds, this is normal behaiour).

after wireless has been turned on go to the network manager (nm-applet) and deselect then reselect enable networking to restart it (right-click). it should no become aware of the available wireless connections.

if your network manager shows no connections, check if any are available with the command;
sudo iwlist scan


That's it. Sorry if its over-simplified, its just a quick guide for noobs.

Ryan"[http://ubuntuforums.org/showthread.php?t=396204&highlight=4965]("http://ubuntuforums.org/showthread.php?t=396204&highlight=4965")

---

### Post by makeitwork on 2007-06-25
Thanks for all of the tips.  In case people haven't seen this, I found the following pages to be very useful:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61)

[http://blogfranz.blogspot.com/2007/06/xorg-options-for-t61-x3100i965.html](http://blogfranz.blogspot.com/2007/06/xorg-options-for-t61-x3100i965.html)

My info (if I can get this right):
t61 lenovo, 2GB RAM, Core 2 Duo, NVIDIA Quadro NVS 140M, 14.1" widescreen 1280x800, Atheros 11a/b/g Wireless PCI, Intel 82566MM Gigabit ethernet

I set my disk controller SATA mode to compatible in the bios, and burned a alternative install CD (the regular installation would hang trying to do graphics stuff).  It's also a good idea to double check the integrity of the CD, because that cost me a few hours of pain.

Right, so currently when I try to start the ubuntu I believe that I'm hanging right before the graphical login.  Switching to other virtual screens (ctrl alt f1, etc.) doesn't show any text whatsoever.  I've only waited for about a minute before restarting.

So I believe I need to set xorg to use basic VESA settings until I can get better drivers installed.  The thinkwiki website above was kind of vague.  When I try to login normally I can't do anything before it hangs.  As part of the GRUB bootup screen I can choose a recovery mode for ubuntu and that works and drops me into the root prompt (no passwd required of course).  So now I'm trying to figure out how to upgrade my NVIDIA drivers.  Any help is appreciated.  Thanks!

---

### Post by caseychan on 2007-06-25
I'm trying to install Ubuntu 7.04 on my Lenovo T61 core 2 duo 7300.  Once I got to the menu options and chose
the installation option.  The installation started and ran up to a point where it said:
PCI: failed to allocate memory resources
...

ethnet Irq: unable to allocate MSI interrupt Error -22.

Then screen just black out and hanged thereafter.

Have anyone seen this before?
Any help or suggestion?

Thanks,
Casey

---

### Post by alexsb on 2007-06-25
@makeitwork

you don't need vesa to install the nvidia drivers. Just download them in the console using wget (or use a usb stick)- setting them up actually requires you to exit X anyway.

Make sure thoug to follow the procedures (especially about uninstalling) described here:
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

It is really important to uninstall all the stuff - it took me a couple of hours to find every last bit of it :) - so if you're stuck, write.

Cheers,

Alex

---

### Post by alexsb on 2007-06-25
I'm still having troubles with my sound:

If I use the method described in the thinkwiki (manually patching the files of 1.0.14) then I have a system where the mixer works fine, has a lot of options (so does alsamixer) but no sound - ever.

If I use the cvs snapshot via rsync and follow the official alsa wiki cvs installation instructions I get a completely difunctional sound system. Alsa won't be loaded at all.

Any suggestions?

---

### Post by makeitwork on 2007-06-25
> **caseychan said:**
> I'm trying to install Ubuntu 7.04 on my Lenovo T61 core 2 duo 7300.  Once I got to the menu options and chose
the installation option.  The installation started and ran up to a point where it said:
PCI: failed to allocate memory resources
...


I got that message, but after I switched to the alternative install cd (txt only), and switched my hard drive controller SATA setting in the BIOS to "compatible" (use the ThinkVantage button when booting) the message pops up but doesn't stop anything.  Not sure which one of those changes fixed the problem, but you probably want to do both of those things anyway.

---

### Post by syxbit on 2007-06-25
i've got wireless working now with ndis, but it's pretty flaky. it disconnects a lot.
i haven't been able to get sound either
i followed the walkthrough from earlier, but get the following error when compiling the utlis
```

Updating configure.in (backup is in configure.in~)

Please run 'aclocal -I m4' to regenerate the aclocal.m4 file.
You need aclocal from GNU automake 1.9 (or newer) to do this.
Then run 'autoconf' to regenerate the configure file.

You might also want to copy the convenience header file gettext.h
from the /usr/share/gettext directory into your package.
It is a wrapper around <libintl.h> that implements the configure --disable-nls
option.

Press Return to acknowledge the previous two paragraphs.

```

any ideas?

---

### Post by alexsb on 2007-06-25
> **syxbit said:**
> i've got wireless working now with ndis, but it's pretty flaky. it disconnects a lot.
i haven't been able to get sound either
i followed the walkthrough from earlier, but get the following error when compiling the utlis
```

Updating configure.in (backup is in configure.in~)

Please run 'aclocal -I m4' to regenerate the aclocal.m4 file.
You need aclocal from GNU automake 1.9 (or newer) to do this.
Then run 'autoconf' to regenerate the configure file.

You might also want to copy the convenience header file gettext.h
from the /usr/share/gettext directory into your package.
It is a wrapper around <libintl.h> that implements the configure --disable-nls
option.

Press Return to acknowledge the previous two paragraphs.

```

any ideas?

I had exactly the same problem - but chose to ignore it, since it looked to me like a bug relevant for a particular case. However, it's not working for me (it compiled fine) so it might be the reason.

Did you try what is described in the error message (running aclocal)? I didn't and I can't atm. Let me know if it helps

---

### Post by makeitwork on 2007-06-25
> **alexsb said:**
> @makeitwork

you don't need vesa to install the nvidia drivers. Just download them in the console using wget (or use a usb stick)- setting them up actually requires you to exit X anyway.

Make sure thoug to follow the procedures (especially about uninstalling) described here:
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

It is really important to uninstall all the stuff - it took me a couple of hours to find every last bit of it :) - so if you're stuck, write.

Cheers,

Alex

Thanks!  I haven't administered a linux machine in a long time, so I have no idea what how to use the package stuff.  When you say uninstall "all the stuff", is there stuff besides nvidia-glx (or nvidia-glx-src!) ?  To uninstall nvidia drivers and get the latest, do I do something like the following:

sudo apt-get --purge remove nvidia-glx
sudo apt-get install nvidia-glx

And to check if I have the xserver-xorg-dev stuff:

apt-cache search xserver-xorg-dev

I would still like to know how to use VESA options so I can have access to xwindows while I figure this out.

---

### Post by alexsb on 2007-06-25
> 
If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:
DISABLED_MODULES="nv nvidia_new"
Additionally, delete the following file if it exists:
rm -f /lib/linux-restricted-modules/.nvidia_new_installed


That's what's written on the NVidia Forum. Furthermore there is a bug with the uninstallation which I ran into. It didn't let me load the nvidia module because of a dependency on the linux-restricted-modules - but if it happens to you to, just google for the error message - or post it here (I don't remember it exactly).

---

### Post by syxbit on 2007-06-25
search for envy nvidia script
that's what i used
you can run in in the terminal and it figures out all the restricted modules problems.

as for sound, i don't know how to apply those patches
i've looked around, but can't find anything.
could someone be a little more specific?
thanks

---

### Post by alexsb on 2007-06-25
Well, if you want to apply those patches the easiest way is to edit the file (all three patches are in one file) by hand (remove the red, add the green part). That's what I did. Something else seems to be wrong though - I still don't have sound.

---

### Post by manioc on 2007-06-26
> **syxbit said:**
> i've got wireless working now with ndis, but it's pretty flaky. it disconnects a lot.
i haven't been able to get sound either
i followed the walkthrough from earlier, but get the following error when compiling the utlis
```

Updating configure.in (backup is in configure.in~)

Please run 'aclocal -I m4' to regenerate the aclocal.m4 file.
You need aclocal from GNU automake 1.9 (or newer) to do this.
Then run 'autoconf' to regenerate the configure file.

You might also want to copy the convenience header file gettext.h
from the /usr/share/gettext directory into your package.
It is a wrapper around <libintl.h> that implements the configure --disable-nls
option.

Press Return to acknowledge the previous two paragraphs.

```

any ideas?

Uhm... do exactly what it tells you to do!

aclocal -I m4
cp /usr/share/gettext/gettext.h .
autoconf

It worked for me...

---

### Post by wesleygriffin on 2007-06-26
> **manioc said:**
> Wes,

Can you paste your dmesg and your modprobe config file so I can figure out how to get my CD/DVD multiwriter to work?  Thanks

Sorry about not getting back to this. I think I've got my forum notify settings messed up. Anyway, I've attached my dmesg output. I'm also attaching /etc/modules as I'm not sure what you mean by the modprobe config file. I see nothing by that name in /etc and there is a ton of stuff under /etc/modprobe.d so if you want something from there, let me know.

HTH,
Wes

---

### Post by syxbit on 2007-06-26
> **manioc said:**
> Uhm... do exactly what it tells you to do!

aclocal -I m4
cp /usr/share/gettext/gettext.h .
autoconf

It worked for me...

i tried that. it keeps giving the same error.
i have automake1.9 installed too

---

### Post by awry on 2007-06-26
> **manioc said:**
> Uhm... do exactly what it tells you to do!

aclocal -I m4
cp /usr/share/gettext/gettext.h .
autoconf

It worked for me...

If you use the ./cvscompile script that comes with the alsa cvs tree, it automagically does the right thing (at least for me).

---

### Post by syxbit on 2007-06-27
i've tried doing the ./cvscompile on both the rsyncs
```

rsync -avz --delete rsync://alsa.alsa-project.org/hg your_directory

You may only get the latest code without .hg repository:
rsync -avz --delete --exclude=.hg* rsync://alsa.alsa-project.org/hg your_directory 
```
get the same thing on both

---

### Post by ktakahashi on 2007-06-27
Here is a summary of what I did on my T61 15.4 inch Intel graphics chip + Feisty 64bit.

It seems to me that most problems are fixed in latest versions of software components,
or at least there are patches out there, and it's basically a matter or catching up with
the front.


What I did:
[LIST]
[*]Install -- Changed AHCI -> Compatibility in BIOS.  Used Alternative CD to avoid 
    the X11 problem during installation process.

[*]Wifi  -- backport kernel-image 2.6.22 from gutsy, then follow the instruction here:
[http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html]("http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html")

  Feisty's 2.6.20 kernel seems not compatible with the intel driver.
  The newer kernel image can be found here, for example:
[http://http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/]("http://http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/") .  You may also need to get kernel-headers, in that case easiest way would be to add gutsy repo to apt sources.list temporarily and apt-get source.


[*]Sound -- installed alsa-driver and alsa-kernel CVS.  Working fine with me.  You could    also obtain 1.0.14 source from gutsy and apply the three patches as mentioned here [http://http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61]("http://http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61").
   CVS already includes the patches.


[*]Intel graphics -- VESA driver worked fine with me.  I now use the Intel driver, though.
   To get this working, follow the instructions in
[http://http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61").

   This page instructs to replace (PFIT_ENABLE | VERT_AUTSCALE ....) with 0, but I
   didn't do this.  Instead I modified the code as:
    
```

    if( mode->HDisplay != adjusted_mode->HDisplay || mode->VDisplay != adjusted_mode->VDisplay )
    {
        pfit_control = 1;
    }
   else
    {
        pfit_control = 0;
    }
 
```
    as suggested in [http://http://www.spinics.net/lists/xorg/msg25099.html]("http://www.spinics.net/lists/xorg/msg25099.html").
    I used debchange -i to avoid overwriting this change by the updater.

[*]Suspend -- add acpi_sleep=s3_bios to kernel parameter.
[/LIST]

---

### Post by rekcuts on 2007-06-27
Hi, just got a t61 with a t7500 and nvidia. I've been trying get kubuntu (64 bit) working. So far I have used the alternative install disk to install kubuntu (7.04). I have access to a console, but anything graphical just goes black on me.

Install went fine until I went for the reboot and basically the system just goes to a black screen as I believe the nvidia card is not reading correctly. I have tried to follow several of the links posted, but I do not believe I did them entirely correctly as I didn't quite understand it that well.

I would appreciate it if someone would post some slightly more specific information on how to setup the nvidia 140m such that I can get to the desktop. I'm not really sure how to download the drivers for the card from the command line as most of the instructions tell what to delete but not how to reinstall the things you need.

Thanks for any help you can give.

---

### Post by makeitwork on 2007-06-28
> **ktakahashi said:**
> Here is a summary of what I did on my T61 15.4 inch Intel graphics chip + Feisty 64bit.

It seems to me that most problems are fixed in latest versions of software components,
or at least there are patches out there, and it's basically a matter or catching up with
the front.



Thanks so much!  One question, which kind of wireless card did you have, Intel or Atheros?  When you upgraded to the new kernel that was for your wireless card?  And what do you mean by "adding to kernel parameter", which file or how?

---

### Post by chem on 2007-06-28
> **ktakahashi said:**
> Here is a summary of what I did on my T61 15.4 inch Intel graphics chip + Feisty 64bit.

Wifi  -- backport kernel-image 2.6.22 from gutsy, then follow the instruction here:
[http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html]("http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html")

  Feisty's 2.6.20 kernel seems not compatible with the intel driver.
  The newer kernel image can be found here, for example:
[http://http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/]("http://http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/") .  You may also need to get kernel-headers, in that case easiest way would be to add gutsy repo to apt sources.list temporarily and apt-get source.

Suspend -- add acpi_sleep=s3_bios to kernel parameter.


Wait, is suspend fully working?  Does that include suspend2disk?  Does the system wake back up smoothly (including wireless, etc)?  Is that using the 2.6.22 or 2.6.20 kernel (I presume 2.6.22)?

I think this is the first report I've seen involving a T61 that implies they got suspend to work.

---

### Post by alexsb on 2007-06-28
> **rekcuts said:**
> Hi, just got a t61 with a t7500 and nvidia. I've been trying get kubuntu (64 bit) working. So far I have used the alternative install disk to install kubuntu (7.04). I have access to a console, but anything graphical just goes black on me.

Install went fine until I went for the reboot and basically the system just goes to a black screen as I believe the nvidia card is not reading correctly. I have tried to follow several of the links posted, but I do not believe I did them entirely correctly as I didn't quite understand it that well.

I would appreciate it if someone would post some slightly more specific information on how to setup the nvidia 140m such that I can get to the desktop. I'm not really sure how to download the drivers for the card from the command line as most of the instructions tell what to delete but not how to reinstall the things you need.

Thanks for any help you can give.

Follow the instructions in the NVidia Forum (I posted the link earlier). Download using wget url or use an usb stick. The rest is just straight forward.

---

### Post by ktakahashi on 2007-06-28
> **makeitwork said:**
> Thanks so much!  One question, which kind of wireless card did you have, Intel or Atheros?  When you upgraded to the new kernel that was for your wireless card?  And what do you mean by "adding to kernel parameter", which file or how?

I have Intel 4965.   I upgraded to 2.6.22 before I compile intel iwl4965 driver.
Add the kernel parameters in /boot/grub/menu.lst.

I hope this helps.

---

### Post by ktakahashi on 2007-06-28
> **chem said:**
> Wait, is suspend fully working?  Does that include suspend2disk?  Does the system wake back up smoothly (including wireless, etc)?  Is that using the 2.6.22 or 2.6.20 kernel (I presume 2.6.22)?

I think this is the first report I've seen involving a T61 that implies they got suspend to work.

Yes, so far I went through almost ten suspend/resume cycles, and it seems working fine.
Everything including wireless wake up fine.
Even before configuring suspend, hibernation worked out of the box on Feisty.  Occasionally
I experienced some instability but I don't know this was related to hibernation.  
Fn+F2 to lock the screen works fine, too.

I use 2.6.22.   I also upgraded acpi-related packages to those of Gutsy.

Make sure ibm_acpi kernel module is loaded.  Modprobe manually or add to /etc/modules if not.

---

### Post by syxbit on 2007-06-28
i noticed today that gutsy tribe 2 liveCD works!!!
i couldn't get wireless on it (though it might if i installed, not sure)
i had to load it up with safe graphics mode, but that's a huge improvement!
sound didn't work either, but i'm tempted to use gutsy till it becomes final

---

### Post by chem on 2007-06-28
> **ktakahashi said:**
> Yes, so far I went through almost ten suspend/resume cycles, and it seems working fine.
Everything including wireless wake up fine.
Even before configuring suspend, hibernation worked out of the box on Feisty.  Occasionally
I experienced some instability but I don't know this was related to hibernation.  
Fn+F2 to lock the screen works fine, too.

I use 2.6.22.   I also upgraded acpi-related packages to those of Gutsy.

Make sure ibm_acpi kernel module is loaded.  Modprobe manually or add to /etc/modules if not.

That's pretty awesome.  This may be the first report of "perfectly" working suspend and suspend2disk using a Santa Rosa laptop.  Hopefully all the knowledge in this thread will find its way to thinkwiki.org and its T61 section.

---

### Post by makeitwork on 2007-06-28
For all of the people like me who need a helping hand, here is an in depth howto for installing the latest alsa drivers for the hda intel card:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

This site has three fixes (currently in CVS, not in 1.0.14) that you might want to manually do:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad) _T61

Just so you know, I actually haven't followed this myself :)  I think I'm going to wait for gutsy to stabilize.  Once I see that gutsy has worked out all of the t61 things (latest alsa fixes, wireless, suspend, latest nvidia drivers) I'll just wipe my linux partition and reinstall.  Dual booting with a FAT32 partition to copy files back and forth is coming in very handy.

---

### Post by rekcuts on 2007-06-28
Getting frustrated.

Now have tried multiple times. I followed the nvidia site for what to remove before installing the 140 driver (tried both 100.14.09 and 100.14.11). Finally got the thing to go through to the end of the install and it says installation successfully completed. I then go to reboot and I still just get a black screen immediately after I make my selection in grub.

Don't know what's going on as others seem to have gotten this to work.

Update: somehow I had already managed to download a newer kernel and installed the driver with that kernel I guess... it didnt give me an option to pick it the first time I rebooted. I have x working with newer kernel.

---

### Post by makeitwork on 2007-06-29
> **rekcuts said:**
> Getting frustrated.

Now have tried multiple times. I followed the nvidia site for what to remove before installing the 140 driver (tried both 100.14.09 and 100.14.11). Finally got the thing to go through to the end of the install and it says installation successfully completed. I then go to reboot and I still just get a black screen immediately after I make my selection in grub.

Don't know what's going on as others seem to have gotten this to work.

Update: somehow I had already managed to download a newer kernel and installed the driver with that kernel I guess... it didnt give me an option to pick it the first time I rebooted. I have x working with newer kernel.

Do you have the Nvidia 140MS

I would try the envy program.  Use dpkg -i to install the .deb file below.  Then run envy, uninstall the current nvidia driver, and install the latest nvidia driver.  The website also has a FAQ.

[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.5-0ubuntu5_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.5-0ubuntu5_all.deb)

      Kevin

---

### Post by makeitwork on 2007-06-29
[http://www.klabs.be/~fpiat/linux/debian/Etch_on_Thinkpad_T61.html](http://www.klabs.be/~fpiat/linux/debian/Etch_on_Thinkpad_T61.html)

Here's another site (for a Debian install, very similar to Ubuntu).  It has a lot of details for a variety of issues.

---

### Post by meba on 2007-06-29
I managed to get functional suspend to ram with proprietary nvidia drivers. I posted a script on ThinkWiki:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61)

(Along with webcam and some ALSA settings)

---

### Post by trivialnobvious on 2007-06-30
> **syxbit said:**
> i noticed today that gutsy tribe 2 liveCD works!!!
i couldn't get wireless on it (though it might if i installed, not sure)
i had to load it up with safe graphics mode, but that's a huge improvement!
sound didn't work either, but i'm tempted to use gutsy till it becomes final

Excellent news.

---

### Post by sujee on 2007-06-30
Hi
the suspend script works wonderfully.  HOw can bind this script to lid-close event?

Also I got sound working, but not the Mic.  I have fiddled with bunch of knobs in Kmixer, but still no success.  Any pointers would be appreciated.

> **meba said:**
> I managed to get functional suspend to ram with proprietary nvidia drivers. I posted a script on ThinkWiki:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61)

(Along with webcam and some ALSA settings)

---

### Post by sujee on 2007-06-30
when I resume from suspend,  the xorg process is consuming 100% CPU.  I have Nvidia 140M with latest driver (100.14.11)
any one else has this issue?

---

### Post by makeitwork on 2007-06-30
I'm running an NVIDIA 140M and I used the envy script to uninstall drivers and then reinstall the latest drivers.

Has anyone with the same graphics card noticed that the first time they log into xwindows the program glxgears runs fine.  Then if you log out and log back in, the next time you run glxgears the system hangs.

---

### Post by makeitwork on 2007-06-30
Also I'm getting a lot of errors trying to use aterm.  Whenever I run it the following errors spew out:

aterm has encountered the following problem interacting with X Windows :
      Request: 64,    Error: 8(BadMatch (invalid parameter attributes))
      in resource: 0x2C0001B

then I type a few characters and the program hangs.  I've noticed that the -fg and -bg color I give at the command line aren't respected.

---

### Post by syxbit on 2007-07-01
i just tried gutsy, but the nvidia drivers have MAJOR issues.
it works right after installing through the nvidia script, but after a reboot, it doesn't

---

### Post by Ashland on 2007-07-01
I _finally_ got my x working with the proprietary NVIDIA driver when I found this guy's how-to for the envy script that does it all for you:

[http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

I had to restart a couple times before it worked, but I could tell it was doing something right because the blue error message screen was crystal clear right after the script had run.

Running: 1.8 Ghz Core 2 Duo, 1 gig of ram, NVIDIA 140M

---

### Post by crankyRobot on 2007-07-01
> **makeitwork said:**
> I'm running an NVIDIA 140M and I used the envy script to uninstall drivers and then reinstall the latest drivers.

Has anyone with the same graphics card noticed that the first time they log into xwindows the program glxgears runs fine.  Then if you log out and log back in, the next time you run glxgears the system hangs.

I just tried it and got almost the same result -- my system didn't hang but glxgears didn't display anything and then segfaulted.  I'm running 64 bit feisty with the 2.6.22-7 kernel from gutsy.

---

### Post by chem on 2007-07-02
People are reporting genuine ubuntu problems here to launchpad (the ubuntu bug tracker), right?  ;)

---

### Post by makeitwork on 2007-07-02
> **makeitwork said:**
> Also I'm getting a lot of errors trying to use aterm.  Whenever I run it the following errors spew out:

aterm has encountered the following problem interacting with X Windows :
      Request: 64,    Error: 8(BadMatch (invalid parameter attributes))
      in resource: 0x2C0001B

then I type a few characters and the program hangs.  I've noticed that the -fg and -bg color I give at the command line aren't respected.

Bug #123474 in aterm (Ubuntu)
[https://bugs.launchpad.net/ubuntu/+source/aterm/+bug/123474](https://bugs.launchpad.net/ubuntu/+source/aterm/+bug/123474)

---

### Post by sujee on 2007-07-02
Ok, I have solved xorg consuming 100% cpu problem.
If I don't run the program 'xosview' ,   X process doesn't go crazy after resume.

I use Xosview to monitor the system (cpu, mem, swap ..etc) ; [http://xosview.sourceforge.net/](http://xosview.sourceforge.net/)

> **sujee said:**
> when I resume from suspend,  the xorg process is consuming 100% CPU.  I have Nvidia 140M with latest driver (100.14.11)
any one else has this issue?

---

### Post by makeitwork on 2007-07-02
> **crankyRobot said:**
> I just tried it and got almost the same result -- my system didn't hang but glxgears didn't display anything and then segfaulted.  I'm running 64 bit feisty with the 2.6.22-7 kernel from gutsy.

I did a couple of things and somehow the problem seemed to go away.

 - I switched to a different virtual terminal and ran "/usr/init.d/gdm stop", then tried running startx myself.  I'm wondering if this overwrote a few configuration files.  For one the NVIDIA splash screen started to show up.  For another running nvidia-bug-report.sh now says that my power settings (DPMS (Energy Star): Standby: 0) are set to 0.
 - I changed the resolution to 1280x800 in xorg.conf (which the nvidia driver auto-selected anyway, I have the 14.1" monitor)
 - my nvidia driver was set to 16bpp so I changed my xorg.conf script to set the default depth to 24, and now the the card uses 32bpp.
 - I changed the login window to restart xwindows after every session.

Now I tried changing the last two things back to their original settings, and the problem hasn't resurfaced.  I probably will just thank my lucky stars and move on.

One question, what's the difference between /usr/init.d/gdm and /usr/sbin/gdm?

---

### Post by aboutblank on 2007-07-02
Does anyone have 24-bit color using the intel driver for X3100 integrated graphics yet? If so, HOW??

---

### Post by deuce868 on 2007-07-02
> **aboutblank said:**
> Does anyone have 24-bit color using the intel driver for X3100 integrated graphics yet? If so, HOW??

Yep, the graphics are really nice once you get a few tweaks done. I have detailed instructions on what I had to do here;
This is on gutsy tribe 2 updated. I don't know if you can pull those xorg driver files over from gutsy or not. 
[http://wiki.avwsystems.com//doku.php/laptop/t61#graphics](http://wiki.avwsystems.com//doku.php/laptop/t61#graphics)

---

### Post by aboutblank on 2007-07-02
Rawrg. I have done the steps for Feisty on thinkwiki. Full res but no dice on 24-bit video.

deuce868, I installed Gutsy and followed all your video steps, including those about disabling TV out. I got full res, but definitely not 24-bit video. Am I missing something here?

---

### Post by ktakahashi on 2007-07-02
Hi,

I disabled TV out following your instructions.  Thanks.

However, xrandr now stopped working.   Do you know of any workaround for this?
Xrandr says; 'Output TV is not disconnected but has no modes'.

---

### Post by deuce868 on 2007-07-02
> **aboutblank said:**
> Rawrg. I have done the steps for Feisty on thinkwiki. Full res but no dice on 24-bit video.

deuce868, I installed Gutsy and followed all your video steps, including those about disabling TV out. I got full res, but definitely not 24-bit video. Am I missing something here?

Not sure. Here's a link to my full org.conf with the scroll button working. You might give it a shot and if it works run a diff. 

[http://wiki.avwsystems.com//lib/exe/fetch.php/laptop/xorg.conf?id=laptop%3At61](http://wiki.avwsystems.com//lib/exe/fetch.php/laptop/xorg.conf?id=laptop%3At61)

---

### Post by deuce868 on 2007-07-02
> **ktakahashi said:**
> Hi,

I disabled TV out following your instructions.  Thanks.

However, xrandr now stopped working.   Do you know of any workaround for this?
Xrandr says; 'Output TV is not disconnected but has no modes'.

Sorry, I haven't messed with xrandr at all except to try out the applet to change my orientation. What are you trying to do with xrandr? I can try to see if it works for me or not as well. 

You can also check out my xorg.conf in my last post and see if there's anything missing.

---

### Post by Darrena on 2007-07-02
Here is an interesting item I discovered regarding the brightness issue when I was playing around in an attempt to find what was causing the issue so I could file a bug.  If I drop to a virtual console (ctrl+F1) I can modify the brightness settings...   

This is on Gutsy.

---

### Post by deuce868 on 2007-07-02
> **Darrena said:**
> Here is an interesting item I discovered regarding the brightness issue when I was playing around in an attempt to find what was causing the issue so I could file a bug.  If I drop to a virtual console (ctrl+F1) I can modify the brightness settings...   

This is on Gutsy.

Yea, I was talking with some friends about this. In older thinkpads you could tell modprobe to ignore the video and you could get the control buttons to work. That seems to have changed in this newer model. 

Old Thinkwiki note for older model:
[http://www.thinkwiki.org/wiki/Problem_with_LCD_brightness_buttons](http://www.thinkwiki.org/wiki/Problem_with_LCD_brightness_buttons)

---

### Post by ktakahashi on 2007-07-02
> **deuce868 said:**
> Sorry, I haven't messed with xrandr at all except to try out the applet to change my orientation. What are you trying to do with xrandr? I can try to see if it works for me or not as well. 

You can also check out my xorg.conf in my last post and see if there's anything missing.

Thanks for the reply.   

I'm sure my xorg.conf is identical to yours.   I just wanted to know if the
problem I'm having is caused by a wrong configuration or an incomplete
package update (I updated some xorg packages to those of gutsy, and not
quite sure if I got all relevant packages.)

What I want to do is to enable VGA out for presentations.
When I restart X with an external projector/monitor connected X detects it, but
wanted to do this without restarting.

My problem is xrandr stopped reporting screen status as usual, nor accept
any other options, but it just halts with the error message I mentioned above.

---

### Post by deuce868 on 2007-07-02
> **ktakahashi said:**
> What I want to do is to enable VGA out for presentations.
When I restart X with an external projector/monitor connected X detects it, but
wanted to do this without restarting.


Ah, no. I haven't gotten the hotplug working. I have to restart X in order to get my display onto my desktop LCD, I'd assumed that it really wasn't working all the way yet, but since you seemed to have some success with it before I'll have to take a look at getting that to work.

---

### Post by crankyRobot on 2007-07-02
> **makeitwork said:**
> I did a couple of things and somehow the problem seemed to go away.

 - I switched to a different virtual terminal and ran "/usr/init.d/gdm stop", then tried running startx myself.  I'm wondering if this overwrote a few configuration files.  For one the NVIDIA splash screen started to show up.  For another running nvidia-bug-report.sh now says that my power settings (DPMS (Energy Star): Standby: 0) are set to 0.
 - I changed the resolution to 1280x800 in xorg.conf (which the nvidia driver auto-selected anyway, I have the 14.1" monitor)
 - my nvidia driver was set to 16bpp so I changed my xorg.conf script to set the default depth to 24, and now the the card uses 32bpp.
 - I changed the login window to restart xwindows after every session.

Now I tried changing the last two things back to their original settings, and the problem hasn't resurfaced.  I probably will just thank my lucky stars and move on.

One question, what's the difference between /usr/init.d/gdm and /usr/sbin/gdm?

So are you now running in 1280x800?  Does the behavior resurface if you switch back t o 1440x900?  I'm not willing to run in 1280x800 -- so I guess I'll just live w/ shutting down/booting every time I close/open the machine (which I'm pretty much stuck w/ anyway since I haven't seen a simple solution yet where suspend will work on lid close w/ the nvidia card).

---

### Post by crankyRobot on 2007-07-02
Has anyone gotten dual monitors working with the nvidia card yet?  I booted w/ an external monitor, and just that monitor came up (nothing on the built-in LCD).  Since then, I've tried to modify my xorg.conf using the "nvidia-settings" application (running as root from a terminal so it can write the xorg.conf) and now, instead of doing a dual monitor setup like I had configured before writing the configuration file, I now get pretty much nothing on either screen if I boot with an external monitor connected (just an X cursor on the external monitor, nothing else).  This behavior persists even after reinstalling the drivers using the nvidia installer and letting it overwrite the xorg.conf file.  Everything still works normally if I boot w/ no external monitor.

If someone has this working, would you mind posting your xorg.conf.  I'll also see if anyone in the nvidia forums has a solution.

Thanks!

---

### Post by colby500 on 2007-07-03
Does any one know when the ALSA update will hit the ubuntu repos??

---

### Post by syxbit on 2007-07-03
i imagine they'll have to fix these problems by the time gutsy is final
i've spent countless hours with Feisty, Gutsy, Fedora 7 and ZenWalk (i'm about to try Slack 12)
i can't wait for Gutsy final to just "work"

---

### Post by Tobba25 on 2007-07-03
I am getting an R61, wich I guess is not all that different. I understand that compatability is not very good NOW, but can we rest assure that it will be better in the future? Since its all intel and all?

---

### Post by makeitwork on 2007-07-03
> **crankyRobot said:**
> So are you now running in 1280x800?  Does the behavior resurface if you switch back t o 1440x900?  I'm not willing to run in 1280x800 -- so I guess I'll just live w/ shutting down/booting every time I close/open the machine (which I'm pretty much stuck w/ anyway since I haven't seen a simple solution yet where suspend will work on lid close w/ the nvidia card).

I have a smaller monitory (14.1") so I believe the native resolution for my monitor is 1280x800.  That's what it is by default in Windows.

---

### Post by crankyRobot on 2007-07-03
> **makeitwork said:**
> I have a smaller monitory (14.1") so I believe the native resolution for my monitor is 1280x800.  That's what it is by default in Windows.

I have the 14.1''  WXGA+ and it's at 1440x900.  I don't know that I would trust windows to have the proper default -- I've had quite a difficult time getting everything working under windows as well (I still don't have sound in XP).   I notice a big difference between 1280x800 and 1440x900.  Is this the difference betweene the WXGA and the WXGA+?  If I get some time, I'll try to replicate your fix (though it won't do me much good w/o suspend).

The question I posted regarding the dual display issue at forums.nvidia.com seems to be pretty much ignored (1 view in 12 hours).  Does anyone know of any other good forums to post linux/nvidia/xorg questions?

---

### Post by deuce868 on 2007-07-03
> **crankyRobot said:**
> Does anyone know of any other good forums to post linux/nvidia/xorg questions?

Have you tried anything like say the xorg mailing lists or irc?

---

### Post by alexsb on 2007-07-03
> **crankyRobot said:**
> Has anyone gotten dual monitors working with the nvidia card yet?  I booted w/ an external monitor, and just that monitor came up (nothing on the built-in LCD).  Since then, I've tried to modify my xorg.conf using the "nvidia-settings" application (running as root from a terminal so it can write the xorg.conf) and now, instead of doing a dual monitor setup like I had configured before writing the configuration file, I now get pretty much nothing on either screen if I boot with an external monitor connected (just an X cursor on the external monitor, nothing else).  This behavior persists even after reinstalling the drivers using the nvidia installer and letting it overwrite the xorg.conf file.  Everything still works normally if I boot w/ no external monitor.

If someone has this working, would you mind posting your xorg.conf.  I'll also see if anyone in the nvidia forums has a solution.

Thanks!

Hi,

yes, and I was surprised how amayingly easy it was. I used the nvidia-settings gui program and saved the changes to the xorg.conf (I actually never even opened the file on this computer yet) - and it worked perfectly with any screen, any resolution, even dvi on my docking station, any positioning etc!

---

### Post by Tobba25 on 2007-07-03
Hello,

I'm not trying to hijack this thread or anything, but I just want to ask some general questions about what you guys are discussing.

The T61 and the R61 are pretty much the same, right, except from chassis, correct?

Will they both get more and more supported? I am on the verge of ordering a R61, but I cant do it before someone assures me that there will be efforts to get it to work properly in the future. You know, plug and play... 

I am thinking of buying the R61 with X3100, but could easily end up cashing up for the T61 with nVIDIA if driver-stuff is easyer...

Whats your take on this?

Thanks :-)

---

### Post by crankyRobot on 2007-07-03
> **alexsb said:**
> Hi,

yes, and I was surprised how amayingly easy it was. I used the nvidia-settings gui program and saved the changes to the xorg.conf (I actually never even opened the file on this computer yet) - and it worked perfectly with any screen, any resolution, even dvi on my docking station, any positioning etc!

Could you post (or e-mail me) your xorg.conf? -- I'd like to see if it's the same as mine.  Also, are you running 32 or 64bit version or ubuntu?  Thanks.

---

### Post by cmanfu on 2007-07-03
Did anyone get dual head working on the Intel X3100?

---

### Post by alexsb on 2007-07-03
> **crankyRobot said:**
> Could you post (or e-mail me) your xorg.conf? -- I'd like to see if it's the same as mine.  Also, are you running 32 or 64bit version or ubuntu?  Thanks.

I am running 32 bit, but I can not post it at the moment, since I'm about 1600 kilometers away from my T61 :(

I'll be back in 2 weeks, if it's still relevant I'll get back to you!

---

### Post by aboutblank on 2007-07-03
> **deuce868 said:**
> Not sure. Here's a link to my full org.conf with the scroll button working. You might give it a shot and if it works run a diff. 

[http://wiki.avwsystems.com//lib/exe/fetch.php/laptop/xorg.conf?id=laptop%3At61](http://wiki.avwsystems.com//lib/exe/fetch.php/laptop/xorg.conf?id=laptop%3At61)

Thanks but unfortunately it didn't work for me. I kept it identical except for removing the 1680x1050 res. Our laptops are nearly identical except I have a 14" and you a 15". I recompiled the intel driver just like it is mentioned in the wiki. I don't know... something is fishy here.

---

### Post by deuce868 on 2007-07-03
> **aboutblank said:**
> Our laptops are nearly identical except I have a 14" and you a 15". I recompiled the intel driver just like it is mentioned in the wiki. I don't know... something is fishy here.

I've got a 14" but at the wxga+ resolution of 1440x900. Did you get the higher resolution display? Maybe your display is only the 1200 model.

---

### Post by aboutblank on 2007-07-03
> **deuce868 said:**
> I've got a 14" but at the wxga+ resolution of 1440x900. Did you get the higher resolution display? Maybe your display is only the 1200 model.

Then I'm confused on why you have a 1680x1050 resolution in your xorg..?

I got a 14" with the higher res display... 1440 x 900. Like I said, it does the full res but not the color. And now I'm confused as all heck because we appear to have identical laptops where you get 24 bit color and I do not.

I'm on the "intel" driver. I turned off TV output. I built the driver from source and did the change (even though I never got any fuzziness of any kind), and installed the created deb.

---

### Post by deuce868 on 2007-07-03
> **aboutblank said:**
> Then I'm confused on why you have a 1680x1050 resolution in your xorg..?


Ah, I hook my laptop up to an external 20" that runs at 1680 so I have that in there for when I hook up the laptop on my office desk to my external stuff.

---

### Post by syxbit on 2007-07-05
i just bought a docking station.
it'll be here on Friday :)
can't wait!

---

### Post by deuce868 on 2007-07-06
anyone update to the new intel driver successfully? I saw .35 was out and a new version of the mac80211, but of course it broke things. Now when I try to connect the whole system locks up.

---

### Post by aboutblank on 2007-07-06
Suhweet! I got 24-bit color. 

First off, I'm on Gutsy. I completely removed the xserver-xorg-video-intel driver (including any config), reinstalled it, and ran dpkg-reconfig xserver-xorg. I mostly chose the default options, and when I rebooted, I had 24 bit color. :)

---

### Post by deuce868 on 2007-07-06
> **deuce868 said:**
> anyone update to the new intel driver successfully? I saw .35 was out and a new version of the mac80211, but of course it broke things. Now when I try to connect the whole system locks up.

Ok, read the fine print. The new mac80211 version 9 is not ready for the N cards yet.

---

### Post by Voland666 on 2007-07-07
Get the latest X3100 driver released by Intel here:

[http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943)

Hope this works for you too. It does on my Dell Latitude D630

---

### Post by meanimal on 2007-07-07
AFAIK these are the problems fixed by the newer (>2.0) intel drivers (not currently available in Feisty).
[LIST]
[*] Auto-scaling at native resolution (blurry graphics)
[*] 24-bit color
[/LIST]

Last night I also discovered the culprit behind 3d instability: mesa.

I believe all of these problems will actually be backported to Feisty in time.  But for those who don't want to wait, but also don't want to run Gutsy, try "apt pinning", described here: [http://techreport.com/forums/viewtopic.php?p=714998#714998](http://techreport.com/forums/viewtopic.php?p=714998#714998)

I used the above technique to install intel & mesa packages from Gutsy, and I'm now running compiz in 24-bit color in Feisty and everything is stable!

---

### Post by syxbit on 2007-07-08
gutsy should soon have the intel wireless driver too, and hopefully add the alsa patch for sound
it won't be too long now

---

### Post by Tobba25 on 2007-07-08
desktop effects is not a must for me. Sound is more important, and right now there is no sound... Someone pointed me to a debate on a fedora forum, but i could not figure out what to do. Please excuse my noobyness..

---

### Post by syxbit on 2007-07-08
i tried it too.
i DL'd the patch that the guy on fedoraforums had uploaded and compile it, but nothing happened.
same happened when i tried to do the intel wifi. It compiled, but i couldn't modprode it: got errors

i'm a little tired of it now. I've installed dozens of distros, and re-compiled the kernel over 20 times, but i think i'll just deal with windoze until gutsy fixes it all

---

### Post by Tobba25 on 2007-07-08
So you reckon Gutsy will fix it all for us?

---

### Post by syxbit on 2007-07-08
they have to
this wireless card is going to be coming on all the new laptops this summer
not supporting it would be stupid.
same for the sound.
the wireless driver is available, and the alsa patch is written.
all they have to do is include them

---

### Post by CoryLinden on 2007-07-10
Well, after following this forum and the excellent post on [ThinkWiki ]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61")I mostly have my spiffy new T61 working.  However, suspend does not work.  Apologies for n00b question, but the directory structure and scripts in /etc/acpi don't seem to follow the examples in ThinkWiki very well.  Where should the example suspend script be saved?  Thanks for the help!

(Edit: corrected "T60" to "T61"  Duh.)

---

### Post by syxbit on 2007-07-11
so what method did you use to get sound working?
i never could compile CVS

---

### Post by CoryLinden on 2007-07-11
Followed the directions on the [AlsaCVS wiki page]("http://alsa.opensrc.org/index.php/AlsaCVS") -- which are mostly copied in this forum [thread as well]("http://ubuntuforums.org/showthread.php?t=76019&page=17") -- and build everything from scratch.  Tricky parts were learning to grab the various build pieces:
```
sudo apt-get install autoconf automake build-essential cvs linux-headers-$(uname -r |cut -f3 -d-)
```
And then to note the comment at the end of the [ThinkWiki entry]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61") that says the built in speakers don't work.  The headphones are fine, but not the speakers.

---

### Post by Tobba25 on 2007-07-11
Bah! I'll prolly wait 'till they get it working by default.

---

### Post by cmonkey on 2007-07-14
Just thought I'd share what I've been able to get working on my Gutsy T61.
[B][SIZE="4"]
Brightness:[/SIZE][/B]

While the hardware buttons still don't work, I have a solution that will automatically raise and lower the backlight when plugged in or on battery.

First, make sure Gnome isn't trying to set the brightness, by going to System > Preferences > Power Management. In the On Battery Power tab, set "Dim display brightness by" to 0%.

Next, install xbacklight.

```
 sudo apt-get install xbacklight
```

You can manually set the backlight by using "xbacklight -set <number from 1-100>". Note that by using xbacklight, you can make the backlight go brighter or dimmer than normally allowed by Windows or Ubuntu.

To automate brightness changes, first enable laptop-mode

```
 sudo nano /etc/default/acpi-support
```

Scroll to the bottom and change ENABLE_LAPTOP_MODE to true

```
 ENABLE_LAPTOP_MODE=true
```

Set laptop mode to start automatically

```
 sudo update-rc.d laptop-mode multiuser
```

Edit laptop-mode.conf to automate brightness changes. Scroll down to LCD brightness settings. Modify the section to read as follows:

```
 CONTROL_BRIGHTNESS=1

 BATT_BRIGHTNESS_COMMAND="xbacklight -set 20"
 LM_AC_BRIGHTNESS_COMMAND="xbacklight -set 100"
 NOLM_AC_BRIGHTNESS_COMMAND="xbacklight -set 100"
 BRIGHTNESS_OUTPUT="/dev/null"
```

Note: You can use any value from 1 to 100 after -set, I used 20 and 100 as examples. After this, start the laptop-mode daemon, and test if it works.
```

 sudo /etc/init.d/laptop-mode start
```

**[SIZE="4"]Intel graphics[/SIZE]**

It worked without much tweaking in Gutsy.  I just had to edit xorg.conf to use the intel driver and apply the tv out stuff described here: [http://forums.fedoraforum.org/forum/showthread.php?t=159516&page=1&pp=15]("http://forums.fedoraforum.org/forum/showthread.php?t=159516&page=1&pp=15")

[SIZE="4"]**Sound**[/SIZE]

By installing [Alsa 1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2") and using the patch_analog.c attached to the above fedoraforum post, it worked fine.

[SIZE="4"]**Intel Wireless-N**[/SIZE]

Using the [guide here]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_Tribe_2_on_a_ThinkPad_T61#Wireless:"), it worked fine.  Make sure to use the 8.x.x branch of mac80211, and the 0.0.x branch of iwlwifi.  The newer, expirimental branches didn't work for me.

[SIZE="4"]**Whats left**[/SIZE]

Most of the major stuff has been taken care of.  Wifi is still quite buggy, but Intel is updating the drivers pretty quickly.  The only big thing left is getting Bluetooth working, though I'll save that for a rainy day.

---

### Post by makeitwork on 2007-07-16
> **cmonkey said:**
> Just thought I'd share what I've been able to get working on my Gutsy T61.
[SIZE="4"]**Sound**[/SIZE]

By installing [Alsa 1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2") and using the patch_analog.c attached to the above fedoraforum post, it worked fine.



If I understand correctly other people said they could get sound to work for the speakers but not the headphone jack.  You got both to work, correct?

---

### Post by cmonkey on 2007-07-16
> **makeitwork said:**
> If I understand correctly other people said they could get sound to work for the speakers but not the headphone jack.  You got both to work, correct?

Yes, both worked, though after mucking around with the kernel, trying to get bluetooth working, audio is borked for me.  IIRC, all I had to do to get speakers working was run alsamixer as root and unmute the Speaker slider.

---

### Post by alexsb on 2007-07-16
Those who have wireless working with the a/g/n driver: which version of the driver did you use? Those specified in [http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html](http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html) or the latest ones? 

I read that the latest ones are not as stable?

---

### Post by cmonkey on 2007-07-16
> **alexsb said:**
> Those who have wireless working with the a/g/n driver: which version of the driver did you use? Those specified in [http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html](http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html) or the latest ones? 

I read that the latest ones are not as stable?

Use the latest ones in the old branch, as in mac80211 8.0.2 and iwlwifi 0.0.39.  The newer branches of both are highly expirimental.

---

### Post by colby500 on 2007-07-19
ATM is seems that the intel drivers for the agn card do not work that well(broke the kernel and I had to reinstall the kernel).....ndiswrapper works fine ATM...

---

### Post by TimsterC on 2007-07-20
Noob ALERT !!!!

Hi Folks,

I've got Fiesty running now, nvidia drivers are fine.

I'm a bit worried about and confused about what instructions I need to follow to get the Intel WiFi A/G/N working. Last time I tried it bombed my system and I had to re-install.
btw, I have a 7663-15G.

Thanks in advance for any advice.

Tim

---

### Post by cmonkey on 2007-07-20
> **TimsterC said:**
> Noob ALERT !!!!

Hi Folks,

I've got Fiesty running now, nvidia drivers are fine.

I'm a bit worried about and confused about what instructions I need to follow to get the Intel WiFi A/G/N working. Last time I tried it bombed my system and I had to re-install.
btw, I have a 7663-15G.

Thanks in advance for any advice.

Tim

Here are exact step by step instructions of what I'm doing right now to get wifi working on my T61 with a fresh install of Gutsy Tribe 3.

```
sudo apt-get install build-essential linux-headers-`uname -r`
sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/source

wget http://intellinuxwireless.org/mac80211/downloads/mac80211-8.0.2.tgz
tar -xzf mac80211-8.0.2.tgz
cd mac80211-8.0.2/
sudo make patch_kernel
cd ..

wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-0.0.42.tgz
tar -xzf iwlwifi-0.0.42.tgz
cd iwlwifi-0.0.42/
make
sudo make install
cd ..

wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-4.44.17.tgz
tar -xzf iwlwifi-4965-ucode-4.44.17.tgz
cd iwlwifi-4965-ucode-4.44.17/
sudo cp iwlwifi-4965.ucode /lib/firmware/`uname -r`

sudo modprobe iwl4965
```

Make sure your hardware wireless switch is on.  After that, you should just be able to connect to wireless networks with the Gnome network manager.

---

### Post by syxbit on 2007-07-22
are yo uall able to get sound working too?
cause i've not been able to get it working (can't compile CVS) and haven't been able to get the patches working either

---

### Post by cmonkey on 2007-07-22
Use the instructions here: [http://forums.fedoraforum.org/forum/showthread.php?t=159516&page=1&pp=15](http://forums.fedoraforum.org/forum/showthread.php?t=159516&page=1&pp=15)

But when it comes to the step where you have to edit /etc/modprobe.conf, add the line to /etc/modprobe.d/alsa-base instead.

---

### Post by syxbit on 2007-07-23
neither wireless nor audio worked for me before (tried with fedora x64 and your fedora guide)
I planned on just waiting for gutsy to fix it all......

i'll try it tomorrow with tribe 3 (while at work :) )

---

### Post by LazyBoy on 2007-07-23
I have a T61 with the X3100 running 1440x900 on the laptop screen fine.

I could use some help getting it to run a 1920x1200 screen when in the docking station.  I don't care about any dual-head/Xinerama/etc. behavior.  Just the external screen when available and the laptop screen otherwise.

I haven't got X up at all on the external monitor yet.  Even with an xorg.conf I was trying to write for just that, not the internal screen.

Thanks,
LB

---

### Post by alexsb on 2007-07-23
Hi guys,

I recently switched to Gutsy, and now the really important things work fine, however, there are some issues left:

Sound:
Sound works, but the controls are not optimal. I can't really use the build in keys, I guess partially because the mixer is messed up (I use KDE, but alsamixer is behaving in the same way). The main volume that is presented by the mixer doen't regulate anything as far as I can tell, it seems to increase/decrease the field called "headphones" - which has no effect (headphone volume is the same as pcm). PCM seems to be the master volume. The Mute button mutes the "headphones" as well, which has no effect on the real volume. The volume plus/minus buttons can change the "headphones" volume by only one step.

Wireless:
Wireless works with madwifi, but it's not really stable. Furthermore the Symbol for the wireless connection is not active, even if I'm connected.

USB:
I'm not 100% whether I had this issue on feisty to that extend. My USB ports don't work or don't work well with storage devices. My camera, which worked perfectly with dapper on my old notebook, is not recognized at all. The same is true for my mp3 player and partially for my external hard drive, which works on only one of the three ports (the others work on no port). I have to check, but I guess it's not a hardware issue.

So, does anyone have the same problems, any ideas, suggestions? 

Thx,

Alex

---

### Post by syxbit on 2007-07-23
> **cmonkey said:**
> Use the instructions here: [http://forums.fedoraforum.org/forum/showthread.php?t=159516&page=1&pp=15](http://forums.fedoraforum.org/forum/showthread.php?t=159516&page=1&pp=15)

But when it comes to the step where you have to edit /etc/modprobe.conf, add the line to /etc/modprobe.d/alsa-base instead.

didn't work.
wireless did though :)


when untarring the patch.c alsa file linked on the fedoraforums site it gives an error.
i continued anyway.
there was no line "options snd-hda-intel index=0" in /etc/modprobe.d/alsa-base
so i added "options snd-hda-intel index=0 model=thinkpad" to the end

---

### Post by alexsb on 2007-07-23
> **syxbit said:**
> didn't work.
wireless did though :)


when untarring the patch.c alsa file linked on the fedoraforums site it gives an error.
i continued anyway.
there was no line "options snd-hda-intel index=0" in /etc/modprobe.d/alsa-base
so i added "options snd-hda-intel index=0 model=thinkpad" to the end

Somebody uploaded the file to this forum as well, which still works. here is a direct link:

[http://ubuntuforums.org/attachment.php?attachmentid=38727&d=1184980075](http://ubuntuforums.org/attachment.php?attachmentid=38727&d=1184980075)

---

### Post by syxbit on 2007-07-23
i do appreciate the help, but sound doesn't work ( i followed the steps exactly twice)
it sucks, i am getting a little tired of re-installing linux over and over, only to not have it completely work.
unless they fix sound in a later tribe, i'll probably just wait till gutsy final

---

### Post by nemik on 2007-07-24
Hmmm I have the option to get this laptop configured the way I want for $895 which seems like a good deal but all these issues with it are really worrying me. :/

I don't know whether to make the jump. I mean, it's a thinkpad, one of the most popular laptops ever, it has to be supported eventually, right?

---

### Post by vinced on 2007-07-24
Having just got my Thinkpad last week, I hope they get it fixed. I Am pretty certain they will. The problems stem from the fact that the hardware is cutting edge, not that its a Thinkpad. The drivers are new and the kinks have to be worked out. If you want it to just work right away the T60 does that fine.
Vince

---

### Post by syxbit on 2007-07-24
but make sure you get the T60 with intel gfx.
that's the reason i bought a thinkpad, cause the T61 switched to nVidia.
don't get the T60 with ATI gfx or you'll regret it.

---

### Post by Lukeg on 2007-07-24
I was able to get my Thinkpad 11a/b/g/n working using ndiswrapper, following [these]("http://www.thinkwiki.org/wiki/How_to_install_ndiswrapper_for_the_ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter") directions.

---

### Post by nemik on 2007-07-24
> **syxbit said:**
> but make sure you get the T60 with intel gfx.
that's the reason i bought a thinkpad, cause the T61 switched to nVidia.
don't get the T60 with ATI gfx or you'll regret it.

i spec'd out a T61 with 2GHZ, 1GB RAM, intel x3100 graphics, ibm atheros wifi, bluetooth, no camera 14" widescreen for $895 which seems like a decent deal. thinking i should just get it asap as lenovo/ibm don't have sales very often. it's just the ubuntu incompatibility is worrying me.

maybe i could vmware ubuntu off vista till all this gets fixed.

---

### Post by syxbit on 2007-07-24
that's what i'm doing, but having your primary OS be emulated is pretty terrible.
i'm just using vista, and counting down the days till i can switch

---

### Post by alexsb on 2007-07-25
> **alexsb said:**
> Hi guys,

I recently switched to Gutsy, and now the really important things work fine, however, there are some issues left:

Sound:
Sound works, but the controls are not optimal. I can't really use the build in keys, I guess partially because the mixer is messed up (I use KDE, but alsamixer is behaving in the same way). The main volume that is presented by the mixer doen't regulate anything as far as I can tell, it seems to increase/decrease the field called "headphones" - which has no effect (headphone volume is the same as pcm). PCM seems to be the master volume. The Mute button mutes the "headphones" as well, which has no effect on the real volume. The volume plus/minus buttons can change the "headphones" volume by only one step.

Wireless:
Wireless works with madwifi, but it's not really stable. Furthermore the Symbol for the wireless connection is not active, even if I'm connected.

USB:
I'm not 100% whether I had this issue on feisty to that extend. My USB ports don't work or don't work well with storage devices. My camera, which worked perfectly with dapper on my old notebook, is not recognized at all. The same is true for my mp3 player and partially for my external hard drive, which works on only one of the three ports (the others work on no port). I have to check, but I guess it's not a hardware issue.

So, does anyone have the same problems, any ideas, suggestions? 

Thx,

Alex

Nobody having similar issues?

---

### Post by syxbit on 2007-07-25
gutsy is not stable
nautilus keeps crashing when trying to read my ext. USB drive.

---

### Post by deuce868 on 2007-07-27
for any of you guys following along in gutsy. The latest restricited modules package includes the initial support for the iwlwifi for intel wireless. It's a slightly older version. I had been using the 1.0 version with a custom kernel, but so far the .42 in the package seems ok.

---

### Post by trivialnobvious on 2007-07-27
It's frustrating but, like syxbit, I'm probably just going to wait for gutsy final. I need the stability and I've gotta keep a vista partition anyway.

I'm curious if there wer any hints that this hardware would have so many out-of-box problems with feisty? Should I always be so wary of brand new hardware or is there some other intuition I'm missing?

---

### Post by syxbit on 2007-07-27
nope, always be weary of new hardware.
i was lucky (ish) last time
I bought an Asus A8Jm. It workede great, except for video and wireles. I just have to wait for Dapper to come out.
The wait wasn't this long though.
I'm going to end up waiting 4-5 months without a properly working linux.
Each time I think to myself I've learnt my lesson, but it's just so tempting when you can get brand new technology at a discount.... (I jumped on the EPP deal on my thinkpad)
paid $1100 for a completely spec'd out one

---

### Post by Barleyman on 2007-07-27
> **syxbit said:**
> nope, always be weary of new hardware.
i was lucky (ish) last time
I bought an Asus A8Jm. It workede great, except for video and wireles. I just have to wait for Dapper to come out.
The wait wasn't this long though.
I'm going to end up waiting 4-5 months without a properly working linux.
Each time I think to myself I've learnt my lesson, but it's just so tempting when you can get brand new technology at a discount.... (I jumped on the EPP deal on my thinkpad)
paid $1100 for a completely spec'd out one

I don't really like pushing another distro, because I really like ubuntu, but the option of not having working linux on my machine for 4-5 months was not an option for me, so I gave Fedora 7 a try.   I have everything major working now, wireless, video, etc.  

So far it has been very stable, I just don't quite like yum as well as apt, and I don't feel there community (forums) are as nice as Ubuntu.  I plan to switch back to Ubuntu later.   

Here is what I followed
[http://forums.fedoraforum.org/showthread.php?t=159516](http://forums.fedoraforum.org/showthread.php?t=159516)

---

### Post by ybisk on 2007-07-27
Hey, 

I've been following this thread basically everyday.  I've got the T61 w/ nvidia and 4965 wireless, Almost everything works for me, graphics/sound/etc..  I went ahead and spent 20bux on a usb wireless adapter which has taken care of internet for the time being.  I'm running in feisty w/ no problems otherwise.  I haven't needed to use vista for anything.  I wouldn't hesitate buying whichever machine you want.

---

### Post by syxbit on 2007-07-28
i have fedora up and running too, just the sound never worked
i guess it's the same with gutsy
although, sometimes, in the terminal i'll get the IRQ errors

---

### Post by yohan on 2007-08-06
Has anyone gotten hdaps to work? Ive tried to get it to work for days, with different kernel versions. I started a thread for this, because this one is getting too big. If anybody can help me, please check out:
[http://ubuntuforums.org/showthread.php?p=3144951#post3144951](http://ubuntuforums.org/showthread.php?p=3144951#post3144951)

---

### Post by nemik on 2007-08-10
So i got my 14" t61 today.

gutsy tribe 4 was also released. so first off, i'm really impressed as to how well it all worked.

**SATA** had to be put in compatibility mode and then was fine. booted, X came up even with proper resolution. but it had that tv-mode problem which after a few lines added to the xorg.conf fixed it and the native 1440x900 of the widescreen looks great.

btw i have the** intel **graphics card. it even started the desktop effects and compiz with bubbly windows and fading and all that works no problem out of the box. wireless also worked out of the box with the atheros card i have but the signal is absolute crap. i think i may open up the laptop and swap the card with the intel one since i hear it works now.

**sound:** did not work but got a CVS tarball of alsa, compiled and installed it and is now great, sound is perfect.

**suspend/hibernate:** suspend worked fine but waking up the backlight would be off. this was fixed by adding acpi_sleep=s3_bios to the kernel parameters during startup.
**but** still have problems with acpi. when i unplug the AC adapter while it is running, it will do a suspend as if i closed the lid. this is insanely annoying and if anyone has a fix let me know.
hibernating has no problems.

built in bluetooth also worked great out of box.

other problems: i cannot adjust brightness with the Fn keys. sound control is fine though.
wifi signal with atheros card is abysmal, if there is a way to tweak that it would be great otherwise i'll swap out wifi card.
the keyring manager thing in gutsy is broken and doesn't remember anything. so if connecting to a WPA network with a passphrase, i have to enter it in like every time i connect.

how is everyone else doing?

---

### Post by deuce868 on 2007-08-10
> **nemik said:**
> ...
the keyring manager thing in gutsy is broken and doesn't remember anything. so if connecting to a WPA network with a passphrase, i have to enter it in like every time i connect.

Hmmm, that was fixed a while ago. I had the same issue for a while, but they corrected it. I wonder why you're still seeing that issue.

---

### Post by nemik on 2007-08-11
> **deuce868 said:**
> Hmmm, that was fixed a while ago. I had the same issue for a while, but they corrected it. I wonder why you're still seeing that issue.

This is the one issue that is driving me insane. because it is prompting me to enter crap in after every single resume even, not just restart.

other than that my biggest annoyance was solved: unplugging no longer acts as a resume. to fix this it seems all that is needed is to 'killall gnome-power-manager' then 'gnome-power-manager' in terminal. this restarting of it i don't know why but it helps in some magic way.

now if only automatix would work and i think i'd be set. gutsy is really impressing me.

---

### Post by deuce868 on 2007-08-11
> **nemik said:**
> 
now if only automatix would work and i think i'd be set

[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

Check that out. I'm not sure what you use automatix for, but you can do the things without it and I'd recommend it. 

Here's the bug info that should have fixed the keyring issue. 
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/121228](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/121228)

---

### Post by chris0 on 2007-08-12
Hey, thanks for all the help with getting things working. I've got the NVidia gpu and Atheros wireless. Got NVidia working great! Sound is still a tiny issue, but my real question is about the Atheros wireless. 

EVERYONE I see claims that atheros wireless 'just works'. For me, it just doesn't. I've run through all of the preliminary checks (wireless switch on front panel is on, wireless key is right, etc.) and they all seem good. Ubuntu automatically detects wireless networks that are in range. The problem is that it won't connect. 

I've tried reinstalling madwifi and that didn't help. I really wouldn't mind if someone who has theirs working would post their config and/or what they did to get it to work. 

Thx!

---

### Post by nemik on 2007-08-12
> **chris0 said:**
> Hey, thanks for all the help with getting things working. I've got the NVidia gpu and Atheros wireless. Got NVidia working great! Sound is still a tiny issue, but my real question is about the Atheros wireless. 

EVERYONE I see claims that atheros wireless 'just works'. For me, it just doesn't. I've run through all of the preliminary checks (wireless switch on front panel is on, wireless key is right, etc.) and they all seem good. Ubuntu automatically detects wireless networks that are in range. The problem is that it won't connect. 

I've tried reinstalling madwifi and that didn't help. I really wouldn't mind if someone who has theirs working would post their config and/or what they did to get it to work. 

Thx!

Well it does 'just work' in terms of detection. the actual 'working' is the actual problem though because the atheros madwifi driver gives it the worst signal iI have ever seen from a laptop.

Mind you this is NOT the problem of the actual Atheros card, it is a very good one and in Windows gets top marks for sensitivity and is actually one of the best performing. It's just that the madwifi driver totally sucks in getting signal with it for some reason

This has been confirmed by others and even madwifi team so hopefully it might be fixed. One solution is to use ndiswrapper but I never had good luck with it.

I already bought an intel 3945 mini-pci card on ebay, they only go for about $18 shipped and will replace the atheros with that. It's signal isn't really as good as atheros can be but will be MUCH better in linux.

---

### Post by chris0 on 2007-08-12
figures. Ok, I'll play around with it. I'm hoping I won't have to go out and buy a new card. I'll let you know what I find.

---

### Post by nemik on 2007-08-12
ok found another BIG issue (IMO).

My widescreen t61 has 3 usb ports, one on the right side by the monitor that has a green light next to it and 2 others on the left side by the PCMCIA slots.

the ONLY port that works is the one on the right side. nothing i insert on the other 2 on the left is detected even and they don't even seem to be seen.

has anyone else seen this? is it a BIOS issue maybe or ubuntu just isn't seeing them?

**FALSE ALARM:** after doing a restart i can indeed use all 3 usb drives with no problem. maybe some upgrades fixed it.

---

### Post by deuce868 on 2007-08-12
> **nemik said:**
> ok found another BIG issue (IMO).

My widescreen t61 has 3 usb ports, one on the right side by the monitor that has a green light next to it and 2 others on the left side by the PCMCIA slots.

the ONLY port that works is the one on the right side. nothing i insert on the other 2 on the left is detected even and they don't even seem to be seen.

has anyone else seen this? is it a BIOS issue maybe or ubuntu just isn't seeing them?

I use all three all the time. I actually use the left two the most since the right one is a bit harder to get back to. This has got to be something hardware-ish I would think.

---

### Post by alexsb on 2007-08-12
> **nemik said:**
> ok found another BIG issue (IMO).

My widescreen t61 has 3 usb ports, one on the right side by the monitor that has a green light next to it and 2 others on the left side by the PCMCIA slots.

the ONLY port that works is the one on the right side. nothing i insert on the other 2 on the left is detected even and they don't even seem to be seen.

has anyone else seen this? is it a BIOS issue maybe or ubuntu just isn't seeing them?

**FALSE ALARM:** after doing a restart i can indeed use all 3 usb drives with no problem. maybe some upgrades fixed it.

Totally agree! Really annoying. Are you using Gutsy? I am. However, basic stuff such as a mouse works sometimes, but more advanced stuff such as a hard drive doesn't.

---

### Post by nemik on 2007-08-12
> **alexsb said:**
> Totally agree! Really annoying. Are you using Gutsy? I am. However, basic stuff such as a mouse works sometimes, but more advanced stuff such as a hard drive doesn't.

try a restart.along with an apt-get update/upgrade. it fixed my problem somehow. and yes i'm on gutsy too, it is the only one that would even run X correctly on this laptop.

---

### Post by chris0 on 2007-08-12
OK, so for reasons mentioned above, the MadWiFi drivers don't work properly on any Atheros card. I've been battling with getting wireless working and I FINALLY got it. Here's how:

[LIST=1]
[*]Download the newest version of ndiswrapper from [http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.38.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.38.tar.gz) . 
[*]Go to IBM.com and get the driver for your Atheros (ThinkPad Wireless) card. Mine is the ThinkPad a/b/g. a/b/g/n users will need a different driver file. Mine came from [http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-52527](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-52527) . 
[*]Put both files where you'll remember them. I used the Desktop.  
[*]You'll need some tools to do this, so type the following into a terminal:
```
sudo apt-get install build-essential
apt-get install cabextract
```
If it says that build-essential is already installed, that's ok. 
[*] Now, type 
```
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils
	sudo rm -R /etc/ndiswrapper
	sudo rm /etc/modprobe.d/ndiswrapper
```
[*]change to the directory where the ndiswrapper source and driver .exe are.
```
cd ~/Desktop
	tar -xvf ndiswrapper-1.38
	cd ndiswrapper-1.38
```
[*]Now, uninstall all ndiswrapper files. Do this by typing
```
sudo make uninstall
```
repeatedly until no more files are removed. 
[*] say 
```
make
	sudo make install
```
[*] cd to the location of the driver.exe
[*]say
```
	cabextract *.exe
	cd WINXP_2K
	sudo /usr/sbin/ndiswrapper -i NET5211.INF
	sudo modprobe ndiswrapper
```
[*] Use Wireless Web
[/LIST]

NOTE: If this doesn't work, try a different driver.  I originally tried using NET5416.INF and it didn't work. I suspect that NET5416.INF is used for the Atheros a/b/g/n card. 

While I'm at it, here's how I got my NVidia Quadro card to work:
[LIST=1]
[*]You need some tools for this, so tell the Terminal
```
sudo apt-get install pkg-config 
	sudo apt-get install xserver-xorg-dev
```
[*]say 
```
sudo apt-get remove --purge nvidia-glx
```
This removes any previous attempts at installing the NVidia driver. 
[*]Edit (remember to sudo) /etc/default/linux-restricted-modules(-common) and change the line that says  ```
DISABLED_MODULES=""
``` to
```
DISABLED_MODULES="nv nvidia_new"
```
[*]say
```
sudo rm -f /lib/linux-restricted-modules/.nvidia_new_installed files /etc/init.d/nvidia-glx /etc/init.d/nvidia-kernel
```
[*]Go to NVidia.com and find their Linux driver installer and download it.
[*]kill X. I found that the easiest way to do that was to add a line to /etc/X11/xorg.conf that says anything you please ('poo on you' worked for me). Then hit Control-Alt-Backspace.
[*] log in as you and then cd to the directory that contains the installer
[*]say 
```
sudo sh <package name>
```
[*] remember to remove your extra line from /etc/X11/Xorg.conf, unless you told the installer to overwrite it. 
[*] reboot.
[/LIST]

This got me running Emerald and Beryl with OpenGL. If you don't want the eye candy, you can find out whether you have OpenGL by saying 
```
glxgears
```
to a terminal. 

Still working on how to get sound...
**EDIT: ** Here's how you do sound(ish). Install the CVS version of alsa by following the instructions at [http://alsa.opensrc.org/index.php/AlsaCVS](http://alsa.opensrc.org/index.php/AlsaCVS). If you're like me, you won't be able to install the libs or tools; that's ok. It will still work. Make sure that you have a root password (sudo su - and then passwd to set a root password) because plain old sudo doesn't seem to work. Now, say
```
su -
Password: <enter the root password>
chmod -R 777 /dev/snd
```
Your sound should work (out of the headphones only) until you reboot. I know that that's teh hax but there's not much I can say at this point. If you are teh 1337 hax you might even make a cron job that does the chmod for you every time you boot, but *I'm* not planning on trying...

---

### Post by vixensjlin on 2007-08-15
I just got my T61 (WXGA+/Nvidia/4965AGN) and tried to install ubuntu several times by following directions on  [ThinkWiki]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_Tribe_4_on_a_ThinkPad_T61").  The only version works at 1440x900 on my monitor is Gusty tribe 4.  However, I could not get nVidia work, even after installation of driver and nvidia-xconfig (NVidia X server setting report no nvidia driver running. log attached), The compling of iwlwifi also got failed (Makefile not found at '/lib/modules/2.6.22-9-generic/source').  Very appreciate if anybody can help!  Thanks!

---

### Post by Darrena on 2007-08-15
> **vixensjlin said:**
> I just got my T61 (WXGA+/Nvidia/4965AGN) and tried to install ubuntu several times by following directions on  [ThinkWiki]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_Tribe_4_on_a_ThinkPad_T61").  The only version works at 1440x900 on my monitor is Gusty tribe 4.  However, I could not get nVidia work, even after installation of driver and nvidia-xconfig (NVidia X server setting report no nvidia driver running. log attached), The compling of iwlwifi also got failed (Makefile not found at '/lib/modules/2.6.22-9-generic/source').  Very appreciate if anybody can help!  Thanks!

You shouldn't need to compile iwlwifi, the latest version will be in Gutsy very soon and the existing version should work fine for you.

Can you post your xorg.log from when X fails to start?

---

### Post by xadder on 2007-08-17
Hi everyone,

I'm looking to recommend a new laptop (+docking possibility) to a student. The T61 was suggested, but the above thread worries me - I would very much prefer something that "just works", as the student has little experience with Linux I think. Much time has elapsed since this thread started, so I have 3 options :

1. Install fiesty - maybe many of the problems have disappeared with recent updates?

2. Wait for Gutsy .... 

3. Choose another laptop. Shame, as I like IBL/Lenova stuff, but maybe this is the best option.

Recommendations welcome!

Thanks

---

### Post by deuce868 on 2007-08-17
> **xadder said:**
> Hi everyone,

I'm looking to recommend a new laptop (+docking possibility) to a student. The T61 was suggested, but the above thread worries me - I would very much prefer something that "just works", as the student has little experience with Linux I think. Much time has elapsed since this thread started, so I have 3 options :

1. Install fiesty - maybe many of the problems have disappeared with recent updates?

2. Wait for Gutsy .... 

3. Choose another laptop. Shame, as I like IBL/Lenova stuff, but maybe this is the best option.

Recommendations welcome!

Thanks

I you need a laptop that just works today then get a T60. It's the slightly older hardware model, but it should really "just work" and it's still a great thinkpad laptop. 

If you can wait for gutsy then grab a T61 with all intel hardware (wireless, graphics, etc) and it'll just work by the time Gutsy gets out the door. I'm running gutsy now and really the only big thing I'm waiting for are the patches for sound to make it into Gutsy.

---

### Post by xadder on 2007-08-17
Thanks deuce868,

I'll choose one of those options, depending on availability of T60 or wishes of the student.

It is one of the nice things with Ubuntu that if a problem arises, the next revision usually fixes it :)

---

### Post by yohan on 2007-08-27
has anyone gotten the mic to work yet with alsa cvs?

---

### Post by lode on 2007-08-27
Has anyone already tried installing the [Gutsy Gibbon Tribe 5 test release]("http://www.ubuntu.com/testing/tribe5") onto a ThinkPad T61? Are the results as positive as told [here]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_Tribe_5_on_a_ThinkPad_T61") (link to a thinkwiki.org page)?

And (if everything works fine), how is the stability of Tribe 5 (especially on the ThinkPad T61)?

Thanks in advance!

---

### Post by Kxpress on 2007-08-28
I am a Linux newbie, i.e. know nothing about the OS. I tried to install Ubuntu 7.04 on my new Levono T61. I want to learn Linux that's all. So, please be patient with me.

My ThinkPad T61 config:
- Intel Centrino Duo 2 Core T7300 2.0 GHz
- 2 GB Ram
- 120 GB SATA
- Nvidia M140 128 MB Graphic
- IntelPRO/3945 Wireless card
-15.4 WSXGA+ 1680x1050

I have used the Alternate CD Ubuntu 7.04 to install Linux along with WinXP Pro as dual-boot machine. Due to problem with X11 server. I followed instructions of some posts on the forum to 'select vesa" mode for my video to pass the installation. Wire internet works fine, wireless internet worked fine when it could connect to my home wireless router (Linksys Draft-N Router).

 However, when I turned the machine on, the wireless connection does not always find the network, I have to manually disable, then enable with WEP key back and forth few times before it made connection. Once it makes connection, it (the wireless) works fine (the longest time I've used is about 1 hour).

I want to install the appropriate Nvidia driver to use my high resolution screen (1680x1050), but some instructions found in the forum are too high level, I don't want to mess up my machine, so far it is usable in some degrees...

Anyone has a "step by step" instruction how to install Nvidia Driver? Then after that, do I need to recongigure the display again ? I mean: going to root then excecute commands such as "sudo dpkp-reconfigure xcerver-xorg" ??? because right now my screen is VGA 800x600 as the initial setup as "vesa".

Anyone experienced the wireless connection I had ? any suggestion how to avoid/improve the connection.

I have not checked Audio, MultiMedia etc ... they are not inportant, I can use Wiindow XP...

Please, don't point to some "high level" instructions, I think I read most of them ... it is too much for a newbie. Eventhough I used Unix about 10 years ago, for Linux I am confused and /or spoiled by Bill Gates's Window Installer... I do not quite to get familiar with all details of command line ..... 

Please, bear with me if you are willing to help.

Thanks,

---

### Post by gamelux on 2007-08-29
> **lode said:**
> Has anyone already tried installing the [Gutsy Gibbon Tribe 5 test release]("http://www.ubuntu.com/testing/tribe5") onto a ThinkPad T61? Are the results as positive as told [here]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_Tribe_5_on_a_ThinkPad_T61") (link to a thinkwiki.org page)?

And (if everything works fine), how is the stability of Tribe 5 (especially on the ThinkPad T61)?

Thanks in advance!

I installed Kubuntu (as well as ubuntu live CD) 7.10 Tribe 5 in my T61. No wireless and no sound so I didn't used it much more than testing to get that working. I am really frustrated :(.

Can anyone give me some help with the wireless? I have the Intel 4965 AGN wireless card and it works perfect in windows.  I am quite new at linux (user for many years, administrator for weeks).

Thanks!

---

### Post by alexsb on 2007-08-29
Is someone else noticing performance issues with their harddrives?

I turned AHCPI back on as described on thinkwiki, but my hard drive is still pretty slow.

```

hdparm -v /dev/sda

/dev/sda:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 14593/255/63, sectors = 234441648, start = 0

```

Is 16-bit ok here? Any Ideas?

---

### Post by trivialnobvious on 2007-08-29
I'm trying to install tribe 5 as we speak. It goes through the install just fine. Then it tries to reboot, the ubuntu screen pops up and I get a blank screen. I can use the fn+home/end to raise/lower brightness but that's it.

 I've got the nvidia card, 2.0 GHz core duo, intel wireless and 2 GB ram. Looking at the thinkwiki page most things should be working right out of the install. Is there some little detail missing on the thinkwiki page I'm missing to get things running?

---

### Post by kachofool on 2007-08-29
I have the same specs as you with 1gb of ram instead of 2. Did you install the video and sound drivers? Along with wireless and trackpoint/fingerprint reader I think that's all that works. There is not much working right out of the box for the T61 we have. On a good note, the sound buttons (vol up vol down) work fine =)

I posted this earlier in a thread, but for those of you running Gutsy on a T61 could you check if your /proc/acpi/ibm folder exists? Mine is missing and its existence is useful for controlling brightness which I've been unable to do on the laptop through Ubuntu. You can (hopefully) also control the fan with it, and the ThinkLight (works with the hardware keys but seems like you can do some useful stuff if you control it with software!).

Most of the important things are up an running even if it's not all automatic... it's just a major pain when it updates to a new build because the video and audio drivers have to reinstalled (I know this is always true for video, but I was suprised I had to reinstall audio).

---

### Post by durrell on 2007-08-29
Ok so I was considering the T61 but this thread has me second guessing.

Has any wireless card been proven to work? I was planning on getting the Intel Wireless WiFi Link 4965AGN instead of the ThinkPad wifi.

I'm not concerned with audio/graphics..I know I can get them working, but wireless is very important to me. It has to work.

It's either this or a MacBook, and I'm having a hard time choosing..

---

### Post by gamelux on 2007-08-29
So? Am I the only one with problems with the wireless (Intel 4965 AGN) with Tribe 5?  If so, is there anything I should install/modify to get it working?

(the front switch is on, and it works in windows if I reboot). 

I am quite new in linux, so it is hard for me to troubleshoot things. 

Any ideas or things I could try?

---

### Post by deuce868 on 2007-08-29
The support for the wireless is there. Try to modprobe iwl4965 and see what you get.

---

### Post by durrell on 2007-08-29
> **deuce868 said:**
> The support for the wireless is there. Try to modprobe iwl4965 and see what you get.

So I shouldn't have any issues getting that card to work? And the nvidia card (I'm assuming) should be fairly easy to get working? I'm using an nvidia card now and haven't had many issues except for widescreen resolutions, but that's an easy fix.

Thanks. :)

And I realize you were talking to the other guy, but you sort of inadvertently answered my question too..haha.

---

### Post by deuce868 on 2007-08-29
I can't promise the other stuff. I intentionally ordered all of the hardware to be intel based (video, wireless, etc) so that it would work easier. I'd imagine the nvidia should be ok with the restricted drivers stuff, but it's not what I have.

---

### Post by durrell on 2007-08-29
So I should go with the Intel video too? I mean I have no problem with that, it's cheaper. I just figured Nvidia had better support.

---

### Post by deuce868 on 2007-08-29
I prefer the intel video because the driver is in the kernel not an add on and the battery life is better than the nvidia driver. The nvidia has better 3d performance, but I don't have big needs for that, especially on a laptop.

---

### Post by thetejon on 2007-08-29
I just got 7.04 running on a T61 (14", Nvidia 140M, 2GB ram, 120GB hard drive, Intel 7500 processor).  I posted how I did it [here]("http://blog.complainthub.com?page_id=598").  I'm pretty inexperienced when it comes to Ubuntu and Linux in general, but I think my experience may be helpful to others.

---

### Post by gamelux on 2007-08-30
> **deuce868 said:**
> The support for the wireless is there. Try to modprobe iwl4965 and see what you get.

Hi, I modprobed iwl4965 and got no messages back. After that, the same, no wireless. 

Any other ideas? I am really really new to linux, so maybe it's something really simple that I have no idea has to be done to enable wireless.

Thx

---

### Post by durrell on 2007-09-01
So how does this look as far as compatibility goes?

  	 ThinkPad T61 with Integrated Graphics
	Intel® Core&#8482; 2 Duo T7100 (1.8GHz 800MHz 2MBL2
	14.1 WXGA TFT, w/o Camera
	Intel GMA X3100 GM965 w/ 1394
	2 GB PC2-5300 DDR2 SDRAM 667MHz SODIMM Memory (2 DIMM)
	UltraNav (TrackPoint and TouchPad)
	120GB Hard Disk Drive, 5400rpm
	CD-RW/DVD-ROM Combo 24X/24X/24X/8X Max, Ultrabay Slim
	Intel Wireless WiFi Link 4965AGN
	7 cell Li-Ion Battery

If that will work I'll be placing the order on Tuesday. :)

---

### Post by vinced on 2007-09-03
Durrell,
Your specs look like mine. With Gutsy Tribe 5 everything seems to be working.
Vince

---

### Post by trivialnobvious on 2007-09-03
looking at the thinkwiki for tribe 5 this appears to be a known problem. They recommend booting in safe graphics mode and then installing envy. I am booted up in safe graphics mode but I'm not sure how to install envy on my hard disk. I can mount it and browse it but I try to save envy to disk and I get a pop up telling me I can't save it to the disk because I cannot change the contents of the folder. I feel like I'm so close to getting this to finally work. Anyone can help me out?

---

### Post by joetaxpayer on 2007-09-03
> **trivialnobvious said:**
> looking at the thinkwiki for tribe 5 this appears to be a known problem. They recommend booting in safe graphics mode and then installing envy. I am booted up in safe graphics mode but I'm not sure how to install envy on my hard disk. I can mount it and browse it but I try to save envy to disk and I get a pop up telling me I can't save it to the disk because I cannot change the contents of the folder. I feel like I'm so close to getting this to finally work. Anyone can help me out?
I followed these instructions and it worked fine:

[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu]("http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu")

---

### Post by durrell on 2007-09-03
> **vinced said:**
> Durrell,
Your specs look like mine. With Gutsy Tribe 5 everything seems to be working.
Vince

Awesome, I'm planning to order tomorrow. :D

Thanks for the help.

---

### Post by wasapeas on 2007-09-07
I'm getting fairly pathetic volume levels out of my T61, even with the PCM channel turned up to 100%. It's audible but not enough to actually be comfortable listening for... well, anything. With headphones on it's a little bit better, but even at 100% it's still just about comfortable listening.

I'm using the latest dev versions of ALSA (alsa-driver-1.0.15rc1) compiled from source.

There's only one volume control channel in alsamixer (PCM)--on my older laptop I see separater master, headphone, and PCM channels. Is this normal?

Anybody else seeing this on the T61?

---

### Post by syxbit on 2007-09-10
i'd not been planning on trying ubuntu again until gutsy final (tried so many times, and it never works)
maybe i'll try again with alsa 1.15rc1
are you still getting the IRQ errors when you leave a terminal open ?

---

### Post by Scabby_al on 2007-09-10
I installed Feisty on my R61, performed all updates, rebooted, used Envy to install new Nvidia drivers and X starts normally. However, when I log into any account (failsafe or normal), the wallpaper comes up but none of my desktop icons appear. This has happened with any video driver and its very annoying. I would love to use Linux on my work computer instead of windows but I need a functioning desktop.

---

### Post by justin on 2007-09-13
I just installed Gutsy Tribe 5 and did a complete update/upgrade. I have the intel 3945ABG wireless card. It works, detects and connects to my network, but does not get above 200 KB/s on any type of transfer. Anyone having this problem?

---

### Post by omega_user on 2007-09-15
hey guys. I own a t61 and i got mine to work perfect(ish) here's the specs:
T61
 Core 2 Duo 2.0ghz
 Intel turbo memory
 7.04 feisty 32bit
 NVS 140M
 3945ABG wireless
 Ethernet
 Cd burner (no dvd burner)

I had a lot of problems but now I've now exactly whats up. Ubuntu doesn't like the AHCI mode (or whatever) in the bios. You need to set to compatibility or it can't auto mount cd's and dvds and it just doesn't work.  So Compatibility is necessary.  my wireless card worked out of the box perfect, however u guys seem to have the newer AGN (i didn't buy that one because i assumed compatibility issues would occur). 

64 bit, although faster, isn't a good idea because of it being unsupported by flashplayer and wine. I did install it but decided that 32 bit was a better overall choice.  

The 140M NVS works great after I got the new drivers [how to install drivers]("http://blog.complainthub.com/?page_id=598")

Turbo Memory is recognized as a mmeory storage device but Ubuntu doesn't know what to do with it 
              * lspci* **returns** *02:00.0 Memory controller: Intel Corporation Unknown device 444e (rev 01)*

cd burner works fine

**Recommended:** if you have 64bit installed or AHCI turned on. Reinstall Ubuntu in 32bit with the AHCI turned off during install (and leave it off, or else it'll mess up the system). For the wireless, I'd wait to see if gutsy will support it. If you can't wait for the actual release you could just change your apt sources list to gutsy registries "Not recommended"

**What I still need to know**: Is there any way that turbo memory could be made to work? Like telling Preload to treat it as a storage space for swap? Because if it's treat that as swap, startups would go much faster for me, seeing as it is basically readyboost. 

Thanks...this forum was a great idea!

---

### Post by Paab on 2007-09-22
Hello Everyone,
i am new in the ubuntu world but thank to all the forums i managed more or less to install Feisty Fawn 7.04 from the live cd on my T61,
like evryone i had the nvidia driver problem, so i started with the vesa driver and the modprobe = piix, removed the break=top in the grub file etc... till there evrything ok.
I made an automatic update, and i think it brought my kernel from 2.6.20-15 to 2.6.20-16 
And it s been 5 days i tried evry possible methods i found online to install the latest Nvidia driver working with my NVS140m, withouet any success, here what i tried ;

Envy automatic install, evrything look like it would work but my resolution gets down to 640x480, imposssible to get it higher, even vesa did better.
so i tried to reconfigure the xserver with *nvidia-xconfig * and with *dpkg-reconfigure xserver-xorg* rebooted the xserver and got the x server sytematicaly crashed ; last error message was if i remeber well, Screen found, but none has an usable config

I tried as well to install the driver manally, just followed a tutorial with the right driver, dowloaded directly on the nvidia page the drivers, it did a lot of stuff i didn t undertand but it looked like it recompiled something, says in the driver sucessfuly intalled in the end, i reboot, xserver down again so i cp the backup of my xorg.conf file, to restore the xserver.

i am really out of idea of what to do next , evryone says on the forum no more problem with the new nvidia driver, so why do i?  did anyone had his resolution stuck down to 640x480? the ubuntu resolution changer doesnt even propose 1024x768


here is my xconf file : (i removed some parts)

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

I wonder if people with T61, 140M NVS and the driver working have the same...
Other things i tried     Option "UseEDID" "FALSE", or adding resolution manually.

If anyone has an idea of what else i could try, i ll be glad to try,
thanks for any help

---

### Post by omega_user on 2007-09-23
the thing is you don't have to do any editing of files or stuff.  Doing that probably destroyed something. To get it to work follow these steps, they worked perfectly for me.  

Messing with the kernel might be your problem...each time the kernel gets updated you need to grab the correct driver over again.

[STEP BY STEP DRIVER INSTALL]("http://trevsblog-life.blogspot.com/2007/09/how-to-install-feisty-on-t61.html")

Since you messed with conf files and the kernel I'd recommend just reinstalling and following the directions from the start.

---

### Post by Paab on 2007-09-24
Thanks, trying right now...

---

### Post by Paab on 2007-09-24
Thanks !  it worked ! realised the driver i installed manually wasnt the one up to date, no more problem with this version, great!!

---

### Post by omega_user on 2007-09-24
no problem Paab...glad to be of help...

---

### Post by syxbit on 2007-09-24
gutsy seems to have fixed sound now, but the volume up/down keys on the laptop now control the microphone volume.....

---

### Post by justin on 2007-09-24
Just did an update today, and now neither the wifi or sound is working. :(

Sorry if this post isn't very informative, but I'm very tired at the moment.

---

### Post by omega_user on 2007-09-24
> **syxbit said:**
> gutsy seems to have fixed sound now, but the volume up/down keys on the laptop now control the microphone volume.....

go to the sound preferences in system > preferences > sound and set them to ALSA mixer, then at the bottom, highlight PCM and hit ok, or exit

that should do it because that same thing happened to me and it worked

---

### Post by syxbit on 2007-09-27
any of you guys have a dock, and tried getting coax audio to work?
it's a nightmare

---

### Post by LazyBoy on 2007-10-12
My T61 with X3100 running Kubuntu Feisty has been driving my 1920x1200 display via the Adv. Mini Dock DVI for months.

But when I moved the dock and LCD to a different location, I had trouble getting it to work again (even though I had no sw or config changes). The monitor was displaying a "signal out of range message". I rebooted a few times with the same result.

The only difference from the earlier set up was that I had had a VGA cable from the dock to the same LCD as well as the DVI (because of some initial issues getting video with the dock).

I added the VGA cable and the DVI now works!

Can anyone guess why?  Does my xorg.conf suck?
I'm attaching the xorg.conf and the good and bad Xorg logs.

Thanks,
LB

---

### Post by syxbit on 2007-10-12
here's my xorg with an external 24" 1920*1200 monitor
you should be able to use almost all of this (except you're intel and I'm nvidia)

```

# Xorg SyXbiT - Thinkpad T61 w/ nVidia Quadro NVS 140M

Section "ServerLayout"
	Identifier	"Layout0"
	Screen 0	"Screen0" 0 0
	InputDevice	"Keyboard0" "CoreKeyboard"
	InputDevice	"Mouse0" "CorePointer"
EndSection


Section "Files"
	RgbPath		"/usr/lib/X11/rgb"
EndSection


Section "Module"
	Load		"dbe"
	Load		"extmod"
	Load		"type1"
	Load		"freetype"
	Load		"glx"
EndSection


Section "ServerFlags"
	Option		"Xinerama" "0"
EndSection


Section "InputDevice"
	Identifier	"Mouse0"
	Driver		"mouse"
	Option		"Protocol" "auto"
	Option		"Device" "/dev/psaux"
	Option		"Emulate3Buttons" "no"
	Option		"Buttons"	"7"
	Option		"ButtonMapping"	"1 2 3 6 7"
	Option		"ZAxisMapping"	"4 5"
  	Option		"EmulateWheel"          "true"
   	Option		"EmulateWheelButton"    "2"
EndSection

Section "InputDevice"
	Identifier	"Mouse1"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection


Section "InputDevice"
	Identifier	"Keyboard0"
	Driver		"kbd"
EndSection


Section "Monitor"
	Identifier	"Monitor0"
	VendorName	"BenQ"
	ModelName		"BenQ 241W"
	HorizSync		30.0 - 83.0
	VertRefresh	56.0 - 76.0
	Option		"DPMS"
	Option		"DynamicTwinView"	"FALSE"
EndSection


Section "Device"
	Identifier	"Videocard0"
	Driver		"nvidia"
	VendorName	"nVIdia"
	BoardName		"Quadro NVS 140M"
EndSection


Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	DefaultDepth	24
	Option		"TwinView" "0"
	Option		"metamodes" "DFP-1: nvidia-auto-select +0+0"
   	SubSection	"Display"
        	Depth	24
		Modes	"1920x1200_60" "1440x900_60"
    	EndSubSection
EndSection


```

---

### Post by LazyBoy on 2007-10-18
> **omega_user said:**
> [QUOTE=syxbit;3420841]gutsy seems to have fixed sound now, but the volume up/down keys on the laptop now control the microphone volume.....
go to the sound preferences in system > preferences > sound and set them to ALSA mixer, then at the bottom, highlight PCM and hit ok, or exit

that should do it because that same thing happened to me and it worked[/QUOTE]

Anyone know the equivalent for KDE/Kubuntu??

LB

---

### Post by justin on 2007-10-19
How long until the brightness controls work with the nvidia card do we think? Really the only thing not working under Gutsy.

---

### Post by sgla1 on 2007-10-21
see Bug #155245 in launchpad.  What happens is that the installer selects the 'nv' driver which does not support the nvidia graphics card.  End result--x refuses to start.

Solution: boot into rescue mode (single user, no x).  Run dpkg-reconfigure xserver-xorg > select the 'vesa' driver.  Afaik, the best resolution supported is 1024x768.  Reboot or *init 2*; use the handy restricted_drivers_manager to enable nvidia driver.  Run dpkg-reconfigure xserver-xorg *again* and select the correct resolution for your screen size.  Restart x.

Note--same solution for gutsy.

---

