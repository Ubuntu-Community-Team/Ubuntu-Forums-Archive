---
title: "Ubuntu 16.04LTS on Lenovo Ideapad Yoga 3 11 - Boot-time Kernel Panics"
date: 2016-10-11
forum: Hardware
---

### Post by atomp on 2016-10-11
Hello all,

Having spent a few days on this I've reached the point of asking for some help.

I have a Lenovo Ideapd Yoga 3 11 and am attempting to run Ubuntu on it. I'm running into a problem with seemingly random and very difficult to reliably reproduce kernel panics on boot. I've tried a variety of solutions so far:

[LIST]
[*]Reinstalled Ubuntu
[*]Tried both UEFI and Legacy Boot Options
[*]Nuked the existing Win8 install and given over the whole drive to Ubuntu (second install)
[*]Run multiple Memtest passes - 7 or 8 full test passes over the course of two sessions
[*]Opened the machine up and re-seated what I could (the M.2 SSD)
[*]Confirmed the health of the M.2 SSD with SMART
[*]Tried a variety of kernels ranging from the default 16.04LTS kernel to the latest 4.8.0 and 4.8.1 releases
[*]Used the Intel Graphics Driver Updater tool to install up to date iGPU drivers on all kernels used, tested before and after
[*]Updated the BIOS to the latest version (whilst the Win8 install still existed)
[*]Fiddled with every BIOS setting available to me (Disabling SecureBoot, Legacy Support, etc)
[*]Tested the laptop under various conditions (on AC, on Battery, Before Sleep, After Sleep) in an attempt to improve reproduce-ability
[/LIST]

I've been bashing my head against this particular wall for some days now to little avail. Is there anything that anyone can see that I haven't done or that could help explain these kernel panics? It's irritatingly difficult to reproduce reliably, but reboot often enough and the problem always returns.

