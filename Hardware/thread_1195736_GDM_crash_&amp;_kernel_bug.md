---
title: "GDM crash &amp; kernel bug"
date: 2009-06-24
forum: Hardware
---

### Post by Iesos on 2009-06-24
At boot there is a ~60% chance that when gdm starts the boot process crashes and says:

```

Jun 24 11:04:48 unimatrix4 kernel: [   53.569929] ------------[ cut here ]------------
Jun 24 11:04:48 unimatrix4 kernel: [   53.577802] kernel BUG at /build/buildd/linux-2.6.28/mm/vmalloc.c:79!
Jun 24 11:04:48 unimatrix4 kernel: [   53.577802] invalid opcode: 0000 [#1] SMP 
Jun 24 11:04:48 unimatrix4 kernel: [   53.577802] last sysfs file: /sys/devices/virtual/vc/vcsa7/dev
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802] Dumping ftrace buffer:
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]    (ftrace buffer empty)
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802] Modules linked in: aes_i586 aes_generic cbc dm_crypt snd_cs4236 snd_opl3_lib snd_hwdep snd_cs4236_lib snd_wss_lib snd_mp
u401_uart lp 3c59x mii ppdev pcmcia snd_pcsp snd_cs46xx snd_pcm_oss gameport snd_mixer_oss snd_ac97_codec ac97_bus snd_pcm snd_seq_dummy snd_seq_oss thinkpad_acpi snd_seq
_midi led_class nvram snd_rawmidi snd_seq_midi_event snd_seq nsc_ircc snd_timer snd_seq_device intel_agp snd parport_pc video psmouse soundcore parport output i2c_piix4 a
gpgart irda yenta_socket serio_raw snd_page_alloc crc_ccitt shpchp rsrc_nonstatic pcmcia_core floppy vesafb fbcon tileblit font bitblit softcursor
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802] 
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802] Pid: 3305, comm: Xorg Not tainted (2.6.28-13-server #44-Ubuntu) 26454EG
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802] EIP: 0060:[<c01b1578>] EFLAGS: 00210212 CPU: 0
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802] EIP is at vunmap_page_range+0xa8/0xb0
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802] EAX: 00ecc000 EBX: d60615c0 ECX: 008e0098 EDX: 008e0098
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802] ESI: 000ffac0 EDI: 00ecc000 EBP: d5ca5d90 ESP: d5ca5d7c
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802] Process Xorg (pid: 3305, ti=d5ca4000 task=d60a6480 task.ti=d5ca4000)
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802] Stack:
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  008e0098 d8dcafff d60615c0 000ffac0 d5ca5dd4 d5ca5db4 c01b1680 d5ca5da0
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  d5ca5dd8 d79ed5e0 d60615a0 000f8000 00000000 d5ca5e60 d5ca5de8 c01b20d3
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  00000000 c07ccdc0 c1309dc4 d7139e58 00000040 c1309da0 d8dcb000 00ecc000
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802] Call Trace:
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  [<c01b1680>] ? __purge_vmap_area_lazy+0x80/0x160
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  [<c01b20d3>] ? vm_unmap_aliases+0x123/0x130
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  [<c012b638>] ? change_page_attr_set_clr+0x168/0x390
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  [<c01cec79>] ? path_to_nameidata+0x19/0x50
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  [<c02cfb72>] ? kobject_get+0x12/0x20
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  [<c02b0d7a>] ? apparmor_capable+0x1a/0x60
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  [<c012bde0>] ? _set_memory_wb+0x40/0x50
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  [<c012a1ff>] ? ioremap_change_attr+0xf/0x50
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  [<c012cff9>] ? phys_mem_access_prot_allowed+0xb9/0x210
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  [<c01c47ad>] ? __dentry_open+0x19d/0x260
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  [<c0338d2e>] ? mmap_mem+0x9e/0x1b0
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  [<c01d1b59>] ? do_filp_open+0x1d9/0x7c0
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  [<c01adc38>] ? mmap_region+0x1d8/0x500
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  [<c028f9c7>] ? security_file_mmap+0x27/0x30
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  [<c01ae1c9>] ? do_mmap_pgoff+0x269/0x360
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  [<c010dddd>] ? sys_mmap2+0xad/0xc0
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  [<c0109eef>] ? sysenter_do_call+0x12/0x2f
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802]  [<c0500000>] ? piix_init_one+0x26e/0x3ee
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802] Code: 90 25 98 0f 00 00 81 e2 00 f0 ff ff 09 c2 74 ab 89 d8 e8 dc 4a ff ff 3b 75 ec 75 af 8d b4 26 00 00 00 00 83 c4 08 
5b 5e 5f 5d c3 <0f> 0b eb fe 8d 74 26 00 55 01 c2 89 e5 e8 46 ff ff ff e8 d1 d6 
Jun 24 11:04:49 unimatrix4 kernel: [   53.577802] EIP: [<c01b1578>] vunmap_page_range+0xa8/0xb0 SS:ESP 0068:d5ca5d7c
Jun 24 11:04:49 unimatrix4 kernel: [   54.190493] ---[ end trace 3b26dadb67cf35b2 ]---
```

It is *very* annoying. Is this something that is for the ubuntu people to handle or should I hand it over to kernel people? I had no problem like this in 8.10 just came when I upgraded to 9.04 and the problem is there with 2.6.28-11 and 2.6.28-13 (-server). Or is there just someone out there with a solution?

---

