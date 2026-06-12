---
title: "Gateway laptop - function keys"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by ward83 on 2007-07-04
I have Ubuntu 7.04 feisty installed on my Gateway MX6030, and I'm having an issue with my volume and brightness function keys. Both work fine for adjusting brightness and volume, but the bios tries to show the built-in volume and brightness icons on the upper left of the screen, and they look all garbled. Also, this causes my mouse pointer to disappear for a few seconds. Is this something hard-coded to the BIOS? Has anyone else ever had a problem like this?

---

### Post by treesurf on 2007-07-04
I have a similar problem with my Gateway NX570.  The audio keys work just fine but the brightness keys only toggle between high and low, with no intermediate steps, and sometimes the mouse pointer does the dissappearing act briefly.

---

### Post by ward83 on 2007-07-05
My brightness and volume keys both work fine, I just can't figure out how to disable the default volume and brightness indicators. There are no options in the BIOS, and the BIOS updates for my laptop on Gateway's site won't install for some reason.

---

### Post by antmo on 2007-07-08
i too am having the brightness/cursor issue.  the best it will do is toggle between bright and dim (2 states).  i have the bios set to disable auto-dim and output lcd+crt, after having tried all the combos, all having the same behavior.  sometimes the small blue graphic shows up "properly", sometimes it is just a bunch of dots on a white background (same size/location though).  the cursor also disappears once in a while, sometimes for no reason i can determine and almost always if i try to adjust the brightness via the hotkeys.  i found simply opening an app will restore it (probably x re-painting/initializing the screen, bringing the graphics driver back into a good state again).

my sound, volume keys, trackpad and sleep work great through...no problems there.

btw, it's a gateway laptop, mt6840 running ubuntu 7.04+standard updates.

has anyone created a bug/fix request for this?

mjb

---

### Post by pavkb on 2007-07-16
Sound keys work perfect for me. But the  screen brightness keys just blank out the screen & return back to same brightness as before.

Is there any gnome applet which would adjest the screen brightness?
My laptop is gateway MX6453.

---

### Post by marsmissionaries on 2007-07-19
Gateway mx6433, ubuntu 7.04, the brightness and volume keys produce the same garbled icons in the left corner. I think it may be videocard related, can you guys post your specs?

---

### Post by cadragon on 2007-07-26
Same problem here with a Gateway Mx6943m, just 2 states for monitor brightness

```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

```

---

### Post by Robbie Pence on 2007-08-18
Same here. Is there a way to get this fixed in Gutsy Gibbon?
In other words, can we contact Ubuntu dev team easily about it?

---

### Post by cadragon on 2007-08-18
Yes, I think we should fill a bug at launchpad. But I think that's already filled... I'm not sure I'll have to look for it

---

### Post by Mizzou_Engineer on 2007-09-09
I'm running an S-1725C tablet (aka C-120X/E-155C). Here's what I have:

