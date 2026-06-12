---
title: "memory corruption detected in low memory message at boot"
date: 2009-03-25
forum: Hardware
---

### Post by bernie9998 on 2009-03-25
I get this error almost immediately after booting up in both 9.04 alpha 6 live cd and also when installed:
```

[   59.816156] Corrupted low memory at ffff88000000fcf0 (fcf0 phys) = 8384000000000000
[   59.816291] Corrupted low memory at ffff88000000fcf8 (fcf8 phys) = 0010000a
[   59.816404] ------------[ cut here ]------------
[   59.816407] WARNING: at /build/buildd/linux-2.6.28/arch/x86/kernel/setup.c:719 check_for_bios_corruption+0xdd/0xe0()
[   59.816410] Memory corruption detected in low memory
[   59.816514] Modules linked in: ppdev bridge stp bnep input_polldev joydev lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm arc4 ecb snd_seq_dummy snd_seq_osssnd_seq_midi snd_rawmidi snd_seq_midi_event iwlagn uvcvideo snd_seq iwlcore compat_ioctl32 snd_timer snd_seq_device psmouse videodev mac80211 snd soundcore video ricoh_mmc sdhci_pci sdhci serio_raw pcspkr asus_laptop intel_agp v4l1_compat output snd_page_alloc iTCO_wdt iTCO_vendor_support cfg80211 led_class ohci1394 ieee1394 tg3 fbcon tileblit font bitblit softcursor
[   59.816576] Pid: 0, comm: swapper Not tainted 2.6.28-11-generic #37-Ubuntu
[   59.816579] Call Trace:
[   59.816582]  <IRQ>  [<ffffffff80250927>] warn_slowpath+0xb7/0xf0
[   59.816594]  [<ffffffff8023e6f0>] ? enqueue_task+0x50/0x60
[   59.816598]  [<ffffffff8024816d>] ? resched_task+0x2d/0x90
[   59.816604]  [<ffffffff8069cc20>] ? printk+0x67/0x6f
[   59.816609]  [<ffffffff8023ec6a>] ? __wake_up_common+0x5a/0x90
[   59.816614]  [<ffffffff8024054e>] ? __wake_up+0x4e/0x70
[   59.816619]  [<ffffffff8026e6fc>] ? sched_clock_cpu+0xcc/0x160
[   59.816623]  [<ffffffff802168dd>] check_for_bios_corruption+0xdd/0xe0
[   59.816628]  [<ffffffff802168e0>] ? periodic_check_for_corruption+0x0/0x40
[   59.816633]  [<ffffffff802168e9>] periodic_check_for_corruption+0x9/0x40
[   59.816638]  [<ffffffff8025be89>] run_timer_softirq+0x179/0x260
[   59.816644]  [<ffffffff802737af>] ? clockevents_program_event+0x4f/0x90
[   59.816648]  [<ffffffff80256acc>] __do_softirq+0x9c/0x170
[   59.816653]  [<ffffffff80213d8c>] call_softirq+0x1c/0x30
[   59.816657]  [<ffffffff80214ffd>] do_softirq+0x5d/0xa0
[   59.816661]  [<ffffffff8025684d>] irq_exit+0x8d/0xa0
[   59.816667]  [<ffffffff80227608>] smp_apic_timer_interrupt+0x88/0xc0
[   59.816671]  [<ffffffff80213668>] apic_timer_interrupt+0x88/0x90
[   59.816673]  <EOI>  [<ffffffff804751b8>] ? acpi_idle_enter_bm+0x28a/0x2da
[   59.816682]  [<ffffffff804751b0>] ? acpi_idle_enter_bm+0x282/0x2da
[   59.816687]  [<ffffffff8058e695>] ? cpuidle_idle_call+0xa5/0x100
[   59.816693]  [<ffffffff80210e85>] ? cpu_idle+0x65/0xc0
[   59.816698]  [<ffffffff8068b19c>] ? rest_init+0x5c/0x70
[   59.816701] ---[ end trace 7fc19544ca61ee62 ]---

```

Initially thinking this was a hardware issue, I attempted to find the memory error with memtest86+.  However, when memtest86+ did not find any issues, and I found that swapping the two memory sticks yielded the same error with the same addresses, I became suspicious that this might have been a kernel bug.