Below is a copy of the log of the latest of said kernel panics. Now the initial BUG marker seems to be a bad pointer, which would (in my mind, although I'm no kernel dev) indicate a memory problem, however I've checked the memory and it's proven to be fine. Anyone with more knowledge of kernel panic debugging is more than welcome to chip in. Any help or suggestions would be very much appreciated.

Thanks for reading,
Tom.

(Full kern.log from the affected machine is here: [https://www.dropbox.com/s/7vy8aw070sf1p13/kern.log?dl=0](https://www.dropbox.com/s/7vy8aw070sf1p13/kern.log?dl=0)) 

```

Oct 11 00:52:49 yoga kernel: [   11.909759] BUG: unable to handle kernel NULL pointer dereference at 0000000000000018
Oct 11 00:52:49 yoga kernel: [   11.910960] IP: [<ffffffff814a8455>] acpi_ns_walk_namespace+0x4b/0x193
Oct 11 00:52:49 yoga kernel: [   11.912161] PGD 0 
Oct 11 00:52:49 yoga kernel: [   11.913345] Oops: 0000 [#1] SMP 
Oct 11 00:52:49 yoga kernel: [   11.914524] Modules linked in: snd_hda_codec_realtek(+) snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep irqbypass crct10dif_pclmul crc32_pclmul snd_pcm aesni_intel snd_seq_midi aes_x86_64 snd_seq_midi_event arc4 lrw gf128mul glue_helper iwlmvm ablk_helper cryptd mac80211 snd_rawmidi input_leds mac_hid uvcvideo iwlwifi videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 serio_raw snd_seq videobuf2_core cfg80211 snd_seq_device btusb v4l2_common btrtl snd_timer btbcm btintel videodev lpc_ich hid_multitouch media bluetooth snd mei_me shpchp mei processor_thermal_device int340x_thermal_zone soundcore intel_soc_dts_iosf parport_pc ppdev lp parport autofs4 usbhid hid rtsx_usb_sdmmc rtsx_usb i915 video i2c_algo_bit drm_kms_helper psmouse ahci libahci syscopyarea sysfillrect sysimgblt fb_sys_fops drm
Oct 11 00:52:49 yoga kernel: [   11.920080] CPU: 0 PID: 438 Comm: modprobe Not tainted 4.4.0-42-generic #62-Ubuntu
Oct 11 00:52:49 yoga kernel: [   11.921492] Hardware name: LENOVO 80J8/Paganini, BIOS B8CN32WW(V2.10) 10/28/2015
Oct 11 00:52:49 yoga kernel: [   11.922909] task: ffff880251a36040 ti: ffff88009ab78000 task.ti: ffff88009ab78000
Oct 11 00:52:49 yoga kernel: [   11.924330] RIP: 0010:[<ffffffff814a8455>]  [<ffffffff814a8455>] acpi_ns_walk_namespace+0x4b/0x193
Oct 11 00:52:49 yoga kernel: [   11.925771] RSP: 0018:ffff88009ab7b9e8  EFLAGS: 00010202
Oct 11 00:52:49 yoga kernel: [   11.927205] RAX: ffff88009ab7ba58 RBX: 0000000000000001 RCX: 0000000000000001
Oct 11 00:52:49 yoga kernel: [   11.928644] RDX: 00000000ffffffff RSI: 0000000000000000 RDI: 0000000000000006
Oct 11 00:52:49 yoga kernel: [   11.930073] RBP: ffff88009ab7ba38 R08: ffffffff814a8a52 R09: 0000000000000000
Oct 11 00:52:49 yoga kernel: [   11.931501] R10: 0000000000000001 R11: ffff88009ae25960 R12: 0000000000000001
Oct 11 00:52:49 yoga kernel: [   11.932928] R13: ffff88009aad2000 R14: 0000000000000000 R15: 0000000000000000
Oct 11 00:52:49 yoga kernel: [   11.934353] FS:  00007f2860c2e700(0000) GS:ffff88025ec00000(0000) knlGS:0000000000000000
Oct 11 00:52:49 yoga kernel: [   11.935787] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Oct 11 00:52:49 yoga kernel: [   11.937220] CR2: 0000000000000018 CR3: 0000000253514000 CR4: 00000000003406f0
Oct 11 00:52:49 yoga kernel: [   11.938660] Stack:
Oct 11 00:52:49 yoga kernel: [   11.940086]  0000000000000000 0000000000000000 ffffffff814a8a52 00000001ffffffff
Oct 11 00:52:49 yoga kernel: [   11.941542]  0000000000000006 0000000000000000 0000000000000000 ffff88009aad2000
Oct 11 00:52:49 yoga kernel: [   11.942991]  ffff88009b1c5000 ffffffffc07c6670 ffff88009ab7ba80 ffffffff814a8958
Oct 11 00:52:49 yoga kernel: [   11.944437] Call Trace:
Oct 11 00:52:49 yoga kernel: [   11.945869]  [<ffffffff814a8a52>] ? acpi_walk_namespace+0xd0/0xd0
Oct 11 00:52:49 yoga kernel: [   11.947314]  [<ffffffff814a8958>] acpi_get_devices+0x6a/0x94
Oct 11 00:52:49 yoga kernel: [   11.948755]  [<ffffffffc07bd350>] ? alc_fixup_disable_aamix+0x20/0x20 [snd_hda_codec_realtek]
Oct 11 00:52:49 yoga kernel: [   11.950210]  [<ffffffffc07c17dc>] hda_fixup_thinkpad_acpi+0xbc/0x1f0 [snd_hda_codec_realtek]
Oct 11 00:52:49 yoga kernel: [   11.951660]  [<ffffffffc06cb985>] apply_fixup+0x1b5/0x2b0 [snd_hda_codec]
Oct 11 00:52:49 yoga kernel: [   11.953094]  [<ffffffffc06cbaa2>] snd_hda_apply_fixup+0x22/0x30 [snd_hda_codec]
Oct 11 00:52:49 yoga kernel: [   11.954522]  [<ffffffffc07c2883>] patch_alc269+0x223/0x5a0 [snd_hda_codec_realtek]
Oct 11 00:52:49 yoga kernel: [   11.955951]  [<ffffffffc06c445b>] hda_codec_driver_probe+0x6b/0x100 [snd_hda_codec]
Oct 11 00:52:49 yoga kernel: [   11.957382]  [<ffffffff81555072>] driver_probe_device+0x222/0x4a0
Oct 11 00:52:49 yoga kernel: [   11.958809]  [<ffffffff81555374>] __driver_attach+0x84/0x90
Oct 11 00:52:49 yoga kernel: [   11.960241]  [<ffffffff815552f0>] ? driver_probe_device+0x4a0/0x4a0
Oct 11 00:52:49 yoga kernel: [   11.961674]  [<ffffffff81552c9c>] bus_for_each_dev+0x6c/0xc0
Oct 11 00:52:49 yoga kernel: [   11.963107]  [<ffffffff8155482e>] driver_attach+0x1e/0x20
Oct 11 00:52:49 yoga kernel: [   11.964539]  [<ffffffff8155436b>] bus_add_driver+0x1eb/0x280
Oct 11 00:52:49 yoga kernel: [   11.965965]  [<ffffffffc06b8000>] ? 0xffffffffc06b8000
Oct 11 00:52:49 yoga kernel: [   11.967392]  [<ffffffff81555c80>] driver_register+0x60/0xe0
Oct 11 00:52:49 yoga kernel: [   11.968824]  [<ffffffffc06c40da>] __hda_codec_driver_register+0x5a/0x60 [snd_hda_codec]
Oct 11 00:52:49 yoga kernel: [   11.970270]  [<ffffffffc06b801e>] realtek_driver_init+0x1e/0x1000 [snd_hda_codec_realtek]
Oct 11 00:52:49 yoga kernel: [   11.971720]  [<ffffffff81002123>] do_one_initcall+0xb3/0x200
Oct 11 00:52:49 yoga kernel: [   11.973168]  [<ffffffff811cfa31>] ? __vunmap+0x91/0xe0
Oct 11 00:52:49 yoga kernel: [   11.974608]  [<ffffffff811ebbe3>] ? kmem_cache_alloc_trace+0x183/0x1f0
Oct 11 00:52:49 yoga kernel: [   11.976051]  [<ffffffff811ec9da>] ? kfree+0x13a/0x150
Oct 11 00:52:49 yoga kernel: [   11.977492]  [<ffffffff8118caa3>] do_init_module+0x5f/0x1cf
Oct 11 00:52:49 yoga kernel: [   11.978935]  [<ffffffff8110a2ff>] load_module+0x166f/0x1c10
Oct 11 00:52:49 yoga kernel: [   11.980377]  [<ffffffff811068a0>] ? __symbol_put+0x60/0x60
Oct 11 00:52:49 yoga kernel: [   11.981819]  [<ffffffff81213740>] ? kernel_read+0x50/0x80
Oct 11 00:52:49 yoga kernel: [   11.983260]  [<ffffffff8110aae4>] SYSC_finit_module+0xb4/0xe0
Oct 11 00:52:49 yoga kernel: [   11.984697]  [<ffffffff8110ab2e>] SyS_finit_module+0xe/0x10
Oct 11 00:52:49 yoga kernel: [   11.986123]  [<ffffffff818318b2>] entry_SYSCALL_64_fastpath+0x16/0x71
Oct 11 00:52:49 yoga kernel: [   11.987539] Code: 28 48 ff c6 4c 0f 44 35 62 6d d3 00 89 7d d0 89 55 c8 45 31 ff 89 4d cc 4c 89 45 c0 41 83 e4 01 4c 89 4d b8 c7 45 d4 00 00 00 00 <4d> 8b 6e 18 85 db 0f 84 ff 00 00 00 4d 85 ed 0f 84 f6 00 00 00 
Oct 11 00:52:49 yoga kernel: [   11.989146] RIP  [<ffffffff814a8455>] acpi_ns_walk_namespace+0x4b/0x193
Oct 11 00:52:49 yoga kernel: [   11.990639]  RSP <ffff88009ab7b9e8>
Oct 11 00:52:49 yoga kernel: [   11.992111] CR2: 0000000000000018
Oct 11 00:52:49 yoga kernel: [   11.993572] ---[ end trace de8967acef88c9ee ]---

```

---

### Post by atomp on 2016-10-13
Update:

I've attempted to blacklist the snd_hda_codec drivers, which didn't work.
I've also swapped out the SSD for a brand new one, with the same result.
I also installed Manjaro to test if it was an Ubuntu specific issue, which also had no effect in stopping the kernel panics.

I've come to the conclusion that this is either a new bug in the Linux Kernel that has yet to be fixed in the 4.x branch, or there's a package that both Ubuntu and Manjaro are pulling in when updating. Or potentially, the worst options, a very deep rooted hardware fault probably on the motherboard, I'm guessing static discharge. Whoever had it open before me didn't seem particularly careful, the warranty sticker was torn up to high hell and the copper CPU heatsink was covered in fingerprints, which doesn't instil confidence especially as this was supposedly an official Lenovo refurbished item.

My next course of action before the final option of RMA is to try using an older Ubuntu version like 15.10 which might not pull down the packages or kernel that causes the issue. (If it is indeed software).

Again, any help would be welcome.

---

### Post by das-jott on 2017-01-06
The same here. Already [filed a bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1634881") which importance was changed to "high", but anyway there seems to be no interest to fix it. I filed it in October and still no progress, not even an answer, nothing.

You can click on "affects me" for the bug, maybe that does something.

Really annoying as Ubuntu from 16.04 on is supporting the internal Wi-Fi, so I wouldn't have to use that USB WiFi thingy...

---

### Post by atomp on 2017-01-06
I'll give my final update:

I ran out of possible solutions and I gave up in the end, RMA'd it and bought a Dell Inspiron 13 5000 instead. (A pretty good price refurbished and discounted).

Sorry I can't be of any more help, best of luck with a solution, the Ideapad Yoga 3 11 does have a really good screen for the size.

---

### Post by mörgæs on 2017-01-06
Have you tried a live boot of 16.10 and/or 17.04 (development version)?

---

### Post by das-jott on 2017-01-17
As you can see in the bugreport I filed, I tried a development version as well.
And boot is what already fails, so no chance to even differ between live or install...

---

### Post by mörgæs on 2017-01-18
> **das-jott said:**
> As you can see in the bugreport I filed

Where? The link in #3 does not lead to a report.

---

### Post by das-jott on 2017-01-18
I am sorry. What I wrote was wrong. The bug appears on both: booting to live system or preparing to install. Both freeze on splash screen.
And you are right, funnily the link does not go to the bug I filed.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1634881](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1634881)

This was supposed to be the link target.

---

### Post by mörgæs on 2017-01-19
But have you tried the development version as of today?

---

### Post by das-jott on 2017-01-19
> **mörgæs said:**
> But have you tried the development version as of today?

I tried the 14.04.5 by USB a several times. I get a "general protection fault 0000 #1" there, before it crashes.

I tried several kernels last night and it seems that the problem occurs from kernel v4.2 upwards. It simply refuses to boot.

Will get the most recent dev version ... I would bet it doesn't work either.

---

### Post by das-jott on 2017-01-20
The most recent version of Ubuntu does also freeze. Of course.
It freezes randomly. I tried nosmp as bootparam, as it seemed to cause that general protection fault... no difference.

So currently, the last version I can use is 14.04. Great. All other versions crash on boot. And Canonical does not care.
The pity is: Kernel 4.2 upwards contains drivers for the internal wifi, so I didn't have to use that bloody usb wifi thingy anymore...

I think, there is no interest to make Lenovo yoga 3 notebooks work with Ubuntu. Obviously not.

---

### Post by mörgæs on 2017-01-27
Has the temper cooled down? 

A bug report is fine but it should first of all contain information for the daily build of 17.04. Old releases are... well, old. It's not clear which versions you are testing at the end of the report.

After you have updated the report I suggest that you discuss the case with the people in the [development forum]("https://ubuntuforums.org/forumdisplay.php?f=427"). Good luck.

---

