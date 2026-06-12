---
title: "wlan dies then system - preempt?"
date: 2005-06-03
forum: Hardware &amp; Laptops
---

### Post by reid on 2005-06-03
Hi,
My wireless network (using ndiswrapper 1.1-1 from hoary repository) stops working, and then the system stops responding, one piece at a time.  The second thing to go is the keyboard, then the mouse buttons, then finally the mouse movement.  Here is my /etc/var/messages from the point of weirdness:

```
Jun  2 20:52:25 localhost kernel: e0d39cd7
Jun  2 20:52:25 localhost kernel: PREEMPT 
Jun  2 20:52:25 localhost kernel: Modules linked in: ipt_TCPMSS ipt_limit ip_nat_irc ip_nat_ftp iptable_mangle ipt_LOG ipt_MASQUERADE iptable_nat ipt_TOS ipt_REJECT ip_conntrack_irc ip_conntrack_ftp ipt_state ip_conntrack iptable_filter ip_tables nls_iso8859_1 nls_cp437 vfat fat proc_intf cpufreq_powersave cpufreq_userspace cpufreq_ondemand freq_table video battery container button pcc_acpi sony_acpi ac ipv6 sd_mod af_packet usb_storage scsi_mod via_velocity crc_ccitt 3c59x shpchp pci_hotplug snd_intel8x0 snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc ehci_hcd ohci_hcd i2c_nforce2 i2c_core nvidia_agp floppy pcspkr rtc md dm_mod capability commoncap nvidia tsdev agpgart evdev ndiswrapper usbcore psmouse mousedev parport_pc lp parport ide_cd cdrom reiserfs ext3 jbd ide_generic ide_disk amd74xx ide_core unix thermal processor fan fbcon font bitblit vesafb cfbcopyarea cfbimgblt cfbfillrect
Jun  2 20:52:25 localhost kernel: CPU:    0
Jun  2 20:52:25 localhost kernel: EIP:    0060:[pg0+547019991/1070015488]    Tainted: P      VLI
Jun  2 20:52:25 localhost kernel: EFLAGS: 00010286   (2.6.10-5-386) 
Jun  2 20:52:25 localhost kernel: EIP is at 0xe0d39cd7
Jun  2 20:52:25 localhost kernel: eax: 00000000   ebx: 00000000   ecx: e0d62340   edx: 002d5731
Jun  2 20:52:25 localhost kernel: esi: dd140000   edi: dd14088c   ebp: c14f9e8c   esp: c14f9e7c
Jun  2 20:52:25 localhost kernel: ds: 007b   es: 007b   ss: 0068
Jun  2 20:52:25 localhost kernel: Process events/0 (pid: 3, threadinfo=c14f8000 task=dfb87020)
Jun  2 20:52:25 localhost kernel: Stack: c14f9eb0 00000000 dc05c000 e0d62340 c14f9ea8 e0d2ddc9 dd140000 c14f9ea4 
Jun  2 20:52:25 localhost kernel:        dd140000 00000002 00000000 c14f9ed0 e0d3086b c14f9eec c14f9eec e0d30c1d 
Jun  2 20:52:25 localhost kernel:        dd140000 00000002 dd7dbd60 dd1405e0 00000002 c14f9ef4 e0d24a5c dd140000 
Jun  2 20:52:25 localhost kernel: Call Trace:
Jun  2 20:52:25 localhost kernel:  [pg0+544839247/1070015488] NdisAcquireSpinLock+0x0/0x3b [ndiswrapper]
Jun  2 20:52:25 localhost kernel:  [pg0+544845140/1070015488] ndis_worker+0xe0/0x1c3 [ndiswrapper]
Jun  2 20:52:25 localhost kernel:  [worker_thread+412/554] worker_thread+0x19c/0x22a
Jun  2 20:52:25 localhost kernel:  [pg0+544844916/1070015488] ndis_worker+0x0/0x1c3 [ndiswrapper]
Jun  2 20:52:25 localhost kernel:  [default_wake_function+0/18] default_wake_function+0x0/0x12
Jun  2 20:52:25 localhost kernel:  [default_wake_function+0/18] default_wake_function+0x0/0x12
Jun  2 20:52:25 localhost kernel:  [worker_thread+0/554] worker_thread+0x0/0x22a
Jun  2 20:52:25 localhost kernel:  [kthread+109/151] kthread+0x6d/0x97
Jun  2 20:52:25 localhost kernel:  [kthread+0/151] kthread+0x0/0x97
Jun  2 20:52:25 localhost kernel:  [kernel_thread_helper+5/11] kernel_thread_helper+0x5/0xb
Jun  2 20:52:25 localhost kernel: Code: fc 05 bc 00 00 00 50 e8 12 fa ff ff 85 c0 0f 85 4c 01 00 00 8b 45 fc 05 bc 00 00 00 50 e8 f0 f9 ff ff 89 45 f8 8b 45 f8 8b 40 08 <0f> b7 40 08 85 c0 74 06 83 65 f0 00 eb 17 68 4e 01 00 00 68 32 
Jun  2 20:52:25 localhost kernel:  <6>note: events/0[3] exited with preempt_count 1
```
If it makes a difference, I am sharing my connection with an XP box through firestarter.
What is this darn PREEMPT anyway?

Any help is appreciated!

---

### Post by az on 2005-06-03
I had a lot of problems like this with a usb wlan device.  

On one system, I fixed the problem by using the very newest version of ndisrapper (you can easily compile it using your linux-headers).  Unfortunately, on another machine, the newer version does not work.  I think it is an upstream (ndiswrapper) problem.

Preemt is a kernel feature which is a way of solving problems involved with multitasking.  On older kernels without preemt, you can get lockups and stalls when two processes depend on each other and are each waiting for the other to finish before moving along.

You could recompile your kernel without preempt, but that would not really be desireable.

---

### Post by reid on 2005-06-08
Thanks azz, that did it - so far at least!
It usually would crash during heavy internet traffic and I have made it past that hurdle.

---

