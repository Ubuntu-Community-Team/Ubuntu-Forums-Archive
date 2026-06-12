---
title: "HP Mini with SSD drive, drive not recognized"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by Donald F. Robertson on 2009-06-12
Using both standard install and alternate install of the desktop version of 9.04, I cannot get the installation to recognize the SSD drive.  In the standard install, the partition manager loads, but shows up blank.  In the alternate install, I'm asked which driver to use.  None appear appropriate for an SSD.

Any suggestions?  I'm not a power user, so I may need pretty much "cookbook" style instructions. . . .

Thanks!

-- Donald

---

### Post by chadk5utc on 2009-06-12
Is the drive recognized in the BIOS?

Chad







Asus 1000HE 32GB SSD 2GB RAM Eeebuntu 2.0 Plus Extras 100% Working

---

### Post by Donald F. Robertson on 2009-06-13
Apparently.  It is in the boot order list.  I'll look more closely when I'm in front of the computer tonight.

Thanks!

-- Donald

---

### Post by Donald F. Robertson on 2009-06-14
I did a HDD test in bios and it reported success.  So, I guess the bios must recognize it.

-- Donald

---

### Post by chadk5utc on 2009-06-15
ok good that the bios sees it, what type SSD is it, size, and manufacture? although really shouldn't matter as long as its listed in the bios the OS should see it. so try this. Boot a live CD watch closely and you should be able to see it show HDD will likely be listed as HDA or SDA may or may not have a number after it?
mine shows as sda/sda1
in a terminal try this: sudo gparted
this is a partition manager and sudo does as ROOT if the drives recognized it should be there.

---

### Post by Donald F. Robertson on 2009-06-17
Okay, the failure to recognize the SSD is intermittent.  It did recognize it in one case, and I was able to get the hard drive partitioned Netbook Remix installed.  Now, I'm running into the same problem: it has yet to successfully boot into the installed program.  The issue appears to come up right at the beginning of the boot and affected both the installation program (in all its varieties) and the installed program.

Any new ideas?

Thanks!

-- Donald

---

### Post by Donald F. Robertson on 2009-06-18
Here's what appears on the screen when it fails:

[3.520568] [<c0503a95>] oops_end+0xz5/0xc0
[3.520568] [<c0106e61>] die+0x51/0x70
[3.520568] [<c0505361>] do_page_fault+0x341/0x790
[3.520568] [<c0154955>] ? sched_clock_cpu+0xc5/0x170
[3.520568] [<c012daad>] ? update_shares+0x1d/0x70
[3.520568] [<c0133f18>] ? load_balance+0x1d8/0x3e0
[3.520568] [<c01520eb>] ? hrtimer_get_next_event+-x10b/0x130
[3.520568] [<c01568f3>] ? getnstimeofday+0x53/0x110
[3.520568] [<c01468f3>] ? getnstimeofday+0x53/0x110
[3.520568] [<c01568f3>] ? getnstimeofday+0x53/0x110
[3.520568] [<c0505020>] ? do_page_fault+0x0/0x790
[3.520568] [<c0503082>] error_code+0x72/0x88
[3.520568] [<c015fa14>] ? generic_8m0_call_function_single_interrupt+0x34/0xb0
[3.520568] [<c0118aed>] smp_call_function_single_interrupt+0x1d/0x40
[3.520568] [<c01052b8>] call_function_single_interrupt+0x1d/0x40
[3.520568] [<c03195b9>] ? acpi_idle_enter_simple+0x153/0x18e
[3.520568] [<c040f4df>] cpuidle_idle_call+0x6f/0xd0
[3.520568] [<c010285d>] cpu_idle+0x6d/0xd0
[3.520568] [<c04f110e>] rest_init+0x4e/0x68
[3.520568] [<c07378fd>] start_kernel+0x310/0x34c
[3.520568] [<c07373a4>] ?unknown_bootoption+8x8/0x1f8
[3.520568] [<c0737099>] __init_begin+-x99/0xa1
[3.520568] ---[ end trace d61d9427101bf268 ]---

This suggest anything?

Thanks!

-- Donald

---

### Post by Donald F. Robertson on 2009-06-19
Somebody in the HP-2140 Forum suggested turning off the dual core option in the bios, and that worked at least for installation and boot.  X appears very unstable, at least in the Netbook Remix.  I think I'll try the desktop version. . . .

-- Donald

---

