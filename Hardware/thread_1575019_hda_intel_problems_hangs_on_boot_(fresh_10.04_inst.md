---
title: "hda_intel problems: hangs on boot (fresh 10.04 installation)"
date: 2010-09-15
forum: Hardware
---

### Post by CptOblivious on 2010-09-15
Hi,

I'm experiencing some problems when I'm booting my fresh 10.04 kubuntu installation. 

When I tried the LiveCD at first, it didn't boot. I added the options "xforcevesa nomodeset acpi=off noapic" and removed "splash" and "quiet" from the boot line and then it worked and I managed to install kubuntu.

When I now boot from the HD without these additional options I get the message "udev: starting version 151" and then it freezes. After 61 seconds I get the message "BUG: soft lockup - cpu stuck for 61s" (CPU#0 is stuck on plymouthd, CPU#1 is stuck on S37apparmor).

When I add the options "xforcevesa nomodeset acpi=off noapic" to the bootline, it boots a bit further, but then it stops again. I get a screen full of "hda-intel: spurious response 0x0:0x0, last cmd=0x0f0000" messages, and then after a second:

> hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x000f0001
hda-intel: no codecs installed

When I press Ctrl+Alt+F2 trough F6 I get a blank screen with only a caret. But when I press Ctrl+Alt+F7, I see these last messages:

> init: dbus pre-start process (650) terminated with status 1
* Starting AppArmor profiles
* Setting sensors limits
Skip stopping firewall: ufw (not enabled)

This happens both in the normal mode and in the recovery mode.

I Googled a bit and found out that disabling the audio in BIOS worked for some, but my system doesn't have that option. It also seems that I can't log in on a terminal. When I press Ctr+Alt+F2, all I see is a blank screen and a caret; I can't type anything.

I have a Toshiba Satellite A350, which seems to work on Ubuntu for other people. I have a ATI Mobility Radeon HD 3650 and an Intel processor and motherboard (Mobile Intel PM45 Express Chipset).

So my question is if anyone knows a solution to this problem, or maybe a version or other distro that might work (but I've seen many posts about hda-intel problems on several versions and other distros)? It also seems that I can't log in on a terminal, so I'm stuck. If someone knows a solution, I'd be very grateful.

Thanks

---

### Post by dino99 on 2010-09-15
have you tried to use distro without kde (ubuntu, xubuntu, lubuntu) ?

you can test with these others settings on the boot line: irqpoll, nomodeset, noacpi, nolapic, noapic (better to remove quiet splash to let you see warnings and errors while booting)

---

### Post by CptOblivious on 2010-09-15
> have you tried to use distro without kde (ubuntu, xubuntu, lubuntu)?

I haven't tried one of those, but I'm now downloading ubuntu 32-bits (now I have kubuntu 64-bits installed). I'll try it out when it's finished. But since the problem occurs before the X server is even started, I'm not very hopeful that it will work on GNOME and not KDE.

> you can test with these others settings on the boot line: irqpoll, nomodeset, noacpi, nolapic, noapic (better to remove quiet splash to let you see warnings and errors while booting)

I added irqpoll and nolapic, I already had the others and removed quiet&splash. Now the computer is completely frozen. It shows a call trace, I can't switch to another terminal and no "cpu lockup" messages are shown.

Here's the call trace:
[LIST]
[*]panic
[*]oops_end
[*]no_context
[*]__bad_area_nosemaphore
[*]elv_queue_empty
[*]bad_area_nosemaphore
[*]do_page_fault
[*]azx_update_rirb
[*]default_spin_lock_flags
[*]azx_interupt
[*]_spin_lock
[*]try_one_irq
[*]tick_handle_periodic
[*]note_interrupt
[*]handle_level_irq
[*]handle_irq
[*]do_IRQ
[*]ret_from_intr
[*]mwait_idle
[*]atomic_notifier_call_chain
[*]cpu_idle
[*]rest_init
[*]start_kernel
[*]x86_64_start_reservations
[*]x86_64_start_kernel
[/LIST]

---

### Post by CptOblivious on 2010-09-15
I downloaded the PCLinuxOS LiveCD and it worked flawlessly on my system, except I had to use vesa for the Xserver. After installing, it booted without a problem and I managed to install the correct ATI drivers. The sound also worked (even while running the LiveCD) and Intel HDA works on PCLinuxOS without any problems. I think I'll give up on ubuntu for this system.

Thanks anyway

---