Also, trying ubuntu 8.10 with the same machine, I found a different error, though similar:
```

[   63.933700] Pid: 5072, comm: modprobe Not tainted 2.6.27-7-generic #1
[   63.933702]
[   63.933702] Call Trace:
[   63.933709]  [<ffffffff8033dea8>] proc_register+0x1e8/0x220
[   63.933712]  [<ffffffff8033e102>] proc_mkdir_mode+0x42/0x60
[   63.933714]  [<ffffffff8033e136>] proc_mkdir+0x16/0x20
[   63.933720]  [<ffffffffa03b1e99>] acpi_video_bus_add_fs+0x2d/0x199 [video]
[   63.933724]  [<ffffffffa03b3251>] acpi_video_bus_add+0xe8/0x2f7 [video]
[   63.933738]  [<ffffffff803ee550>] acpi_device_probe+0x4e/0x91
[   63.933743]  [<ffffffff80430552>] really_probe+0x72/0x1a0
[   63.933747]  [<ffffffff804306d0>] driver_probe_device+0x50/0x60
[   63.933750]  [<ffffffff8043076b>] __driver_attach+0x8b/0x90
[   63.933753]  [<ffffffff804306e0>] ? __driver_attach+0x0/0x90
[   63.933755]  [<ffffffff8042fcdb>] bus_for_each_dev+0x6b/0xa0
[   63.933759]  [<ffffffff802e1ecb>] ? kmem_cache_alloc+0x8b/0xd0
[   63.933762]  [<ffffffffa0079000>] ? acpi_video_init+0x0/0x63 [video]
[   63.933765]  [<ffffffff804303b1>] driver_attach+0x21/0x30
[   63.933768]  [<ffffffff8042f548>] bus_add_driver+0x1f8/0x270
[   63.933771]  [<ffffffffa0079000>] ? acpi_video_init+0x0/0x63 [video]
[   63.933774]  [<ffffffff80430965>] driver_register+0x75/0x170
[   63.933778]  [<ffffffffa0079000>] ? acpi_video_init+0x0/0x63 [video]
[   63.933781]  [<ffffffff803ee8a6>] acpi_bus_register_driver+0x43/0x45
[   63.933784]  [<ffffffffa0079041>] acpi_video_init+0x41/0x63 [video]
[   63.933787]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
[   63.933791]  [<ffffffff8026c261>] ? __blocking_notifier_call_chain+0x21/0x90
[   63.933795]  [<ffffffff8027d085>] sys_init_module+0xb5/0x1f0
[   63.933799]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
[   63.933800]

```

This is all on a brand new lenovo laptop (IdeaPad Y530).  It seems very odd that such a error would manifest almost immediately after boot, yet memtest fails to see it.  Is this a kernel bug or a hardware issue?

Any help with this issue would be greatly appreciated.

---

### Post by y530user on 2009-03-28
Hello.  I just received my IdeaPad Y530 - 405166U today.  I have not tried using 8.10, but I receive the same exact same error message that you did under 9.04 beta (same memory addresses, etc (word-for-word)).  I ran memtest before googling the error, and memtest did not find any errors.

---

### Post by bernie9998 on 2009-03-30
Sounds like we're in the same boat here.  I happen to have the same 405166U variant as well.

Nice to know it's a kernel bug and not a defect (what are the chances of the same exact defect occurring to both of us?)

Are you having suspend issues on your laptop as well?  I wonder is this error is related-- Whenever I try to suspend, I just get a blank screen with a blinking cursor.  The laptop remains unresponsive at that point.

If you find a solution to this, please post it-- not being able to suspend my new laptop has been quite a nuisance.

---

### Post by bernie9998 on 2009-03-30
I believe I found a bug report on launchpad that applies to our issue.

I updated the issue with the error message I've been receiving:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/324894/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/324894/)

---

### Post by go2dell on 2009-04-27
I've noticed this happening on the release kernel.  Added my report in Launchpad.

---

### Post by meatlover on 2009-04-28
I'm getting very similar errors, please read this link