Fn+F1 (kill LED indicators): works
Fn+F2 (WLAN on/off): works
Fn+F3 (suspend-to-RAM): works (FYI: I'm using s2ram)
Fn+F4 (LCD/CRT toggle): works
Fn+F6 (Bluetooth): didn't order Bluetooth, so I can't tell if it would work or not.
Fn+F7 (screen brightness overrride): works
Fn+F8 (volume down): works
Fn+F9 (volume up): works
Fn+F10 (volume mute): works
Fn+F11 (F12 key): works
Fn+left arrow (dim screen): does not work
Fn+right arrow (brighten screen): does not work

The screen brightness keys seem to be a real issue with many people, myself included. I looked on the "Howto Screen Brightness on HP Laptops" and I have a /proc/acpi/video/GFX0 rather than a /proc/acpi/video/VGA as they had in their HOWTO. The only thing that looks promising is that /proc/acpi/video/GFX0/DD04 does have something listed for the brightness:

```

levels: 100 56 0 14 28 42 56 70 84 100
current: 0
```

This *seems* to be where the brightness is located. The Fn+F7 override has three settings: minimum, medium, and high-bright, so 100/56/0 sounds right. The Fn+arrow keys have many more graduated steps, so the latter part sounds reasonable for those. But pressing Fn+an arrow key just makes the kernel "oops:" Oops: [1] SMP CR2: 000000000000004. Pressing it again yields no oops. The dmesg gives the following:

```
[  488.127244] Unable to handle kernel NULL pointer dereference at 0000000000000004 RIP: 
[  488.127251]  [<ffffffff8849059e>] :video:acpi_video_device_notify+0x77/0x10a
[  488.127266] PGD 62474067 PUD adac3067 PMD 0 
[  488.127272] Oops: 0000 [1] SMP 
[  488.127276] CPU 0 
[  488.127280] Modules linked in: button psmouse binfmt_misc rfcomm l2cap bluetooth nfs i915 drm nfsd exportfs lockd sunrpc ppdev acpi_cpufreq cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table tc1100_wmi pcc_acpi sony_acpi dev_acpi video battery container sbs i2c_ec dock ac asus_acpi backlight nls_utf8 ntfs ext3 jbd ext2 mbcache ipv6 eeprom lm90 i2c_i801 i2c_core sbp2 parport_pc lp parport fuse joydev snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss pcmcia snd_seq_midi snd_rawmidi ipw3945 xpad snd_seq_midi_event tifm_7xx1 ieee80211 ieee80211_crypt snd_seq tifm_core iTCO_wdt iTCO_vendor_support snd_timer snd_seq_device serio_raw yenta_socket rsrc_nonstatic pcmcia_core sdhci mmc_core snd soundcore shpchp pci_hotplug intel_agp snd_page_alloc af_packet tsdev evdev reiserfs sd_mod usbhid hid sg sr_mod cdrom generic e1000 ehci_hcd ahci ohci1394 ieee1394 uhci_hcd ata_piix ata_generic libata scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor vesafb cfbcopyarea cfbimgblt cfbfillrect capability commoncap
[  488.127400] Pid: 37, comm: kacpi_notify Not tainted 2.6.20-16-generic #2
[  488.127404] RIP: 0010:[<ffffffff8849059e>]  [<ffffffff8849059e>] :video:acpi_video_device_notify+0x77/0x10a
[  488.127415] RSP: 0000:ffff8100baee9de0  EFLAGS: 00010246
[  488.127419] RAX: 0000000000000005 RBX: 0000000000000086 RCX: 00000000000000ff
[  488.127422] RDX: 00000000000019e5 RSI: 0000000000000000 RDI: 0000000000000000
[  488.127427] RBP: ffff8100b1589d00 R08: 0000000000000000 R09: 0000000000000000
[  488.127431] R10: 00000000000000ff R11: 0000000000000000 R12: ffff8100bb4c4800
[  488.127436] R13: 0000000000000282 R14: ffffffff8035cd23 R15: ffff8100bb4dd700
[  488.127441] FS:  0000000000000000(0000) GS:ffffffff8054e000(0000) knlGS:0000000000000000
[  488.127445] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
[  488.127449] CR2: 0000000000000004 CR3: 000000005c82e000 CR4: 00000000000006e0
[  488.127455] Process kacpi_notify (pid: 37, threadinfo ffff8100baee8000, task ffff8100baed6040)
[  488.127458] Stack:  ffff8100baed6040 ffff8100b2fd37a0 00000000000019e5 ffff810033332f50
[  488.127468]  ffff8100bb4dd6c0 ffff8100ae4c7a90 0000000000000282 ffffffff80362977
[  488.127475]  ffff8100ae4c7a80 ffffffff8035cd46 ffff8100ae4c7a98 ffffffff8024fa28
[  488.127482] Call Trace:
[  488.127506]  [<ffffffff80362977>] acpi_ev_notify_dispatch+0x57/0x60
[  488.127515]  [<ffffffff8035cd46>] acpi_os_execute_notify+0x23/0x2c
[  488.127523]  [<ffffffff8024fa28>] run_workqueue+0xa8/0x160
[  488.127536]  [<ffffffff8024be00>] worker_thread+0x0/0x190
[  488.127543]  [<ffffffff802a3170>] keventd_create_kthread+0x0/0x90
[  488.127550]  [<ffffffff8024bf4b>] worker_thread+0x14b/0x190
[  488.127560]  [<ffffffff8028dca0>] default_wake_function+0x0/0x10
[  488.127575]  [<ffffffff802a3170>] keventd_create_kthread+0x0/0x90
[  488.127594]  [<ffffffff8024be00>] worker_thread+0x0/0x190
[  488.127600]  [<ffffffff80233fa9>] kthread+0xd9/0x120
[  488.127621]  [<ffffffff80261ec8>] child_rip+0xa/0x12
[  488.127630]  [<ffffffff802a3170>] keventd_create_kthread+0x0/0x90
[  488.127644]  [<ffffffff8031a360>] dummy_d_instantiate+0x0/0x10
[  488.127664]  [<ffffffff80233ed0>] kthread+0x0/0x120
[  488.127671]  [<ffffffff80261ebe>] child_rip+0x0/0x12
[  488.127682] 
[  488.127684] 
[  488.127685] Code: 45 8b 6b 04 eb 2e 49 8b 43 08 8b 04 38 39 c8 7d 05 39 d0 0f 
[  488.127703] RIP  [<ffffffff8849059e>] :video:acpi_video_device_notify+0x77/0x10a
[  488.127712]  RSP <ffff8100baee9de0>
[  488.127715] CR2: 0000000000000004
[  488.127718]  
```

Might there be a bug in the ACPI video somewhere that is preventing us from using the Fn+arrow key brightness controls?

---

### Post by kpictjl on 2007-09-18
I'm on a Gateway 200 ARC laptop with Feisty.  My Fn-up/down arrows cause the entire screen to wig-out/go garbled.  I have to do a hard reboot to get the computer back.  Ctrl-alt-backspace doesn't kill X.

---

### Post by chocolatetoothpaste on 2007-09-23
I have the same issue.  I press fn+down-arrow, sometimes it dims, sometimes not.  If i press it repeatedly, it jumps around unpredictably, but only between 2 brightnesses.  I'm running feisty 7.04 on a gateway mt3705.  This is really the last problem I want to fix on my laptop, everything else I have gotten to work!

---

### Post by yoshic on 2007-10-24
Hi guys, here the same probrelm with feisty, the display does not show correctly and the Fn + Arrow Keys does not work, btw i'm using a Gateway 6941mx. Tonight i'll try with gusty to see what happens.

---

### Post by kpictjl on 2007-10-24
> **kpictjl said:**
> I'm on a Gateway 200 ARC laptop with Feisty.  My Fn-up/down arrows cause the entire screen to wig-out/go garbled.  I have to do a hard reboot to get the computer back.  Ctrl-alt-backspace doesn't kill X.
I installed 7.10 and I still have this same problem.

---

### Post by malfist on 2007-10-24
On the Gateway C-140x, the dim and brighten buttons do nothing. It shows the icon and acts as if it is dimming but nothing happens to the screen, it stays at full bright. Gusty

---

### Post by yoshic on 2007-10-25
hi guys! like [kpictjl]("http://ubuntuforums.org/member.php?u=172397") said still the same issue in gusty, but recently i installed vista on my laptop and vista has the same problem with the display if the driver is not installed correctly, in linux the works well when the system is loading, bo¿ut once x loads it stops working, maybe we've had to look in the drivers if there is a solution.

I like a lot use ubuntu on my lap, everything works well, except for that:(

---

### Post by icechen1 on 2007-10-27
> **treesurf said:**
> I have a similar problem with my Gateway NX570.  The audio keys work just fine but the brightness keys only toggle between high and low, with no intermediate steps, and sometimes the mouse pointer does the dissappearing act briefly.

Same here with a Gateway MX6214.
This is serious :[http://bugzilla.gnome.org/show_bug.cgi?id=469748](http://bugzilla.gnome.org/show_bug.cgi?id=469748) BUG SPOTTED
Ubuntu 7.10 Here

---

### Post by kpictjl on 2007-11-06
Here's a new observable.  I can adjust the brightness during boot!   While I can see the grub menu I can use the fn+up/down arrows and I get the little "pie-chart" brightness display.  This also works while I see the Ubuntu name/progress bar.  However, once I get to the logon window the same function keys hose the display.

---

### Post by Shoadow56 on 2008-02-29
My Gateway MT 3705 Laptop didn't work in 7.04, but was automatically fixed in 7.10 without any updates. YAY!

---