[http://ubuntuforums.org/showthread.php?p=7165346#post7165346](http://ubuntuforums.org/showthread.php?p=7165346#post7165346)

---

### Post by birumak on 2010-06-18
guys i have the same problem with my Dell Optiplex GX260, plix help

---

### Post by nutznboltz on 2010-10-11
I was able to get a DELL Dimension 4500S that experienced "BIOS memory corruption" to install 10.10 by using 

memory_corruption_check_size=128K

in the boot options.

The default is

memory_corruption_check_size=64K

but it seems that's not enough for some systems.

---

### Post by nutznboltz on 2010-10-11
An interesting thread:

[http://linux.derkeiler.com/Mailing-Lists/Kernel/2009-07/msg04621.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2009-07/msg04621.html)

> From: "H. Peter Anvin" <hpa@xxxxxxxxx>
> Date: Fri, 10 Jul 2009 07:59:01 -0700
> Re: Intel BIOS - Corrupted low memory at ffff880000004200
>
> Ingo Molnar wrote:
>
>
>> So I'd really like to know what is happening there,
>> instead of just zapping support for 64K of RAM on the
>> majority of Linux systems.
>>
>> We might end up doing the same thing in the end
>> (i.e. disable that 64k of RAM) - but it should be an
>> informed decision, not a wild stab in the dark.
>
>
> Speaking as a boot loader author, I can let you know that
> these kinds of problems are in no [ways] limited to
> suspend/resume.
>
> Pretty much any time you're executing BIOS code you're
> going to have *some* platform which has severe memory
> corruption somewhere. This is particularly painful for boot
> loaders, obviously, because the BIOS corrupts the boot
> loader as it is running. In most cases, there simply isn't
> any way to prevent the corruption, and it's simply dumb
> luck that you will boot most of the time.
>
> And no, I don't think EFI is going to magically solve
> anything. EFI will just spread the same class of corruption
> problems over the entire memory map. It will reduce the
> density of such bugs -- in particular it will eliminate
> the "right offset, wrong segment" as well as "idiot coding
> assembly" class of problems -- but it will not confine the
> ones that can and will happen; it's still fundamentally a
> super-privileged flat memory space.
>
> The root cause seems to be a lack of verification practices
> in the BIOS industry in the post-DOS era. Back when DOS was
> still a commercially significant system, the BIOS didn't
> just support the running OS, it also directly supported
> running applications. That put a relatively high bar on how
> broken your BIOS could be and still have a viable platform.
> These days, it doesn't look like neither the BIOS vendors
> nor the OEMs necessarily even know how to QA, and since the
> BIOS industry is relatively small and highly consolidated,
> if there isn't sufficient OEM pressure it simply won't
> happen since there is no money in it.
>
> The HDMI case is a good example -- that probably involved
> SMI being triggered and the SMI code then clobbering a wild
> pointer.
>
> -hpa
>
> --
> H. Peter Anvin, Intel Open Source Technology Center
> I work for Intel. I don't speak on their behalf.

---

### Post by iandouglas on 2010-10-26
> **nutznboltz said:**
> I was able to get a DELL Dimension 4500S that experienced "BIOS memory corruption" to install 10.10 by using 

memory_corruption_check_size=128K
but it seems that's not enough for some systems.

I installed 10.04 and 10.10 just fine on a Dell/Alienware m17x, but only recently has the "corrupted low memory" issue been a real drain on system performance, even on 10.4. It's like something changed in the kernel/startup (I don't pretend to understand where it's happening) some time in the last 2-3 months. I really notice the slowdown when I have Chrome running, but still get the error in my syslog every 60 seconds even when I kill Chrome.

I was ready to swap out my RAM, thinking maybe my RAM was going bad, and now see it's a kernely/startup issue.

I added the 128K option in my grub setup and *still* get the corrupted low memory errors during everyday use. Should I try setting it higher?

---

### Post by nutznboltz on 2010-10-28
> **iandouglas said:**
> I added the 128K option in my grub setup and *still* get the corrupted low memory errors during everyday use. Should I try setting it higher?
Can't hurt to try.
I got the 128K for DELL 4500S by examining the range of memory corruption reported by kernel messages.  Other systems may have different requirements.

---

### Post by iandouglas on 2010-11-17
I've tried 32kb, 64kb, 128kb, 256kb, and 512kb, and none of them help.

I'm at a loss, and the performance on the machine gets SO slow when this happens.

Any other advice would be awesome.

---

